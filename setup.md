
# Django REST Framework Project Setup 🚀

## 🔹 Create and Activate Virtual Environment
```bash
python -m venv env
# Activate Virtual Environment
# On cmd
env\Scripts\activate
# On Linux/Mac
source env/bin/activate
# On Windows(bash)
source env/Scripts/activate
````

---

## 🔹 Install Required Packages

```bash
pip install django djangorestframework
```

---

## 🔹 Create Project and App

```bash
django-admin startproject <project_name> .
python manage.py startapp <app_name>
```

---

## 🔹 Optional Packages

```bash
pip install psycopg2-binary         # PostgreSQL support
pip install python-decouple         # Environment variables
pip install djangorestframework-simplejwt  # JWT Authentication
pip install drf-spectacular         # API documentation
```

---

## 🔹 Save Dependencies

```bash
pip freeze > requirements.txt
```

---

## 🔹 Docker Commands

### Build and Run Containers

```bash
cd ..
source env/Scripts/activate
cd <project_name>/
docker-compose up --build
```

### Stop and Remove Containers

```bash
cd ..
source env/Scripts/activate
cd <project_name>/
docker-compose down
```

### Run Django Migrations Inside Docker

```bash
cd ..
source env/Scripts/activate
cd <project_name>/

# Make migrations
docker exec -it <continer name> python manage.py makemigrations

# Apply migrations
docker exec -it <continer name> python manage.py migrate
```



---

✅ You now have a ready-to-use Django REST Framework project setup with Docker support.
