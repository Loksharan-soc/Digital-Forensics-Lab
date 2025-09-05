# FTK Imager & Autopsy Forensic Lab

## Objective
This lab demonstrates a **complete forensic acquisition and analysis workflow** using **FTK Imager** and **Autopsy/Sleuth Kit**. We capture a disk image from a Windows 10 victim VM and perform initial artifact analysis on Ubuntu.

---

## 1️⃣ FTK Imager Installation

**Steps Taken:**
1. Downloaded **FTK Imager 4.7** from Exterro using a `.edu` email.
2. Installed FTK Imager on the **Windows 10 victim VM** using default settings.
3. Verified successful launch of the FTK Imager GUI.

**Metadata Entered During Image Capture:**
- Case Number: `001`
- Evidence Number: `WIN10-VM-01`
- Unique Description: `Windows 10 Victim VM`
- Examiner: `Loksharan Saravanan`
- Notes: `Test forensic acquisition for lab project`

---

## 2️⃣ Disk Image Acquisition

**Procedure:**
1. Opened **FTK Imager → File → Create Disk Image**.
2. Selected **Physical Drive** (C: drive of victim VM).
3. Chose **E01 format** for forensic standard, which includes metadata and hash verification.
4. Set destination on a **separate disk / shared folder** (never the source disk).
5. Enabled **MD5/SHA1 hashing** to maintain integrity.
6. Started acquisition and waited for completion.

> ⚠️ Note: The destination folder must not reside on the disk being imaged.

---

## 3️⃣ Ubuntu Setup for Analysis

**Commands Used:**
```bash
# Update system
sudo apt update && sudo apt upgrade -y

# Install Sleuth Kit CLI + Java dependencies
sudo apt install sleuthkit openjdk-11-jdk unzip wget -y

# Download Autopsy 4.21.0
wget https://github.com/sleuthkit/autopsy/releases/download/autopsy-4.21.0/autopsy-4.21.0.zip

# Unzip to /opt
sudo unzip autopsy-4.21.0.zip -d /opt/

# Set executable permission
sudo chmod +x /opt/autopsy-4.21.0/bin/autopsy

# Launch Autopsy
sudo /opt/autopsy-4.21.0/bin/autopsy
```

**Notes:**
- Autopsy runs as a **web interface** accessible at `http://localhost:9999`.
- Sleuth Kit CLI tools (`fls`, `icat`, `tsk_recover`) are available for command-line analysis.

---

## 4️⃣ Sleuth Kit (TSK) CLI Basics

**Common Commands:**

- **List Partitions:**
```bash
mmls win10-victim.E01
```

- **List Files Recursively:**
```bash
fls -r -m / win10-victim.E01
```

- **Extract a Single File:**
```bash
icat win10-victim.E01 <inode> > recovered_file.txt
```

- **Recover Entire Partition:**
```bash
tsk_recover -a win10-victim.E01 /recovered_files/
```

- **Inspect Metadata:**
```bash
istat win10-victim.E01 <inode>
```

---

## ✅ Current Status
- FTK Imager installed and disk image acquisition in progress.
- Ubuntu VM ready with **Autopsy + Sleuth Kit** for analysis.
- TSK CLI commands verified and ready to process the acquired image.

---

This workflow demonstrates a **professional forensic process**: acquisition, integrity verification, and analysis, making it a strong addition to a cybersecurity portfolio.

