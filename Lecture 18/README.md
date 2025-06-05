# 🚀 Class 18 - Containerizing Web Applications using AWS, GitHub & Docker

![Course Badge](https://img.shields.io/badge/Course-IT%20%26%20Japanese%20Language-blue)  
![Date Badge](https://img.shields.io/badge/Date-May%2031%2C%202025-brightgreen)  
![Platform Badge](https://img.shields.io/badge/Platform-AWS%20%7C%20Docker%20%7C%20GitHub-lightgrey)

**👨‍🏫 Instructors:** [Hafiz Muhammad Umair Munir](https://www.linkedin.com/in/hafiz-muhammad-umair-munir-b929b0173/), [Abdul Ahad](https://www.linkedin.com/in/ahad-pro-soft/), [Abdul Hanan Ashraf](https://www.linkedin.com/in/abdul-hanan-ashraf-156115157/)  
**🎓 Organized by:** [Plus W 株式会社](https://www.linkedin.com/company/plus-w) & [Pakistan Japan Centre](https://www.linkedin.com/company/pakistan-japan-centre)  
**🌐 Supported by:** [AOTS](https://www.linkedin.com/company/aotsjapan/) & [Overseas Employment Corporation (OEC)](https://oec.gov.pk/)

---

## 🧠 Topics Covered

- 📁 Cloning GitHub repositories for deployment  
- 📦 Dockerizing Django applications  
- ⛅️ Deploying Django apps on AWS EC2  
- ⚖️ EC2 Security group configuration  
- 🧰 Understanding `ALLOWED_HOSTS` and its usage  
- 🧲 Docker Compose usage and setup  
- 🔹 Live Quiz & Q&A session  

---

## 📊 Recap: Last Week

- ⏭ Control & Loop Flow in Bash  
- ✘ Linear Algebra using NumPy  
- 🧰 Importance of Requirement Analysis  
- 📅 Software Development Life Cycle  
- 🔒 Security Compliance Importance  
- 🔹 Linux & Networking Commands  
- 🔄 Bash Scripting Introduction  
- 📦 Docker & Docker Compose Basics  

---

## 📚 Class Content Walkthrough

### 🔹 Cloning GitHub Repository & Local Setup
1. Login to Azure and go to EC2
![EC2 select](images/1%20Select%20EC2.png)

2. Select Launch Instance
![Launch Instance](images/2%20Select%20Launch%20Instance.png)

3. Enter a name and select Ubuntu
![Create Instance](images/3%20Create%20Instance%20P1.png)
Select Launch Instance
![Create Instance](images/3%20Create%20Instance%20P2.png)

4. Go to the instances tab, select the instance and click connect
![Connect to Instance](images/4%20Connect%20to%20Instance%20P1.png)
Click on the SSH client tab and copy the command
![Connect to Instance](images/4%20Connect%20to%20Instance%20P2.png)
Paste the command in your terminal and run it
![Connect to Instance](images/4%20Connect%20to%20Instance%20P3.png)

5. Update Ubuntu with the command:
```bash
sudo apt update
```
![Update Ubuntu](images/5%20update%20ubuntu%20P1.png)
![Update Ubuntu](images/5%20update%20ubuntu%20P2.png)

6. Upgrade Ubuntu with the command:
```bash
sudo apt upgrade -y
```
![Update Ubuntu](images/6%20upgrade%20ubuntu%20P1.png)
![Update Ubuntu](images/6%20upgrade%20ubuntu%20P2.png)
![Update Ubuntu](images/6%20upgrade%20ubuntu%20P3.png)

7. Reboot the instance and reconnect to it
![Update Ubuntu](images/7%20reboot%20and%20reconnect.png)

8. Check for any files with the `ls` command.

- Clone the Github repo
- Confirm the files are there with the `ls` command again
- enter the django-todo folder
```bash
cd django-todo
```
- Check the files with the `ls` command
- Check if Pyhton is installed with
```bash
python --version
```
- Enter the Python shell by typing `python3`
- Check if Django is installed with
```Python
import django
```
- Exit the shell by press `Ctrl + D`
- Check if pip is installed by typing
```bash
pip --version
```

![GitHub Clone and Stuff](images/8%20Clone%20and%20others.png)


9. Install pip with
```bash
sudo apt install python3-pip
```
- Check if pip is installed correctly with
```bash
pip --version
```
![Pip Version Check](images/9%20check%20pip%20version.png)

10. Install py-venv with the command
```bash
sudo apt install python3.12-venv -y
```
![install py-venv Check](images/10%20install%20py%20venv.png)

11. Create a virtual environment with the command
```bash
python3 -m venv myenv
```
- Enter the virtual environment with
```bash
source myenv/bin/activate
```
- Install Django in the virtual environment
```bash
pip3 install django
```
- Enter the `django-todo` folder
![run py venv install django](images/11%20run%20py%20venv%20install%20django.png)

---

### 💻 Running Django App

12. Run the following commands
```bash
python manage.py makemigrations
python manage.py migrate
```
![Local Server](images/12%20makemigrations%20migrate.png)
---

### ☁️ Deploying on AWS EC2

13. In the instances tab, select the instance and copy the public ipv4 address in the details tab
![AWS EC2 IP](images/13%20edit%20settings.py%20P1.png)
- Open the `todoApp` folder
- Open the `settings.py` file in an editor
![AWS EC2 IP](images/13%20edit%20settings.py%20P2.png)
- Paste the instance public ip in `ALLOWED_HOSTS` in single quotes ' '
![AWS EC2 IP](images/13%20edit%20settings.py%20P3.png)

---

### 🌐 Making App Publicly Accessible

14. Select the instance, go into the Security tab and select Security Groups
![App Public Access](images/14%20exposing%20port%208000%20P1.png)
- In Inbound rules, select Edit inbound rules
![App Public Access](images/14%20exposing%20port%208000%20P2.png)
- Select Add rule, set it to Custom TCP, Port range to 8000, Source to anywhere and Click Save rules
![App Public Access](images/14%20exposing%20port%208000%20P3.png)

15. To run the app, type the following command

```bash
python3 manage.py runserver 0.0.0.0:8000
```
![Run Server](images/15%20runserver.png)

16. In a browser, enter the public IP of the instance followed by the port number 8000
![Run Server](images/16%20run%20app%20P1.png)
![Run Server](images/16%20run%20app%20P2.png)

17. To kill the server, run the following command
```bash
sudo kill -9 $(sudo lsof -t -i :8000)
``` 
![Kill Server](images/17%20kill%20server%20P1.png)
![Kill Server](images/17%20kill%20server%20P2.png)

---

## 🛠️ Dockerizing the Django App

### 📂 Dockerfile Example

![Dockerfile Code](images/dockerfile.png)

```dockerfile
FROM python:3
RUN pip install django

COPY . .

RUN python manage.py makemigrations
RUN python manage.py migrate

RUN ["python", "manage.py", "runserver", "0.0.0.0:8001"]
```

---

### 🚀 Build & Run Docker Image

![Docker Run](images/docker-run.png)

```bash
sudo docker build . -t todo-app
sudo docker run -p 8001:8001 todo-app
```

---
