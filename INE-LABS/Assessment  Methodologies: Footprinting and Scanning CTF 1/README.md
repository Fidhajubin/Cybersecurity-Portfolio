
##  Overview

This lab focuses on Footprinting and Scanning, the initial stages of penetration testing.

The objective is to gather information about a target, identify open ports and services, discover hidden files, and retrieve flags.

## 🛠️ Tools Used

- **Nmap** – Port and service scanning
- **Curl** – Web information gathering
- **FTP** – File transfer and access
- **MySQL** – Database enumeration

## Practical Steps

### 1. Network Scanning

Identify open ports and running services.

nmap -sSCV target.ine.local


### 2. Web Footprinting

Check the `robots.txt` file for hidden directories.

curl http://target.ine.local/robots.txt

Access the discovered directory and retrieve the flag.

curl http://target.ine.local/secret-info/flag.txt

### 3. FTP Enumeration

Connect to the FTP server.

ftp target.ine.local

Login using anonymous credentials and list available files.

get flag.txt

get creds.txt

Read the downloaded files and capture flag.


### 4. MySQL Enumeration

Connect to the MySQL server using the credentials discovered from FTP.

mysql -u db_admin -p -h target.ine.local

List available databases.

SHOW DATABASES;

Explore the relevant database and tables to locate the final flag.

##  Flags

FLAG1_8aa2d44d79224fa894a68cf099dbda9c

FLAG2_d1c01423ab474c27b2df2f9b58632ac5

FLAG3_47fa45d4a3ae455682d7f1812190e664

FLAG4_202a4f6fda90420cb3e9e1d149914f8c

## 📚 Key Learnings

- Performing network scans using Nmap.
- Identifying open ports and services.
- Discovering hidden directories.
- Accessing anonymous FTP.
- Retrieving exposed credentials.
- Enumerating MySQL databases.

##  Conclusion

Successfully completed the Footprinting and Scanning CTF 1 lab.

This practical helped me understand how to gather information, identify services, and enumerate a target system during the initial stages of penetration testing.

