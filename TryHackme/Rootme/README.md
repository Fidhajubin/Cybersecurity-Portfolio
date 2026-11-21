
## RootMe

Lab Information

Platform:TryHackMe

Room: RootMe

Difficulty:Easy

Category:Web Exploitation / Privilege Escalation

Target IP:10.10.XX.XX

Tools Used:Nmap, Gobuster, Netcat

 ## Objective
The objective was to enumerate the target machine, identify web vulnerabilities, gain initial access, and perform privilege escalation to obtain root access.

## Reconnaissance
Started with Nmap to identify open ports and running services.

nmap -sSCV 10.10.XX.XX

Finding:Identified the available services and open ports for further enumeration.

## Directory Enumeration

Used Gobuster to discover hidden directories on the web server.

gobuster dir -u http://10.10.XX.XX -w /usr/share/wordlists/dirb/common.txt

Finding: Discovered directories that helped identify potential attack points.

## Initial Access
Investigated the file upload functionality and identified an opportunity to exploit unrestricted file uploads using a PHP reverse shell.

Started a Netcat listener:
nc -lvnp 4444

Successfully established a reverse shell connection.

## Privilege Escalation
Enumerated SUID binaries to identify possible privilege escalation opportunities.

find / -perm -4000 -type f 2>/dev/null

Investigated the results to obtain higher privileges and achieve root access.

## Flags
 User Flag: [Add your flag]
 
 Root Flag: [Add your flag]

 Key Learnings
- Nmap scanning and service enumeration.
- Directory brute-forcing using Gobuster.
- File upload vulnerability exploitation.
- PHP reverse shell and Netcat.
- Linux enumeration and SUID privilege escalation.
