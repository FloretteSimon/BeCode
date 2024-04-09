## The Mission

One of the most important responsibilities a system administrator or SOC analyst have is monitoring the systems he manages. Indeed it's one thing to set them up and install software on them, but then what!? Well the next step is ensuring that the machines you provisioned as well as the services you deployed on them remain **available**, **reliable** and **secure**!
This challenge is divided in two tasks, the first one having you **research how to monitor** a Linux system as well as **what to look for** when doing so. You will have to **take note** of all your findings in a text file (EX: _markdown_) while being as **exhaustive** as possible (_what to monitor_, _how to monitor it_, _commands used_, _..._). Try to answer, but **don't limit yourself to**, the questions below to guide you through 
the research process:

- What are the main area of concern when monitoring a system? (EX: _CPU load_, _disk usage_, ...)
- How can you check what are the most memory intensive [running processes](https://www.computerhope.com/jargon/p/process.htm) ?
- What are log files? Where can you fin them on a typical Linux system ?
- How can you check who where the last connected users, what they did, when they left ?
- What are the different metrics of health and performance of a system ?
- How can you check the uptime of a machine ?
- How can you assess the network traffic ?

The second task is meant to serve as practice and will have you, in a different file, **write a report** with as many relevant information (_what would make sense in a report_) as you can muster on a system you manage. It most preferably would be a remote machine, but it can also be your local machine as this is just practice.


> **IMPORTANT**: Take your time when researching, it's the most important part of this challenge as you'll need to be able to find out what is happening on any given system at any given time. Whether it's the percentage of system's resources currently used, what commands are being run, who is logged in, and so on...

## Complementary Resources

* [Useful monitoring commands](https://www.ubuntupit.com/most-comprehensive-list-of-linux-monitoring-tools-for-sysadmin/)
* [Linux system monitoring fundamentals](https://www.linode.com/docs/guides/linux-system-monitoring-fundamentals/)

## Final Words

There are plenty of tools out there but remember that collecting the metrics is only the first step towards an end goal, which is, to be able to keep track of the state of machines, troubleshoot them to understand errors and in the best cases prevent issues before they even happen!

One last thing, we cannot understate how **important**, even **crucial**, monitoring for servers, services and applications deployment.

<br>
<p align="center">
  <img src="https://c.tenor.com/FSFcij2DJkAAAAAC/watching-you-warning.gif" />
</p>

Sources:
https://www.logpoint.com/fr/blog/le-guide-complet-de-lanalyse-de-logs/
ChatGPT
https://medium.com/@btk667/cest-quoi-un-rapport-soc2-def8c4506cef
https://openclassrooms.com/fr/courses/1750566-optimisez-la-securite-informatique-grace-au-monitoring/7144124-tirez-le-maximum-de-ce-cours
https://cyber.gouv.fr/uploads/IMG/pdf/NP_Journalisation_NoteTech.pdf



## What are the main area of concern when monitoring a system? (EX: _CPU load_, _disk usage_, ...)
1: CPU Usage: Monitoring CPU load helps identify if the system is under heavy processing load, which could lead to performance degradation or even system crashes.

2: Memory Usage: Monitoring memory usage helps ensure that the system has enough available memory to run applications efficiently. High memory usage could lead to slowdowns or out-of-memory errors.

3: Disk Usage: Monitoring disk space usage is important to prevent disk space exhaustion, which can cause system instability and application failures.

4: Network Traffic: Monitoring network traffic helps identify potential network bottlenecks, security breaches, or abnormal activity that could indicate unauthorized access or attacks.

5: System Uptime: Monitoring system uptime ensures that the system is available and operational within expected parameters. Sudden downtime could indicate hardware failures or software issues.

6: Application Performance: Monitoring the performance of critical applications helps ensure they are running smoothly and responding to user requests within acceptable timeframes.

7: Security Events: Monitoring for security events such as failed login attempts, unusual access patterns, or malware activity helps identify and mitigate potential security breaches.

8: Logs and Error Messages: Monitoring system logs and error messages provides insights into system behavior, potential issues, and troubleshooting information.

9: Hardware Health: Monitoring hardware health parameters such as temperature, fan speed, and voltage levels helps detect hardware failures or potential issues before they impact system performance

10: Backup Status: Monitoring backup processes and verifying backup integrity ensures data is protected and recoverable in the event of data loss or system failures.


## How can you check what are the most memory intensive [running processes](https://www.computerhope.com/jargon/p/process.htm) ?
Command linux: top 
This will display a dynamic list of processes, sorted by various criteria including memory usage. By default, top sorts by CPU usage, but you can toggle sorting by memory by pressing Shift + M.


## What are log files?
Log files are files that contain records of events, actions, or transactions that occur within a software application, operating system, or other system components. These files serve several important purposes:
- Troubleshooting and Debugging: Log files record information about system or application behavior, errors, warnings, and other relevant events. They are invaluable for diagnosing and resolving issues, as they provide a historical record of what happened leading up to a problem.
- Performance Monitoring: Log files can contain performance-related data such as response times, resource usage, and throughput. Analyzing this data helps administrators identify performance bottlenecks and optimize system performance.
- Auditing and Compliance: Log files can be used to track user actions, system access, and changes to system configuration. They are essential for auditing purposes to ensure compliance with regulatory requirements and security policies.
- Security Monitoring: Log files record security-related events such as login attempts, access control changes, and security breaches. Analyzing these logs helps detect and respond to security incidents in a timely manner.
- Forensic Analysis: In the event of a security breach or system compromise, log files can provide valuable forensic evidence to investigate the incident, identify the root cause, and mitigate future risks.

Log files are typically stored in text format, making them human-readable and easily parseable. They may be stored locally on the system or centralized on a logging server for easier management and analysis. Log files can vary in size and frequency of rotation, depending on the logging configuration and system requirements. Regular log file analysis is essential for maintaining system health, security, and performance.


## Where can you fin them on a typical Linux system ?

On a typical Linux system, logs are typically located in the /var/log

## How can you check who where the last connected users, what they did, when they left ?
 Here are some methods:
 1: last command: This will display a list of users who have logged in, along with the login time, duration of the session, and logout time (if available). If a user is still logged in, it will display (still logged in) instead of a logout time.

 2: w command: Shows who is currently logged in and what they are doing. It also displays login times and idle times.

 3: /var/log/wtmp: Contains historical login records, including login and logout times. You can use the last command to read this file and display the login history. Similarly, /var/run/utmp contains current login records.

 4: .bash_history: Each user typically has a .bash_history file in their home directory that logs their command-line activity. You can inspect these files to see what commands were executed.

 5: Syslog and Audit Logs: System logs (/var/log/syslog, /var/log/messages, etc.) may contain information about user logins and logouts, especially if auditing is enabled. You can search these logs for relevant entries using tools like grep

 6: Journalctl: If your system uses systemd, you can use journalctl to view system logs, including user login/logout events.

 ## What are the different metrics of health and performance of a system ?

The metrics of health and performance of a system can be broadly categorized into several key areas, each providing insights into different aspects of the system's functioning. Here are the main categories:

- Resource Utilization
- Performance
- Availability and Reliability
- Error and Exception Handling
- Security
- Scalability and Capacity Planning
- User Experience


  ## How can you check the uptime of a machine ?
  Using the uptime command: This command will display the current time, how long the system has been running, the number of users logged in, and the system load averages for the past 1, 5, and 15 minutes.

  ## How can you assess the network traffic ?
  Wireshark: Wireshark is a popular network protocol analyzer that allows you to capture and inspect the traffic on a network in real-time. It provides detailed information about individual packets, protocols, and conversations.

  ## What is log analysis and why is it important?
  Log analysis involves examining and understanding computer-generated records, so you can effectively manage a data-driven business. Logs are generated by any modern device or application, including connected objects(IoT), servers, 
  networked devices and operating systems. Logs describe the activities taking place in the system. They can be sent to a collector prior to centralized log analysis, to improve accuracy and performance. Log analysis in a SIEM         (Security Information and Event Management) solution makes it easier for security analysts to examine and interpret what's happening on the network, and obtain actionable information.
  With an increasingly diverse IT infrastructure featuring a wide variety of applications located in the cloud, on-premises, in virtual instances and more, data often comes in unpredictable formats. To unleash the full power of the     business and operational insights contained in data, centralized log analysis is becoming increasingly critical. It facilitates a multitude of use cases, including problem diagnosis, security threat detection, fraud detection and     compliance support for stringent regulations.

  ## What is SIEM?:
  SIEM (Security Information and Event Management) is an IT tool designed to provide a consolidated, real-time view of security information on a computer system or network. SIEM solutions collect, aggregate and analyze data from a      variety of sources, such as event logs, network data streams, intrusion detection systems, firewalls, intrusion prevention systems and so on. The main objective of a SIEM is to detect and respond to security threats by identifying    suspicious or malicious patterns of activity.


  ## The following table gives an overview of the logs that can be found under Linux. Most logs are stored in /var/log/. There may be additional logs depending on the program.
<img width="183" alt="Capture d’écran 2024-04-08 à 15 55 40" src="https://github.com/FloretteSimon/BeCode/assets/155719677/58ff76b2-23f3-4b03-9154-e383d5d00bb2">


  ## What is log collection management?
  Managing your log collection involves setting up logging and centralization systems. Logging is the implementation of a system enabling automatic log reporting. Sending your logs to a central point describes centralization, which     will give you a global view of events on the information system.
  Log management has several objectives:
- Obtain a general overview of the IS and identify abnormal events.
- Detect intrusions, for example using IPS/IDS solutions or SIEM rules.
- Trace the history and actions of an attacker as part of a forensic investigation.
  Visualize IS actions, define statistics and identify weak signals.

  ## Which logs are relevant to monitor?
  The following is a list of logs of interest for IS security monitoring:
  - Authentification.
  - Gestion des comptes et des droits.
  - Accès aux ressources.
  - Modification des stratégies de sécurité.
  - Activité des processus. 
  - Activité des systèmes.

  ## What is the parsing of log?
  In the event of a security incident, or simply as part of daily monitoring, it can be useful to explore logs manually, also known as log parsing.
  - Extract words with grep
  - Cut file lines with awk: Awk is another utility available on any Linux system. With awk, you can thoroughly parse your log files.
  - Display log output in real time with tail. When you need to monitor ongoing processes, such as restarting a service or testing a modification, tail is a good tool to know. Tail is another command-line tool that displays the           latest modifications to a file. You can also use it to display the last lines of a file, or combine it with grep to filter the output of a log file.
    The "-f" optiondisplays log output in real time: $ tail -f syslog$
    <img width="204" alt="Capture d’écran 2024-04-08 à 16 17 38" src="https://github.com/FloretteSimon/BeCode/assets/155719677/4f245253-cfe7-4670-abf8-b49f41ae7efa">

  ## What's syslog?
  The syslog protocol is used to send and receive logs in a particular format from various systems. Messages include timestamps, event messages, criticality, IP addresses, diagnostics, etc., but in a digestible way.
  The syslog protocol is designed to monitor network and system devices to send notification messages in the event of malfunctions. It can also send alerts for pre-notified events, and monitor suspicious activity via the various        monitoring logs.
  There are 3 different versions of syslog:
  - Syslog : the initial version just discussed. The other versions are enhanced versions.
  - Syslog-ng: extends the initial functionality by adding content-based filtering, TCP support and TLS encryption.
  - Rsyslog: the latest and most widely used version.

  ## The logs are classified according to several themes
  <img width="539" alt="Capture d’écran 2024-04-09 à 09 12 04" src="https://github.com/FloretteSimon/BeCode/assets/155719677/7bfd34f4-3a28-4b97-983c-fd1405eae756">

  ## Logs are also sorted by log level
  <img width="313" alt="Capture d’écran 2024-04-09 à 09 15 00" src="https://github.com/FloretteSimon/BeCode/assets/155719677/39360559-bfa3-4068-a353-d4456f387300">

  ## IDS et IPS
  IDS(Intrusion Detection System) are network intrusion detection tools. IPS(Intrusion Prevention System), on the other hand, block intrusion on the network by means of rules.

  ## Stack ELK
  ELK is an open source suite comprising 3 main components: Elasticsearch, Logstash and Kibana. Beats was then added to form the ELK stack. ELK enables data indexing and analysis. It is possible, for example, to load different types    of data, such as logs, and visualize them in the form of customized diagrams.
  Each letter represents a specific component:
  - Elasticsearch(https://www.elastic.co/guide/index.html#install-beats): This is a distributed data search and analysis engine, designed to store, search and analyze large volumes of data in real time. Elasticsearch is used as a         database to store logs and other data for analysis.
  - Logstash (https://www.elastic.co/guide/en/logstash/current/getting-started-with-logstash.html): Logstash is a data processing tool that ingests, transforms and sends logs and other data to Elasticsearch for subsequent indexing         and analysis. It can also be used to enrich data with additional information before storing it in Elasticsearch.
  - Kibana: Kibana is a data visualization and exploration interface that integrates with Elasticsearch. It enables users to create interactive dashboards, charts and visualizations based on data stored in Elasticsearch. Kibana makes     it easy to analyze and understand logs and other data.

   ## SIEM with ELK
  The integration of SIEM (Security Information and Event Management) functionality with ELK (Elasticsearch, Logstash, Kibana) offers several significant advantages for IT security management:
  - Event correlation: SIEMs are designed to collect and correlate security events from a variety of sources, enabling the detection of suspicious patterns of activity or potential threats. By integrating ELK into a SIEM, you can         benefit from Elasticsearch's ability to store and query vast volumes of data quickly and efficiently, making it easier to correlate events and identify security incidents.
  - Advanced log analysis: ELK offers powerful log analysis capabilities, enabling log data to be searched, queried and visualized in a flexible, granular way. By integrating ELK with a SIEM, security analysts can leverage these          features to perform in-depth log analysis, identify trends, detect anomalies and investigate security incidents.
  - Security data visualization: Kibana, as ELK's visualization interface, enables the creation of customized dashboards and visualizations to visually represent security data. By integrating Kibana with a SIEM, security teams can        create interactive dashboards and graphical visualizations to monitor security status in real time, quickly identify potential problems and effectively communicate security information to other stakeholders.
  - Scalability and flexibility: Elasticsearch, as a distributed search and analysis engine, offers great scalability and flexibility for managing large volumes of security data. This capability makes it possible to efficiently           manage the growth of log data and adapt to evolving security needs.

    In summary, the integration of SIEM functionality with ELK enhances organizations' ability to detect, analyze and respond to security threats effectively, by leveraging the advanced data analysis and visualization capabilities        offered by ELK.

    ## ATT&CK matrix (https://attack.mitre.org/matrices/enterprise/linux/)
    The ATT&CK matrix lists the tactics and techniques used by attackers during an attack. It is a knowledge base based on real-world observations.
    The matrix is a versatile tool that makes Red Team exercises more effective, by setting up real attack scenarios and copying known operating modes. It also provides SOC teams with a concise and comprehensive presentation of the       attack lifecycle. Thanks to its diagrams, SOC teams have the means to understand attackers, in order to evaluate current controls and defense mechanisms.
    The matrix will help you answer the following questions:
    - On which tactics are our surveillance resources weakest?
    - Which are the riskiest for our environment and our business?
    - Which techniques can be detected using the matrix, and how can we reduce the gap?
    - Which techniques lack practical prevention and controls, and therefore become more critical for detection?
    When you identify tactics or techniques where your organization needs better detection, the matrix provides the technical details to help you. Eventually, it enables you to create monitoring rules or set up proactive controls,        with the aim of detecting threats present on the system.

    

















