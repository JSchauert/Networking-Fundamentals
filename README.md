# Networking-Fundamentals

Josh Schauert Week 8 Homework

Phase 1 :
fping -s 15.199.100.91 203.0.113.32 15.199.94.91 161.35.96.20 192.0.2.0
 
IP 161.35.96.20 comes back as alive which is a vulnerability since rockstar corp doesnt want responses
Reccomendation to restrict ICMP echo requests against ip 161.35.96.20 to prevent responses:
 sudo traceroute -I 161.35.96.20 - Shows below information
 
Found at Layer 3 ( Networking Layer )

Phase 2: 

sudo nmap -sS 161.35.96.20
 
The open ports the Syn Scan came back with is Port 22
Port 22 is accepting connections
Found on Layer 4 ( Transport Layer )
This can be mitigated by using an encrypted VPN connection to access the system, this way the vpn would have to be bypassed before hackers can access the vulnerable port.
OR you can filter traffic to port 22 to prevent unathorized access

Phase 3: 
ssh jimi@161.35.96.20 -p 22
password: hendrix
ping rollingstone.com
vim /etc/hosts
FINDINGS = 98.137.246.8 rollingstone.com
exit Jimi
nsloopkup > rollingstone.com
>98.137.246.8
 
RESULTS = unknown.yahoo.com.
Found in the application layer ( layer 7 )
The mitigation strategy here is quite an obvious one, Default usernames and passwords should never be used. A simple staff training with reinforced credential changes could solve this problem.
Phase 4: 
Found leftover hacker file at etc/packetcaptureinfo.txt
cat /etc/packetcaptureinfo.txt
RESULTS = https://drive.google.com/file/d/1ic-CFFGrbruloYrWaw3PvT7ielTkh3eF/view?usp=sharing
downloaded and opened in wireshark
under ARP on line 5 got "duplicate IP address detected for 192.168.47.200
This was found on the application layer ( Layer 7 )
An easy way to mitigate the risk of MAC address spoofing would be to use a network monitor to set up an alert to alert the administrators when a MAC address is detected using 2 seperate IP's . You could also implement intrusion detection systems to monitor for activities incompatible with normal behavior.
 
seems the hacker spoofed the MAC Address on line 4 to get access
under HTTP on line 16 shows the hackers message which you can see in the screenshot below:
 



