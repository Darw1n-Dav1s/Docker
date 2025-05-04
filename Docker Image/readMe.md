# Docker Image with Python, Flask, and Node.js

This guide explains how to build a Docker image that includes Python, Flask, and Node.js.

---

##  Requirements

- Docker installed: https://docs.docker.com/get-docker/

---

##  What Will Be Included

- Python 3.11
- Flask (via `pip`)
- Node.js 18 (via official setup script)

---

##  Step-by-Step Guide

### 1. Create a `Dockerfile`

Create a file named `Dockerfile` (no extension) in your project folder and paste the code given in the file Dockerfile.

### 2. Build the Docker Image  
```
docker build -t flask-node-image .
```
### 3. Run a Container
To start a container from your new image:

```
docker run -it -p 5000:5000 flask-node-image
```

Accessible at http://localhost:5000.

### Cleanup:
To stop the container:
Ctrl + C


To remove the image:
```
docker rmi flask-node-image
```


### Notes:

You can add more Python or Node.js dependencies by modifying the Dockerfile (pip install or npm install).

Flask app should be inside the same directory or mounted with a volume.

