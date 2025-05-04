FROM --platform=linux/amd64 python:3.9-slim

WORKDIR /app
FROM --platform=linux/amd64 python:3.9-slim

WORKDIR /app

# Установка системных зависимостей
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

# Копирование и установка Python зависимостей
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt gunicorn==20.1.0

# Копирование проекта
COPY . .

# Проверка структуры проекта
RUN ["sh", "-c", "if [ ! -f 'backend/wsgi.py' ]; then echo 'ERROR: backend/wsgi.py not found!'; exit 1; fi"]

CMD ["gunicorn", "--bind", "0.0.0.0:8000", "backend.wsgi"]