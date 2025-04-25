# 🚀 Class 13 - AWS EC2 Virtual Server Setup

![Course Badge](https://img.shields.io/badge/Course-IT%20%26%20Japanese%20Language-blue)  
![Date Badge](https://img.shields.io/badge/Date-April%2019%2C%202025-brightgreen)  
![Platform Badge](https://img.shields.io/badge/Platform-AWS%20EC2-yellow)  

**👨‍🏫 Instructors:** [Mr. Yasir Nawaz](https://www.linkedin.com/in/yasirnawaz1/), [Mr. Mahmood Iqbal](https://www.linkedin.com/in/mahmood-iqbal-55299849/)  
**🎓 Organized by:** Plus W 株式会社 & Pakistan Japan Centre  
**🌐 Supported by:** AOTS & Overseas Employment Corporation (OEC)  

---

## 🧠 What We Learned Last Week

- 🔁 Control & loop flow statements in Python  
- ➕ Linear algebra using NumPy  
- 🔍 Dataset inspection and understanding  
- 💡 Importance of requirement analysis  
- ✅ Practices for effective requirement gathering  
- 🤖 Overview of machine learning algorithms  
- 🛠️ Software Development Life Cycle (SDLC)  
- 🌊 Gitflow, Waterfall & Agile methodologies  
- 🔒 Introduction to Security Compliance  

---

## 📅 Today's Agenda

- ☁️ Intro to AWS & EC2  
- 🐧 Comparing Linux Distros (Ubuntu, Amazon Linux, CentOS, Rocky)  
- 🧾 Creating an AWS account + Free Tier explained  
- ⚙️ Step-by-step: Launching EC2 instance  
- 🔐 Creating & managing SSH key pairs  
- 💻 Connecting via terminal (SSH)  
- ❓ Q&A + Quiz session  

---

## 🛠️ EC2 Setup - Quick Reference

### 🔸 1. Create AWS Account  
- [aws.amazon.com](https://aws.amazon.com)

### 🔸 2. Launch EC2 Instance  
- Choose AMI (e.g. Ubuntu 22.04 LTS)  
- Instance type: `t3.micro` (Free Tier)  
- Security group: allow port `22` (SSH)  
- Create key pair: download `.pem`

### 🔸 3. Connect via Terminal / Git Bash  
```bash
chmod 400 your-key.pem
ssh -i "your-key.pem" ubuntu@<Your-Public-IP>
