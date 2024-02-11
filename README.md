# Group Chat using Django

---

### 1. User can a create, login, edit account.

### 2. Upload photo avatar.

### 3. Add, edit, delete their rooms.

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
DB_NAME={your_database_name}
DB_USER={your_database_user}
DB_PASS={your_database_password}
DB_HOST={your_database_host}
DB_PORT=5432
SECRET_KEY={secret_key}
```

- The secret key can be anything you want. But make sure it is at least 32 characters.
- You can create a key by using "openssl rand -hex 32"
- If you want to use sqllite not postgesql then comment the first "default" database and uncomment the next "default". It will create a new sqllite database on your project directory.
- You can also use POSTGRES image from docker.

```
docker run -d --name db -e POSTGRES_DB=mydatabase -e POSTGRES_USER=myuser -e POSTGRES_PASSWORD=mypassword -p 5432:5432 postgres:13-alpine
```

### 6. Go to app folder using "cd app"

### 7. Run migrations

```
python manage.py makemigrations
python manage.py migrate
```

### 8. Create superuser

```
python manage.py createsuperuser
```

### 9. Run the website using

```
python manage.py runserver
```

### 10. Go to "127.0.0.1:8000" to see the website

### 11. You can access the admin panel by this "127.0.0.1:8000/admin" and give the superuser username, password that you set earlier to see the admin panel.

# Docker Hub

### 1. Pull the image from docker hub.

```
docker pull mahadi025/group-chat-app
```

### 2. Create a docker-compose.yml file.

### 3. On that file copy the followings.

```
version: "3"

services:
  app:
    image: mahadi025/group-chat-app
    command: sh -c "python manage.py migrate && python manage.py runserver 0.0.0.0:8000"
    ports:
      - "8000:8000"
    depends_on:
      - db
    environment:
      - DB_NAME=mydatabase
      - DB_USER=myuser
      - DB_PASSWORD=mypassword
      - DB_HOST=db
      - DB_PORT=5432
      - SECRET_KEY=12afa4e41be911d248958ca0c757a9a8f5931409eee0e68cbcabe86699dd4f8f

  db:
    image: postgres:13-alpine
    environment:
      - POSTGRES_DB=mydatabase
      - POSTGRES_USER=myuser
      - POSTGRES_PASSWORD=mypassword
    volumes:
      - postgres_data:/var/lib/postgresql/data

volumes:
  postgres_data:

```

### 4. To run the app open the terminal or command prompt(where the docker-compose.yml file is) run:

```
docker-compose up
```

### 5. To create a superuser

```
docker compose run sh -c app "python manage.py createsuperuser"
```
