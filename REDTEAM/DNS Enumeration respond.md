1. What is the ip address of adlp-corp.com ?
ping adlp-corp.com

52.51.133.160

2. What is the TXT record of adlp-corp.com?
nslookup -type=TXT adlp-corp.com

BC{DESCRIPTIVE-DOMAIN-TXT}

4. What are the MX records of becode.org ?
dig mx becode.org

- alt1.aspmx.l.google.com.
- alt4.aspmx.l.google.com.
- aspmx.l.google.com.
- alt3.aspmx.l.google.com.
- alt2.aspmx.l.google.com.


6. What are the MX records of adlp-corp.com ?
dig mx adlp-corp.com

- alt3.aspmx.l.google.com.
- alt2.aspmx.l.google.com.
- alt1.aspmx.l.google.com.
- alt4.aspmx.l.google.com.
- aspmx.l.google.com.

8. What is the first NS name server of adlp-corp.com?
dig NS adlp-corp.com

ns-269.awsdns-33.com.

10. Uses a brute force tool to find subdomains of adlp-corp.com. How many did you find?
nmap -p 53 --script dns-brute adlp-corp.com


