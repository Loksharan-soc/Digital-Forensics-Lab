# Disk Image Acquisition Lab

## Objective
The goal of this lab is to **capture a complete forensic disk image** of a Windows 10 victim VM using **FTK Imager**, preserving data integrity for analysis with Autopsy and Sleuth Kit.

---

## Tools Used
- **FTK Imager 4.7** (Windows)
- **Disk Type:** Physical Drive (C:)
- **Image Format:** E01 (EnCase Evidence File)
- **Hashing:** MD5 & SHA1

---

## Image Acquisition Steps
1. Open **FTK Imager** → `File` → `Create Disk Image`.
2. Select the **Physical Drive** (C: drive of Windows 10 victim VM).
3. Choose **E01 format** to preserve metadata and enable segmenting.
4. Fill in metadata:
   - Case Number: `001`
   - Evidence Number: `WIN10-VM-01`
   - Unique Description: `Windows 10 Victim VM`
   - Examiner: `Loksharan Saravanan`
   - Notes: `Test forensic acquisition for lab project`
5. Set **destination folder** on a separate disk or shared folder (never the source disk).
6. Enable **MD5 and SHA1 hashing** to ensure integrity.
7. Start the acquisition and wait for completion.

> ⚠️ Note: Destination folder must not reside on the disk being imaged.

---

## Image Details
- **Total Size:** 49 GB
- **Number of Segments:** 34 (`win10-victim.E01` → `win10-victim.E34`)
- **Storage Location:** Shared folder on host machine
- **Hashes:** Copy MD5 & SHA1 values from FTK Imager log for verification

---

## Verification
- Verify integrity of the acquired image using terminal commands:
```bash
md5sum win10-victim.E01
sha1sum win10-victim.E01
```
- Ensure all 34 segments are present in the same folder.

---

## Observations / Notes
- All E01 segments must remain together for analysis.
- The E01 format preserves forensic metadata and supports hash verification.
- The disk image is now ready for **Autopsy import** or **TSK CLI analysis**.
- Using a shared folder avoids storage limitations on the Ubuntu VM.

---

This documentation provides a clear, step-by-step record of **forensic disk acquisition**, suitable for portfolio or GitHub projects.

