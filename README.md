# 🔐 AWS Security Lab: Incident Investigation with CloudTrail

This project simulates a real-world AWS security incident where a web server was modified without authorization. The investigation was conducted using AWS CloudTrail, EC2, and Security Groups.

---

## 🚨 Problem Statement

A web server hosted on AWS EC2 was unexpectedly modified, displaying unauthorized content.

The goal of this lab is to:
- Identify the source of the change
- Analyze the security breach
- Use AWS CloudTrail to investigate the incident

---

## 🏗️ Environment Setup

- Amazon EC2 instance (Web Server)
- Security Groups configured for HTTP and SSH
- Public access enabled (port 80)
- Web application deployed (Café website)

---

## 🔄 Step-by-Step Investigation

---

### 🔹 Step 1: EC2 Instance Deployment

The EC2 instance was launched and configured to host a web server.

![EC2 Instances](images/01-ec2-instances.png)

---

### 🔹 Step 2: Initial Security Group Configuration

The security group initially allowed:
- HTTP (port 80) from anywhere (`0.0.0.0/0`)
- SSH (port 22) from a specific IP

![Initial Security Group](images/02-security-group-initial.png)

---

### 🔹 Step 3: Modified Security Group

Changes were made to the security group rules, enabling broader access.

![Modified Security Group](images/03-security-group-modified.png)

---

### 🔹 Step 4: Web Server Running

The web server was successfully deployed and accessible via public IP.

![Web Server Running](images/04-web-server-running.png)

---

### 🔹 Step 5: Normal Website Behavior

The café website was functioning correctly.

![Normal Website](images/05-cafe-page-normal.png)

---

### 🔹 Step 6: Website Compromised

Unexpected content appeared on the website, indicating a potential security breach.

![Hacked Website](images/06-cafe-page-hacked.png)

---

### 🔹 Step 7: CloudTrail Enabled

AWS CloudTrail was configured to log all events for investigation.

![CloudTrail Setup](images/07-cloudtrail-created.png)

---

### 🔹 Step 8: Event History Analysis

CloudTrail logs were reviewed to identify suspicious activity.

![Event History](images/08-event-history.png)

---

### 🔹 Step 9: Event Detail Investigation

Detailed event analysis revealed:
- The action performed: `AuthorizeSecurityGroupIngress`
- Source IP address involved
- User and service responsible for the change

![Event Detail](images/09-event-detail.png)

---

## 🔍 Investigation Findings

- The EC2 instance was publicly accessible via HTTP
- Unauthorized content appeared on the web application
- CloudTrail logs captured security group modification events
- The source IP address of the action was identified
- The change allowed broader access to the server

---

## ⚠️ Root Cause

The security group allowed unrestricted inbound access (`0.0.0.0/0`) on port 80, exposing the web server to the public internet and increasing the risk of unauthorized modifications.

---

## 🛡️ Mitigation Actions

- Restricted inbound traffic to trusted IP addresses only
- Enabled CloudTrail for continuous monitoring
- Reviewed and hardened Security Group configurations
- Reduced unnecessary public exposure of services

---

## 📚 Key Learnings

- Importance of properly configuring Security Groups
- Risks of exposing services to the public internet
- How to use CloudTrail for forensic investigation
- Basics of incident detection and response in AWS
- Understanding how misconfigurations can lead to vulnerabilities

---

## 🚀 Future Improvements

- Implement CloudWatch alerts for suspicious activity
- Apply IAM least privilege principles
- Automate infrastructure using Terraform
- Add AWS Config for compliance monitoring

---

## 💡 Conclusion

This lab demonstrates how misconfigured security settings can lead to vulnerabilities and highlights the importance of monitoring, logging, and proper access control in cloud environments.

---

## 👩‍💻 Author

**Barbara Gomez**  
Aspiring Cloud & DevOps Engineer 🚀  
