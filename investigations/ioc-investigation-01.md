# IOC Investigation Report
**Date:** 5th June 2026 
**Analyst:** Natasha  
**Classification:** TLP:WHITE 

---

## 1. Overview

This report documents the investigation of three indicators of compromise
(IOCs) using open-source threat intelligence platforms: VirusTotal,
AbuseIPDB, and AlienVault OTX.

---

## 2. Indicators Analyzed

| # | Indicator | Type | Verdict |
|---|-----------|------|---------|
| 1 | 185.220.101.34 | IP Address | MALICIOUS |
| 2 | malware-c2-update.com | Domain | SUSPICIOUS |
| 3 | 275a021bbfb6489e54d471899f7db9d1663fc695ec2fe2a2c4538aabf651fd0f | File Hash | TEST FILE |

---

## 3. Detailed Findings

### IOC 1 - IP Address: 185.220.101.34

**VirusTotal**
- Flagged by 15 out of 91 security vendors
- Vendor categories: Malicious, Phishing, Malware
- Community score: -25 (actively flagged by the security community)
- Tag: Tor exit node

**AbuseIPDB**
- Reported 8,431 times by the security community
- Abuse confidence score: 100% (maximum)
- ISP: Network for Tor-Exit traffic
- Hostname: tor-exit-34.for-privacy.net
- Location: Berlin, Germany (AS60729)

**AlienVault OTX**
- 50 threat intelligence pulses referencing this IP
- Verdict: TOR Node
- Related attack tags: BruteForce, SSH attacks, web app attack,
  webscanner, Honeypot
- 7 domains historically resolved to this IP

**Analyst Assessment:**
This IP is a confirmed Tor exit node with a 100% abuse confidence
score and over 8,000 community reports. It has been associated with
brute force attacks, SSH scanning, phishing, and malware delivery
across 50 separate threat intelligence reports. Any internal host
communicating with this IP should be treated as a high-priority
incident requiring immediate escalation.

---

### IOC 2 - File Hash: 275a021b...651fd0f

**VirusTotal**
- Flagged by 65 out of 67 security vendors
- Threat label: virus.eicar/test
- Threat categories: Virus, Trojan
- Family labels: eicar, test, file
- File size: 68 bytes
- Distributed by: OffSec Services Limited
- Tags: powershell, attachment, via-tor, detect-debug-environment

**Analyst Assessment:**
This hash belongs to the EICAR test file — a standardised, harmless
string used to verify antivirus detection capability. It is NOT real
malware and cannot cause damage. However, its presence in an
environment warrants attention for two reasons:

1. It may indicate legitimate IT staff testing AV coverage
2. It could indicate an attacker probing defences before deploying
   real malware — checking whether security tools will trigger

Context is critical here. If this file appeared on an endpoint
without authorisation, the next step would be to identify who
executed it, from where, and what followed immediately after.

---

## 4. Summary & Recommended Actions

| IOC | Verdict | Priority | Recommended Action |
|-----|---------|----------|--------------------|
| 185.220.101.34 | Malicious | 🔴 HIGH | Block at firewall. Investigate any internal host that communicated with this IP. Escalate immediately. |
| malware-c2-update.com | Suspicious | 🟡 MEDIUM | Block at DNS layer. Check proxy logs for any internal requests. |
| EICAR hash | Test file | 🟢 LOW | Verify whether authorised IT testing. If unauthorised, investigate who executed it and what ran before/after. |

---

## 5. Tools Used

| Tool | Purpose |
|------|---------|
| VirusTotal | Multi-vendor malware and IP reputation scanning |
| AbuseIPDB | Community-sourced IP abuse reporting |
| AlienVault OTX | Threat intelligence pulses and attack campaign correlation |

---

## 6. Key Takeaway

A single IOC rarely tells the full story. Cross-referencing across
multiple platforms builds confidence in your verdict. In this case,
all three platforms agreed on the IP - 100% confidence, 50 threat
pulses, 15 vendor flags. That level of corroboration means escalation
is the only correct action.
