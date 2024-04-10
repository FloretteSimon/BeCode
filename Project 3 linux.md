# El Doctor - A monitoring tool to rule them all!

- Module: **Scripting** 
- Competence: `is able to write a custom script to monitor machines`
- Type of Challenge: `Consolidation`
- Duration: `3 day`
- Deadline: `12/04/2024`
- Participants: : `solo`

## The mission

There exist a plethora of amazing monitoring tools out there, some of which go as far as offering a full blown graphical dashboard collecting metrics on your entire system in a single unified interface, isn't it great?! Well, this challenge will have you throw all those pre-made solution out the window to **create your own** monitoring script!

You will have multiple days to make it as **useful** (_collect the data you want or need_) and **fancy** (_interactive interface_, _features_, _..._) as possible, the goal is for you to **be creative** and **make it your own**! As such, we won't give you clear instructions to follow nor specific features to implement. Still, we are no monster so here are some idea to inspire you:

- Make an interactive [curses interface](https://en.wikipedia.org/wiki/Curses_(programming_library)) (_or similar_) for your script.
- Deploy your script on a machine you manage and use something like [cron](https://en.wikipedia.org/wiki/Cron) to execute once an hour.
- Collect metrics every hour and store them in an [CSV file](https://en.wikipedia.org/wiki/Comma-separated_values).
- If the state of the machine is critical (_not enough ram_, _..._), notify yourself by mail.
- Send yourself a system report once a week.

In order to validate this challenge, you must have a repository containing your script and its documentation along with your script. 

> **NOTE**: As mentioned you should make the script as complex and fancy as you can, use this opportunity to practice both your understanding of monitoring and your scripting capabilities.

## Complementary Resources

* Article: [Five ways to send email from the CLI](https://tecadmin.net/ways-to-send-email-from-linux-command-line/)
* Article: [Cron Job: A Comprehensive Guide for Beginners](https://www.hostinger.com/tutorials/cron-job)

## Final Words

Even though the modern IT ecosystem is full of wonderfully designed tools it's always a good thing to know how it works under the hood and to be able to spin up your own solution when needed. Sometimes a bazooka, no matter how pretty it is, is a bit overkill to hit the target!

<br>
<p align="center">
  <img src="https://c.tenor.com/JVrP5Ievj_sAAAAC/insainment-mind-space-apocalypse.gif" />
</p>


# Sources: 

| Old command (Deprecated)                             | New command                            |
| ---------------------------------------------------- | -------------------------------------- |
| ifconfig -a                                          | ip a                                   |
| ifconfig enp6s0 down                                 | ip link set enp6s0 down                |
| ifconfig enp6s0 up                                   | ip link set enp6s0 up                  |
| ifconfig enp6s0 192.168.2.24                         | ip addr add 192.168.2.24/24 dev enp6s0 |
| ifconfig enp6s0 netmask 255.255.255.0                | ip addr add 192.168.1.1/24 dev enp6s0  |
| ifconfig enp6s0 mtu 9000                             | ip link set enp6s0 mtu 9000            |
| ifconfig enp6s0:0 192.168.2.25                       | ip addr add 192.168.2.25/24 dev enp6s0 |
| netstat                                              | ss                                     |
| netstat -tulpn                                       | ss -tulpn                              |
| netstat -neopa                                       | ss -neopa                              |
| netstat -g                                           | ip maddr                               |
| route                                                | ip r                                   |
| route add -net 192.168.2.0 netmask 255.255.255.0 dev | ip route add 192.168.2.0/24 dev enp6s0 |
| route add default gw 192.168.2.254                   | ip route add default via 192.168.2.254 |
| arp -a                                               | ip neigh                               |
| arp -v                                               | ip -s neigh                            |
| ---------------------------------------------------- | -------------------------------------- |

<img width="637" alt="Capture d’écran 2024-04-10 à 09 53 13" src="https://github.com/FloretteSimon/BeCode/assets/155719677/b9fcec0f-45ed-4d94-9239-200a915fcda3">
<img width="126" alt="Capture d’écran 2024-04-10 à 10 03 57" src="https://github.com/FloretteSimon/BeCode/assets/155719677/8be3e1a7-f95c-4492-a865-117f9a4cd46c">

## Step 1: Decide which metrics to monitor
- CPU Usage
- Memory Usage
- Disk Usage
- Network Traffic
- System Uptime
- Application Performance
- Security Events
- Logs and Error Messages
- Hardware Health
- Backup Status

## 


























