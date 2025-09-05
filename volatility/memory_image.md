# Memory Image Documentation

## 1. Memory Image Overview
- **File Name:** `memdump.raw`
- **Type:** Physical memory dump
- **Operating System:** Windows (build number: 0x65f4)
- **Purpose of Capture:** Forensic analysis for system processes, malware detection, and overall memory inspection.
- **Capture Tool:** WinPmem (version: 1.0-rc2)

## 2. System Information at Time of Capture
- **CR3 (Page Directory Base):** 0x1ae000
- **Kernel Base Address:** 0xfffff800bdc00000
- **KPCR Addresses:**
  - 0xfffff8004e6c5000
  - 0xffffb601c4fe0000
  - 0xffffb601c5451000
- **NtBuildNumber Address:** 0xfffff800bea0a5ac

## 3. Memory Capture Details
- **Command Used:**
```powershell
.\go-winpmem_amd64_1.0-rc2_signed.exe acquire C:\MemoryDumps\memdump.raw
```
- **Memory Ranges Captured:**
| Base Address       | Number of Bytes   |
|------------------|----------------|
| 0x1000           | 0x9f000        |
| 0x100000         | 0xde45f000     |
| 0xde5a8000       | 0x545000       |
| 0xdedff000       | 0x36f000       |
| 0x100000000      | 0x20000000     |

- **Sparse Output File:** `C:\MemoryDumps\memdump.raw`
- **Time to Complete:** ~5.89 seconds

## 4. Capture Process
1. Driver written to temporary location: `C:\Users\VBOXUS~1\AppData\Local\Temp\2584639463.sys`
2. Service `winpmem` installed and started
3. Memory pages copied (sparse capture) with padding for unmapped regions
4. Service stopped and driver removed

## 5. Notes / Observations
- The capture was successful and completed quickly.
- Sparse capture ensures that large unused memory areas were skipped efficiently.
- No errors or warnings during the process.

