# Cybersecurity Forensics Lab


## Lab Overview
This lab simulates a Windows system compromise and demonstrates **disk and memory forensics** using:
- FTK Imager → Disk imaging
- Autopsy → Disk analysis
- WinPmem → Memory acquisition
- Volatility → Memory analysis

![Forensics Badge](https://img.shields.io/badge/DFIR-Forensics-blue)
![Autopsy Badge](https://img.shields.io/badge/Tool-Autopsy-orange)
![Volatility Badge](https://img.shields.io/badge/Tool-Volatility-red)

**Objectives:**
- Analyze **disk images** to find malware files, deleted data, and persistence mechanisms using **Autopsy**.
- Analyze **memory dumps** to detect running malware, injected processes, and network connections using **Volatility 3**.
- Simulate attacks from a Kali VM and observe artifacts on the victim system.
- Correlate disk and memory artifacts to identify Indicators of Compromise (IOCs) and suspicious activity.
- Generate professional reports documenting findings and remediation steps.

## Lab Workflow
1. Prepare Windows VM (victim) and Ubuntu/Kali VM (analyst).
2. Capture disk image using FTK Imager or `dd`.
3. Capture memory dump using WinPmem.
4. Analyze disk image in Autopsy.
5. Analyze memory dump in Volatility.
6. Correlate artifacts and generate report.

## Lab Setup

### **Virtual Machines**
| VM | Role | Purpose |
|----|------|---------|
| Windows VM | Victim / Agent | Target system for disk and memory capture |
| Ubuntu VM | Manager / Analyst | Run Autopsy & Volatility, store and analyze images |
| Kali VM | Attacker | Simulate attacks such as malware execution or network scanning |


[Kali VM (Attacker)] 
        |
        v
[Windows VM (Victim/Agent)]
    |          \
    |           --> [Disk Image (.E01/.dd) via FTK Imager] --> [Autopsy Analysis on Ubuntu VM]
    |
    --> [Memory Dump via WinPmem] --> [Volatility Analysis on Ubuntu VM]


**Note on Remote Acquisition:**

In enterprise environments, digital forensic analysts often perform **remote acquisition** of disk and memory images.  
This allows analysts to collect evidence **without directly accessing the live compromised system**, minimizing risk and maintaining system integrity.  

Remote acquisition typically requires **paid enterprise tools** such as:
- FTK Enterprise
- EnCase Enterprise

For this lab, we use **local acquisition on the victim VM** with free tools (FTK Imager Lite and WinPmem),  
and then transfer the images to the analyst VM for analysis.  
This approach is safe, free, and suitable for learning and portfolio purposes.



## Tools used
- [FTK Imager](https://accessdata.com/product-download/ftk-imager-version-4-5)
- [Autopsy](https://www.sleuthkit.org/autopsy/)
- [WinPmem](https://github.com/Velocidex/WinPmem)
- [Volatility 3](https://github.com/volatilityfoundation/volatility3)







