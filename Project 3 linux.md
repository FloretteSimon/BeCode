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
<img width="324" alt="Capture d’écran 2024-04-10 à 10 05 27" src="https://github.com/FloretteSimon/BeCode/assets/155719677/65522b40-b855-409b-912a-85513d452aec">
<img width="350" alt="Capture d’écran 2024-04-10 à 10 10 08" src="https://github.com/FloretteSimon/BeCode/assets/155719677/94564ff1-b36e-4cae-b0d7-a02d43c9b84e">
<img width="350" alt="Capture d’écran 2024-04-10 à 10 10 31" src="https://github.com/FloretteSimon/BeCode/assets/155719677/0a792f12-e275-4e99-bceb-b5c7934c2622">
https://www.youtube.com/watch?v=7Od-gg01MVE
https://crontab.guru/
https://www.youtube.com/watch?v=4G_cthFZeJ8
https://github.com/metal3d/bashsimplecurses


## Step 1: Decide which metrics to monitor

- CPU Usage
- Memory Usage
- Disk Usage
- Network Traffic
- System Uptime

## Step 2: Install bash simple curse

1/ cd /usr/local/lib/

2/ git clone https://github.com/metal3d/bashsimplecurses.git

## Step 3: Create the bash file
1/ cd BeCodeMonitoring

2/ sudo nano Monitoring.sh

## Step 4: CPU 
                                             
#!/bin/bash

#Source Curses
source /usr/local/lib/bashsimplecurses/simple_curses.sh

#Main
main () {
        #CPU
        window "CPU Usage" "red" "50%"
        current_date=$(date +"%Y-%m-%d")

        for i in {2..6}; do
        # Capture process information
        process_info=$(ps ax -o pid,rss,pcpu,ucmd --sort=-cpu,-rss | sed -n "$i,$i p" | awk '{printf "%s: %smo:  %s%%", $4, $2/1024, $3 }')
    
         # Combine process info with date
        formatted_line="$current_date  $process_info"
  
         # Append formatted line to window
         append_tabbed "$formatted_line" 3
        done
        endwin
}
main_loop

- #!/bin/bash: This is called a shebang line, and it indicates to the operating system that the script should be executed using the Bash shell.

- source /usr/local/lib/bashsimplecurses/simple_curses.sh: This line sources (loads) a Bash script named simple_curses.sh from the specified path (/usr/local/lib/bashsimplecurses/). This script likely contains functions for creating simple curses-based user interfaces.

- main () {: This line defines a function named main. In Bash, functions are defined using the function_name() { ... } syntax.

- window "CPU Usage" "red": This line creates a window with the title "CPU Usage" and a red background color. It's likely a function provided by the simple_curses.sh script.

- current_date=$(date +"%Y-%m-%d"): This line uses the date command to get the current date in the format "YYYY-MM-DD" and stores it in the variable current_date.

- for i in {2..16}; do: This line starts a loop that iterates from 2 to 16 inclusive. It's used to capture process information.

- process_info=$(ps ax -o pid,rss,pcpu,ucmd --sort=-cpu,-rss | sed -n "$i,$i p" | awk '{printf "%s: %smo: %s%%", $4, $2/1024, $3 }'): This line captures process information using the ps command with specific options to format the output, sort by CPU and memory usage, and extracts the line corresponding to the current iteration ($i). The sed command filters the output to extract the desired line, and awk is used to format the output.

- formatted_line="$current_date $process_info": This line combines the current date with the captured process information into the variable formatted_line.

- append_tabbed "$formatted_line" 3: This line appends the formatted line to the window created earlier. It's likely a function provided by the simple_curses.sh script.

- done: This marks the end of the loop.

- endwin: This line marks the end of the window creation process.

- }: This marks the end of the main function.

- main_loop: This likely starts a loop to continuously run the main function, allowing the user interface to remain open and responsive.

## Step 5: Memory Usage
 #Memory Usage
 
        window "Memory Usage" "magenta" "50%"`
        
        #total
        
        append_tabbed `cat /proc/meminfo | awk '/MemTotal/ {print "Total:" $2/1024}'` 2
        
        #used
        
        append_tabbed `cat /proc/meminfo | awk '/MemFree/ {print "Used:" $2/1024}'` 2
        
        endwin


- #Memory Usage: This is a comment indicating that the following lines of code relate to memory usage.

- window "Memory Usage" "magenta" "50%": This line creates a window with the title "Memory Usage" and a magenta background color. It specifies that the window should occupy 50% of the terminal's width.
  
- #total: This is a comment indicating that the following line of code retrieves total memory information.

- append_tabbed `cat /proc/meminfo | awk '/MemTotal/ {print "Total:" $2/1024}'` 2: This line executes a command within backticks () and appends the result to the window. The command cat /proc/meminfo | awk '/MemTotal/ {print "Total:" $2/1024}'reads the/proc/meminfo` file, searches for the line containing "MemTotal", and prints "Total:" followed by the total memory in megabytes (MiB). The result is appended to the window with a tab offset of 2.

- #used: This is a comment indicating that the following line of code retrieves used memory information.

- append_tabbed `cat /proc/meminfo | awk '/MemFree/ {print "Used:" $2/1024}'` 2: Similar to the previous line, this line retrieves the amount of free memory from the /proc/meminfo file and prints it in megabytes (MiB). The result is appended to the window with a tab offset of 2.

- endwin: This line marks the end of the window creation process.

## Step 6: Disk Usage

 #Disk Usage
        
        window "Disk Usage" "cyan" "70%"
        
        iostat -d
        
        endwin

- #Disk Usage: This is a comment indicating that the following lines of code relate to disk usage.

- window "Disk Usage" "cyan" "70%": This line creates a window with the title "Disk Usage" and a cyan color. It specifies that the window should occupy 70% of the terminal's width.

- iostat -d: This command executes the iostat command with the -d option, which provides detailed statistics about disk usage. The output of this command will be displayed within the window.

- endwin: This line marks the end of the window creation process.


## Step 7: Network



## Step 8: System Uptime

#System Uptime

        window "System Uptime" "yellow" "80%"
        
        sudo uptime
        
        endwin


- #System Uptime: This is a comment indicating that the following lines of code relate to displaying system uptime.

- window "System Uptime" "yellow" "80%": This line creates a window titled "System Uptime" with a yellow color. The window will occupy 80% of the terminal's width.

- sudo uptime: This command executes the uptime command with superuser privileges (using sudo). The uptime command provides information about how long the system has been running, the number of users currently logged in, and the load averages for the system over the last 1, 5, and 15 minutes.

- The output of the uptime command will be displayed within the window created earlier.

- endwin: This line marks the end of the window creation process.


## Step 9: Make it executable
sudo chmod +x Monitoring.sh
<img width="1226" alt="Capture d’écran 2024-04-11 à 14 25 49" src="https://github.com/FloretteSimon/BeCode/assets/155719677/e422f3ce-d3df-4161-9384-8712b4e4a06e">













