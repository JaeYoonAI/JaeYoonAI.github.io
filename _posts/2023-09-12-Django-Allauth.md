---
layout: post
title: Django Allauth
date: 2023-09-12 20:10:20 +0900
description: Django # Add post description (optional)
img: pydj.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Django, Python, Allauth]
---

Today, I spent all day implementing the member sign-up, login, and log-out functions for the team project.

Since the basic functions were implemented in the existing 'clon' data, I focused on additional things.


The things I would like to add are listed below.

1. Only valid emails are accepted.
2. Added 're_password' input text box to confirm password when signing up.
3. Change member status to 'activate' with email verification
4. Find password function.


1 and 2 were solved somewhat easily, but I tried to apply the remaining part because it was easier to use a library called 'Allauth' among the functions provided by Django.

However, since the table called 'user' was already in use, I ended up deleting and installing the 'user' application.


It took all day because there were too many errors, but in the end, I was able to edit the HTML of 'templates'.

I'm still lacking in email authentication, but I plan to spend some time tomorrow to complete it.

<h1> How to Install </h1>
Here are the steps on how to install Allauth in Django:

1. Install the `django-allauth` package using pip:

```
pip install django-allauth
```

2. Add `allauth` to your Django settings file's `INSTALLED_APPS` setting:

```
INSTALLED_APPS = [
    ...
    'allauth',
    'allauth.account',
    'allauth.socialaccount',
]
```

3. If you are using Django 3.2 or higher, you need to add the `SITE_ID` setting to your Django settings file:

```python
SITE_ID = 1
```

4. If you want to allow users to sign in with social media accounts, you need to add the following settings to your Django settings file:

```python
AUTHENTICATION_BACKENDS = [
    'django.contrib.auth.backends.ModelBackend',
    'allauth.account.auth_backends.AuthenticationBackend',
]

SOCIAL_AUTH_PROVIDERS = {
    'facebook': {
        'SCOPE': ['email', 'public_profile'],
    },
    'twitter': {
        'SCOPE': ['email', 'profile'],
    },
}
```

5. In your Django project's root directory, create a file called `urls.py` and add the following code:

```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('accounts/', include('allauth.urls')),
]
```

6. Run the following command to migrate your database:

```
python manage.py migrate
```

7. You can now start using Allauth in your Django project.

Here are some additional things to keep in mind when installing Allauth:

* If you are using a custom user model, you need to make sure that it inherits from `AbstractUser`.
* You can customize the behavior of Allauth by overriding the settings in your Django settings file.
* For more information on how to install and use Allauth, please refer to the Allauth documentation: https://django-allauth.readthedocs.io/en/stable/installation.html.


<h1> Caution </h1>
Here are some things to be careful about when using Allauth in Django:

* **Make sure you understand the security implications of using Allauth.** Allauth is a powerful tool, but it can also be used for malicious purposes. Make sure you are familiar with the security features of Allauth and how to configure them properly.
* **Be careful about which social media providers you allow users to sign in with.** Some social media providers have stricter privacy policies than others. Make sure you choose providers that are compatible with your own privacy policy.
* **Configure Allauth correctly.** Allauth comes with a lot of default settings. It is important to configure Allauth correctly for your specific needs. For example, you may need to change the default username and password policies.
* **Test Allauth thoroughly.** Before you deploy Allauth in production, make sure you test it thoroughly. This includes testing with different social media providers and different user types.
* **Keep Allauth up to date.** Allauth is constantly being updated with new features and security fixes. It is important to keep Allauth up to date to ensure that you are using the latest and most secure version.

Here are some additional cautions that have been mentioned in the Allauth documentation and issue tracker:

* The `TEMPLATE_CONTEXT_PROCESSORS` setting must be moved inside the `TEMPLATES` setting.
* When using Django 3.2, you may need to add the `SITE_ID` setting to your Django settings file.
* There is a known issue with the `django-allauth` package when installing it with pip v22.3. You can work around this issue by installing the package with pip v22.2 or lower.