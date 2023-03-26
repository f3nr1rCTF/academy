# Fuzzing

# Directory fuzzing

==> quickhits.txt

wfuzz --field url -f wfuzz_quickhits,raw -c -z file,/usr/share/wordlists/seclists/Discovery/Web-Content/quickhits.txt --hc 404 -t 50 "$URL/FUZZ"  

feroxbuster --url $URL --burp-replay --no-state -w /usr/share/wordlists/seclists/Discovery/Web-Content/quickhits.txt -o ferox_quickhits --threads 2 --scan-limit 1

ffuf -c -o ffuf_quickhits -w /usr/share/wordlists/seclists/Discovery/Web-Content/quickhits.txt -t 100 -u $URL

==> dirb_common

wfuzz --field url -f wfuzz_dirb_common,raw -c -z file,/usr/share/wordlists/dirb/common.txt --hc 404 -R 2 -t 50 "$URL/FUZZ/"  

feroxbuster --url $URL --burp-replay --no-state -w /usr/share/wordlists/dirb/common.txt -o ferox_common --threads 2 --scan-limit 1

==> directory-list-2.3-medium

wfuzz --field url -f wfuzz_2.3-medium,raw -c -z file,/usr/share/wordlists/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt --hc 404 -t 50 "$URL/FUZZ/"  

feroxbuster --url $URL --burp-replay -w /usr/share/wordlists/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt -o ferox_23_medium --threads 2 --scan-limit 1

==> raft-large-directories

wfuzz --field url -f wfuzz_large-directories,raw -c -z file,/usr/share/wordlists/seclists/Discovery/Web-Content/raft-large-directories.txt --hc 404 -t 50 "$URL/FUZZ/"  

feroxbuster --url $URL --burp-replay -w /usr/share/wordlists/seclists/Discovery/Web-Content/raft-large-directories.txt -o ferox_large-directories --threads 2 --scan-limit 1

ffuf -c -o ffuf_large-directories -w /usr/share/wordlists/seclists/Discovery/Web-Content/raft-large-directories.txt -t 100 -u $URL/FUZZ

==> directory-list-2.3-big.txt

wfuzz --field url -f wfuzz_2.3-big,raw -c -z file,/usr/share/seclists/Discovery/Web-Content/directory-list-2.3-big.txt --hc 404 -t 50 "$URL/FUZZ/"

feroxbuster --url $URL --burp-replay -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-big.txt -o ferox_2.3-big --threads 2 --scan-limit 1

ffuf -c -o ffuf_directory-list-2.3-big -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-big.txt -t 100 -u $URL/FUZZ

tech  = = = PHP (słownik z wordlists.assetnote.io)

wfuzz --field url -f wfuzz_httparchive_php,raw -c -z file,/usr/share/wordlists/httparchive_php_2022_12_28.txt --hc 404 -t 2 "$URL/FUZZ"  

feroxbuster --url $URL --burp-replay -w /usr/share/wordlists/httparchive_php_2022_12_28.txt -o ferox_httparchive_php --threads 2 --scan-limit 1

tech  = = = java (słownik z wordlists.assetnote.io)
wfuzz --field url -f wfuzz_httparchive_jsp_jspa,raw -c -z file,/usr/share/wordlists/httparchive_jsp_jspa_do_action --hc 404 -t 2 "$URL/FUZZ"  
feroxbuster --url $URL --burp-replay -w /usr/share/wordlists/httparchive_jsp_jspa_do_action -o ferox_httparchive_jsp_jspa --threads 2 --scan-limit 1

tech  = = = asp, aspx (słownik z wordlists.assetnote.io)
wfuzz --field url -f wfuzz_asp,raw -c -z file,/usr/share/wordlists/asp_lowercase.txt --hc 404 -t 3 "$URL/FUZZ"

feroxbuster --url $URL --burp-replay -w /usr/share/wordlists/asp_lowercase.txt -o ferox_httparchive_asp --threads 2 --scan-limit 1

wfuzz --field url -f wfuzz_aspx,raw -c -z file,/usr/share/wordlists/aspx_lowercase.txt --hc 404 -t 3 "$URL/FUZZ"
feroxbuster --url $URL --burp-replay -w /usr/share/wordlists/aspx_lowercase.txt -o ferox_httparchive_aspx --threads 2 --scan-limit 1

tech  = = = tomcat (słownik z wordlists.assetnote.io)
wfuzz --field url -f wfuzz_httparchive_tomcat,raw -c -z
file,/usr/share/wordlists/httparchive_tomcat --hc 404 -t 2 "$URL/FUZZ"  

feroxbuster --url $URL --burp-replay -w /usr/share/wordlists/httparchive_tomcat -o ferox_httparchive_tomcat --threads 2 --scan-limit 1

tech  = = = rubyonrails (słownik z wordlists.assetnote.io)
feroxbuster --url $URL --burp-replay --no-state -w /usr/share/wordlists/httparchive_rails -o ferox_rails --threads 2 --scan-limit 1

# # # File fuzzing
==> raft-large-files

wfuzz --field url -f wfuzz_large-files,raw -c -z file,/usr/share/wordlists/seclists/Discovery/Web-Content/raft-large-files.txt --hc 404 -t 50 "$URL/FUZZ"  
feroxbuster --url $URL --burp-replay -w /usr/share/wordlists/seclists/Discovery/Web-Content/raft-large-files.txt -o ferox_large-files --threads 2 --scan-limit 1

==> raft-large-words

wfuzz --field url -f wfuzz_large-words,raw -c -z file,/usr/share/wordlists/seclists/Discovery/Web-Content/raft-large-words.txt --hc 403,404 -t 50 "$URL/FUZZ"
feroxbuster --url $URL --burp-replay -w /usr/share/wordlists/seclists/Discovery/Web-Content/raft-large-words.txt -o ferox_large-words --threads 2 --scan-limit 1

Subdomain fuzzing

wfuzz -f wfuzz_subdomains,raw -c -u http://team.thm/ -H "Host: FUZZ.team.thm" -w /usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-5000.txt

wfuzz -f wfuzz_subdomains,raw -c -u http://team.thm/ -H "Host: FUZZ.team.thm" -w /usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-20000.txt




