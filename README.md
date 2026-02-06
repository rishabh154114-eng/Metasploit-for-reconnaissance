# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find out the ip address of the attackers system
## OUTPUT:
<img width="1045" height="468" alt="image" src="https://github.com/user-attachments/assets/719b56ce-9401-4ea7-aa1a-b2395f4c941b" /></br>


Invoke msfconsole:
## OUTPUT:

<img width="1465" height="1014" alt="image" src="https://github.com/user-attachments/assets/b6364fd9-7de2-4ea1-b8a4-4ca32c7ca8b2" /> </br>

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.




Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000  (Replace with appropriate IP Address)
## OUTPUT:
<img width="827" height="393" alt="image" src="https://github.com/user-attachments/assets/95f64d5c-5c55-49dc-b4c4-424f64efa76f" /></br>

step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:

<img width="941" height="647" alt="Screenshot 2026-02-06 212513" src="https://github.com/user-attachments/assets/9f83477c-da48-4b76-a308-8b061158bb83" /> </br>


Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:

<img width="1178" height="571" alt="image" src="https://github.com/user-attachments/assets/7b21e24a-0b9d-42d1-88ef-c96380cf7432" /> </br>


Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT:

<img width="1908" height="1083" alt="image" src="https://github.com/user-attachments/assets/d74fea90-d944-4bae-94b7-b0c0efb38626" /></br>


The info command provides information regarding a module or platform,

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## OUTPUT:

<img width="1573" height="525" alt="image" src="https://github.com/user-attachments/assets/b02cc7bb-2606-4414-91ad-fa23f22c576d" /></br>



## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:

<img width="1612" height="195" alt="image" src="https://github.com/user-attachments/assets/52c30cc9-50bb-4511-8d50-16a939bf8e34" /></br>

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
## OUTPUT:

<img width="1918" height="724" alt="image" src="https://github.com/user-attachments/assets/28b8ae51-a654-4a0f-88b2-1c0534cc934a" />

use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
## OUTPUT:

<img width="1022" height="67" alt="image" src="https://github.com/user-attachments/assets/c07af9cb-aecc-4c72-a558-ab51b0a72f2e" /> </br>
<img width="1919" height="692" alt="image" src="https://github.com/user-attachments/assets/5c25ffba-2e99-4e80-b63e-8dd66f8335a0" /> </br>




Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:

<img width="1209" height="116" alt="Screenshot 2026-02-06 214518" src="https://github.com/user-attachments/assets/dc59666e-5b3d-4bb4-bf0e-f0978f18953c" /></br>


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
## OUTPUT:


<img width="1729" height="361" alt="Screenshot 2026-02-06 215400" src="https://github.com/user-attachments/assets/c43e51ab-6a05-46ef-97b8-71d9c187256f" /></br>


set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true












## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
