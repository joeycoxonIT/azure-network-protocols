<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Create a Resource Group
- Create a Windows 10 Virtual Machine (VM)
- Create a Linux Virtual Machine
- Ensure both VMs are within the same Virtual Network (VNet) and Subnet
- Use Remote Desktop to connect to your Windows 10 Virtual Machine
- Install and Open Wireshark on a Windows 10 Virtual Machine
- Observe Network Traffic
- Clean Up Azure Environment

<h2>Actions and Observations</h2>

<h3>1) Create a Resource Group</h3>
<p>
  
- Within Azure, navigate to "Resource Groups".
- Once you're at the resource groups page, click "Create".
- Name your resource group and click "Review + Create".
</p>
<p>
<img src="https://i.imgur.com/tFssktD.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
</p>
<br />

<h3>2) Create a Windows 10 Virtual Machine</h3>
<p>
  
- Within Azure, navigate to "Virtual Machines".
- Once you're at the virtual machines page, click "Create" -> "Azure virtual machine".
- Under "Resource group", select the resource group that you previously created (for this tutorial, "RG-Network-Activities").
- Name your virtual machine (for this tutorial, we will name it "windows-vm").
</p>
<p>
<img src="https://i.imgur.com/Xh8PM7l.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
- Under image, select "Windows 10 Pro".
</p>
<p>
<img src="https://i.imgur.com/nPNCsuo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
- Under "Size", select anything with 2 vcpus.
- Create a username and password.
- Once that's done, make sure "Licensing" is checked, then click "Review + Create".
</p>
<p>
<img src="https://i.imgur.com/wdWBKWS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />



<h3>3) Create a Linux Virtual Machine</h3>
<p>
  
- Within Azure, navigate to "Virtual Machines"
- Once you're at the virtual machines page, click "Create" -> "Azure virtual machine".
- Under "Resource group", select the same resource group used in the previous step.
- Name your virtual machine (for this tutorial, we will name it "linux-vm").
- Under image, select "Ubuntu Server 22.04 LTS" or "Ubuntu Server 24.04 LTS".
</p>
<p>
<img src="https://i.imgur.com/DxRcczj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
- Like the previous step, under "Size" select anything with 2 vcpus
- Create a username and password
</p>
<p>
<img src="https://i.imgur.com/oJmMEuq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

- At the bottom of the page, click "Next: Disks" then "Next: Networking" to navigate to the "Networking" tab.
- Select the virtual network you created when setting up the Windows 10 Virtual Machine (for this tutorial: Lab2-Vnet).
- Click "Review + Create".
</p>
<p>
<img src="https://i.imgur.com/RXDhfxi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<h3>4) Ensure both VMs are within the same Virtual Network (VNet) and Subnet</h3>
<p>

- Navigate to Virtual Machines.
- Click on your Windows virtual machine and check the name of the virtual network/subnet.
- Click on your Linux virtual machine and ensure that the virtual network/subnet is the same as your Windows virtual machine.
</p>
<p>
<img src="https://i.imgur.com/dWUwyEu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.imgur.com/MrvPL8O.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<h3>5) Use Remote Desktop to connect to your Windows 10 Virtual Machine</h3>
<p>

- Go to the search bar at the bottom of the screen and enter and select "Remoke Desktop Connection"
- After opening "Remote Desktop Connection", enter the Public IP Address for your Windows 10 Virtual Machine. To find it, go to "Virtual machines" in Azure and click on your Windows 10 Virtual machine (in this case "windows-vm").
- After entering the public IP address, login to your virtual machine.
</p>
<p>
<img src="https://i.imgur.com/HCEAQJu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<h3>6) Install and Open Wireshark on a Windows 10 Virtual Machine</h3>
<p>

- In your Windows 10 Virtual Machine paste this link into a browser: "https://www.wireshark.org".
- Click "Download". Then select the "Windows x64 Installer".
- After downloading the file, click "open file" and install "Wireshark".
</p>
<p>
<img src="https://i.imgur.com/VNAJ3c5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.imgur.com/Oze6GJ6.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<br />

<h3>7) Observe Network Traffic</h3>
<p>

- In the search bar at the bottom of the screen, type and open "Wireshark"
- Once "Wireshark" is open, single click "Ethernet" to ensure it's highlighted, then start packet capture by clicking the blue fin icon at the top left of the page (below "File")
</p>
<p>
<img src="https://i.imgur.com/ree9GLk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<h3>8) Observe ICMP Traffic</h3>
<p>

