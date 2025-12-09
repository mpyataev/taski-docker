FROM python:3.12

WORKDIR /app

RUN pip install gunicorn==23.0.0
# Устанавливаем необходимые системные зависимости
RUN apt-get update && apt-get install -y \
    python3-dev \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

# Обновляем pip и устанавливаем setuptools
RUN pip install --upgrade pip setuptools wheel

COPY requirements.txt .
RUN pip install -r requirements.txt --no-cache-dir

COPY . .

CMD ["gunicorn", "--bind", "0.0.0.0:8000", "backend.wsgi"]