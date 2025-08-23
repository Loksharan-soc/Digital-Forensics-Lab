# VM Setup for Cyber Forensic Lab

This document describes the **virtual machines (VMs)** used in the Cyber Forensic Lab, including their roles, purposes, and recommended configurations.

---

## **1. Victim VM (Windows)**

**Role:** Target / Agent  
**Purpose:**  
- Simulate a compromised system.  
- Capture **disk and memory images** for analysis.  
- Optional: Receive attacks from Kali VM for lab exercises.  

**Recommended Configuration:**  
- OS: Windows 10 or 11  
- RAM: 4 GB minimum  
- Disk: 40 GB or more  
- Tools Installed:  
  - FTK Imager (Lite) → for disk imaging  
  - WinPmem → for memory acquisition  

**Notes:**  
- Save all images in a dedicated folder on the VM or in a shared folder accessible by the Analyst VM.  

---

## **2. Analyst VM (Ubuntu / Linux)**

**Role:** Manager / Analyst  
**Purpose:**  
- Analyze **disk images** using Autopsy.  
- Analyze **memory dumps** using Volatility 3.  
- Generate reports and document findings.  

**Recommended Configuration:**  
- OS: Ubuntu 22.04 LTS (or similar)  
- RAM: 4 GB minimum  
- Disk: 40 GB or more  
- Tools Installed:  
  - Autopsy → for disk analysis  
  - Volatility 3 → for memory analysis  

**Notes:**  
- This VM should have access to the images from the Victim VM via **shared folders** or network transfer.  
- All analysis should be done on **copies of the images**, never on the live victim VM.  

---

## **3. Attacker VM (Kali Linux)**

**Role:** Attacker / Simulation  
**Purpose:**  
- Simulate attacks on the Victim VM to create artifacts (malware files, scripts, network activity).  
- Helps generate realistic forensic scenarios for the lab.  

**Recommended Configuration:**  
- OS: Kali Linux latest version  
- RAM: 2–4 GB minimum  
- Disk: 20–40 GB  
- Tools Installed: Kali default tools (metasploit, nmap, netcat, etc.)  

**Notes:**  
- This VM is optional if you just want to practice forensic analysis on pre-generated images.  
- Keep attacks safe — only simulate in your lab environment.  

---

### **Summary Table**

| VM | Role | Purpose | Tools |
|----|------|---------|-------|
| Windows VM | Victim / Agent | Capture disk/memory images, target system | FTK Imager, WinPmem |
| Ubuntu VM | Analyst / Manager | Analyze images, generate reports | Autopsy, Volatility 3 |
| Kali VM | Attacker | Simulate attacks, generate artifacts | Kali Linux tools |

---

### **Notes**
- Ensure all VMs are **isolated in a virtual network** to prevent accidental spread of malware.  
- Keep a **shared folder** or **host-mounted folder** for transferring images safely between Victim and Analyst VMs.
