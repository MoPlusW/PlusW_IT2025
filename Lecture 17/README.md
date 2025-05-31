
# 🐳 Class 17 - Introduction to Docker & Docker Compose for AI Engineers

![Course Badge](https://img.shields.io/badge/Course-IT%20%26%20Japanese%20Language-blue)  
![Date Badge](https://img.shields.io/badge/Date-May%2024%2C%202025-brightgreen)  
![Platform Badge](https://img.shields.io/badge/Platform-Docker%20%7C%20Linux%20Terminal%20%7C%20AWS%20EC2-lightgrey)

**👨‍🏫 Instructors:** [Hafiz Muhammad Umair Munir](https://www.linkedin.com/in/hafiz-muhammad-umair-munir-b929b0173/), [Abdul Ahad](https://www.linkedin.com/in/ahad-pro-soft/), [Abdul Hanan Ashraf](https://www.linkedin.com/in/abdul-hanan-ashraf-156115157/)  
**🎓 Organized by:** [Plus W 株式会社](https://www.linkedin.com/company/plus-w) & [Pakistan Japan Centre](https://www.linkedin.com/company/pakistan-japan-centre)  
**🌐 Supported by:** [AOTS](https://www.linkedin.com/company/aotsjapan/) & [Overseas Employment Corporation (OEC)](https://oec.gov.pk/)

---

## 🧠 Topics Covered

- 🐳 Introduction to Docker and Docker Compose
- 🆚 Containers vs Virtual Machines
- 🛠️ Installing Docker on Linux
- 🧱 Building Docker images and running containers
- 📦 Writing Dockerfiles and docker-compose.yml
- 💬 Quiz and Q&A Session

---

## 📘 Recap of Last Week

- 🔁 Control and loop flow statements in Bash
- 📐 Linear Algebra using NumPy
- 📋 Requirement Analysis in Software Development
- 🤖 Machine Learning Algorithms
- 🔄 Software Development Life Cycle
- 🔐 Importance of Security Compliance
- 🖥️ Basic Linux Networking Commands
- 📜 Bash Scripting Essentials

---

## 📦 Docker Overview

### 📌 What is Docker?

Docker is an open-source platform that allows developers to package, ship, and run applications in containers.  
- Contains everything an app needs: code, runtime, system tools  
- Ensures consistency across dev and prod environments

---

### 📌 What is Containerization?

Containerization is a method to bundle applications with their dependencies.  
- Shares host OS kernel  
- Starts quickly and uses fewer resources than VMs  
- Ideal for microservices deployment

---

### 📌 Why Docker?

- 🚫 Eliminates "it works on my machine"
- 🔁 Enables repeatable deployments
- 🧪 Useful in CI/CD and testing environments
- ☁️ Perfect for cloud-native development

---

### 📌 Docker Architecture

- **Docker Engine:** Core engine to run containers  
- **CLI & Daemon:** Interface and management tool  
- **Docker Hub:** Public repository  
- **Dockerfile:** Instructions to build custom containers

---

### 📌 Key Terminology

- **Image:** Template for container  
- **Container:** Instance of image  
- **Volume:** Persistent data storage  
- **Network:** Communication between containers  
- **Dockerfile:** Blueprint to create image

---

## 🧩 Docker Compose

### 📌 Overview

Docker Compose is a tool to define and manage multi-container Docker apps via YAML files.  
- Define services, ports, volumes  
- One command to start/stop the entire environment

**Example:**
```yaml
version: '3'
services:
  web:
    image: nginx
  db:
    image: mysql
```

---

## 🔧 Installing Docker (Linux)

**Requirements:** Linux OS, internet, sudo access

**Steps:**
```bash
sudo apt update
sudo apt install docker.io
sudo systemctl enable docker
sudo systemctl start docker
```

**Test Installation:**
```bash
docker --version
docker run hello-world
```

**To avoid sudo:**
```bash
sudo usermod -aG docker $USER
```

---

## 📂 What is a Dockerfile?

A text file containing instructions to build a Docker image.

### 🛠 Dockerfile Example

```Dockerfile
FROM node:18
COPY . /app
WORKDIR /app
RUN npm install
CMD ["node", "index.js"]
```

**Build and Run:**
```bash
docker build -t my-node-app .
docker run -d -p 3000:3000 my-node-app
docker ps
```

---
## 📁 Docker Compose

Used to manage multi-container applications using a `docker-compose.yml` file.

**Basic Example:**
```yaml
version: '3'
services:
  web:
    image: nginx
    ports:
      - "8080:80"
```

**Multi-Service Example:**
```yaml
version: '3'
services:
  web:
    image: nginx
    ports:
      - "8080:80"
  db:
    image: mysql
    environment:
      MYSQL_ROOT_PASSWORD: root123
```

**Commands:**
```bash
docker-compose up -d
docker-compose down
docker-compose logs
```
---

## 🔬 Practical Assignments

### 🧪 Docker Hello World
```bash
sudo docker pull hello-world
sudo docker run hello-world
```

---

### 🌐 NGINX Example
```bash
sudo docker pull nginx
sudo docker run -p 5000:80 nginx
```

---

### 🐍 Flask App (Dockerized)

**app.py**
```python
from flask import Flask
app = Flask(__name__)
@app.route('/')
def home():
    return "Hello from Flask in Docker!"
app.run(host='0.0.0.0', port=8000)
```

**requirements.txt**
```
flask
```

**Dockerfile**
```Dockerfile
FROM python:3.11-slim
WORKDIR /app
COPY . .
RUN pip install --no-cache-dir -r requirements.txt
EXPOSE 8000
CMD ["python", "app.py"]
```

```bash
sudo docker build -t python_app .
sudo docker run -p 8000:8000 python_app
```

---

### 📦 Node.js App

**index.js**
```js
const express = require('express');
const app = express();
app.get('/', (req, res) => {
  res.send('Hello from Node.js Express!');
});
app.listen(3000, () => {
  console.log('Node app listening on port 3000');
});
```

**package.json**
```json
{
  "name": "node-app",
  "version": "1.0.0",
  "main": "index.js",
  "scripts": {
    "start": "node index.js"
  },
  "dependencies": {
    "express": "^4.17.1"
  }
}
```

**Dockerfile**
```Dockerfile
FROM node:18
WORKDIR /app
COPY . .
RUN npm install
EXPOSE 3000
CMD ["npm", "start"]
```

```bash
sudo docker build -t node_app .
sudo docker run -p 3000:3000 node_app
```

---

### 📄 Task 1
![Task 1 Docker Compose](https://via.placeholder.com/600x300?text=Task+1+-+Basic+Docker+Compose)

Create a basic `docker-compose.yml` file:
```yaml
version: '3'
services:
  web:
    image: nginx
    ports:
      - "8080:80"
```

### 📄 Task 2
![Task 2 Multi-container App](https://via.placeholder.com/600x300?text=Task+2+-+Multi-container+App)

Create a multi-container app:
```yaml
version: '3'
services:
  web:
    image: nginx
    ports:
      - "8080:80"
  db:
    image: mysql
    environment:
      MYSQL_ROOT_PASSWORD: root123
```

---

## 📚 References

- [Docker Docs](https://docs.docker.com/)
- [Dockerfile Reference](https://docs.docker.com/engine/reference/builder/)
- [Docker Compose Guide](https://docs.docker.com/compose/)
