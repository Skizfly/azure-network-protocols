<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this guide, we explore network traffic to and from Azure Virtual Machines using Wireshark and experiment with Network Security Groups. <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>Advanced Steps</h2>

- Launch Wireshark on the Azure Virtual Machine
- Analyze incoming and outgoing network traffic
- Identify patterns and protocols used in the communication
- Access the Azure portal and navigate to the desired Virtual Machine
- Open the Network Security Groups section
- Modify NSG rules to observe the impact on traffic
- Evaluate the changes in Wireshark's network capture

<h2>Activities and Notations</h2>

![image](https://github.com/Skizfly/azure-network-protocols/assets/153954157/34f50e0b-2507-44e3-88a7-0c342ba26215)

<p>
</p>
<p>
Utilizing Remote Desktop Connection, I establish a connection to the Windows VM using its public IP address. Subsequently, I install Wireshark to initiate traffic inspection.
<br />

![image](https://github.com/Skizfly/azure-network-protocols/assets/153954157/2ca22bc9-e9b6-410f-b542-735412518e5e)

<p>
</p>
<p>
In Wireshark, I applied a filter for ICMP (Internet Control Message Protocol) traffic and launched PowerShell to execute a ping command. Ping, leveraging ICMP, aids devices in network communication and problem identification in data transmission. I employed ping to test communication with the Ubuntu VM using its private IP address and with google.com. Subsequently, I initiated a continuous ping to the Ubuntu VM to observe the functionality of network security groups. The perpetual ping was executed using the command:<b>`ping -t </b> 
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