- Within Wireshark, type in "icmp" in the search bar at the top then hit enter to filter only ICMP traffic.
- Go into the "Virtual machines" page in Azure to retrieve the private IP address of the Linux virtual machine (linux-vm).
- Go to the search bar at the bottom of the screen in your Windows virtual machine and type and open "Windows Powershell"
- Within Powershell, we want to ping the private IP address of the Linux virtual machine. Type in "ping" followed by the private IP address (example: ping 10.0.0.5).
</p>
<p>
<img src="https://i.imgur.com/Yu7RHNd.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
- Attempt to ping a public website and observe traffic (example: www.google.com)
</p>
<p>
<img src="https://i.imgur.com/nEpSfRs.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
- Initiate a perpetual/non-stop ping from your Windows 10 virtual machine to your Linux virtual machine (example: ping 10.0.0.5 -t)
</p>
<p>
<img src="https://i.imgur.com/OMQdH8r.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
- Open the Network Security Group that your Linux virtual machine is using and disable incoming (inbound) ICMP traffic. To do this, navigate to virtual machines in Azure, then click your Linux virtual machine (linux-vm), then click "Networking" -> "Network settings" and then select your Network security group (example: linux-vm-nsg).
- Once you're in the Network security group page, on the left of the page, click "Settings" -> "Inbound security rules", then click "Add". Once that's done, under "Destination port ranges" type in "*". Under Protocol, select "ICMPv4". Under "Action", select "Deny". Under "Priority" type "290". Then click "Add".
</p>
<p>
<img src="https://i.imgur.com/tRcOBti.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.imgur.com/Hpn0XHV.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>

- Back in the Windows 10 virtual machine, observe the ICMP traffic in WireShark and the command line Ping activity. If done correctly, the ping requests should time out.
</p>
<p>
<img src="https://i.imgur.com/9rK6eS6.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>

- Re-enable ICMP traffic by deleting it from the Network Security Group.
- Back in the Windows 10 virtual machine, observe the ICMP traffic in WireShark and the command line Ping activity, the ping requests should start working again
- Stop the ping activity by hitting "Ctrl + C" in Powershell, then click the "Square" icon in Wireshark.
</p>
<p>
<img src="https://i.imgur.com/7QNtzP9.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<br />


<h3>9) Observe SSH Traffic</h3>
<p>

- In Wireshark, type in the search bar "SSH" and hit "Enter" to filter for only SSH traffic.
- Open Powershell again and type ssh (username@ private IP address) (example: ssh labuser@10.0.0.5).
- Once that's done, type commands (username, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark.
</p>
<p>
<img src="https://i.imgur.com/6FfxOHf.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>

- To close the SSH connection, type "exit" in Powershell
</p>
<br />

<h3>10) Observe DHCP Traffic</h3>

<p>

- In Wireshark, type in the search bar "dhcp" and hit "Enter" to filter for only DHCP traffic.
- Next we want to create a script to enter in Powershell later, open Notepad and type in "ipconfig /release" and "ipconfig /renew".
- Save the file to "c:\programdata". Make sure "all files" is selected and name it "dhcp.bat".
</p>
<p>
<img src="https://i.imgur.com/RfvpNBl.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.imgur.com/ijybvew.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
- Go to Powershell and type and enter ".\dhcp.bat" to issue your virtual machine a new IP address.
- Observe DHCP traffic.
</p>
<p>
<img src="https://i.imgur.com/HRH0Txr.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<br />

<h3>11) Observe DNS Traffic</h3>

<p>

- In Wireshark, type in the search bar "dns" and hit "Enter" to filter for only DNS traffic.
- In Powershell, use "nslookup" to see the IP address for a website (example: "nslookup google.com" or "nslookup disney.com").
- Observe DNS traffic.
</p>
<p>
<img src="https://i.imgur.com/HfL7qhh.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
</p>
<br />

<h3>12) Observe RDP Traffic</h3>

<p>

- In Wireshark, type in the search bar "tcp.port == 3389" and hit "Enter" to filter for only RDP traffic.
- Observe RDP traffic.
- You'll notice that the traffic is non-stop because the RDP (protocol) is constantly showing a live stream from one computer to another, therefore traffic is always being transmitted.
</p>
<p>
<img src="https://i.imgur.com/70sUnmd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<h3>13) Clean Up Azure Environment</h3>

<p>

- First close your Remote Desktop connection.
- Go into Azure and navigate to "Resource groups".
- Delete the Resource group that you created at the beginning of the lab.
- Verify that the resource group has been deleted.
</p>
<p>
<img src="https://i.imgur.com/GatVzak.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.imgur.com/OkURrNk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<h3>Congratulations! You've completed this tutorial.</h3>
