
# 🐚 Class 16 - Introduction to Bash Scripting Language & GitHub for AI Engineers

![Course Badge](https://img.shields.io/badge/Course-IT%20%26%20Japanese%20Language-blue)  
![Date Badge](https://img.shields.io/badge/Date-May%2017%2C%202025-brightgreen)  
![Platform Badge](https://img.shields.io/badge/Platform-Bash%20%7C%20Linux%20Terminal%20%7C%20AWS%20EC2-lightgrey)

**👨‍🏫 Instructors:** [Hafiz Muhammad Umair Munir](https://www.linkedin.com/in/hafiz-muhammad-umair-munir-b929b0173/), [Abdul Ahad](https://www.linkedin.com/in/ahad-pro-soft/), [Abdul Hanan Ashraf](https://www.linkedin.com/in/abdul-hanan-ashraf-156115157/)  
**🎓 Organized by:** [Plus W 株式会社](https://www.linkedin.com/company/plus-w) & [Pakistan Japan Centre](https://www.linkedin.com/company/pakistan-japan-centre)  
**🌐 Supported by:** [AOTS](https://www.linkedin.com/company/aotsjapan/) & [Overseas Employment Corporation (OEC)](https://oec.gov.pk/)

---

## 🧠 Topics Covered

- 🐧 Introduction to Shell, Terminal, and Bash
- ✍️ Writing and executing bash scripts
- 🔤 Working with variables and user input
- 🔁 Conditional logic and loops in bash
- ⚙️ Bash functions and error handling
- 📁 Creating practical automation scripts
- 💡 Quiz (20 MCQs) and Q&A session

---

## 💡 Why Use Bash Scripting?

- ✅ Automate repetitive tasks  
- 🧪 Configure and manage servers  
- 🕐 Schedule tasks via cron  
- ⚙️ Lightweight automation in DevOps  

---

## 📁 Class Summary

### 📌 Part 1: What is Bash?

- Bash stands for **Bourne Again SHell**, a widely used Unix shell.
- It acts as a command-line interpreter to interact with the operating system.
- Students explored differences between **shell**, **terminal**, and **console**.

---

### 📌 Part 2: Writing Basic Bash Scripts

**Simple Script:**
```bash
#!/bin/bash
echo "Hello from Bash!"
```

📌 _Output:_

![Part 2 — Basic Bash Script Output](images/part2_basic_script.png)

---

### 📌 Part 3: Using Variables and User Input

**Examples:**
```bash
name="John"
echo "Hello, $name"

read -p "Enter your age: " age
echo "You are $age years old"
```

📌 _Output:_

![Part 3 — Variables and Input](images/part3_variables_input.png)

---

### 📌 Part 4: Conditional Statements and Loops

**Conditionals:**
```bash
if [ $age -ge 18 ]; then
  echo "Adult"
else
  echo "Minor"
fi
```

📌 _Output:_

![Part 4.1 — Conditionals](images/part4_conditionals.png)

**Loops:**
```bash
for i in {1..5}; do
  echo "Number: $i"
done
```

📌 _Output:_

![Part 4.2 — Loops](images/part4_loops.png)

---

### 📌 Part 5: Bash Functions & Script Structure

**Function Declaration:**
```bash
greet() {
  echo "Welcome, $1!"
}
greet "Ali"
```

📌 _Output:_

![Part 5 — Functions](images/part5_functions.png)

---

### 📌 Part 6: Error Handling & Logic Operators

**Example:**
```bash
if [ $? -ne 0 ]; then
  echo "An error occurred."
  exit 1
fi
```

📌 _Output:_

![Part 6 — Error Handling](images/part6_error_handling.png)

---

## 🧪 Practical Tasks

### 🧮 Task 1: Arithmetic Function (`sum.sh`)
```bash
#!/bin/bash
add() {
  echo "Sum is: $(($1 + $2))"
}
add 5 10
```

📌 _Output:_

![Task 1 — Arithmetic Function](images/task1_sum.png)

---

### 👤 Task 2: User Authentication Script (`login.sh`)
```bash
#!/bin/bash
read -p "Enter username: " user
if [ "$user" == "admin" ]; then
  echo "Welcome, admin!"
else
  echo "Access Denied."
fi
```

📌 _Output:_

![Task 2 — User Authentication](images/task2_login.png)

---

### 📦 Task 3: GitHub Cloning Script with Checks
```bash
#!/bin/bash
read -p "Enter GitHub URL: " url
folder=$(basename -s .git "$url")

if [ -d "$folder" ]; then
  echo "Directory $folder already exists."
else
  git clone "$url"
fi
```

📌 _Output:_

![Task 3 — GitHub Cloning Script](images/task3_clone.png)

---

## 📚 References

- [GNU Bash Manual](https://www.gnu.org/software/bash/manual/)
- [Shell Scripting Tutorial](https://www.shellscript.sh/)
- [GitHub Docs](https://docs.github.com/)
