# Simulation #1: Memory Acquisition with WinPmem

**Objective:** Capture a full memory dump from a Windows victim VM for forensic analysis.

---

## Lab Setup

**Windows Victim VM:**
- OS: Windows 10/11
- Tools Installed:
  - FTK Imager (for disk imaging)
  - WinPmem (memory acquisition)

**Folder Structure:**
```
C:\
├─ ForensicTools\
│   ├─ FTKImager\
│   └─ WinPmem\
└─ MemoryDumps\
```

---

## Step 1: Download WinPmem

- Official GitHub release: [WinPmem Releases](https://github.com/Velocidex/WinPmem/releases)
- File used: `go-winpmem_amd64_1.0-rc2_signed.exe` (5 MB, signed)

**Safety Check:**
```powershell
Get-FileHash .\go-winpmem_amd64_1.0-rc2_signed.exe -Algorithm SHA256
```
- Verified SHA256 hash against official release.

---

## Step 2: Capture Memory

**Command (PowerShell as Administrator):**
```powershell
cd C:\ForensicTools\WinPmem
.\go-winpmem_amd64_1.0-rc2_signed.exe acquire -v C:\MemoryDumps\memdump.raw
```

**Output:**
- Service installed: `winpmem`
- Memory ranges copied
- Sparse output file created: `C:\MemoryDumps\memdump.raw`
- Service removed automatically

**Result:** Memory dump successfully captured in ~5.9 seconds.

---

## Next Steps

1. Transfer `memdump.raw` to Ubuntu VM for analysis with **Volatility** or other forensic tools.
2. Document and analyze findings in lab report.

---

**Notes:**
- Run all commands as **Administrator** in an isolated VM.
- Keep memory dumps organized in `C:\MemoryDumps\`.

