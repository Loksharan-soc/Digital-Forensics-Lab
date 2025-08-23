# Tools Used in Cyber Forensic Lab

This document lists all the tools used in the **Cyber Forensic Lab**, along with their purpose, usage, and download links.

| Tool | Purpose | Notes / Download |
|------|---------|-----------------|
| **FTK Imager (Lite)** | Disk imaging | Create `.E01` or `.dd` disk images of the victim VM. Free version for labs: [FTK Imager Download](https://accessdata.com/product-download/ftk-imager-version-4-5) |
| **Autopsy** | Disk forensics analysis | Open-source GUI tool to analyze disk images, timelines, deleted files, registry, etc. Download: [Autopsy](https://www.sleuthkit.org/autopsy/) |
| **WinPmem** | Memory acquisition | Open-source tool to capture RAM memory dumps (`.raw`) from Windows systems. Download: [WinPmem GitHub](https://github.com/Velocidex/WinPmem) |
| **Volatility 3** | Memory forensics | Open-source framework to analyze memory dumps, detect processes, injected DLLs, network connections, etc. Download: [Volatility 3](https://github.com/volatilityfoundation/volatility3) |
| **VirtualBox / VMware** | VM environment | Run Victim (Windows), Analyst (Ubuntu), and Attacker (Kali) VMs for lab simulations. |
| **Kali Linux** | Attack simulations | Simulate attacks against the victim VM to generate artifacts for analysis. Download: [Kali Linux](https://www.kali.org/get-kali/) |

---

### **Notes**
- All tools used in this lab are **free for educational purposes**, except enterprise versions of FTK and Volatility which are optional in professional environments.  
- Ensure that the **Victim VM** has FTK Imager and WinPmem installed, and the **Analyst VM** has Autopsy and Volatility installed.  
- Kali Linux is optional, used only if performing attack simulations.


# Installation & Setup for Cyber Forensic Lab Tools

This document explains how to **install and set up the four primary forensic tools** used in the lab: FTK Imager, WinPmem, Autopsy, and Volatility 3.

---

## FTK Imager (Lite) – Disk Imaging

**VM:** Victim VM (Windows)
**Purpose:** Create disk images (`.E01` or `.dd`) of the victim system.

**Installation Steps:**

1. Download FTK Imager Lite from [AccessData](https://accessdata.com/product-download/ftk-imager-version-4-5).
2. Run the installer (`FTKImagerSetup.exe`).
3. Follow the prompts to complete installation.
4. Launch FTK Imager to verify it opens successfully.

**Notes:**

* Run FTK Imager as **Administrator** to access all drives.

---

## WinPmem – Memory Acquisition

**VM:** Victim VM (Windows)
**Purpose:** Capture RAM memory dumps for analysis.

**Installation Steps:**

1. Download WinPmem from [GitHub](https://github.com/Velocidex/WinPmem).
2. Extract the ZIP file to a folder on the Victim VM.
3. Open **PowerShell or Command Prompt as Administrator**.
4. Test the executable:

```powershell
winpmem_2.1.exe -h
```

to see available options.

**Usage:**

```powershell
winpmem.exe --output <path>\memory.raw
```

* Replace `<path>` with the folder where you want to save the memory dump.
* Save the dump in a **shared folder** accessible to the Analyst VM.

---

## Autopsy – Disk Forensics Analysis

**VM:** Analyst VM (Ubuntu / Linux)
**Purpose:** Analyze disk images for files, deleted data, registry, and timelines.

**Installation Steps (Ubuntu Example):**

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install autopsy sleuthkit -y
autopsy --version
```

**Usage:**

* Launch Autopsy with:

```bash
autopsy
```

* Open your disk image (`.E01` or `.dd`) to start analysis.

---

## Volatility 3 – Memory Forensics Analysis

**VM:** Analyst VM (Ubuntu / Linux)
**Purpose:** Analyze memory dumps to find running processes, injected DLLs, network connections, etc.

**Installation Steps (Ubuntu Example):**

```bash
sudo apt install python3 python3-pip -y
git clone https://github.com/volatilityfoundation/volatility3.git
cd volatility3
pip3 install -r requirements.txt
python3 vol.py -h
```

**Usage:**

* Run analysis on memory dumps:

```bash
python3 vol.py -f <memory.raw> windows.pslist
```

* Replace `<memory.raw>` with your memory image path.

---

### Summary

* **Victim VM:** FTK Imager + WinPmem
* **Analyst VM:** Autopsy + Volatility 3
* **Notes:** Always analyze **copies of images**, never the live system.
