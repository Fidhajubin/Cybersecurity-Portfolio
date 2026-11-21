# TryHackMe – Blue

**Platform:** TryHackMe  
**Difficulty:** Easy  
**Category:** Windows Exploitation  
**Target IP:** 10.10.XX.XX  
**Tools Used:** Nmap, Metasploit, SMB

### Objective
To identify vulnerabilities in a Windows machine, exploit the MS17-010 vulnerability (EternalBlue), and gain access to the target system.

### Methodology

**1. Reconnaissance**

```bash
nmap -sC -sV <TARGET_IP>
```
Scanned the target to identify open ports and running services.

**2. SMB Enumeration**

```bash
nmap --script smb-vuln-ms17-010 -p445 <TARGET_IP>
```
Checked whether the target was vulnerable to MS17-010.

**3. Exploitation**

Used Metasploit to exploit the EternalBlue vulnerability and gain access to the Windows machine.

**4. Access Verification**

```bash
whoami
```
Verified the privileges of the obtained session.

**5. Flag Collection**

Located and collected the required flags from the target machine.

### Key Learnings
- Nmap scanning and enumeration.
- SMB service analysis. 
- EternalBlue exploitation.
- Windows privilege escalation.

