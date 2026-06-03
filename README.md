# FIT2173 A2 Report

This repository contains a LaTeX-built report for the FIT2173 Assignment 2 penetration testing and threat modelling task.

The report is based on the **Basic Pentesting: 1** lab machine and includes:

- Q1 penetration testing findings with student-captured screenshot evidence.
- Q2 threat modelling for a medical wearable diagnosis system.
- Two TikZ data flow diagrams (DFDs): an original Level 2/3 DFD and a mitigated DFD.
- A machine-readable PDF generated from LaTeX.

## Important Submission Note

Before submitting the PDF, replace the placeholders in the cover page:

```text
[Your Name]
[Student ID]
[UnitCode]
```

The final submission filename should follow the assignment format:

```text
[Your Name]-[Student ID]-[UnitCode]-A2.pdf
```

Only submit the final PDF unless the teaching team explicitly asks for LaTeX source files.

## Repository Contents

```text
.
├── README.md
├── .gitignore
└── outputs/
    ├── A2-latex-report.pdf
    ├── A2-latex-report.tex
    └── A2-latex-source.zip
```

### Key Files

| File | Purpose |
|---|---|
| `outputs/A2-latex-report.pdf` | Final LaTeX-generated PDF draft. This is the main file to review and rename before submission. |
| `outputs/A2-latex-report.tex` | Main LaTeX source file. It includes the written report and TikZ DFD diagrams. |
| `outputs/A2-latex-source.zip` | Portable source package containing the `.tex` file and all screenshot figures used by the report. |

## Report Structure

The PDF is organised into two major sections.

### Q1 Penetration Testing

The Q1 report is structured around three confirmed vulnerabilities:

1. **WordPress Username Enumeration**
   - WPScan identified the `admin` WordPress user without authentication.
   - Severity: Medium.

2. **Default WordPress Administrative Credentials Leading to RCE**
   - The WordPress account accepted `admin/admin`.
   - Administrative access was used with the WordPress admin shell upload module.
   - The exploit resulted in a `www-data` shell.
   - Severity: Critical.

3. **ProFTPD 1.3.3c Backdoor Command Execution**
   - Nmap identified ProFTPD 1.3.3c on port 21.
   - Searchsploit and Metasploit confirmed a backdoor command execution path.
   - Exploitation resulted in a root shell.
   - Severity: Critical.

The `/etc/passwd` permission check is **not** listed as a vulnerability because the student evidence showed:

```text
NOT WRITABLE
```

### Q2 Threat Modelling

The Q2 section models a medical wearable diagnosis system and includes:

- External entities:
  - Patient
  - Clinician
- Processes:
  - Wearable Device
  - Mobile Application
  - Cloud API
  - Authentication Service
  - ML Inference Service
  - Report Service
- Data stores:
  - Diagnosis Report Database
  - Audit Log Store
- Trust boundaries:
  - Wearable Device Boundary
  - Bluetooth Wireless Boundary
  - Mobile Device Boundary
  - Public Internet Boundary
  - Cloud Environment Boundary
  - Database Boundary

The threat table includes four STRIDE categories:

- Information Disclosure
- Spoofing
- Tampering
- Denial of Service

The mitigated DFD adds controls such as:

- M1: BLE Secure Pairing
- M2: TLS
- M3: MFA + RBAC
- M4: Encryption at Rest + KMS
- M5: Input Validation
- M6: Rate Limiting
- M7: Audit Logging

## How to Rebuild the PDF

The report was compiled with [Tectonic](https://tectonic-typesetting.github.io/), a modern LaTeX engine that downloads required LaTeX packages automatically.

If Tectonic is installed and available in your terminal:

```powershell
cd outputs
tectonic A2-latex-report.tex
```

If using the included source zip:

```powershell
Expand-Archive .\A2-latex-source.zip -DestinationPath .\A2-latex-source
cd .\A2-latex-source
tectonic A2-latex-report.tex
```

The generated PDF should be machine-readable, meaning text can be selected and copied.

## Evidence and Academic Integrity

The screenshots embedded in the report are intended to reflect the student's own lab execution. Do not replace them with walkthrough screenshots or copied evidence from another student.

The report includes a GenAI declaration. The student should review the declaration and ensure it accurately reflects their actual use of AI assistance before submission.

## Final Review Checklist

Before submitting:

- Replace `[Your Name]`, `[Student ID]`, and `[UnitCode]`.
- Rename the PDF to the required assignment filename.
- Open the PDF and confirm text can be selected/copied.
- Check that all screenshot captions are visible.
- Confirm the Vulnerability List includes CVSS 3.0 scores and page numbers.
- Confirm Q2 includes both the original DFD and the mitigated DFD.
- Submit only the final PDF unless source files are explicitly requested.

## References Used in the Report

The report cites:

- NIST NVD CVE-2010-20103
- Rapid7 WordPress Admin Shell Upload module documentation
- WPScan user documentation
- FIRST CVSS v3.0 calculator
- Oracle VirtualBox documentation
- Kali Linux VirtualBox documentation
- VulnHub Basic Pentesting: 1
