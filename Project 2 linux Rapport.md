# The second task is meant to serve as practice and will have you, in a different file, **write a report** with as many relevant information (_what would make sense in a report_) as you can muster on a system you manage. It most preferably would be a remote machine, but it can also be your local machine as this is just practice.


## Rsyslog 
Allows these logs from multiple machines to be centralized in a single location, making them easier to manage and analyze. In short, Rsyslog helps system administrators keep track of what's happening on their systems, which is essential for troubleshooting, security and regulatory compliance.
- sudo apt install rsyslog
- To configure our server, simply edit /etc/rsyslog. conf and uncomment the following lines to enable log collection on UDP port 514, which is the default port:
  #provides UDP syslog reception
  module(load="imudp")
  input(type="imudp" port="514")
- service rsyslog restart
- To receive logs, they must be sent. The Linux client must be configured to send its logs to the centralization server. To do this, edit the default file: /etc/rsyslog.d/50-default.conf

Why use Rsylog in a SOC report:
- Centralized log collection: Rsyslog enables centralized log collection from a variety of sources, facilitating log management and analysis in a complex IT environment. For SOC reporting, complete, centralized logs are essential to meet compliance requirements.
- Log filtering and enrichment: Rsyslog offers advanced log filtering and enrichment features, enabling you to collect only logs relevant to the SOC report. For example, you can filter out critical security events or enrich logs with additional metadata for more in-depth analysis.
- Secure log storage: Rsyslog can be configured to store logs securely, using methods such as encryption and restricted access to log files. This guarantees the integrity and confidentiality of log data, which is essential to meet the security requirements of SOC reporting.
- Log analysis and reporting: Rsyslog offers log analysis and reporting capabilities, enabling you to create detailed reports to meet SOC reporting compliance requirements. You can generate customized reports that demonstrate compliance with specific SOC requirements.
- Integration with other security tools: Rsyslog can be integrated with other security tools, such as SIEM (Security Information and Event Management), for more in-depth log analysis and management. This integration enables more effective proactive threat detection and incident response, strengthening an organization's security posture.

In summary, using Rsyslog for SOC reporting provides a robust and flexible solution for log collection, storage, analysis and reporting, helping to demonstrate compliance with security standards and meet SOC reporting compliance requirements.

## Network monitoring
IDS(Intrusion Detection System) are network intrusion detection tools. IPS(Intrusion Prevention System), on the other hand, block intrusion on the network by means of rules.
Snort installation: To activate Snort in pfSense, simply open pfSense and go to package manager to install the Snort package.
Once Snort has been installed, it is now possible to monitor the network in the interface with its default configuration, and add additional detection rules.

Why use snort in a SOC report:
- Network threat detection: Snort is designed to detect and report malicious activity on a network. Using Snort, you can identify intrusion attempts, port scans, denial-of-service attacks, vulnerability exploitation attempts and other   suspicious behavior.
- Real-time monitoring: Snort can operate in real-time mode, which means it can detect threats as soon as they occur on the network. This enables rapid response to security incidents and reduces the latency between detection and         response.
- In-depth alert analysis: Snort generates detailed alerts when it detects suspicious activity. These alerts include information such as source and destination IP addresses, the protocol used, the type of attack detected, and so on.     This information is invaluable to security analysts when investigating incidents.
- Integration with other security tools: Snort can be integrated with other security tools, such as SIEM (Security Information and Event Management), for more comprehensive management of security incidents. This integration enables      deeper correlation of security events and a more complete visualization of the network's security status.
- Customization and extensibility: Snort is highly customizable and extensible. You can create your own detection rules to meet the specific needs of your environment, and add further functionality using add-ons and plug-ins.

In short, Snort is a powerful tool for network threat detection, making it an essential part of any SOC report. Using Snort, you can quickly detect malicious activity on your network, analyze the alerts generated and take action to protect your organization against cyber threats.

OR/AND

Why use Wireshark is a SOC report:
- Network threat detection: Wireshark enables security analysts to capture and analyze network traffic in real time, enabling them to detect malicious activity such as port scans, denial-of-service attacks, vulnerability exploitation attempts, suspicious communications and other abnormal network behavior.
- Security incident investigation: When a security incident is detected, Wireshark can be used to capture network traffic associated with the incident to understand its origin, scope and effects. Security analysts can examine network packets in detail to identify the sources of the attack, the attack vectors used and associated malicious activity.
- Forensic network analysis: Wireshark is an invaluable tool for forensic investigation of compromised network infrastructures. Network traffic captures made with Wireshark can be used to reconstruct event histories, identify traffic anomalies, collect digital evidence and help determine the extent of damage caused by an attack.
- Identifying indicators of compromise (IOCs): Wireshark enables security analysts to identify indicators of compromise (IOCs) in network traffic, such as suspicious IP addresses, malicious domain names, known attack signatures and so on. This information can be used to improve threat detection rules and enhance network security.
- Security incident response: Using Wireshark, security teams can quickly identify the sources and vectors of an attack, enabling them to take swift corrective action to mitigate risks, block attackers and restore network integrity.

