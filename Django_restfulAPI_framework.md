# Django REST framework [Link](https://www.django-rest-framework.org)

Already there are many framework or lib for making restfulAPI with Django. One is `Django REST framework`.

## Install django rest framework
It's easy to install. Just click Link, follow example. done!

## Make admin(superuser)
To login by admin, I should make an admin account. As write python manage.py 
createsuperuser at console window, I can make admin account.

## Finish install and I wonder how it works.

Should I use restfulAPI?.. is not.  RestfulAPI is a design for easy developing and maintaining. But some system are not suitable. Let me do restfulAPI for my Login API Server.

## Create New Project

1. Create Virtual environment.
    virtualenv env
    source env/bin/activate

2. Install Django and utility
    pip install django
    pip install djangorestframework
    pip install pygments -- it's a highlight tool

3. install snippets

__What is the snippets?!__
It seems ... a program which is like code viewer, imo.
I can guess because it has some variance

## Add class Snippet

```Python class Snippet(models.Model):
    created = models.DateTimeField(auto_now_add = True)
    title = models.CharField(max_length=100, blank=True, default='')
    code = models.TextField()
    linenos = models.BooleanField(default=False)
    language = models.CharField(choices=LANGUAGE-LANGUAGE_CHOICES, default='python', max_length=100)
    style = models.CharField(choices=STYLE_CHOICES, default='friendly', max_length=100)

    class Meta:
        ordering = ('created',) 
```
        
I add this source. I guess, modles.Model is the lib which help us make a database model (schema?). How I get it is we can check the attributes of classes. `models.DataTimeField`, `models.CharField` etc... and we can find some attribute are relatied with database like `max_length`, `default`, `black` and more.


## __serializer__
I think, it's very important thing in rest-framework. Form in Django is a model what kind of data it has. In rest-framework we can use serializer instance of from. There are 2-way form, `form` and `modelform`. `Modelform` is more simple and easy to use. 

## __model.serializer__
If we use model.serializer, It's not assential that makes create and update classes. After I change serializer to model.serializer and add `Meta` class, I remove both create and update class, and run. It works.


