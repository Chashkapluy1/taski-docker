    FROM python:3.12

    RUN apt-get update && apt-get install -y dos2unix build-essential libpq-dev libjpeg-dev zlib1g-dev && rm -rf /var/lib/apt/lists/*

    WORKDIR /app

    RUN pip install gunicorn==23.0.0

    COPY requirements.txt .
    RUN dos2unix requirements.txt
    RUN pip install -r requirements.txt --no-cache-dir

    COPY . .

    CMD ["gunicorn", "backend.wsgi:application", "--bind", "0:8000"]
