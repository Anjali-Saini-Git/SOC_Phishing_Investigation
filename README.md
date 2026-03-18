# SOC Analyst Phishing Investigation: HR Policy Update

## Project Overview
This repository contains a full-scope SOC investigation of a targeted phishing campaign. The attack leveraged a compromised internal account to distribute a malicious Python payload and a credential-harvesting link.

## Tools Used
**PhishTool**: For deep email header forensics, attachment analysis, and URL reputation checks.
**VirusTotal**: For verifying malicious file hashes and domain reputation.
**WHOIS**: For domain registration investigation.

## Repository Structure
**Artifacts/**: Contains the raw phishing email sample.
**Evidence/**: Screenshots from PhishTool documenting the investigation (Headers, URLs, and Hashes).
**Report/**: The final SOC Investigation Report answering the 10 core investigation questions.

## Key Findings
**Attack Vector**: Internal Phishing via compromised account `23csu141@ncuindia.edu`.
**Malicious Artifacts**:
    **File**: `help.pdf.py` (Python executable disguised with a double extension).
    **URL**: A redirect from a look-alike domain to `evil.com`.
**Authentication**: Found SPF, DKIM, and DMARC failures, indicating a lack of email security validation.

## Remediation Strategy
1. **Containment**: Recommended blocking malicious domains and quarantining the email from all user inboxes.
2. **Account Security**: Recommended immediate disablement and password reset for the compromised sender account.
3. **User Protection**: Alerted the 7 targeted recipients to prevent interaction with the links/attachments.

---
**Author**: Anjali Saini
**Role**: Cybersecurity Student / Aspiring SOC Analyst
