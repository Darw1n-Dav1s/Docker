# How the Docker Image Script Was Made (Python + Flask + Node.js)

This document explains the logic and steps behind writing the Dockerfile to create a Docker image that supports Python, Flask, and Node.js.

---

## 1. Choosing the Base Image

- We used `python:3.11-slim` as the base.
  - `python:3.11` gives us the latest Python version.
  - `slim` is a minimal version to reduce image size.
  - A smaller image = faster builds and smaller attack surface.

---

## 2. Setting Environment Variables

- `PYTHONDONTWRITEBYTECODE=1` prevents Python from writing `.pyc` bytecode files, keeping the container clean.
- `PYTHONUNBUFFERED=1` ensures logs are written directly to the console (important for real-time logging).

---

## 3. Setting the Working Directory

- `WORKDIR /app` sets the default directory in the container.
  - Every command like `COPY`, `RUN`, and `CMD` works inside `/app`.

---

## 4. Installing Node.js

- Since Node.js is not part of the Python base image, we manually installed it:
  - First, we installed system packages like `curl`, `gnupg`, and `build-essential` (needed for building Node and some Python packages).
  - Then we downloaded and added the official Node.js 18 repo using the script from NodeSource.
  - We installed `nodejs` using `apt`.
  - `apt-get clean` is used at the end to reduce image size.

**Important Tip:** Always clean up with `apt-get clean` and avoid unnecessary packages to keep the image lean.

---

## 5. Copying the Project Files

- `COPY . .` copies everything from your current host directory into the container.
  - This includes your Python app (`app.py`) and other files like `requirements.txt`.

---

## 6. Installing Python Dependencies

- We installed Flask directly using `pip install Flask`.
  - If you have many dependencies, it's better to use a `requirements.txt`:
    ```dockerfile
    COPY requirements.txt .
    RUN pip install -r requirements.txt
    ```

**Tip:** Installing from `requirements.txt` makes it easier to manage dependencies in production.

---

## 7. Verifying Installed Versions (Optional)

- We printed out the versions of Python, pip, Node.js, and npm using:
  ```dockerfile
  RUN python --version && pip --version && node --version && npm --version
