# Volatility 3 Memory Analysis Lab

**Lab Date:** 2025-09-04  
**Memory Dump:** `memdump.raw`  
**Tool:** Volatility 3 Framework 2.26.0  
**OS Analyzed:** Windows

---

## 1. Overview

This lab focuses on analyzing a Windows memory dump using Volatility 3. The goal is to investigate running processes, detect suspicious memory regions, and identify potential malware or anomalies in memory.

---

## 2. Commands Executed and Observations

### 2.1 List Running Processes
**Command:**
```bash
vol -f memdump.raw windows.pslist
```
**Purpose:**
- Lists all active processes and their process IDs.

**Observations:**
- Normal system processes like `csrss.exe`, `winlogon.exe`, and `lsass.exe` detected.
- Security-related processes identified: `MsMpEng.exe` (Windows Defender) and `splunkd.exe`.
- Noted PIDs for further analysis.

---

### 2.2 Detect Suspicious Memory (Malfind)
**Command:**
```bash
vol -f memdump.raw windows.malfind
```
**Purpose:**
- Detects memory regions marked as executable and writable, which may indicate code injection or malware.

**Observations:**
- `MsMpEng.exe` shows multiple VADs with `PAGE_EXECUTE_READWRITE` protection.
- Hex dumps show patterns suggesting potential injected code.
- `splunkd.exe` has a smaller suspicious executable region.
- File output for dumps is currently disabled but can be enabled for deeper investigation.

---

### 2.3 Notes on Plugin Availability
- Attempted `windows.chromehistory` plugin from Volatility 2; it is not available in Volatility 3.
- Volatility 3 uses different plugin naming conventions; some older plugins do not exist.

---

## 3. Summary of Findings
- Multiple suspicious memory regions found in `MsMpEng.exe` and a smaller one in `splunkd.exe`.
- No confirmed malware yet, but `malfind` highlights areas that require further analysis.
- Understanding VADs, protection flags, and commit size is essential for memory forensics.

---

## 4. Recommended Next Steps
1. Investigate loaded modules using:
```bash
vol -f memdump.raw windows.dlllist
```
2. Check open handles for suspicious memory regions:
```bash
vol -f memdump.raw windows.handles
```
3. Dump suspicious memory regions for offline analysis:
```bash
vol -f memdump.raw windows.malfind --dump
```
4. Explore registry-related plugins for process artifacts:
```bash
vol -f memdump.raw windows.registry.*
```
5. Scan network activity for suspicious processes:
```bash
vol -f memdump.raw windows.netscan
```

---

*This document is part of the ongoing Volatility 3 memory analysis exercises for Windows forensic investigations.*

