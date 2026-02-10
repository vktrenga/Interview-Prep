# Django Interview Questions

## Table of Contents

- [Basic Django Questions](#basic-django-questions)
- [Intermediate Django Questions](#intermediate-django-questions)
- [Advanced Django Questions](#advanced-django-questions)
- [Django REST Framework (DRF)](#django-rest-framework-drf)
- [Async Django / Performance](#async-django--performance)
- [Django Signals](#django-signals)
- [Middleware](#middleware)
- [Caching](#caching)
- [Deployment & Performance](#deployment--performance)




## **Basic Django Questions**

### 1. **What is Django?**

**Answer:**
Django is a high-level Python web framework that encourages rapid development and clean, pragmatic design. It follows the **MTV (Model-Template-View)** architectural pattern, similar to MVC.

* **Model:** Defines the data structure (database tables).
* **Template:** Handles the presentation layer (HTML).
* **View:** Contains the business logic and interacts with models/templates.

**Explanation:**
Django abstracts repetitive tasks like authentication, routing, and ORM, allowing developers to focus on application logic. Its philosophy is **“Don’t Repeat Yourself (DRY)”** and **“Convention over Configuration”**.

---

### 2. **What are Django’s key features?**

**Answer:**

* **ORM:** Maps Python classes to database tables.
* **URL Routing:** Clean URLs via `urls.py`.
* **Authentication:** Built-in user management.
* **Admin Interface:** Auto-generated interface for CRUD operations.
* **Security:** Protects against SQL injection, XSS, CSRF.
* **Scalability & Reusability:** Apps can be reused in multiple projects.

**Explanation:**
Django is a “batteries-included” framework, meaning it provides most common web development features out-of-the-box, which reduces development time.

---

### 3. **Explain Django Project vs App**

**Answer:**

* **Project:** A Django project is the **entire web application** with configuration settings (`settings.py`), root URLs (`urls.py`), and WSGI/ASGI entry points.
* **App:** A Django app is a **self-contained module** performing a specific functionality (like a blog, auth, payment).

**Explanation:**
A project can have multiple apps. Apps can also be reused in other projects. Think of a project as the house and apps as individual rooms.

---

### 4. **What is `settings.py`?**

**Answer:**
`settings.py` contains **configuration** for a Django project:

* Database settings (`DATABASES`)
* Installed apps (`INSTALLED_APPS`)
* Middleware (`MIDDLEWARE`)
* Templates settings
* Static and media files settings

**Explanation:**
It centralizes all configuration, making it easy to manage environments (development, testing, production).

---

### 5. **What is `urls.py` in Django?**

**Answer:**
`urls.py` defines the mapping between **URL patterns and views**. Example:

```python
from django.urls import path
from . import views

urlpatterns = [
    path('home/', views.home_view, name='home'),
]
```

**Explanation:**
Django uses **URL dispatcher** to route HTTP requests to the appropriate view. URL patterns can also include variables and regex for dynamic routing.

---

### 6. **Explain Django Models**

**Answer:**
Models define the **database structure** using Python classes:

```python
from django.db import models

class Product(models.Model):
    name = models.CharField(max_length=100)
    price = models.FloatField()
```

**Explanation:**
Django ORM translates these models into SQL tables. Each attribute represents a table column, and Django handles CRUD operations automatically.

---

### 7. **What are Django Views?**

**Answer:**
Views handle **business logic** and return HTTP responses. There are two types:

1. **Function-Based Views (FBV):**

```python
def home_view(request):
    return HttpResponse("Hello Django")
```

2. **Class-Based Views (CBV):**

```python
from django.views import View

class HomeView(View):
    def get(self, request):
        return HttpResponse("Hello Django")
```

**Explanation:**
CBVs provide **reusability and inheritance**, while FBVs are simpler for basic tasks.

---

### 8. **What are Django Templates?**

**Answer:**
Templates are HTML files with **Django Template Language (DTL)** for dynamic content:

```html
<h1>{{ product.name }}</h1>
```

**Explanation:**
Templates allow separation of **presentation and logic**. Filters and tags enhance HTML rendering.

---

### 9. **Explain Django ORM**

**Answer:**
Django ORM (Object-Relational Mapping) converts **Python objects into database queries**.

* Query examples:

```python
Product.objects.all()        # SELECT * FROM product
Product.objects.filter(price__gt=100)  # SELECT * WHERE price > 100
```

**Explanation:**
ORM abstracts SQL, reducing errors and improving security. It supports relationships: **OneToOne, ForeignKey, ManyToMany**.

---

### 10. **Explain Django Middleware**

**Answer:**
Middleware is a **layer between request and response**. Example uses:

* Authentication checks
* Session management
* Logging

**Explanation:**
Each middleware is a Python class with `__call__` or `process_request`/`process_response` methods. They execute in the order defined in `settings.py`.

---

## **Intermediate Django Questions**

### 11. **What is `Migrations` in Django?**

**Answer:**
Migrations are **version control for your database schema**.

```bash
python manage.py makemigrations
python manage.py migrate
```

**Explanation:**
They track changes in models and apply them safely to the database. Django generates SQL behind the scenes.

---

### 12. **Explain Django Forms**

**Answer:**
Forms handle **input validation and rendering**.

```python
from django import forms

class ProductForm(forms.Form):
    name = forms.CharField(max_length=100)
    price = forms.FloatField()
```

**Explanation:**
Forms handle security automatically (e.g., CSRF tokens) and can be linked to models using **ModelForm**.

---

### 13. **What is Django Admin?**

**Answer:**
A pre-built admin interface for managing models.

```python
from django.contrib import admin
from .models import Product

admin.site.register(Product)
```

**Explanation:**
The admin panel speeds up development and is highly customizable (custom forms, permissions, filters).

---

### 14. **What are Django Signals?**

**Answer:**
Signals allow **decoupled communication** between apps:

```python
from django.db.models.signals import post_save
from django.dispatch import receiver
from .models import Product

@receiver(post_save, sender=Product)
def notify_new_product(sender, instance, **kwargs):
    print(f"New product added: {instance.name}")
```

**Explanation:**
Useful for triggering actions after events (e.g., send email after user registration).

---

### 15. **Explain Django Authentication**

**Answer:**
Built-in system with models like `User`, `Group`, `Permission`. Provides:

* Login/logout
* Password hashing
* Permission-based access

**Explanation:**
Custom user models can be created by extending `AbstractUser` or `AbstractBaseUser`.

---

### 16. **What are Django REST Framework (DRF) basics?**

**Answer:**
DRF provides tools to build **RESTful APIs**:

* Serializers for converting models to JSON
* ViewSets and Routers for routing
* Authentication classes

Example:

```python
from rest_framework import serializers

class ProductSerializer(serializers.ModelSerializer):
    class Meta:
        model = Product
        fields = '__all__'
```

**Explanation:**
DRF simplifies API development with built-in pagination, filtering, and authentication.

---

### 17. **How does Django handle static and media files?**

**Answer:**

* **Static files:** CSS, JS, images → `STATIC_URL` and `STATICFILES_DIRS`
* **Media files:** User-uploaded files → `MEDIA_URL` and `MEDIA_ROOT`

**Explanation:**
In development, `django.contrib.staticfiles` serves static content. In production, a web server like Nginx is recommended.

---

### 18. **Explain Django caching**

**Answer:**
Caching improves performance by storing expensive queries or rendered pages:

* File-based, memory-based (Memcached, Redis), database caching

```python
from django.core.cache import cache
cache.set('my_key', 'my_value', 60)
```

**Explanation:**
Reduces database hits and response time for frequently accessed data.

---

### 19. **What is Django CSRF Protection?**

**Answer:**
Cross-Site Request Forgery protection ensures forms are submitted **from trusted sources**:

```html
<form method="POST">{% csrf_token %}</form>
```

**Explanation:**
Django automatically checks tokens for POST requests to prevent malicious attacks.

---

### 20. **What is `select_related` vs `prefetch_related`?**

**Answer:**

* `select_related`: Fetches related objects in **one SQL JOIN** (best for ForeignKey/OneToOne)
* `prefetch_related`: Fetches related objects in **separate queries** and caches them (best for ManyToMany)

**Explanation:**
Optimizes database queries and prevents **N+1 query problem**, which is common in ORM usage.

---

## **Advanced Django Questions**

### 21. **Explain Django’s Request/Response Cycle**

**Answer:**

1. User sends an HTTP request
2. URL dispatcher (`urls.py`) maps URL to a view
3. Middleware processes request
4. View queries database/models
5. Template renders response
6. Middleware processes response
7. Response is sent back to the user

**Explanation:**
Understanding this helps optimize middleware, caching, and error handling.

---

### 22. **How does Django handle transactions?**

**Answer:**
Django uses **atomic transactions**:

```python
from django.db import transaction

with transaction.atomic():
    # All queries here are atomic
```

**Explanation:**
If any query fails, all changes rollback, ensuring database consistency.

---

### 23. **Explain Custom Managers in Django**

**Answer:**
Custom managers define reusable query methods:

```python
class ProductManager(models.Manager):
    def expensive(self):
        return self.filter(price__gt=100)

class Product(models.Model):
    name = models.CharField(max_length=100)
    price = models.FloatField()
    objects = ProductManager()
```

**Explanation:**
Custom managers encapsulate complex queries for cleaner code.

---

### 24. **Explain Middleware order importance**

**Answer:**
Middleware executes **in order** for requests and **reverse order** for responses.

* Important because authentication middleware must run before view access, and security middleware should wrap response last.

---

### 25. **What is Django’s `apps.py`?**

**Answer:**
`apps.py` configures a Django app:

```python
from django.apps import AppConfig

class BlogConfig(AppConfig):
    default_auto_field = 'django.db.models.BigAutoField'
    name = 'blog'
```

**Explanation:**
It’s used to register signals and app-level configurations.

---

### 26. **How to optimize Django queries?**

**Answer:**

* Use `select_related` and `prefetch_related`
* Avoid `all()` when unnecessary
* Index database fields
* Use caching
* Batch updates

---

### 27. **Explain `get_object_or_404`**

**Answer:**
Returns an object or raises `Http404` if not found:

```python
from django.shortcuts import get_object_or_404
product = get_object_or_404(Product, id=1)
```

**Explanation:**
Simplifies error handling in views.

---

### 28. **What is Django Signals vs Celery?**

**Answer:**

* **Signals:** Synchronous, triggered immediately (in-process)
* **Celery:** Asynchronous, runs in background, useful for long-running tasks like emails, report generation

---

### 29. **Explain Django Custom Middleware**

**Answer:**
Example:

```python
class SimpleMiddleware:
    def __init__(self, get_response):
        self.get_response = get_response

    def __call__(self, request):
        print("Before view")
        response = self.get_response(request)
        print("After view")
        return response
```

**Explanation:**
Custom middleware allows pre/post-processing of requests/responses.

---

### 30. **How to implement multi-database support in Django?**

**Answer:**

* Define multiple databases in `settings.py`
* Use `using('db_name')` in queries
* Route queries via `DatabaseRouter`

**Explanation:**
Useful for read/write separation, legacy databases, or sharding.

---




##DRF
Perfect! Let’s go all-in and cover **50+ advanced Django questions** with **detailed explanations, code examples, and best practices** across **DRF, async Django, signals, middleware, caching, deployment, and security**. This batch will go beyond basics and intermediate topics—everything you need to ace a senior Django interview.

---



---

## **Django REST Framework (DRF)**

### 1. **What is Django REST Framework (DRF)?**

**Answer:**
DRF is a toolkit for building **RESTful APIs** in Django. It simplifies serialization, authentication, permission handling, pagination, filtering, and viewsets.

**Explanation:**
DRF integrates seamlessly with Django ORM and provides **class-based views, routers, serializers, and authentication classes** for scalable API development.

---

### 2. **Explain Serializers in DRF**

**Answer:**
Serializers convert **complex Python objects (querysets/models) to JSON** and vice versa.
Example:

```python
from rest_framework import serializers
from .models import Product

class ProductSerializer(serializers.ModelSerializer):
    class Meta:
        model = Product
        fields = ['id', 'name', 'price']
```

**Explanation:**

* `ModelSerializer` auto-generates fields from models.
* Custom validation can be added using `validate_<field>` methods.

---

### 3. **What are ViewSets in DRF?**

**Answer:**
ViewSets combine multiple views into a single class. Example:

```python
from rest_framework import viewsets
from .models import Product
from .serializers import ProductSerializer

class ProductViewSet(viewsets.ModelViewSet):
    queryset = Product.objects.all()
    serializer_class = ProductSerializer
```

**Explanation:**

* CRUD operations are automatically handled.
* Works with **routers** to generate URLs automatically.

---

### 4. **What are Routers in DRF?**

**Answer:**
Routers automatically map ViewSets to URLs.

```python
from rest_framework.routers import DefaultRouter
from .views import ProductViewSet

router = DefaultRouter()
router.register(r'products', ProductViewSet)
urlpatterns = router.urls
```

**Explanation:**

* Reduces manual URL mapping.
* Works well with `ModelViewSet` and `ReadOnlyModelViewSet`.

---

### 5. **Explain DRF Authentication & Permissions**

**Answer:**

* **Authentication:** Who the user is. Examples: Token, Session, JWT, OAuth2.
* **Permissions:** What the user can do. Examples: `IsAuthenticated`, `IsAdminUser`.

```python
from rest_framework.permissions import IsAuthenticated

class ProductViewSet(viewsets.ModelViewSet):
    permission_classes = [IsAuthenticated]
```

**Explanation:**
DRF separates authentication from permission, allowing granular access control.

---

### 6. **How to handle pagination in DRF?**

**Answer:**
Pagination limits API response size.

```python
REST_FRAMEWORK = {
    'DEFAULT_PAGINATION_CLASS': 'rest_framework.pagination.PageNumberPagination',
    'PAGE_SIZE': 10
}
```

**Explanation:**
Reduces load on database and frontend, especially for large datasets.

---

### 7. **How to filter and search in DRF?**

**Answer:**

```python
from rest_framework import filters

class ProductViewSet(viewsets.ModelViewSet):
    filter_backends = [filters.SearchFilter]
    search_fields = ['name', 'category__name']
```

**Explanation:**
DRF supports **search, ordering, and custom filter backends** for API queries.

---

### 8. **Explain DRF throttling**

**Answer:**
Throttling controls API rate limits:

```python
REST_FRAMEWORK = {
    'DEFAULT_THROTTLE_CLASSES': ['rest_framework.throttling.UserRateThrottle'],
    'DEFAULT_THROTTLE_RATES': {'user': '100/day'}
}
```

**Explanation:**
Prevents abuse of APIs by limiting requests per user or IP.

---

### 9. **How to handle nested serializers?**

**Answer:**

```python
class CategorySerializer(serializers.ModelSerializer):
    class Meta:
        model = Category
        fields = ['id', 'name']

class ProductSerializer(serializers.ModelSerializer):
    category = CategorySerializer()
    class Meta:
        model = Product
        fields = ['id', 'name', 'price', 'category']
```

**Explanation:**
Nested serializers allow representing **related models** directly in the JSON output.

---

### 10. **Explain DRF signals**

**Answer:**
DRF itself doesn’t add new signals, but Django signals can be used for **pre/post-save actions** for API-driven models.

Example: Send email after creating a product via API:

```python
from django.db.models.signals import post_save
from django.dispatch import receiver
from .models import Product

@receiver(post_save, sender=Product)
def notify_new_product(sender, instance, **kwargs):
    print(f"New product via API: {instance.name}")
```

---

## **Async Django / Performance**

### 11. **What is Async Django?**

**Answer:**
Since Django 3.1, views and middleware can be **asynchronous**, using `async def`.
Example:

```python
async def async_view(request):
    await asyncio.sleep(1)
    return HttpResponse("Async response")
```

**Explanation:**
Improves I/O-bound performance (e.g., calling external APIs) without blocking the server.

---

### 12. **Explain ASGI vs WSGI**

**Answer:**

* **WSGI:** Synchronous interface for Python web apps (traditional Django).
* **ASGI:** Asynchronous interface supporting WebSockets and long-lived connections.

**Explanation:**
ASGI allows Django to handle real-time features (chat, notifications) efficiently.

---

### 13. **How to use async ORM in Django?**

**Answer:**
Django 4+ supports async ORM:

```python
product = await Product.objects.aget(id=1)
```

**Explanation:**
Avoids blocking I/O in async views, improving throughput for API-heavy apps.

---

### 14. **What is QuerySet evaluation in async?**

**Answer:**
QuerySets are **lazy-evaluated**. In async, use `await` with `a*` methods:

* `aget()`, `afilter()`, `aall()`

**Explanation:**
This ensures database queries are non-blocking in async views.

---

### 15. **How to implement caching in async views?**

**Answer:**
Use Django’s cache with `async_to_sync` or async-compatible cache backends like Redis:

```python
from asgiref.sync import sync_to_async

@sync_to_async
def get_cached_data():
    return cache.get('my_key')
```

---

## **Django Signals**

### 16. **What are Django signals and use cases?**

**Answer:**
Signals allow **decoupled communication** between apps.
Use cases:

* Sending emails after user registration
* Logging model changes
* Triggering background tasks

---

### 17. **Pre-save vs post-save signals**

* **pre_save:** Executes before saving object.
* **post_save:** Executes after saving object.

Example:

```python
from django.db.models.signals import pre_save, post_save

@receiver(pre_save, sender=User)
def before_save(sender, instance, **kwargs):
    print("User is about to be saved")
```

---

### 18. **Custom signal example**

```python
from django.dispatch import Signal

order_completed = Signal(providing_args=["order_id"])

def send_invoice(sender, **kwargs):
    print(f"Invoice sent for order {kwargs['order_id']}")

order_completed.connect(send_invoice)
order_completed.send(sender=None, order_id=123)
```

**Explanation:**
Custom signals allow **modular event-driven design** in Django apps.

---

## **Middleware**

### 19. **Explain Django middleware**

**Answer:**
Middleware is a **hook between request and response**:

* Authentication
* Session management
* Logging, throttling
* Security headers

---

### 20. **How to write custom middleware**

```python
class LogMiddleware:
    def __init__(self, get_response):
        self.get_response = get_response

    def __call__(self, request):
        print(f"Request path: {request.path}")
        response = self.get_response(request)
        print(f"Response status: {response.status_code}")
        return response
```

**Explanation:**
Middleware can modify request, response, or raise exceptions.

---

### 21. **Middleware execution order**

* **Request:** Top → Bottom
* **Response:** Bottom → Top

**Explanation:**
Critical for authentication and logging. Misordered middleware can break app logic.

---

### 22. **Middleware for performance monitoring**

Example: measure request time:

```python
import time
class TimerMiddleware:
    def __call__(self, request):
        start = time.time()
        response = self.get_response(request)
        print(f"Time taken: {time.time() - start}")
        return response
```

---

## **Caching**

### 23. **Explain caching strategies**

* **File-based cache**: Disk storage
* **Memory-based cache**: Fast, in-memory (Memcached, Redis)
* **Database cache**: Store cached data in DB

---

### 24. **Django low-level cache API**

```python
from django.core.cache import cache
cache.set('key', 'value', timeout=60)
value = cache.get('key')
```

---

### 25. **Template fragment caching**

```html
{% load cache %}
{% cache 500 sidebar %}
   <!-- Expensive sidebar HTML -->
{% endcache %}
```

**Explanation:**
Caches only parts of the template for faster page rendering.

---

### 26. **View-level caching**

```python
from django.views.decorators.cache import cache_page

@cache_page(60 * 15)
def my_view(request):
    return HttpResponse("Hello Cache")
```

---

### 27. **Per-site caching**

```python
MIDDLEWARE = [
    'django.middleware.cache.UpdateCacheMiddleware',
    'django.middleware.cache.FetchFromCacheMiddleware',
    ...
]
CACHE_MIDDLEWARE_ALIAS = 'default'
CACHE_MIDDLEWARE_SECONDS = 600
```

---

## **Deployment & Performance**

### 28. **How to deploy Django in production?**

* Use **Gunicorn + Nginx** or **ASGI server (Uvicorn/Daphne)**
* Configure **settings.py**: `DEBUG=False`, `ALLOWED_HOSTS`
* Use **environment variables** for secrets
* Use **WhiteNoise** for static files or CDN

---

### 29. **Database optimization**

* Index frequently queried fields
* Use `select_related` / `prefetch_related`
* Avoid `all()` on large datasets
* Use `annotate` and `aggregate` for calculations

---

### 30. **Static & media file handling**

* Serve static files via **CDN/Nginx**
* Store media in **S3/GCP/Azure blob storage**
* Use `collectstatic` for production

---

### 31. **Django logging in production**

```python
LOGGING = {
    'version': 1,
    'handlers': {'file': {'class': 'logging.FileHandler', 'filename': '/logs/django.log'}},
    'loggers': {'django': {'handlers': ['file'], 'level': 'INFO'}}
}
```

---

### 32. **Database connection pooling**

* Use `pgbouncer` for Postgres or MySQL pooling
* Reduces overhead for repeated connections

---

### 33. **Async tasks with Celery**

* Offload long-running tasks like emails or data processing
* Works with **Redis or RabbitMQ** as broker
  Example:

```python
from celery import shared_task

@shared_task
def send_email_task(email_id):
    print(f"Sending email to {email_id}")
```

---

### 34. **Security best practices**

* `DEBUG=False` in production
* Use HTTPS (`SECURE_SSL_REDIRECT=True`)
* Set `X-Frame-Options`, `X-Content-Type-Options` headers
* CSRF tokens for POST forms
* Password hashing (`Argon2` or `PBKDF2`)
* Validate user input to prevent SQL Injection/XSS

---

### 35. **Django rate limiting**

* DRF throttling for APIs
* Middleware or reverse proxies (Nginx, Cloudflare) for web requests

---

### 36. **Explain Django Signals vs Celery**

* Signals: synchronous, in-process
* Celery: asynchronous, background tasks

---

### 37. **Async vs Celery**

* Async views: non-blocking I/O
* Celery: long-running tasks offloaded to workers

---

### 38. **Database transactions & atomicity**

```python
from django.db import transaction

with transaction.atomic():
    product.save()
    order.save()
```

**Explanation:**
Ensures all-or-nothing changes.

---

### 39. **Explain `select_for_update`**

* Locks rows during a transaction to prevent race conditions.

---

### 40. **Handling concurrency**

* Use database-level locks (`select_for_update`)
* Use optimistic concurrency with versioning fields
* Use Celery for async batch tasks

---

### 41. **Django signals best practices**

* Avoid heavy operations in signal handlers
* Use Celery for long tasks triggered by signals
* Disconnect signals in tests to avoid side effects

---

### 42. **Advanced DRF: ViewSet Mixins**

* `CreateModelMixin`, `RetrieveModelMixin`, `UpdateModelMixin`
* Combine for custom CRUD behavior without full `ModelViewSet`

---

### 43. **Throttle classes in DRF**

* `UserRateThrottle`, `AnonRateThrottle`, `ScopedRateThrottle`
* Control API usage and prevent abuse

---

### 44. **DRF Serializer `validate`**

* `validate_<field>`: field-specific
* `validate`: object-level

---

### 45. **DRF HyperlinkedModelSerializer**

* Returns URLs instead of IDs for related objects

```python
class ProductSerializer(serializers.HyperlinkedModelSerializer):
    class Meta:
        model = Product
        fields = ['url', 'name', 'price']
```

---

### 46. **DRF Pagination Types**

* `PageNumberPagination`
* `LimitOffsetPagination`
* `CursorPagination` (stable ordering, avoids duplicates)

---

### 47. **DRF Filtering**

* `DjangoFilterBackend` for complex filters
* Custom filters for multi-field or relational filtering

---

### 48. **Django Admin customization**

* Customize list display, search, filters

```python
class ProductAdmin(admin.ModelAdmin):
    list_display = ('name', 'price')
    search_fields = ('name',)
```

---

### 49. **Django Custom Management Commands**

* Automate tasks via CLI

```python
from django.core.management.base import BaseCommand

class Command(BaseCommand):
    help = 'Send daily reports'

    def handle(self, *args, **kwargs):
        print('Sending reports...')
```

---

### 50. **Django Testing & Debugging**

* Unit tests: `TestCase`
* API tests: `APITestCase`
* Use `pytest-django` for enhanced features
* Debug with `django-debug-toolbar`

---

### 51. **Django Internationalization (i18n)**

* Support multiple languages
* `gettext` for translation
* Middleware handles language selection

---

### 52. **Django Signals vs Webhooks**

* Signals: internal app events
* Webhooks: external app notifications

---

### 53. **Django Context Processors**

* Inject variables into all templates

```python
def site_info(request):
    return {'SITE_NAME': 'MySite'}
```

---

### 54. **Django File Upload Optimization**

* Use **streaming uploads** for large files
* Store in **S3 or cloud storage**
* Use async tasks for processing

---

### 55. **Django Security Headers**

* `SECURE_BROWSER_XSS_FILTER`
* `SECURE_CONTENT_TYPE_NOSNIFF`
* `SECURE_HSTS_SECONDS`

---

