# TryHackMe – Brute It

**Platform:** TryHackMe  
**Difficulty:** Easy  
**Category:** CTF / Penetration Testing  
**Target IP:** 10.10.XX.XX  
**Tools Used:** Nmap, Gobuster, Hydra, John the Ripper, SSH

### Objective
The objective was to enumerate the target machine, brute-force a web login, crack password hashes, gain SSH access and perform privilege escalation to obtain root access.

### Methodology

**1. Reconnaissance**

```bash
nmap -sC -sV <TARGET_IP>
```
Identified open ports and running services.

**2. Directory Enumeration**

```bash
gobuster dir -u http://<TARGET_IP> -w /usr/share/wordlists/dirb/common.txt
```
Discovered hidden directories and investigated the web application.

**3. Password Brute Forcing**

Used Hydra to test login credentials against the discovered login page.

**4. Hash Cracking**

Used John the Ripper to crack the identified password hash.

```bash
john hash.txt --wordlist=/usr/share/wordlists/rockyou.txt
```

**5. Initial Access**

Used the recovered credentials and SSH to access the target machine.

```bash
ssh <USERNAME>@<TARGET_IP>
```

**6. Privilege Escalation**

Checked sudo permissions to identify possible privilege escalation opportunities.

```bash
sudo -l
```

Investigated the available permissions to obtain root access.

### Key Learnings
- Network scanning using Nmap.
- Directory enumeration using Gobuster.
- Password brute-forcing using Hydra.
- Password hash cracking using John the Ripper.
- SSH authentication.
- Linux privilege escalation.

