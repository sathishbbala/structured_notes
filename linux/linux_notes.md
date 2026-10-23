## Journalctl command 
The journal in Linux refers to the systemd journal which is a centralized logging system managed by systemd-journald service. It collects and stores logs from:
1. Kernel
2. System services
3. User applications
4. Boot messages
   
The logs sent to stdout or error messages to stderr or any background processes that send logs to syslog using logger. As the logs are stored in binary format in /run/log/journal (volatile) 
or /var/log/journal (persistent), a utility like journalctl is needed to read the logs. 

|command|explanation|
|-------|-----------|
|journalctl|Displays the logs in reverse chronological order| 
|journalctl -u service|Displays the logs for the service| 
|Journalctl -b|Displays the logs since the last reboot|
|Journalctl -b -1|Displays the logs from the previous reboot|
|Journalctl -f|Tails the journal logs.. Most commonly used|
|Jounalctl –since today|Logs since the start of today|
|Journalctl –since yesterday|Logs from yesterday onward|
|Journalctl -p err|Shows any logs with priority “err” and above|
|Journalctl -xe|Shows the latest logs with priority and helpful context for failures|
|journalctl --since "YYYY-MM-DD HH:MM:SS" --until "YYYY-MM-DD HH:MM:SS"|Lists journal entries between the time mentioned on the CLI|


## nmap


## How to find internet speed from a VM? 
Used the curl command below to check the internet speed from a ubuntu virtualbox VM. 
```curl -s https://raw.githubusercontent.com/sivel/speedtest-cli/master/speedtest.py | python3```

Using NAT: 
```sathishb@openstack:~$ curl -s https://raw.githubusercontent.com/sivel/speedtest-cli/master/speedtest.py | python3
Retrieving speedtest.net configuration...
Testing from ACT Fibernet (49.205.82.163)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Tata Play Fiber (Chennai) [21.06 km]: 7.649 ms
Testing download speed................................................................................
Download: 27.91 Mbit/s
Testing upload speed.....................................................................................................
.Upload: 11.17 Mbit/s
```

Using bridged Network Adapter:  
```sathishb@testvm:~$ curl -s https://raw.githubusercontent.com/sivel/speedtest-cli/master/speedtest.py | python3
Retrieving speedtest.net configuration...
Testing from ACT Fibernet (49.205.82.163)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Infonet Comm Enterprises Pvt Ltd (Chennai) [21.06 km]: 4.232 ms
Testing download speed................................................................................
Download: 197.94 Mbit/s
Testing upload speed......................................................................................................
Upload: 255.67 Mbit/s
```

I got better speed with bridge networking than NAT. 


