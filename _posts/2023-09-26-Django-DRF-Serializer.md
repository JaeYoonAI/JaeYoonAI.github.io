---
layout: post
title: DRF Serializer, Custom Models
date: 2023-09-26 20:10:20 +0900
description: DRF Serializer # Add post description (optional)
img: DRF12.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Django, DRF, Serializer, SerializerMethodField]
---

I spent four hours working on my assignment, and it was all because of a tiny error. That darn "SerializerMethodField" was the culprit. I finally found it was due to a missing pair of parentheses. Thanks to that, I couldn't finish my assignment.

<h1>What is Serializer?</h1>

In Django REST framework (DRF), a serializer is a key component used to convert complex data types, such as Django model instances or Python dictionaries, into a format that can be easily rendered into JSON, XML, or other content types. Serializers also handle deserialization, which means they can parse data in the requested format (usually JSON) and convert it back into complex types, after performing validation.

Serializers in DRF are very similar to Django forms. They provide a simple way to validate and convert complex data types, such as Django model instances, into a representation that can be easily rendered into JSON or other content types. Here's a detailed explanation of serializers with examples:

### Defining a Serializer

To create a serializer, you need to create a Python class that subclasses `serializers.Serializer` or `serializers.ModelSerializer`. 

1. **Using `serializers.Serializer`**:

   ```python
   from rest_framework import serializers

   class MySerializer(serializers.Serializer):
       name = serializers.CharField(max_length=100)
       age = serializers.IntegerField()
   ```

2. **Using `serializers.ModelSerializer`**:

   If you're working with Django models, you can use `ModelSerializer` for a more concise way of defining serializers:

   ```python
   from rest_framework import serializers
   from .models import MyModel

   class MyModelSerializer(serializers.ModelSerializer):
       class Meta:
           model = MyModel
           fields = ['name', 'age']
   ```

### Serializing Data

Now that you have a serializer, you can use it to convert your data into JSON or another format:

```python
# Using MySerializer
data = {'name': 'John', 'age': 30}
serializer = MySerializer(data=data)

# Check if the data is valid before serializing
if serializer.is_valid():
    serialized_data = serializer.data
else:
    errors = serializer.errors
```

### Deserializing Data

To deserialize data and convert it back into complex types, you can use the serializer:

```python
# Using MySerializer
data = {'name': 'Alice', 'age': 25}
serializer = MySerializer(data=data)

# Check if the data is valid before deserializing
if serializer.is_valid():
    instance = serializer.save()
else:
    errors = serializer.errors
```

### Model Serializer

When working with Django models, you can use `ModelSerializer` for a more concise way of defining serializers. This serializer automatically generates fields based on the model's fields:

```python
from rest_framework import serializers
from .models import MyModel

class MyModelSerializer(serializers.ModelSerializer):
    class Meta:
        model = MyModel
        fields = '__all__'
```

### Validation

Serializers perform validation by default. You can define validation rules by adding fields to the serializer and specifying their types and constraints. If the input data doesn't meet these rules, the serializer will raise a validation error.

For example, in the `MySerializer` example above, `name` is expected to be a string, and `age` is expected to be an integer. If the input data doesn't match these types, a validation error will be raised.

### Custom Validation

You can also define custom validation methods in your serializer class by creating methods like `validate_fieldname(self, value)`:

```python
class MySerializer(serializers.Serializer):
    name = serializers.CharField(max_length=100)
    age = serializers.IntegerField()

    def validate_age(self, value):
        if value < 0:
            raise serializers.ValidationError("Age cannot be negative.")
        return value
```

In this example, we have a custom validation for the `age` field to ensure it's not negative.

### Conclusion

In summary, serializers in DRF provide a powerful way to handle data serialization and deserialization, making it easy to work with complex data types like Django models in your API views. They also allow you to define validation rules and custom validation methods to ensure the data being processed meets your requirements.

<h1>SerializerMethodField</h1>

In Django REST framework (DRF), the `SerializerMethodField` is a versatile field that allows you to include custom, read-only fields in your serializers. These fields do not correspond to any specific model attribute but instead allow you to define custom logic to determine their values based on the data in the serialized object. It's a great way to include additional data or computed values in your API responses. Here's a detailed explanation of `SerializerMethodField` with examples:

### Definition of `SerializerMethodField`

To use `SerializerMethodField`, you typically include it in your serializer class and define a corresponding method that calculates the value of the field. The method name should match the name you specify for the field in the serializer.

```python
from rest_framework import serializers

class MySerializer(serializers.Serializer):
    regular_field = serializers.CharField()
    custom_field = serializers.SerializerMethodField()

    def get_custom_field(self, instance):
        # Your custom logic to calculate the value of custom_field
        return some_value_based_on_instance_data
```

### Example Usage

Let's consider an example where you have a model representing books, and you want to include a `rating` field in your API response that is not a direct attribute of the model. You can use `SerializerMethodField` for this purpose:

```python
# models.py
from django.db import models

class Book(models.Model):
    title = models.CharField(max_length=100)
    author = models.CharField(max_length=50)
    publication_year = models.PositiveIntegerField()

# serializers.py
from rest_framework import serializers
from .models import Book

class BookSerializer(serializers.ModelSerializer):
    average_rating = serializers.SerializerMethodField()

    def get_average_rating(self, instance):
        # Calculate and return the average rating for the book
        # (This is a simplified example, actual implementation would vary)
        ratings = instance.rating_set.all()
        if ratings:
            total_ratings = sum(rating.value for rating in ratings)
            return total_ratings / len(ratings)
        else:
            return None

    class Meta:
        model = Book
        fields = '__all__'
```

In this example, `average_rating` is a custom field added to the `BookSerializer` using `SerializerMethodField`. The `get_average_rating` method calculates the average rating based on the book's associated ratings.

### Usage in Views

When you use the `BookSerializer` in your views, the `average_rating` field will be included in the serialized representation of the book:

```python
from rest_framework import generics
from .models import Book
from .serializers import BookSerializer

class BookList(generics.ListCreateAPIView):
    queryset = Book.objects.all()
    serializer_class = BookSerializer
```

Now, when you retrieve a list of books using the `BookList` view, each book's `average_rating` will be included in the response.

```json
[
    {
        "id": 1,
        "title": "Sample Book 1",
        "author": "Author 1",
        "publication_year": 2020,
        "average_rating": 4.5
    },
    {
        "id": 2,
        "title": "Sample Book 2",
        "author": "Author 2",
        "publication_year": 2021,
        "average_rating": 3.8
    },
    ...
]
```

In summary, `SerializerMethodField` in DRF allows you to include custom, read-only fields in your serializers by defining methods that calculate their values. This is useful for including additional data or computed values in your API responses.