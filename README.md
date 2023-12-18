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

![image](https://github.com/Skizfly/azure-network-protocols/assets/153954157/d45f1822-6732-4f2d-a325-0550cc1dc183)


<p>
</p>
<p>
In the Azure portal, I accessed the networking settings for the Ubuntu VM and incorporated an inbound security rule to restrict ICMP traffic. It's essential to set the priority higher than SSH (300) to ensure the rule takes precedence.
</p>
<br />

![image](https://github.com/Skizfly/azure-network-protocols/assets/153954157/bfbf756a-90ea-48b5-a789-106066372cae)

<p>
</p>
<p>
Upon revisiting the Windows VM, I observe that ICMP traffic is now blocked following the implementation of the inbound security rule. After modifying the rule to permit traffic once more, the perpetual ping resolves without timing out.
</p>
<br />

![image](https://github.com/Skizfly/azure-network-protocols/assets/153954157/1aa143af-7a0e-4082-b61e-08710e4605a4)

<p>
</p>
<p>
Subsequently, I opted to analyze SSH traffic. Using the ssh command, I logged into the Ubuntu server via PowerShell. Employing Wireshark, I filtered the traffic using <b>tcp.port == 22`</b>. While logged into the Ubuntu server, each command I executed during my session is recorded in Wireshark.
</p>
<br />

![image](https://github.com/Skizfly/azure-network-protocols/assets/153954157/cec014c9-880e-4ebe-9875-9772d051c565)

<p>
</p>
<p>
After scrutinizing SSH traffic, I exited the Ubuntu server to focus on DHCP traffic. To witness its effects, I attempted to acquire a new IP address from my VM using the command <b>`ipconfig /renew`</b>. This command would initiate the issuance of a new IP address, resulting in a brief disconnection for a few seconds. After reconnecting, the ensuing traffic is captured and displayed in Wireshark.
</p>
<br />

![image](https://github.com/Skizfly/azure-network-protocols/assets/153954157/627e79d7-c5ad-46b5-a46a-0fa1696f2390)

<p>
</p>
<p>
To examine DNS traffic, I employed the filter <b>`udp.port == 53`</b> and the nslookup command. My objective was to observe the results of looking up google.com and disney.com, two highly popular sites.
<br />

![image](https://github.com/Skizfly/azure-network-protocols/assets/153954157/969474c1-3c65-439a-aca3-911efc4f3e65)

<p>
</p>
<p>
To conclude my lab, I chose to scrutinize RDP traffic. The Wireshark filter for this is <b>`tcp.port == 3389`</b>. Continuous traffic is observed as RDP constantly provides a live stream from one computer to another (in my case, from my computer accessing the VM hosted on Azure), resulting in constant data transmission.
<br />

<h2>Insights Gained</h2>
<p>
</p>
<p>
The primary goal of this lab is to explore the utilization of various protocols and ports within a network involving different devices. Although troubleshooting is not the immediate objective, the lab serves the purpose of gathering valuable information. In a troubleshooting scenario, the use of tools such as Wireshark and the command line becomes crucial to understand how traffic moves through ports and protocols in a network. Success in troubleshooting requires both familiarity with these tools and an inquisitive mindset!
</p>
<br />
