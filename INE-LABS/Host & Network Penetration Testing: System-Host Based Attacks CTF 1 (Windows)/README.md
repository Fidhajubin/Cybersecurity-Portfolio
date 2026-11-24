

## 1. Introduction
This CTF is part of the INE/eJPT Host & Network Penetration Testing module.

The main objective is to identify services, find weak credentials, access Windows systems, explore files, and capture hidden flags.

## 2. Objectives
- Identify running services on target machines.
- Perform password attacks.
- Enumerate SMB shares.
- Access WebDAV directories.
- Explore Windows files and directories.
- Capture all four flags.

## 3. Target Machines
- `target1.ine.local`
- `target2.ine.local`

## 4. Tools Used
- Nmap
- Hydra
- Cadaver
- Davtest
- Metasploit
  
## 5. CTF Walkthrough

### Flag 1: Brute-Forcing Bob's Credentials

**Objective:** Find the weak password of the user `bob`.

hydra -l bob -P /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt target1.ine.local http-get

After finding the password, access the WebDAV directory.

cadaver http://target1.ine.local/webdav/

After successful login, enumerate the directory and locate Flag 1.

### Flag 2: Exploring the C: Drive

**Objective:** Find the flag stored on the Windows C: drive.

First, test the WebDAV upload permissions.

davtest -auth bob:password_123321 -url http://target1.ine.local/webdav/

An ASP webshell can be uploaded if the server allows it.

Use the webshell to execute commands and read the flag.

type C:\flag2.txt

Flag 2 is successfully captured.

### Flag 3: SMB Enumeration and Credential Attack


Use the Metasploit SMB login module:

msfconsole

search smb_login

use auxiliary/scanner/smb/smb_login

Configure the required options:

- `RHOSTS` –target2.ine.local
- `USER_FILE` – Username wordlist.
- `PASS_FILE` – Password wordlist.
- `CreateSession` – Enable session creation.

Run the module to identify valid credentials.

After successful authentication, enumerate available SMB shares and locate Flag 3.

### Flag 4: Searching the Administrator Desktop

**Objective:** Find the flag inside the Administrator's Desktop directory.

After gaining SMB access:

1. Navigate to the `Users` directory.
2. Open the `Administrator` directory.
3. Navigate to `Desktop`.
4. List the available files.
5. Read the flag file using the `cat` command.

Flag 4 is successfully captured.

## 6. Key Learnings

Through this CTF, I learned:

- How to perform password attacks using Hydra.
- How to access and enumerate WebDAV directories.
- How to test WebDAV upload permissions using Davtest.
- How to perform SMB authentication testing.
- How to enumerate Windows shares.
- How to explore Windows directories and locate sensitive files.
- How to use Metasploit for system-based attacks.

## 7. Conclusion

This CTF helped me understand Windows host-based attacks, password testing, WebDAV enumeration, and SMB security testing.

It provided practical experience in identifying weak credentials, accessing services, exploring Windows systems, and capturing flags.

