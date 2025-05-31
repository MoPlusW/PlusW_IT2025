# 🚀 Class 18 - Containerizing Web Applications using AWS, GitHub & Docker

![Course Badge](https://img.shields.io/badge/Course-IT%20%26%20Japanese%20Language-blue)  
![Date Badge](https://img.shields.io/badge/Date-May%2031%2C%202025-brightgreen)  
![Platform Badge](https://img.shields.io/badge/Platform-AWS%20%7C%20Docker%20%7C%20GitHub-lightgrey)

**👨‍🏫 Instructors:** [Hafiz Muhammad Umair Munir](https://www.linkedin.com/in/hafiz-muhammad-umair-munir-b929b0173/), [Abdul Ahad](https://www.linkedin.com/in/ahad-pro-soft/), [Abdul Hanan Ashraf](https://www.linkedin.com/in/abdul-hanan-ashraf-156115157/)  
**🎓 Organized by:** [Plus W 株式会社](https://www.linkedin.com/company/plus-w) & [Pakistan Japan Centre](https://www.linkedin.com/company/pakistan-japan-centre)  
**🌐 Supported by:** [AOTS](https://www.linkedin.com/company/aotsjapan/) & [Overseas Employment Corporation (OEC)](https://oec.gov.pk/)

---

## 🧠 Topics Covered

![Topics Covered](images/topics-covered.png)

- 📁 Cloning GitHub repositories for deployment  
- 📦 Dockerizing Django applications  
- ⛅️ Deploying Django apps on AWS EC2  
- ⚖️ EC2 Security group configuration  
- 🧰 Understanding `ALLOWED_HOSTS` and its usage  
- 🧲 Docker Compose usage and setup  
- 🔹 Live Quiz & Q&A session  

---

## 📊 Recap: Last Week

![Recap Overview](images/recap-overview.png)

- ⏭ Control & Loop Flow in Bash  
- ✘ Linear Algebra using NumPy  
- 🧰 Importance of Requirement Analysis  
- 📅 Software Development Life Cycle  
- 🔒 Security Compliance Importance  
- 🔹 Linux & Networking Commands  
- 🔄 Bash Scripting Introduction  
- 📦 Docker & Docker Compose Basics  

---

## 📚 Class Content Summary

### 🔹 Cloning GitHub Repository & Local Setup

![GitHub Clone](images/github-clone.png)

```bash
# Clone project
https://github.com/shreys7/django-todo

# Setup virtual environment
sudo apt install python3-virtualenv
python3 -m venv ~/myenv
source ~/myenv/bin/activate

# Navigate and install
cd django-todo
pip install django
```

---

### 💻 Running Django Locally

![Local Server](images/django-local-run.png)

```bash
python manage.py makemigrations
python manage.py migrate
python manage.py runserver
```

---

### ☁️ Deploying on AWS EC2

![AWS EC2 Terminal](images/aws-ec2-deploy.png)

```bash
# SSH into EC2
ssh -i "key.pem" ubuntu@<EC2_PUBLIC_IP>

# Clone repo
git clone https://github.com/shreys7/django-todo.git
cd django-todo
pip3 install django
```

---

### 🌐 Making App Publicly Accessible

![App Public Access](images/public-access.png)

```bash
python3 manage.py runserver 0.0.0.0:8001
```

#### ⚠️ Fix Security Group

![Security Group Settings](images/security-group.png)

- Go to EC2 > Security Groups > Inbound Rules  
- Add Custom TCP Rule:  
  - Port Range: `8001`  
  - Source: `0.0.0.0/0`  

#### ❌ Disallowed Host Error Fix

![Disallowed Hosts](images/disallowed-hosts.png)

```python
# In settings.py
ALLOWED_HOSTS = ['<your-ec2-public-ip>', 'localhost']
# Or
ALLOWED_HOSTS = ['*']
```

---

## 🛠️ Dockerizing the Django App

### 📂 Dockerfile Example

![Dockerfile Code](images/dockerfile.png)

```dockerfile
FROM python:3
RUN pip install django==3.2
COPY . .
RUN python manage.py migrate
CMD ["python", "manage.py", "runserver", "0.0.0.0:8001"]
```

---

### 🚀 Build & Run Docker Image

![Docker Run](images/docker-run.png)

```bash
sudo docker build . -t todo-app
sudo docker run -p 8001:8001 todo-app
```

---
