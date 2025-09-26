# Lab 01 – Applying the Daubert Standard to Forensic Evidence (4e)

## Introduction
One legal standard that is key to forensics and too often overlooked in forensic books is the **Daubert standard**. This standard is used by a trial judge to make a preliminary assessment of whether an expert’s scientific testimony is based on reasoning or methodology that is scientifically valid and can properly be applied to the facts at issue.  

Under this standard, the following factors may be considered in determining whether the methodology is valid:
- Has the theory or technique in question been tested?
- Has the theory or technique been subjected to peer review and publication?
- Does the theory or technique have any known or potential errors?
- Does the theory or technique adhere to the maintenance of standards controlling its operation?
- Has the theory or technique attracted widespread acceptance within a relevant scientific community?

Established in 1993 as a result of the Supreme Court case **Daubert v. Merrell Dow Pharmaceuticals, Inc. (509 U.S. 579)**, the Daubert standard is the test currently used in federal and most state courts. Because the Daubert standard requires that scientific evidence presented in court be generally accepted in the field, it is unlikely that new tools would be immediately approved for use in court. For this reason, it is important that a forensic investigator be familiar with emerging technologies and developments in the field of forensic techniques.

In this lab, you will act as a forensic specialist assisting the lead forensics investigator at the Cyber Crimes Division (CCD) of the Boston Police Department. You have been given a hard drive image taken from a seized computer suspected to contain evidence of a sophisticated drug trafficking operation. First, you will review the search warrant and complete the Chain of Custody form that accompanies the evidence drive. You will then prepare the contents of the seized hard drive image as evidence in accordance with the Daubert standard using a variety of forensic tools.

---

## Lab Overview
**Section 1** of this lab has three parts, which should be completed in the order specified:
1. Review a search warrant and complete a Chain of Custody form for seized evidence.
2. Use FTK Imager to create hash codes for suspicious files.
3. Validate the hash codes using Paraben's E3.

**Section 2** allows you to apply what you learned in Section 1 with less guidance and different deliverables, as well as expanded tasks and alternative methods. You will:
- Explore the suspect’s drive image to locate additional evidence.
- Use **Autopsy** to validate the hash codes created during your preliminary investigation.

**Section 3** allows you to explore the virtual environment independently and answer questions and challenges that simulate real-world investigation tasks.

---

## Learning Objectives
Upon completing this lab, you will be able to:
- Prepare evidence for court and complete forms used in evidence handling.
- Understand how a judge will determine the admissibility of evidence using the Daubert standard.
- Import a drive image as evidence using digital forensics software.
- Identify suspicious files as evidence using digital forensics software.
- Create hash codes to verify the integrity of forensic evidence.

---

## Topology
This lab contains the following virtual machines:
- **vWorkstation (Windows Server 2019)**

![Network Topology](1622666045223_mceclip29.png)

---

## Tools and Software
The following software/utilities are required to complete this lab:
- **FTK Imager**
- **Paraben's E3**
- **Autopsy**

Students are encouraged to explore the Internet to learn more about these forensic tools.

---

## Deliverables
### Section 1
- Lab Report file with screen captures of:
  - Contents of the search warrant in Adobe Reader
  - Completed Chain of Custody form in Adobe Reader
  - Contents of the `0002665_hash.csv` file
  - Contents of the `RecycleBinEvidence_hash.csv` file
  - Contents of the `MyRussianMafiaBuddies_hash.csv` file
  - Contents of the `Nice guys_hash.csv` file
  - MD5 and SHA1 values for the `MyRussianMafiaBuddies.txt` file
  - MD5 and SHA1 values for the `Nice Guys.png` file

- Additional written analysis:
  - Describe how the hash values produced by E3 for the incriminating files compare to those produced by FTK. Do they match?

### Section 2
- Lab Report file with screen captures of:
  - Contents of the suspicious email file in the Display pane
  - Two hash values for the suspicious email file
  - MD5 field in the Result Viewer
  - MD5 value produced by E3

- Additional written analysis:
  - Describe how the hash value produced by Autopsy compares to the values produced by FTK Imager for the two `.eml` files.
  - Describe how the hash value produced by E3 compares to the values produced by FTK Imager for the two `.eml` files and the value produced by Autopsy.

### Section 3
- Lab Report file with screen captures of:
  - Hash values for the `Evidence_drive1.001` file

- Additional written analysis:
  - Define the original file names and file paths for each of the three files.

