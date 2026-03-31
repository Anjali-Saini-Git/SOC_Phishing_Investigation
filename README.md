# SOC Phishing Investigation: HR Policy Update

A practical incident response project demonstrating real-world phishing email analysis, forensics, and threat assessment procedures following industry best practices.

---

## Project Overview

This project documents a complete phishing investigation workflow from initial alert to final incident report. It simulates a realistic SOC L1 analyst scenario where a suspicious email requires thorough investigation to determine legitimacy and threat level.

**Objective**: Analyze a phishing email claiming to be an HR policy update, identify indicators of compromise (IOCs), assess malicious intent, and document findings for escalation.

---

## Investigation Steps

### 1. Email Header Analysis
- **Tool**: PhishTool
- **Analysis**: SPF, DKIM, DMARC authentication failures
- **Findings**: Email spoofing detected - sender domain not authenticated
- **IOC**: Sender domain mismatch with display name

### 2. Payload Analysis
- **Suspicious Element**: `help.pdf.py` file (Python double-extension exploit)
- **Technique**: Using legitimate file extension (.pdf) to disguise executable (.py)
- **Risk**: If executed, would run arbitrary Python code on victim's machine

### 3. URL & Link Analysis
- **Suspicious URL**: Credential-harvesting redirect
- **Detection Method**: VirusTotal URL scanning
- **Verdict**: Malicious domain confirmed with high threat score

### 4. File Hash Verification
- **Hash Type**: SHA-256
- **Tool**: VirusTotal
- **Result**: File hash flagged by multiple antivirus engines as malicious

### 5. Domain Reputation Check
- **Tool**: WHOIS lookup
- **Findings**: Newly registered domain with no legitimate history
- **Risk Assessment**: High - typical behavior of malicious domains

---

## Tools Used

| Tool | Purpose | Finding |
|------|---------|---------|
| **PhishTool** | Email header forensics | SPF/DKIM/DMARC failures |
| **VirusTotal** | File & URL scanning | Malicious verdict |
| **WHOIS** | Domain registration data | Suspicious domain history |
| **Email Headers** | Metadata analysis | Spoofed sender |

---

## Investigation Results

### Email Classification
- **Status**: **MALICIOUS** 
- **Threat Level**: **HIGH**
- **Action**: DELETE & BLOCK

### Indicators of Compromise (IOCs)
```
Sender Domain: fake-hr-update.net
File Hash (SHA256): [hash_from_analysis]
Malicious URL: http://[credential-harvest-site.com]/login
File Name: help.pdf.py
```

### Attack Chain
1. Spoof HR sender identity
2. Social engineering via urgent policy update
3. Double-extension file trick to evade detection
4. Credential harvesting via fake login redirect
5. Potential system compromise via Python script execution

---

## Incident Report Template

```
INCIDENT REPORT - PHISHING EMAIL

SUMMARY:
Suspicious phishing email attempting to harvest credentials and potentially 
execute malicious code on victim system.

EMAIL DETAILS:
- From: fake-hr-update.net
- Subject: [Original Subject]
- Received: [Date/Time]
- Headers: Spoofed, SPF/DKIM failed

MALICIOUS ELEMENTS:
1. Double-extension executable (help.pdf.py)
2. Credential harvesting URL
3. Spoofed sender domain

RECOMMENDATION:
- DELETE all instances from user mailboxes
- BLOCK sender domain
- Alert affected users to change passwords
- Monitor for lateral movement indicators
```

---

## Key Learnings

### Email Spoofing
- Attackers spoof legitimate company domains
- Authentication protocols (SPF, DKIM, DMARC) are essential first defense
- Header analysis reveals true sender path

### File Type Tricks
- Double extensions hide malicious intent
- Always verify file hashes even if extension seems legitimate
- Users should be trained on suspicious file patterns

### OSINT & Threat Intelligence
- Domain registration data reveals intent
- File reputation databases accelerate threat assessment
- Multiple data sources provide comprehensive threat picture

### Incident Response Procedures
- Follow structured investigation methodology
- Document all findings with evidence
- Escalate with clear recommendations
- Think like an attacker to understand tactics

---

## Resources & References

- [MITRE ATT&CK - Phishing (T1566)](https://attack.mitre.org/techniques/T1566/)
- [Cyber Kill Chain - Reconnaissance & Weaponization](https://www.lockheedmartin.com/en-us/capabilities/cyber/cyber-kill-chain.html)
- [Email Authentication Standards](https://support.google.com/a/answer/33786)
  - SPF (Sender Policy Framework)
  - DKIM (DomainKeys Identified Mail)
  - DMARC (Domain-based Message Authentication, Reporting and Conformance)

---

## Related Documentation

- [PhishTool User Guide](https://www.phishtool.com/)
- [VirusTotal API Documentation](https://developers.virustotal.com/)
- [WHOIS Lookup Guide](https://www.whois.com/)

---

## Skills Developed

✓ Email forensics and header analysis  
✓ Phishing investigation procedures  
✓ OSINT and threat intelligence gathering  
✓ Malicious file identification  
✓ Structured incident reporting  
✓ SOC L1 alert triage workflow  
✓ Incident response fundamentals  

---

**Author**: Anjali Saini  
**Status**: Complete Investigation Case Study
**Role**: Cybersecurity Student / Aspiring SOC Analyst
