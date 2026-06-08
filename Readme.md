# 🚀 Enterprise CI/CD Automation Platform

## 📌 Project Overview

This project demonstrates a complete Continuous Integration and Continuous Deployment (CI/CD) pipeline using GitHub, Jenkins, AWS EC2, and Nginx.

The platform automatically deploys website changes from GitHub to an AWS-hosted web server whenever code is pushed to the repository.

This project simulates a real-world DevOps workflow where manual deployments are eliminated through automation.

![](./img/overview%20image.png)

---

## 🏗️ Architecture

```text
Developer
    │
    ▼
GitHub Repository
    │
    ▼
GitHub Webhook
    │
    ▼
Jenkins Server (AWS EC2)
    │
    ▼
Build & Deployment
    │
    ▼
Nginx Web Server
    │
    ▼
Live Website
```

---

## 🛠️ Technologies Used

* AWS EC2
* Jenkins
* Git
* GitHub
* Linux (Ubuntu)
* Nginx
* Bash Scripting

---

## 🎯 Key Features

✅ Automated Deployment

✅ Continuous Integration

✅ Continuous Delivery

✅ GitHub Integration

✅ Jenkins Automation

✅ Nginx Web Hosting

✅ Real-Time Code Deployment

---

# 📂 Project Structure

```bash
enterprise-devops-platform/
│
├── index.html
├── README.md
└── assets/
```

---

# ⚙️ Jenkins Deployment Script

```bash
#!/bin/bash

echo "Starting Deployment..."

echo "Current Workspace:"
pwd

echo "Listing Workspace Files:"
ls -la

echo "Deploying Files to Nginx..."

cp -rvf * /var/www/html/

echo "Deployment Completed Successfully!"
```

---

# 🚀 EC2 Setup

![](./img/jenkins%20sserver.png)

## Update Server

```bash
sudo apt update
sudo apt upgrade -y
```

## Install Git

```bash
sudo apt install git -y
```

## Install Java

```bash
sudo apt install openjdk-17-jdk -y
```

## Verify Java

```bash
java -version
```

---

# 🚀 Jenkins Installation

```bash
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
/usr/share/keyrings/jenkins-keyring.asc > /dev/null
```

```bash
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
/etc/apt/sources.list.d/jenkins.list > /dev/null
```

```bash
sudo apt update
sudo apt install jenkins -y
```

```bash
sudo systemctl enable jenkins
sudo systemctl start jenkins
```
![](./img/installation%20jenkins.png)


---

# 🌐 Install Nginx

```bash
sudo apt install nginx -y
```

```bash
sudo systemctl enable nginx
sudo systemctl start nginx
```

![](./img/nginx%20installation.png)

---

# 🔐 Jenkins Permissions

```bash
sudo chown -R jenkins:jenkins /var/www/html
```

---

# ⚡ CI/CD Workflow

### Step 1

Developer pushes code to GitHub.

```bash
git add .
git commit -m "website updated"
git push origin main
```

### Step 2

GitHub Webhook triggers Jenkins Job.

### Step 3

Jenkins pulls latest source code.

### Step 4

Deployment script executes.

### Step 5

Files are copied to Nginx Web Root.

### Step 6

Website is updated automatically.

![](./img/cicd%20pipeline.png)

![](./img/output%20with%20changes.png)

---

# 📋 Jenkins Job Configuration

## Source Code Management

```text
Git
Repository URL:
https://github.com/rohandhenge/enterprise-devops-platform
```

---

## Build Trigger

```text
GitHub hook trigger for GITScm polling
```

![](./img/github%20webhook%20log.png)

---

## Build Step

```bash
#!/bin/bash

cp -rvf * /var/www/html/
```

---

# 🔥 Challenges Faced

### Issue 1

Build failed due to incorrect deployment path.

```bash
cp: cannot stat 'workspace/*'
```

### Solution

Updated deployment script to use Jenkins workspace directly.

---

### Issue 2

Website returned 404 Not Found.

### Root Cause

Nginx web root did not contain index.html.

### Solution

Configured Jenkins deployment script to copy files into:

```bash
/var/www/html/
```

---

### Issue 3

Permission Denied Error

### Solution

```bash
sudo chown -R jenkins:jenkins /var/www/html
```

---

# 📈 Learning Outcomes

* Jenkins Installation & Configuration
* GitHub Integration
* CI/CD Concepts
* Automated Deployments
* Linux Administration
* AWS EC2 Management
* Nginx Web Hosting
* Troubleshooting Real Deployment Issues
s
---

# 👨‍💻 Author

**Rohan Dhenge**

AWS | DevOps | Cloud Computing

Building Real-World DevOps Projects 🚀
