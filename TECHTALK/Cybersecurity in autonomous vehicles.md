# Cybersecurity in autonomous vehicles

## Advantages
1. Improving road safety:
   - Reducing accidents: Autonomous cars can significantly reduce the number of road accidents caused by human error (distraction, fatigue, drink-driving).
   - Faster reaction: Autonomous driving systems can react faster than humans, detecting and responding to hazards in a fraction of a second.
     
2. Traffic efficiency and fluidity:
   - Traffic optimisation: Autonomous cars can communicate with each other and with the road infrastructure to optimise traffic flows, reducing traffic jams.

3. Accessibility and increased mobility:
   - Mobility for all: Autonomous cars can offer greater mobility to old people, the disabled and those who cannot drive.

4. Improving crisis management:
   - Emergency response: Autonomous vehicles can be used for disaster relief missions, delivering medicines or transporting people safely without risking the lives of rescue workers.
   - Surveillance and security: They can also be used for surveillance and security, helping to prevent and respond rapidly to incidents.


## Potential Threats
 Autonomous vehicles are a major technological advance, but like any technology, they present potential vulnerabilities that can be exploited by malicious actors.

 1. Hacking into control systems:
    https://www.youtube.com/watch?v=MK0SrxBC1xs
    - Autonomous vehicle control systems manage critical functions such as steering, braking and acceleration -> An attacker could exploit a software vulnerability to take control of the vehicle remotely.
    - In 2015, security researchers Charlie Miller and Chris Valasek demonstrated a critical vulnerability in the Jeep Cherokee's Uconnect system, an in-car entertainment system developed by Fiat Chrysler Automobiles (FCA). Their research has highlighted the risks associated with connectivity in modern vehicles.:
   

         - Methodology:

      
           1. Analysis of the Uconnect system:

              . The researchers began by analysing the Uconnect system, which enables vehicles to connect to the Internet via a cellular network. This system offers various functions such as navigation, hands-free calling and media control.
               They studied Uconnect's technical documentation and carried out a reconnaissance of the services available and potential entry points.

            3. Exploiting vulnerabilities:

                  . Port scanning: They scanned public IP addresses to identify vehicles equipped with the Uconnect system and found that port 6667 was open, used for the D-Bus service, an inter-process messaging system.

                  . Reverse engineering: They carried out reverse engineering on the Uconnect firmware to understand how the system worked and to identify potential vulnerabilities.

            4. Initial takeover:

                  . Vulnerability found: They discovered a vulnerability in the D-Bus service that allowed them to remotely execute code on the Uconnect system.
               
                  . Privilege escalation: By exploiting this vulnerability, they were able to escalate their privileges to gain root access to the system.

           5.  Controlling critical vehicle functions:

               . With root access, the researchers were able to interact with the vehicle's internal network, which controls critical functions such as steering, brakes and engine. They used this access to send malicious commands, enabling functions such as braking and steering to be remotely manipulated.


           6. Impact:
           
               . Fiat Chrysler had to recall 1.4 million vehicles to correct the vulnerability. They have released a security update for the Uconnect system and have also taken steps to secure their future systems.





2. Interference in Communications:

Autonomous vehicles depend on vehicle-to-vehicle (V2V) and vehicle-to-infrastructure (V2I) communications to navigate safely.

            . Interception of communications: Attackers can intercept communications to obtain sensitive information.

            . Signal manipulation: By sending false signals, attackers can mislead vehicles about road conditions or the position of other vehicles.
            

            Consequences:

            . Intentional accidents: False information can lead to dangerous driving decisions.

            . Route rerouting: Attackers can redirect vehicles into dangerous areas or traffic jams.



3. Data Theft:

Autonomous vehicles collect and transmit large amounts of data, including personal data, journeys, and user preferences.
      
         . Attackers can exploit vulnerabilities to access data stored or transmitted by the vehicle.
         
         . Spying: Collected data can be used to spy on users' movements and habits.
         

         Consequences:

         . Breach of privacy: The theft of personal data can lead to breaches of privacy.

         . Malicious use of data: Stolen information can be used for blackmail, identity theft or other criminal activities.




## One Other Exemple

1. Hacking Tesla vehicles during Pwn2Own competitions (2019):
     In 2019, Tesla took part in the event, offering rewards for discovering vulnerabilities in its vehicles.

   - How:

     . Focus on the infotainment system: The researchers targeted the Tesla Model 3's infotainment system, which is a complex component integrating features such as the web browser, multimedia applications, and vehicle controls.

     . Exploitation of a vulnerability in the web rendering engine: Researchers identified a vulnerability in the web rendering engine used in Tesla's embedded browser. The vulnerability was related to the way the engine handled certain types of web content.

     . Code injection: Using the flaw, researchers injected malicious code into the web browser. This code was used to execute commands on the car's operating system.

     . Access to Internal Functionality: By gaining access to the system via the browser, the researchers were able to interact with some of the vehicle's internal functionality, such as the display of personalised information on the car's main screen.

     . Finally: The attack demonstrated the researchers' ability to manipulate elements of the infotainment system, but did not allow them to take complete control of critical vehicle functions such as the steering wheel or brakes.



   - At The End:

     . Quick fix: Tesla has taken immediate action to correct the vulnerability by deploying a software patch for affected vehicles. The company has also strengthened the security of its systems to prevent future vulnerabilities.


     . Reward: The researchers received a $375,000 reward for discovering and demonstrating the vulnerability, highlighting the importance of cybersecurity research in improving product security.


   - 2024: https://www.securityweek.com/200000-awarded-at-pwn2own-2024-for-tesla-hack/#:~:text=Participants%20have%20earned%20more%20than,pieces%20of%20widely%20used%20software.
         
