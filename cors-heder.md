
Here’s a clean version you can drop into your project:

---


# 🌍 CORS Setup in Django REST Framework

When building APIs with **Django REST Framework**, you may need to allow requests from external domains (e.g., React, Vue, Angular frontends).  
We use [`django-cors-headers`](https://github.com/adamchainz/django-cors-headers) to handle **CORS (Cross-Origin Resource Sharing)**.

<!-- ---
````markdown -->

## 🔹 Installation
Install the package inside your virtual environment:
```bash
pip install django-cors-headers
````

---

## 🔹 Add to Installed Apps

In your `settings.py`:

```python
INSTALLED_APPS = [
    ...
    "corsheaders",
    "rest_framework",
    ...
]
```

---

## 🔹 Add Middleware

Place it **at the top**, before `CommonMiddleware`:

```python
MIDDLEWARE = [
    "corsheaders.middleware.CorsMiddleware",
    "django.middleware.common.CommonMiddleware",
    ...
]
```

---

## 🔹 Configuration Options

### Allow All Origins (Development Only ⚠️)

```python
CORS_ALLOW_ALL_ORIGINS = True
```

---

### Allow Specific Origins (Recommended for Production)

```python
CORS_ALLOWED_ORIGINS = [
    "http://localhost:3000",   # React (local)
    "http://127.0.0.1:8000",  # Django (local)
    "https://myfrontend.com", # Production frontend
]
```

---

### Allow Credentials (if using authentication cookies)

```python
CORS_ALLOW_CREDENTIALS = True
```

---

### Allow Specific Headers

```python
CORS_ALLOW_HEADERS = [
    "authorization",
    "content-type",
    "accept",
    "origin",
    "user-agent",
    "x-csrftoken",
    "x-requested-with",
]
```

---

## 🔹 Verify

Run your server:

```bash
python manage.py runserver
```

Now your API will accept cross-origin requests from allowed domains.

---

✅ You’re all set! Your Django REST Framework project now supports **CORS** so you can connect your API with frontend apps securely.




