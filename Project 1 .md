# Set up the following Linux infrastructure:

One server (no GUI) running the following services:

- DHCP (one scope serving the local internal network) isc-dhcp-server
- DNS (resolve internal resources, a redirector is used for external resources) bind
- HTTP+ mariadb (internal website running GLPI)
## Required
- Weekly backup the configuration files for each service into one single compressed archive
- The server is remotely manageable (SSH)
## Optional
Backups are placed on a partition located on separate disk, this partition must be mounted for the backup, then unmounted


  ## ISC-DHCP-SERVER:
  1/ sudo apt install isc-dhcp-server
  2/sudo nano /etc/dhcp/dhcpd.conf:
    default-lease-time 600;
    max-lease-time 7200;
    option subnet-mask 255.255.255.240;
    option broadcast-address 192.169.64.15;
    option routers 192.168.64.14
    option domain-name-servers 192.168.64.1, 192.168.64.2;
    option domain-name "local.library.com";

    subnet 192.168.64.0 netmask 255.255.255.240 {
      range 192.168.64.3 192.168.64.13;
    }

    authorative;
    
  ## Security (https://www.youtube.com/watch?v=ZhMw53Ud2tY&t=950s)
  1/ Automatic update:
    ° apt install unattended-upgrades
    ° dpkg-reconfigure --priority=low unattended-upgrades
    ° Yes
    
  2/ SSH:
    ° chmod 700 ~/.ssh
    ° ssh-keygen -b 4066
    ° passphrase: BibiILoveU
    ° sudo nano /etc/ssh/sshd_config 
      port 717

  3/ Firewall
    ° sudo apt install ufw
    ° sudo ufw allow 717
    ° sudo ufw enable 

## HTTP+ mariadb (https://www.youtube.com/watch?v=WTZAhHgkz4s)
  1/ mariadb (https://www.youtube.com/watch?v=sfJe5tWtsaA)
    ° sudo apt install mariadb-server
    ° sudo mysql_secure_installation
    ° sudo mysql -u -root -p
        > create database glpi_db
        > create user 'adminglpi'@'localhost' identified by 'mdpadminglpi';
        > grant all privileges on glpi_db.*to adminglpi@localhost
        > flush privileges
        > exit
  2 apache2
    ° sudo apt install apache2
    ° sudo apt install apache2 libapache2-mod-php
  3/ PHP 
    ° sudo apt install php php-cli (permet d'exécuter des scripts PHP à la fois sur votre serveur web et directement à partir de votre terminal.)
    ° sudo apt install php-curl (permet à vos scripts PHP d'effectuer des requêtes HTTP et d'accéder à des ressources sur des serveurs distants via le protocole HTTP.)
    ° sudo apt install php-intl (permet à vos scripts PHP d'effectuer des opérations avec des chaînes de caractères internationales de manière efficace et conforme aux règles locales.)
    ° sudo apt install php-memcache (permet à PHP de se connecter à un serveur Memcached, un système de mise en cache distribué en mémoire, et d'y effectuer des opérations de mise en cache.)
    ° sudo apt install php-mbstring (particulièrement utile pour les applications Web multilingues ou qui manipulent des données textuelles provenant de différentes sources encodées.)
    ° sudo apt install php-xml (utile pour le développement d'applications Web qui communiquent avec des services Web basés sur XML ou qui manipulent des données XML, telles que des flux de données ou des configurations.)
    ° sudo apt install php-zip (particulièrement utile pour les applications Web qui nécessitent la manipulation de fichiers compressés, tels que les téléchargements et les archives de fichiers.)
    ° sudo apt install php-json






















  
