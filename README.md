# 🚀 AWS EC2 + Application Load Balancer Setup

## 📌 Project Overview

This project demonstrates how to deploy a web application using **AWS EC2** behind an **Application Load Balancer (ALB)**, ensuring secure and controlled access through **port 80 (HTTP)**.

The infrastructure is designed following basic DevOps best practices:

* Traffic is routed through a Load Balancer
* Direct access to EC2 is restricted
* Security Groups are configured for controlled access
* Target Group is used for routing requests

---

## 🏗️ Architecture

```
Client (Browser)
        │
        ▼
Application Load Balancer (Port 80)
        │
        ▼
Target Group
        │
        ▼
EC2 Instance (Nginx Web Server)
```

---

## ⚙️ Components Used

### 1. EC2 Instance

* Hosted a web server (Nginx)
* No direct public access (restricted via Security Group)

---

### 2. Application Load Balancer (ALB)

* Listens on **HTTP (Port 80)**
* Routes incoming traffic to the target group

---

### 3. Target Group

* Contains EC2 instance(s)
* Performs health checks
* Routes traffic from ALB to EC2

---

### 4. Security Groups

#### ALB Security Group

* Allows:

  * **Inbound:** Port 80 (HTTP) from anywhere (0.0.0.0/0)
* Purpose:

  * Accept traffic from users

#### EC2 Security Group

* Allows:

  * **Inbound:** Port 80 only from ALB Security Group
* Purpose:

  * Prevent direct access to EC2
  * Only ALB can communicate with EC2

---

## 🔒 Security Design

* EC2 is **not publicly exposed**
* Only ALB can send traffic to EC2
* Users access the application via ALB DNS

---

## 🚀 Setup Steps

1. Launch EC2 instance
2. Install and configure Nginx
3. Create Security Groups:

   * ALB SG (allow HTTP from internet)
   * EC2 SG (allow HTTP only from ALB SG)
4. Create Target Group

   * Register EC2 instance
5. Create Application Load Balancer

   * Attach ALB SG
   * Configure listener on port 80
   * Forward requests to target group
6. Access application using ALB DNS

---

## 🌐 Access the Application

Use the **ALB DNS name** in your browser:

```
http://<your-alb-dns-name>
```

---

## 📷 Expected Output

* Nginx default page OR your deployed application
* Accessible only via Load Balancer

---

## 🧠 Key Learnings

* Difference between **Security Group** and **Target Group**
* How **ALB routes traffic**
* How to **secure EC2 instances**
* Basic **AWS networking and architecture**

---

## 📌 Future Improvements

* Add HTTPS (SSL using ACM)
* Auto Scaling Group
* Deploy real application instead of Nginx default page
* Use Terraform for automation

---


## 👨‍💻 Author

Nagendra BS

---

## ⭐ If you like this project

Give it a star ⭐ on GitHub!
