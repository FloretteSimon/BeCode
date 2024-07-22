1. What is the ip address of adlp-corp.com ?
ping adlp-corp.com

52.51.133.160

2. What is the TXT record of adlp-corp.com?
nslookup -type=TXT adlp-corp.com

BC{DESCRIPTIVE-DOMAIN-TXT}

4. What are the MX records of becode.org ?
dig mx becode.org

becode.org.             2228    IN      MX      5 alt1.aspmx.l.google.com.
becode.org.             2228    IN      MX      10 alt4.aspmx.l.google.com.
becode.org.             2228    IN      MX      1 aspmx.l.google.com.
becode.org.             2228    IN      MX      10 alt3.aspmx.l.google.com.
becode.org.             2228    IN      MX      5 alt2.aspmx.l.google.com.


6. What are the MX records of adlp-corp.com ?
dig mx adlp-corp.com

adlp-corp.com.          377     IN      MX      10 alt3.aspmx.l.google.com.
adlp-corp.com.          377     IN      MX      5 alt2.aspmx.l.google.com.
adlp-corp.com.          377     IN      MX      5 alt1.aspmx.l.google.com.
adlp-corp.com.          377     IN      MX      10 alt4.aspmx.l.google.com.
adlp-corp.com.          377     IN      MX      1 aspmx.l.google.com.

8. What is the first NS name server of adlp-corp.com?
dig NS adlp-corp.com

adlp-corp.com.          4502    IN      NS      ns-269.awsdns-33.com.

10. Uses a brute force tool to find subdomains of adlp-corp.com. How many did you find?
nmap -p 53 --script dns-brute adlp-corp.com

5

12. Use theHarvester tool at becode.org. How many Linkedin Users?
Your response Your command

13. Use theHarvester tool at becode.org. How many ip addresses did you find?
Your response Your command

14. Write a small script to attempt a zone transfer from adlp-corp.com using a higher-level scripting language such as Python, Perl, or Ruby
Your Script

15. Write a small script to attempt a brute force search for subdomains using a higher level scripting language such as Python, Perl or Ruby.
Your Script
