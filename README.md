# Incident-Response-Analysis
Using Wireshark and a live capture of traffic, detected, and reported on, abnormal traffic on a corporate network.


## Activity: Incident Response Analysis

### Overview

Working as a "Security Engineer" for X-CORP to support the SOC infrastructure, SOC analysts have noticed some discrepancies with alerting in the Kibana system and the manager has asked the Security Engineering team to investigate. 

Our team has confirmed that newly created alerts are working. 

1. You are to monitor live traffic on the wire to detect any abnormalities that aren't reflected in the alerting system. 

2. Report back all your findings to both the SOC manager and the Engineering Manager with appropriate analysis.

### Setup

You will use the Kali VM to analyze live traffic on the wire.

In order to get started, you will need to:
- Connect to the Kali VM.
- Open a terminal window and run the command `systemctl start sniff`. 
    - This command uses `tcpreplay` to replay PCAPs in `/opt/pcaps` onto Kali’s `eth0` interface. 
- Launch Wireshark and capture traffic on the `eth0` interface.
- After 15 minutes have passed, run the command `systemctl stop sniff` to stop the `tcpreplay`. 
  - Please note that replaying the PCAPs will use up the CPU memory. You will need to stop this service in order to avoid performance issues with your virtual machine. 
- Save the capture to file. (**This is an important step**.)
- Profile users' behavior from their packet data.

If you are unable to find some of the solutions, it is possible you did not allow Wireshark to capture traffic for long enough. To save time, feel free to use the following PCAP file below:
  
  - [PCAP](https://drive.google.com/file/d/1td7SF7oFsgTJ_itbVw2XOyHWvzyyedoq/view?usp=sharing) 
  
**Note:** You will be dealing with live malware in this activity. Please make sure all work is done on Azure machines. **

### Overview 

The Security team requested this analysis because they have evidence that people are misusing the network. Specifically, they've received tips about:

    - "Time thieves" spotted watching YouTube during work hours.
    - At least one Windows host infected with a virus.
    - Illegal downloads.

- A number of machines from foreign subnets are sending traffic to this network. Therefore, you will see many IP ranges in your capture. 

### Hints
At least two users on the network have been wasting time on YouTube. Usually, IT wouldn't pay much mind to this behavior, but it seems these people have created their own web server on the corporate network. So far, Security knows the following about these time thieves:

- They have set up an Active Directory network.
- They are constantly watching videos on YouTube.
- Their IP addresses are somewhere in the range `10.6.12.0/24`.

The Security team received reports of an infected Windows host on the network. They know the following:
- Machines in the network live in the range `172.16.4.0/24`.
- The domain mind-hammer.net is associated with the infected computer.
- The DC for this network lives at `172.16.4.4` and is named Mind-Hammer-DC.
- The network has standard gateway and broadcast addresses.

IT was informed that some users are torrenting on the network. The Security team does not forbid the use of torrents for legitimate purposes, such as downloading operating systems. However, they have a strict policy against copyright infringement.

IT shared the following about the torrent activity:

- The machines using torrents live in the range `10.0.0.0/24` and are clients of an AD domain.
- The DC of this domain lives at `10.0.0.2` and is named DogOfTheYear-DC.
- The DC is associated with the domain dogoftheyear.net.

---
© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.  
