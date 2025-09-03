# Django Project Deployment with Supabase & Vercel

This guide helps you set up and deploy a Django project with a Supabase PostgreSQL database and Vercel hosting.

## 🚀 Quick Setup

### 1️⃣ Create a Supabase Database
1. Go to [Supabase](https://supabase.com/) and create an account.
2. Set up a new project and get the PostgreSQL database credentials.

### 2️⃣ Configure Django Database Settings
In your `settings.py`, update the `DATABASES` configuration:

```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'postgres',
        'USER': 'masteruser',
        'PASSWORD': '12345678',
        'HOST': 'w3-django-project.cdxmgq9zqqlr.us-east-1.rds.amazonaws.com',
        'PORT': '5432'
    }
}
```

### 3️⃣ Install Required Dependencies
Run the following command to install necessary packages:

```
pip install psycopg2 whitenoise
```

### 4️⃣ Clean `requirements.txt`
Run:
```
awk -F'==' '{print $1}' requirements.txt > new_requirements.txt
mv new_requirements.txt requirements.txt
```

### 5️⃣ Update `MIDDLEWARE` in `settings.py`
Add:
```
"whitenoise.middleware.WhiteNoiseMiddleware",
```
At the top in INSTALLED_APPS:
```
"whitenoise.runserver_nostatic",
```

### 6️⃣ Run Migrations & Create Superuser
```
python manage.py makemigrations
python manage.py migrate
python manage.py createsuperuser
```

### 7️⃣ Update Security Settings
Edit `settings.py`:

```
ALLOWED_HOSTS = ['127.0.0.1', '.vercel.app']
CSRF_TRUSTED_ORIGINS = ["https://api-project-name.com", "https://*.127.0.0.1"]
```

### 8️⃣ Configure Static Files
Add in `settings.py`:
```
STATIC_ROOT = BASE_DIR / 'staticfiles'
```

### 9️⃣ Create `.gitignore`
Create a `.gitignore` file and add:
```
RedDrop/.env
.env
db.sqlite3
__pycache__/
```

### 🔟 Create `vercel.json`
Create `vercel.json` and add:
```
{
    "builds": [
        {
            "src": "project_name/wsgi.py",
            "use": "@vercel/python",
            "config": {
                "maxLambdaSize": "15mb",
                "runtime": "python3.11.3"
            }
        }
    ],
    "routes": [
        {
            "src": "/(.*)",
            "dest": "project_name/wsgi.py"
        }
    ]
}
```

### 1️⃣1️⃣ Update `wsgi.py`
Modify `wsgi.py`:
```
app = application
```

### 1️⃣2️⃣ Update `WSGI_APPLICATION` in `settings.py`
```
WSGI_APPLICATION = '<project_name>.wsgi.app'
```

### 1️⃣3️⃣ Collect Static Files
```
python manage.py collectstatic
```

### 1️⃣4️⃣ Deploy to Vercel 🎉
Upload your project to Vercel and deploy!
