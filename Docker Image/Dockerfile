FROM python:3.11-slim

# Set environment
ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

# Set workdir
WORKDIR /app

# Install Node.js
RUN apt-get update && apt-get install -y curl gnupg build-essential \
    && curl -fsSL https://deb.nodesource.com/setup_18.x | bash - \
    && apt-get install -y nodejs \
    && apt-get clean

# Copy your Flask app files (optional)
COPY . .

# Install Flask (or other Python dependencies)
RUN pip install Flask

# Print versions to verify
RUN python --version && pip --version && node --version && npm --version

# Run Flask app (if you have one)
CMD ["python", "app.py"]
