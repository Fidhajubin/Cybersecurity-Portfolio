# INE eJPT – Information Gathering CTF 1


##  Lab Information

- **Platform:** INE
- **Course:** eJPT
- **Module:** Assessment Methodologies
- **Lab:** Information Gathering CTF 1
- **OS:** Kali Linux
- **Target:** target.ine.local


##  Tools Used

| Nmap | Port and service scanning |
| DIRB | Directory enumeration |
| curl | Retrieve website information |
| HTTrack | Download website content |
| Firefox | Browse the target website |

##  Practical Steps

### Scanning Target

nmap -sSCV target.ine.local

**Purpose:** To identify open ports, running services, and service versions.

**Result:** http port open

check HTTP service and web server information.

###  Find robots.txt

curl http://target.ine.local/robots.txt

**Purpose:** To find information and hidden paths listed in robots.txt.

**Result:**got FLAG1


### Find Hidden Directories


dirb http://target.ine.local

**Purpose:** To discover hidden directories and files.

**Result:** Check the discovered paths and investigate interesting directories.


### Find Backup Files

dirb http://target.ine.local -w /usr/share/dirb/wordlists/big.txt -X .bak,.zip,.sql

**Purpose:** To search for publicly accessible backup files.

If a backup file is discovered, retrieve it using:

curl http://target.ine.local/wp-config.bak

**Result:** Inspect the file for information relevant to the lab.


###  Download Website Content

**Install HTTrack:**

sudo apt update
sudo apt install httrack -y

**Download website content:**


httrack http://target.ine.local -O target.html

**List downloaded files:**

ls -la target.html

Find PHP files and read files

Search for flag-like strings


**Purpose:** To download and inspect website files locally.

**Result:** Investigate relevant files and identify the information requested by the challenge.


## Flags

FLAG1{0ef9b34836bb4d62adfea20caaf7a7bb}

FL@G2{8b186b984b4c4f4b853a8b4c08d90ce5}

FLAG3{0ec34fa3d11c43b699a8332a06172e21}

FLAG4{62cb21f80eb74a068720ae43e12fe472}

FLAG5{7c7c4d3838a04f35a1483a8968eed94d}


##  Learning Outcomes

- Learned basic information gathering.
- Understood robots.txt.
- Practiced Nmap scanning.
- Learned directory enumeration using DIRB.
- Identified potentially exposed backup files.
- Downloaded website content using HTTrack.
- Practiced website reconnaissance.

##  Conclusion

This lab helped me understand the basics of information gathering using Kali Linux.

I learned how to collect website information, identify services, discover directories, and inspect website files.

These skills are useful for penetration testing and SOC-related security investigations.


