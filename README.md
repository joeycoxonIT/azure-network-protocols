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
  
- Within Azure, navigate to "Resource Groups"
- Once you're at the resource groups page, click "Create"
- Name your resource group and click "Review + Create"
</p>
<p>
<img src="https://i.imgur.com/tFssktD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<h3>2) Create a Windows 10 Virtual Machine</h3>
<p>
  
- Within Azure, navigate to "Virtual Machines"
- Once you're at the virtual machines page, click "Create" -> "Azure virtual machine"
- Under "Resource group", select the resource group that you previously created (for this tutorial, "RG-Network-Activities")
- Name your virtual machine (for this tutorial, we will name it "windows-vm")
</p>
<p>
<img src="https://i.imgur.com/Xh8PM7l.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
- Under image, select "Windows 10 Pro"
</p>
<p>
<img src="https://i.imgur.com/nPNCsuo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
- Under "Size", select anything with 2 vcpus
- Create a username and password
- Once that's done, make sure "Licensing" is checked, then click "Review + Create"
</p>
<p>
<img src="https://i.imgur.com/wdWBKWS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />



<h3>3) Create a Linux Virtual Machine</h3>
<p>
  
- Within Azure, navigate to "Virtual Machines"
- Once you're at the virtual machines page, click "Create" -> "Azure virtual machine"
- Under "Resource group", select the same resource group used in the previous step
- Name your virtual machine (for this tutorial, we will name it "linux-vm")
- Under image, select "Ubuntu Server 22.04 LTS" or "Ubuntu Server 24.04 LTS"
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

- At the bottom of the page, click "Next: Disks" then "Next: Networking" to navigate to the "Networking" tab
- Select the virtual network you created when setting up the Windows 10 Virtual Machine (for this tutorial: Lab2-Vnet)
- Click "Review + Create"
</p>
<p>
<img src="https://i.imgur.com/RXDhfxi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<h3>4) Ensure both VMs are within the same Virtual Network (VNet) and Subnet</h3>
<p>

- Navigate to Virtual Machines
- Click on your Windows virtual machine and check the name of the virtual network/subnet
- Click on your Linux virtual machine and ensure that the virtual network/subnet is the same as your Windows virtual machine
</p>
<p>
<img src="https://i.imgur.com/dWUwyEu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.imgur.com/MrvPL8O.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
