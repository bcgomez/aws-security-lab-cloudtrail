# 🔐 AWS Security Lab: Incident Investigation with CloudTrail

## 📌 Overview

This project demonstrates how to detect, analyze, and investigate a security incident in AWS using **CloudTrail**.

A simulated attack is performed by modifying Security Group rules, exposing a web server and allowing unauthorized changes.

---

## 🧰 Technologies Used

- Amazon EC2
- Security Groups
- AWS CloudTrail
- Amazon S3

---

## 🧩 1. EC2 Instance Deployment

An EC2 instance was launched to host a web application.

![EC2 Instances](./images/01-ec2-instances.png)

---

## 🔐 2. Initial Security Configuration

The Security Group initially allowed only HTTP traffic (port 80), restricting access to the application.

![Initial Security Group](./images/02-security-group-initial.png)

---

## ⚠️ 3. Security Group Modification (Attack Vector)

An inbound rule was added allowing SSH access (port 22) from an external IP.

This change exposed the instance to potential unauthorized access.

![Modified Security Group](./images/03-security-group-modified.png)

---

## 🌐 4. Web Server Validation

The web server was accessed successfully using the public IP address.

![Web Server Running](./images/04-web-server-running.png)

---

## ☕ 5. Normal Application State

The application displayed its original content correctly.

![Normal Café Page](./images/05-cafe-page-normal.png)

---

## 🚨 6. Compromised Application

After unauthorized access, the application content was modified.

This demonstrates the impact of insecure configurations.

![Hacked Café Page](./images/06-cafe-page-hacked.png)

---

## 🕵️ 7. CloudTrail Activation

CloudTrail was enabled to log all activity within the AWS environment.

This is critical for auditing and forensic analysis.

![CloudTrail Created](./images/07-cloudtrail-created.png)

---

## 📊 8. Event History Analysis

CloudTrail logs revealed multiple actions related to Security Group changes.

The event `AuthorizeSecurityGroupIngress` was identified as a key indicator of compromise.

![Event History](./images/08-event-history.png)

---

## 🔍 9. Detailed Event Investigation

The suspicious event was analyzed in detail.

### Key Findings:
- **Event Name:** AuthorizeSecurityGroupIngress  
- **User:** Barbara_Catalina_Gomez_Perez  
- **Source IP:** 181.53.96.117  
- **Resource:** Security Group (sg-0740f4f52b0ec1c9d)  

This confirms that the attack originated from an external IP and modified inbound rules.

![Event Detail](./images/09-event-detail.png)

---

## 🧠 Key Learnings

- Misconfigured Security Groups can expose infrastructure
- CloudTrail is essential for auditing and investigation
- Monitoring changes in real-time is critical for security
- Even simple misconfigurations can lead to full compromise

---

## 🚀 Conclusion

This lab simulates a real-world cloud security incident and demonstrates how to:

- Detect unauthorized access
- Investigate security events
- Understand the importance of cloud monitoring tools

---

## 👩‍💻 Author

**Barbara Catalina Gomez Perez**  
Cloud / DevOps / Security Learner 🚀
