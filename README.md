<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1 align="center">Network Security Groups and Inspecting Traffic Between Azure Virtual Machines</h1>

<h2 align="center">Summary</h2>
This readme.md outlines the installation of WireShark onto a virtual machine, and the usage of that application to inspect traffic between two Azure virtual machines. The purpose of this project was to get a better understanding of not just Azure but networking in general, and how we can use applications to inspect the various network protocols and how they operate. This project was repeated multiple times to ensure we gained a strong understanding of WireShark and the capabilites of applications like WireShark.

<h2 align="center">Environments and Technologies Used</h2>

- Microsoft Azure
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark
  
<h2 align="center">Operating Systems Used</h2>

- Windows 10
- Ubuntu Server 20.04

<h2 align="center">Macro-Level Steps</h2>

- Set-up two virtual machines in Azure, a Windows 10 installation and an Ubuntu server installation.
- Install WireShark onto the Windows 10 installation.
- Observe all ICMP traffic between the two virtual machines using WireShark and _ping_.
- Observe all SSH traffic between the two virtual machines using WireShark.
- Observe all DHCP traffic between the two virtual machines using WireShark and _ipconfig_.
- Observe all DNS traffic between the two virtual machines using WireShark and _nslookup_.
- Observe all RDP traffic between the two virtual machines using WireShark.

<h2 align="center">Actions and Observations</h2>

<p align="center" >
<img src="https://github-production-user-asset-6210df.s3.amazonaws.com/1596195/276994422-24f3efa5-71e9-4e38-b82d-d9aa21491685.png" height="80%" width="80%" alt=""/>
</p>
<p>
Our first step is to set-up two virtual machines in Microsoft Azure. One should be a Windows 10 installation, and the other an Ubuntu server installation. We should then connect to the Windows virtual machine by using Remote Desktop. We then install WireShark from http://www.wireshark.org .
</p>
<br />

<p align="center">
<img src="https://github-production-user-asset-6210df.s3.amazonaws.com/1596195/276994845-89cef51b-a35d-46a0-ac87-3765156e1a0d.png" height="80%" width="80%">
</p>
<p>
We open up WireShark and we can begin to start to inspect the network traffic that can occur between our two virtual machines. First, we filter for ICMP traffic. We must also enable ICMP traffic for the Ubuntu server, as by default it is turned off. We can do this in the network settings of the Azure admin panel. Then, using the private IP address of our Ubuntu virtual machine, we <i>ping</i> it from our Windows installation. The <i>ping</i> protocol uses ICMP to connect to different devices, and as soon as we use <i>ping</i> we notice in WireShark that data has been sent over the network. We can fiddle with this even more by turning ICMP on and off in the Azure panel for the Ubuntu installation. When it is on, <i>ping</i> requests go through as normal. When it is off, <i>ping</i> requests no longer function.
</p>
<br />

<p align="center">
<img src="https://github-production-user-asset-6210df.s3.amazonaws.com/1596195/276999472-88512868-e948-4f79-ba26-36d78b3c2968.png" height="80%" width="80%">
</p>
<p>
Next we filter for SSH traffic. SSH is the protocol for remotely connecting to another device using the command line. To test this, we open the command line on our Windows installation and connect to our Ubuntu server using SSH. Then we can type various commands into the command line and observe the traffic that is created in WireShark. Any time we type, data is sent back and forth between the two virtual machines, and we can see this in WireShark.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next we filter for DHCP traffic. DHCP is the protocol that assigns IP addresses to devices. To see this type of traffic, we go into the command line and use the <i>ipconfig /renew</i> command. This command requests a new IP address for the Windows installation from the network. When we use this command, we will see traffic on the DHCP port (ports 67 and 68) within WireShark.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next we filter for DNS traffic. DNS is the protocol that converts website names into IP addresses. To see this type of traffic, we go into the command line and use the <i>nslookup</i> command. This command takes a website address and returns the IP addresses that are commonly associated with those names. In this example we used Google and Disney. When we do this, we can see in WireShark DNS traffic being sent back and forth.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next we filter for RDP traffic. RDP is the protocol for remote connecting to another device, and is what Remote Desktop uses to connect to other devices. When we filter for RDP traffic, we can see that traffic is being sent non-stop between our own computer and the Windows 10 virtual machine. This may seem strange, because even if we aren't doing anything on the virtual machine traffic is still being sent. However, that is because the remote connection is basically a 'live stream' of the virtual machine, and therefore data must be sent constantly to the home computer even if 'nothing' is actually happening.
</p>
<br />

<p>
With that our testing is done! We just have to delete our virtual machines and move onto the next project.
</p>
<br />
