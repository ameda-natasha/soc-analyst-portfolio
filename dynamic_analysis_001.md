# Dynamic Malware Analysis Report: Remcos RAT & RedLine Stealer

**Date:** 2026-06-20  
**Analyst:** Ameda Natasha  
**Sandbox Used:** ANY.RUN  
**Sample Hash (SHA256):** 1cfa0be60378ba94c6753d535b15fb6fd34944c9d3f0f12a1e60097d588d566c  

## 1. Executive Summary
A malicious sample identified as Remote Access Trojan was detonated in a Windows 10 sandbox environment. 
The malware exhibited behavior consistent with an Information Stealer, specifically establishing outbound Command and Control (C2) communications and dropping secondary payloads.

## 2. Process Execution Tree
* `svchost.exe` (PID: 2232)  
  * `sihost.exe` (PID: 4412)  
    * `explorer.exe` (PID: 4696)  
    * `RuntimeBroker.exe` (PID: 5232)    

## 3. Network Indicators (IOCs)
* **Malicious Domains:** `http://crl.microsoft.com/pki/crl/products/MicRooCerAut2011_2011_03_22.crl`
* **C2 IP Addresses:** `[224.0.0.251 : 5353 `

## 4. Host Indicators (IOCs)
*What files should the antivirus look for?*
* **Dropped Files:** `svchost.exe.exe`
* **Registry Keys Modified:** `C:\Users\admin\AppData\Local\Temp\Rar$EXa7944.88663\prueba.exe`

## 5. MITRE ATT&CK Mapping
* **Execution:** T1047 - Windows Management Instrumentation
* **Persistence:** T1053.005 - Scheduled Task/job 1/6
