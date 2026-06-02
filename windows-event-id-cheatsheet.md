# Windows Event ID Cheat Sheet

## Authentication Events

### Event ID 4624 - Successful Logon

**Meaning:** User successfully authenticated  
**Attack Mapping:** Account compromise, lateral movement  
**Why SOC Analysts Care:** Tracks successful access to systems and identifies suspicious logins  

### Event ID 4625 - Failed Logon

**Meaning:** Authentication attempt failed  
**Attack Mapping:** Brute force attacks, password spraying  
**Why SOC Analysts Care:** Detect repeated login failures and possible credential attacks

### Event ID 4648 - Logon Using Explicit Credentials

**Meaning:** User attempted authentication using alternate credentials  
**Attack Mapping:** Credential theft, lateral movement  
**Why SOC Analysts Care:** Attackers commonly use stolen credentials to move between systems

### Event ID 4672 - Special Privileges Assigned to New Logon

**Meaning:** Elevated or administrative privileges assigned during login  
**Attack Mapping:** Privilege escalation  
**Why SOC Analysts Care:** Highlights privileged account activity that may be abused

### Event ID 4768 - Kerberos Authentication Ticket Requested

**Meaning:** Ticket Granting Ticket (TGT) requested from domain controller  
**Attack Mapping:** Initial access, authentication monitoring  
**Why SOC Analysts Care:** Useful for tracking authentication activity in Active Directory environments

### Event ID 4769 - Kerberos Service Ticket Requested

**Meaning:** Service ticket requested from Kerberos  
**Attack Mapping:** Kerberoasting attacks  
**Why SOC Analysts Care:** Unusual ticket requests may indicate credential theft attempts

### Event ID 4771 - Kerberos Pre-Authentication Failed

**Meaning:** Kerberos authentication failed before completion  
**Attack Mapping:** Password attacks, brute force  
**Why SOC Analysts Care:** Identifies repeated authentication failures against accounts

### Event ID 4776 - Credential Validation Attempt

**Meaning:** NTLM authentication attempt performed  
**Attack Mapping:** Credential abuse, password attacks  
**Why SOC Analysts Care:** Detects NTLM-based authentication activity and abuse

---

## Account Management Events

### Event ID 4720 - User Account Created

**Meaning:** A new user account was created  
**Attack Mapping:** Persistence, unauthorized access  
**Why SOC Analysts Care:** Attackers may create accounts to maintain access

### Event ID 4724 - Password Reset Attempt

**Meaning:** Password reset was attempted on an account  
**Attack Mapping:** Account takeover, privilege abuse  
**Why SOC Analysts Care:** Unexpected resets may indicate compromised accounts

### Event ID 4728 - User Added to Privileged Group
**Meaning:** User added to security-enabled privileged group  
**Attack Mapping:** Privilege escalation  
**Why SOC Analysts Care:** Detects unauthorized privilege assignments

### Event ID 4738 - User Account Changed
**Meaning:** User account details modified  
**Attack Mapping:** Account manipulation  
**Why SOC Analysts Care:** Identifies suspicious account changes or modifications

---

## Process and Execution Events

### Event ID 4688 - Process Created
**Meaning:** New process started on the system  
**Attack Mapping:** Malware execution, command execution  
**Why SOC Analysts Care:** Essential for identifying suspicious processes and commands

### Event ID 4689 - Process Terminated

**Meaning:** Process execution ended  
**Attack Mapping:** Malware analysis  
**Why SOC Analysts Care:** Helps reconstruct attacker timelines and process chains

### Event ID 4104 - PowerShell Script Block Logging
**Meaning:** PowerShell commands or scripts executed  
**Attack Mapping:** Fileless malware, malicious scripts  
**Why SOC Analysts Care:** Detects attacker use of PowerShell for execution

## Persistence and System Modification Events

### Event ID 7045 - New Service Installed
**Meaning:** New service installed on system  
**Attack Mapping:** Persistence mechanisms  
**Why SOC Analysts Care:** Malware commonly creates services to remain persistent

### Event ID 4698 - Scheduled Task Created
**Meaning:** New scheduled task created  
**Attack Mapping:** Persistence, malware automation  
**Why SOC Analysts Care:** Attackers use scheduled tasks for recurring execution

### Event ID 4719 - Audit Policy Changed
**Meaning:** System auditing configuration modified  
**Attack Mapping:** Defense evasion  
**Why SOC Analysts Care:** Changes to logging policies may indicate attacker activity

### Event ID 1102 - Security Logs Cleared
**Meaning:** Security logs deleted or cleared  
**Attack Mapping:** Defense evasion, anti-forensics  
**Why SOC Analysts Care:** High-priority indicator of suspicious activity

### Event ID 4616 - System Time Changed
**Meaning:** System clock modified  
**Attack Mapping:** Anti-forensics  
**Why SOC Analysts Care:** Attackers sometimes manipulate timestamps to hide activity

## Network and Lateral Movement Events

### Event ID 5140 - Network Share Accessed
**Meaning:** Shared network resource accessed  
**Attack Mapping:** Lateral movement, data theft  
**Why SOC Analysts Care:** Detects suspicious access to shared resources