In short, Wireshark is an essential tool for security teams working in an SOC, as it provides in-depth visibility into network traffic, enables early detection of threats, facilitates the investigation of security incidents and helps reinforce the organization's overall security posture.


## ELK + ELK SIEM
https://openclassrooms.com/fr/courses/1750566-optimisez-la-securite-informatique-grace-au-monitoring/7145362-installez-elk
ELK enables data indexing and analysis. It is possible, for example, to load different types of data, such as logs, and visualize them in the form of customized diagrams.
https://openclassrooms.com/fr/courses/1750566-optimisez-la-securite-informatique-grace-au-monitoring/7145749-allez-plus-loin-avec-elk-siem

Why use ELK + ELK SIEM in a SOC report:
- Centralized log collection and storage: Elasticsearch, combined with Logstash, enables the centralized collection and efficient storage of logs from a variety of sources, including system logs, application logs, security logs and more. This ensures that all relevant data is available in one place, which is essential for in-depth analysis and rapid response to security incidents.
- Advanced log analysis: Elasticsearch offers powerful indexing and search capabilities, enabling in-depth analysis of logs to detect anomalies, suspicious behavior patterns and indicators of compromise (IOCs). This advanced log analysis is essential for detecting security threats and responding rapidly to incidents.
- Security data visualization: Kibana offers flexible, interactive visualization features to create customized dashboards and charts based on log data. This enables security analysts to monitor security status in real time, identify trends and visualize data to quickly identify potential problems.
- Threat detection and incident response: ELK SIEM is a specific ELK extension designed for threat detection and security incident management. It includes advanced features such as event correlation, anomaly detection, custom detection rule creation, incident case management and security reporting. This functionality enables security teams to detect threats faster, investigate incidents more effectively and respond to incidents appropriately.
- Integration with other security tools: ELK can be integrated with other security tools, such as firewalls, intrusion prevention systems (IPS), antivirus, etc., for more extensive visibility and event correlation. This integration enables more accurate threat detection and coordinated incident response.

In summary, using the ELK package with ELK SIEM for SOC reporting provides a complete solution for the collection, analysis, visualization and management of security logs and events. This enables organizations to detect threats proactively, respond rapidly to security incidents and strengthen their overall security posture.

## ATT&CK matrix
ATT&CK matrix:

°Lists attackers' methods by :
- their tactics, a series of progressive actions to carry out a cyber attack,
- their techniques, the different specific methods for carrying out a tactic ;

°Establishes a common vocabulary and helps SOC teams strengthen their architectures by simulating real attacks.

Why use ATT&CK matrix in a SOC report:
- Understanding threats: The ATT&CK matrix provides a detailed view of the tactics and techniques attackers can use to compromise a network. Using the ATT&CK matrix, security teams can better understand the different phases of an attack and the methods used by attackers, helping them to anticipate potential threats and reinforce their security posture.
- Proactive threat detection: The ATT&CK matrix can be used as a guide for the development of detection rules and detection scenarios in a SOC environment. By identifying the techniques used by attackers, security teams can develop proactive detection strategies to identify and counter potential threats before they cause damage.
- Incident analysis: When investigating security incidents, the ATT&CK matrix can be used as a reference to identify the techniques used by attackers and understand their modus operandi. This enables security analysts to analyze incidents more effectively, understand the extent of the attack and take appropriate corrective action.
- Prioritizing security measures: Using the ATT&CK matrix, security teams can identify the techniques most commonly used by attackers and the potential areas of vulnerability in their environment. This enables them to prioritize security measures and investments according to the threats most relevant to their organization.
- Security posture assessment: The ATT&CK matrix can be used as a framework for assessing an organization's security posture. By comparing the techniques listed in the matrix with the security controls in place, organizations can identify security gaps and implement corrective measures to strengthen their defense against attacks.

In summary, the ATT&CK matrix is a valuable tool for security teams working in an SOC, as it provides a detailed reference of the tactics and techniques used by attackers, helping them to better understand threats, detect security incidents and strengthen their overall security posture.





















