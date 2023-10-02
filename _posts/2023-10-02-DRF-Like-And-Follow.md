---
layout: post
title: How to set Like and Follow on DRF?
date: 2023-10-02 20:10:20 +0900
description: How to set Like and Follow on DRF? # Add post description (optional)
img: likefollow.jpeg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [DRF, Like, Follow]
---

To implement the "like" and "follow" functions between users for posts using serializers in Django Rest Framework (DRF), you will need to create serializers, views, and models for both actions. I'll provide a step-by-step guide on how to do this:

**1. Define your models:**

You'll need models for users, posts, likes, and follows. Here's a basic example:

```python
from django.db import models
from django.contrib.auth.models import User

class Post(models.Model):
    user = models.ForeignKey(User, on_delete=models.CASCADE)
    content = models.TextField()
    created_at = models.DateTimeField(auto_now_add=True)

class Like(models.Model):
    user = models.ForeignKey(User, on_delete=models.CASCADE)
    post = models.ForeignKey(Post, on_delete=models.CASCADE)
    created_at = models.DateTimeField(auto_now_add=True)

class Follow(models.Model):
    follower = models.ForeignKey(User, related_name='following', on_delete=models.CASCADE)
    following = models.ForeignKey(User, related_name='followers', on_delete=models.CASCADE)
```

**2. Create serializers:**

You need serializers to serialize and deserialize data for your API. You can use DRF serializers for this. Here's how you can define serializers:

```python
from rest_framework import serializers
from .models import Post, Like, Follow

class PostSerializer(serializers.ModelSerializer):
    class Meta:
        model = Post
        fields = '__all__'

class LikeSerializer(serializers.ModelSerializer):
    class Meta:
        model = Like
        fields = '__all__'

class FollowSerializer(serializers.ModelSerializer):
    class Meta:
        model = Follow
        fields = '__all__'
```

**3. Create views:**

You'll need views to handle HTTP requests and interact with your models. You can use DRF's `ViewSet` and `ModelViewSet` classes. Here's how you can define views for posts, likes, and follows:

```python
from rest_framework import viewsets
from .models import Post, Like, Follow
from .serializers import PostSerializer, LikeSerializer, FollowSerializer

class PostViewSet(viewsets.ModelViewSet):
    queryset = Post.objects.all()
    serializer_class = PostSerializer

class LikeViewSet(viewsets.ModelViewSet):
    queryset = Like.objects.all()
    serializer_class = LikeSerializer

class FollowViewSet(viewsets.ModelViewSet):
    queryset = Follow.objects.all()
    serializer_class = FollowSerializer
```

**4. Configure URLs:**

You need to configure URLs to map the views to specific endpoints. Here's an example `urls.py` configuration:

```python
from rest_framework import routers
from django.urls import path, include
from . import views

router = routers.DefaultRouter()
router.register(r'posts', views.PostViewSet)
router.register(r'likes', views.LikeViewSet)
router.register(r'follows', views.FollowViewSet)

urlpatterns = [
    path('', include(router.urls)),
]
```

**5. Implement Like and Follow functionality in views:**

To implement the "like" and "follow" functionality, you need to add custom logic in your views. For example, to implement "liking" a post, you can override the `create` and `destroy` methods in your `LikeViewSet`:

```python
from rest_framework import status
from rest_framework.response import Response
from rest_framework.decorators import action

class LikeViewSet(viewsets.ModelViewSet):
    queryset = Like.objects.all()
    serializer_class = LikeSerializer

    @action(detail=True, methods=['POST'])
    def like_post(self, request, pk=None):
        post = Post.objects.get(pk=pk)
        like, created = Like.objects.get_or_create(user=request.user, post=post)
        if not created:
            like.delete()
        return Response(status=status.HTTP_204_NO_CONTENT)
```

To implement "following" a user, you can similarly add custom logic in your `FollowViewSet`:

```python
class FollowViewSet(viewsets.ModelViewSet):
    queryset = Follow.objects.all()
    serializer_class = FollowSerializer

    @action(detail=True, methods=['POST'])
    def follow_user(self, request, pk=None):
        user_to_follow = User.objects.get(pk=pk)
        follow, created = Follow.objects.get_or_create(follower=request.user, following=user_to_follow)
        if not created:
            follow.delete()
        return Response(status=status.HTTP_204_NO_CONTENT)
```

With this setup, you can now use the `/likes/like_post/` and `/follows/follow_user/` endpoints to like and follow users, respectively.

Remember to configure your authentication and permission settings according to your project's requirements to ensure that only authenticated users can perform these actions. Also, consider adding error handling and validation as needed for your specific use case.