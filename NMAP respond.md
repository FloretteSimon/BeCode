Ip : 10.12.1.36

1. How many tcp ports are open on the box? What command did you use?
nmap  10.12.1.36 | grep 'open' | wc -l

21
2. How many udp ports are open on the box? What command did you use?
sudo nmap -sU  10.12.1.36 | grep 'open' | wc -l


3. What is the version of ftp?
sudo nmap -sU -F 10.12.1.36

7

4. What is the version of ssh?
nmap -sV -p 22 10.12.1.36

OpenSSH 4.7p1

5. What is the version of Apache?
nmap -sV -p 80,443 10.12.1.36

Apache httpd 2.2.8

6. Is anonymous ftp access allowed on the box? What command did you use? (Use only nmap)
nmap -sV -p 21 10.12.1.36 --script ftp-anon

Yes:
<img width="788" alt="Capture d’écran 2024-07-22 à 15 02 09" src="https://github.com/user-attachments/assets/688821ee-4e79-4d33-9098-975637138f38">

7. Do a SYN scan. Which command did you use?
sudo nmap -sS 10.12.1.36

<img width="546" alt="Capture d’écran 2024-07-22 à 15 05 26" src="https://github.com/user-attachments/assets/9828414d-33ee-4e7f-84dc-f581f46d146e">

8. Do a scan that bypasses a firewall. What command did you use?
sudo nmap -sF 10.12.1.36

9. Run a scan with the default NSE scripts. Which flag do you use?
-sC

10. What service occupies port 8180?
unknown

<img width="547" alt="Capture d’écran 2024-07-22 à 15 17 45" src="https://github.com/user-attachments/assets/11fe6f24-ee5d-4cb4-ac2c-26ae495bdea3">

11. What is the salt of the mysql service?
nmap -p 3306 --script mysql-info 10.12.1.36

Salt: [Vy"86C.[`QT5HIx?q;r

12. What is the domain name ?

Your response

What is the FQDN of the box ?

Your response

What is the os version ?

Your response

What is the version of Samba ?

Your response

Wat is the name of the box ?

Your response

Do a scan on the subnet 10.xx.1.0/24. How many IP addresses respond? What command did you use? Charleroi : 10.11.0.1/24 Bruxelles : 10.12.0.1/24 Ghent : 10.13.0.1/24

Your response

Do the same thing but with the top port option at 10. What command did you use?

Your response
