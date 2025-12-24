# Attack-Detection-and-Hardening-of-a-Cloud-Based-Enterprise-Environment

📌 Project Description

This project demonstrates a **complete cyber security workflow** involving **attack simulation, detection, investigation, and security hardening** in a **cloud-based enterprise environment** deployed on **Microsoft Azure**.

A deliberately vulnerable infrastructure was created to simulate a real-world organization. Various cyber-attacks were performed to generate security events, which were analyzed using system and application logs. Based on the findings, security misconfigurations were identified and remediated. The effectiveness of the applied security controls was validated by re-performing the same attacks and comparing system behavior before and after hardening.

---

## 🎯 Objectives

* Deploy a cloud-based enterprise infrastructure
* Simulate real-world cyber-attacks
* Generate and analyze security logs
* Identify vulnerabilities and misconfigurations
* Apply security hardening techniques
* Validate security improvements through re-attack

---

## 🏗️ System Architecture

### Infrastructure Overview

| Virtual Machine | Role             | Purpose                      |
| --------------- | ---------------- | ---------------------------- |
| VM1             | Internal Server  | Identity & internal services |
| VM2             | Web Server (DMZ) | Primary attack target        |
| VM3             | SIEM / Analyst   | Log monitoring and analysis  |

### Network Design

* **Azure Virtual Network (VNet)**
* **Internal Subnet** → VM1, VM3
* **DMZ Subnet** → VM2

📸 *Architecture and configuration screenshots are included in the project report.*

---

## 🔴 Red Team – Attack Simulation (Phase 1)

The following attacks were performed on the Web Server (VM2):

### 1. SSH Brute Force Attack

* Multiple invalid login attempts using non-existing users
* Logs generated in `/var/log/auth.log`

### 2. Directory Traversal Attack

* Attempts to access sensitive system files using manipulated URLs
* Logged in Apache access logs

### 3. Port Scanning

* Open ports and running services identified using **Nmap**

---

## 🔵 Blue Team – Investigation & Log Analysis (Phase 2)

### Logs Analyzed

* Authentication logs (`auth.log`)
* Apache access logs
* Apache error logs

### Indicators of Compromise (IOC)

| Indicator       | Value                                |
| --------------- | ------------------------------------ |
| Attacker IP     | 127.0.0.1                            |
| Attack Types    | SSH brute force, Directory traversal |
| Tools Used      | SSH, curl, Nmap                      |
| Target Services | SSH, Apache                          |

---

## ⚠️ Misconfigurations Identified

* Password-based SSH authentication enabled
* No firewall rules applied
* Apache server information disclosure
* Excessive file permissions

---

## 🔐 Security Hardening (Phase 3)

### SSH Hardening

* Root login disabled
* Password authentication disabled

### Firewall Configuration

* UFW firewall enabled
* Only required ports (SSH and HTTP) allowed

### Web Server Hardening

* Apache server tokens hidden
* Server signature disabled

### File Permission Hardening

* Least privilege permissions applied to web directories

---

## 🔁 Re-Attack & Validation (Phase 4)

The same attacks were repeated after applying security hardening.

### Observations

* SSH brute-force attempts blocked
* Directory traversal attempts denied
* Reduced attack surface
* Cleaner and controlled log entries

### Before vs After Comparison

| Parameter | Before Hardening      | After Hardening |
| --------- | --------------------- | --------------- |
| SSH       | Vulnerable            | Secured         |
| Firewall  | Disabled              | Enabled         |
| Apache    | Information Disclosed | Hidden          |
| Logs      | Noisy                 | Controlled      |

---

## ✅ Final Security Posture

After hardening, the system demonstrated a **significantly improved security posture**. Attack attempts were effectively blocked or detected, and logging mechanisms provided clear visibility into security events.

---

## 🛠️ Technologies Used

* Microsoft Azure
* Linux (Ubuntu)
* Apache Web Server
* SSH
* UFW Firewall
* Nmap
* Log Analysis & SOC Concepts

---

## 🏁 Conclusion

This project successfully demonstrates **real-world cyber-attack simulation**, **log-based detection**, **vulnerability identification**, **security hardening**, and **post-hardening validation** in a cloud environment. It provides hands-on experience with both **Red Team and Blue Team operations**, closely aligned with SOC-level practices.

---

## 📚 References

* Linux System Administration Documentation
* Apache Security Guide
* Azure Virtual Machine Documentation
* SIEM and SOC Fundamentals

---

## 👩‍💻 Author

**Minakshi Sinha**
B.Tech – Cyber Security (5th Semester)
Rungta College of Engineering & Technology, Bhilai
Academic Year: 2025–26

