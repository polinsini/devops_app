# Dockerfile
FROM python:3.9-slim

# Set environment variables
ENV PYTHONUNBUFFERED 1
ENV PYTHONDONTWRITEBYTECODE 1

# Set working directory
WORKDIR /app


# Install dependencies
COPY requirements.txt /app/requirements.txt
COPY . .

RUN pip install --no-cache-dir -r /app/requirements.txt
RUN apt-get update && apt-get install -y libpq-dev gcc

# Copy project files
COPY  . .

# Run migrations and start server
CMD ["sh", "-c", "python manage.py makemigrations && python manage.py migrate && python manage.py runserver 0.0.0.0:8000"]
