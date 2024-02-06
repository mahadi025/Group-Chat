# Group Chat using Django

---

### 1. User can a create, login, edit account.

### 2. Upload photo avatar.

### 3. Add, edit rooms.

### 4. Send message to rooms.

# How to use

### 1. Clone the repo or download as zip and open it on a terminal or command prompt.

### 2. Create a virtual environment.

```
python -m venv env
```

### 3. Activate your environment

Windows

```
env\scripts\activate
```

Linux

```
source env/bin/activate
```

### 4. Install all the requirements from requirements.txt

```
pip install -r requirements.txt
```

### 5. Create a .env file in your project like the followings

```
DATABASE_NAME={your_database_name}
DATABASE_USER={your_database_user}
DATABASE_PASS={your_database_password}
DATABASE_HOST={your_database_host}
DATABASE_PORT=5432
SECRET_KEY={secret_key}
```

- The secret key can be anything you want. But make sure it is at least 32 characters.
- You can create a key by using "openssl rand -hex 32"

### 6. Run migrations

```
python manage.py makemigrations
python manage.py migrate
```

### 7. Create superuser

```
python manage.py createsuperuser
```

### 8. Run the website using

```
python manage.py runserver
```

### 9. Go to "127.0.0.1:8000" to see the website

### 10. You can access the admin panel by this "127.0.0.1:8000/admin" and give the superuser username, password that you set earlier to see the admin panel.
