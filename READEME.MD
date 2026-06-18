# 🚀 Infinity Backend

A production-ready Django REST Framework backend powered by:

* Django
* Django REST Framework
* PostgreSQL
* Redis
* Celery Worker
* Celery Beat
* Gunicorn
* Docker Compose

---

# 📋 Prerequisites

Before getting started, install:

* Docker
* Docker Compose
* Git

Verify installation:

```bash
docker --version
docker compose version
git --version
```

---

# 📥 Clone Repository

```bash
git clone <repository-url>
cd infinity-backend
```

---

# ⚙️ Environment Variables

Create a `.env` file in the project root:

```env
DEBUG=True

SECRET_KEY=your-secret-key

DB_NAME=infinity_db
DB_USER=postgres
DB_PASSWORD=password
DB_HOST=db
DB_PORT=5432

EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_HOST_USER=your_email@gmail.com
EMAIL_HOST_PASSWORD=your_app_password
EMAIL_USE_TLS=True

FRONTEND_BASE_URL=http://localhost:3000
```

Update the values according to your environment.

---

# 🐳 Start Project

Build and start all services:

```bash
docker compose up -d --build
```

Verify services:

```bash
docker compose ps
```

---

# 🗄 Database Setup

Apply migrations:

```bash
docker compose exec web python manage.py migrate
```

Create admin user:

```bash
docker compose exec web python manage.py createsuperuser
```

---

# 🌐 Access Application

API:

```text
http://localhost:8000
```

Admin:

```text
http://localhost:8000/admin
```

---

# 🏗 Services

| Service       | Description       |
| ------------- | ----------------- |
| web           | Django + Gunicorn |
| db            | PostgreSQL        |
| redis         | Redis             |
| celery_worker | Background Tasks  |
| celery_beat   | Scheduled Tasks   |

---

# 📂 Project Structure

```text
infinity-backend/
│
├── apps/
├── config/
├── media/
├── static/
├── Dockerfile
├── docker-compose.yml
├── requirements.txt
├── manage.py
└── .env
```

---

# 🔄 Development Workflow

## Code Changes

```bash
docker compose restart web
```

---

## Model Changes

```bash
docker compose exec web python manage.py makemigrations

docker compose exec web python manage.py migrate

docker compose restart
```

---

## Static File Changes

```bash
docker compose exec web python manage.py collectstatic --noinput

docker compose restart web
```

---

## Celery Changes

```bash
docker compose restart celery_worker

docker compose restart celery_beat
```

---

## New Package Added

After updating requirements.txt:

```bash
docker compose build

docker compose up -d
```

---

## Dockerfile Changes

```bash
docker compose build --no-cache

docker compose up -d
```

---

## docker-compose.yml Changes

```bash
docker compose down

docker compose up -d
```

---

# 🚀 Deployment Workflow

After pulling new code:

```bash
git pull

docker compose build

docker compose up -d

docker compose exec web python manage.py migrate

docker compose exec web python manage.py collectstatic --noinput

docker compose restart
```

---

# 🩺 Monitoring & Logs

View all logs:

```bash
docker compose logs -f
```

View Django logs:

```bash
docker compose logs -f web
```

View Celery Worker logs:

```bash
docker compose logs -f celery_worker
```

View Celery Beat logs:

```bash
docker compose logs -f celery_beat
```

Check running containers:

```bash
docker compose ps
```

---

# 🧪 Running Tests

```bash
docker compose exec web pytest
```

Run specific tests:

```bash
docker compose exec web pytest apps/accounts/tests -v
```

Coverage:

```bash
docker compose exec web pytest --cov=apps --cov-report=term-missing
```

---

# 🚨 Emergency Recovery

```bash
docker compose down

docker compose build --no-cache

docker compose up -d

docker compose exec web python manage.py migrate

docker compose exec web python manage.py collectstatic --noinput
```

---

# 👨‍💻 Author

Infinity Solutions

Built with:

* Django
* Django REST Framework
* PostgreSQL
* Redis
* Celery
* Gunicorn
* Docker Compose
