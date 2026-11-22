# INE / eJPT – Enumeration CTF 1

## 📌 Lab Overview
This lab focuses on enumeration techniques used in penetration testing. The main goal is to discover open ports, services, users, and hidden information.

## 🎯 Objectives
- Identify open ports and services.
- Enumerate SMB shares.
- Find valid usernames and passwords.
- Enumerate FTP services.
- Capture all four flags.

## 🛠️ Tools Used
- Nmap
- SMBClient
- SMBMap
- Enum4linux
- Hydra
- Netcat

##  Practical Steps

### 1. Port Scanning
Identify open ports and running services.

nmap -sSCV Target.ine.local

### 2. SMB Enumeration
Find available SMB shares.

smbclient -L //target.ine.local -N

Enumerate SMB users:

enum4linux -a Target.ine.local

### 3. FTP Enumeration
Identify FTP services and test access.

nmap -p- target.ine.local

Connect to FTP:

ftp Target.ine.local

### 4. SSH Enumeration
Connect to the SSH service and check the login banner.

ssh alice@target.ine.local

## 🚩 Flags Captured

FLAG1{4355fe8f1b3c4212a3874205687ae1eb}

FLAG2{fc3c6eca1bf1413d9b3b3bcd27bf7743}

FLAG3{ae89f2e407cb49d39783c04a3a54688e}

FLAG4{27db16d4c5524052ba98bfab09b1f550} 


## 📚 Key Learnings
- Network scanning using Nmap.
- SMB share and user enumeration.
- FTP service enumeration.
- Understanding enumeration techniques.

## 🏁 Conclusion
This lab helped me understand basic enumeration techniques and gain practical experience with different cybersecurity tools.

