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



































