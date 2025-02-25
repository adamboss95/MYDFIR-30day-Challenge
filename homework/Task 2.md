## Network Monitoring & Log Analysis  

- **Objective:** Monitor network traffic and analyze logs for suspicious activity.  
Tasks:

- Use tcpdump to capture 100 packets on interface eth0 and save to capture.pcap

```
sudo tcpdump -i eno1 -c 100 -w capture.pcap
```

to verify
```
tcpdump -r capture.pcap
```



- Install iftop to monitor real-time bandwidth usage.
```
sudo apt install iftop
```



- Write a script (scan-logs.sh) to search /var/log/auth.log for "Failed password" attempts and save results to failed-logins.txt.

```
vim scan-logs.sh
```

add these lines for configuration:
```
#!/bin/bash
logfiles="/var/log/auth.log"
mal_ip="/home/abdulwahab/mal_ip"


grep "Failed password" $logfilenew > $outputfilenew


awk '{print $(NF-3)}' $outputfilenew | sort | uniq >> $mal_ip


echo "Results are saved to $outputfilenew"

```




- Block an IP address (e.g., 192.168.1.100) with ufw if it appears in failed-logins.txt.


we create and edit file blockip
```
#!/bin/bash


mal_ip="/home/abdulwahab/mal_ip"



while read -r ip; do
    sudo ufw deny from "$ip" to any
    echo "IP address $ip has been blocked."
done < "$mal_ip"

```


- Schedule the script to run hourly.

crontab -e

```
0 * * * * /home/abdulwahab/block-ip.sh
0 * * * * /home/abdulwahab/scan-logs.sh
```
