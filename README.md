

# Creating Virtual Machines
<p align="center">
</p>

<h1>Creating Two VMs on the Same Virtual Network. (Azure)</h1>
This tutorial outlines creating a resource group and two VMs on the same virtual network.<br />


- Microsoft Azure subscription (Virtual Machines/Computer)
- Remote Desktop
- Windows Desktop

<h2>Operating Systems Used </h2>

- Ubuntu Server 24.04 D4 LTS
- Windows 10 (21H2)

<h2>Creating a Resource Group and VM Steps</h2>

- Step 1: Creating a Resource Group
- Step 2: Creating a VM
- Step 3: Remoting Into Our Windows Machine
- Step 4: Observing ICMP Traffic

<h2>Creating a Resource Group</h2>

![image](https://github.com/user-attachments/assets/fec4ac63-9a48-48f2-b565-7d046611d799)

<p>
Once we are in Azure, go up to the Azure Search bar that says, "Search resources, services, and docs". From here, we will go ahead and type "Resource Group" and Create. Next, we're going to need to set our subscription. Since I am doing this for testing purposes, I will select Azure Subscription 1. We are also going to select a Region. I am selecting Region West US 2. !! MAKE SURE TO ALWAYS USE THE SAME REGION THAT IS SET TO THE RESOURCE GROUP !! We will name this VM-Test. Click Review + Create and then click on Create. 
</p>
<br />
</p>
<h2> Creating a VM </h2>
<p>
From here, we will need to create our first Windows Virtual Machine! Back in the search bar, type "Virtual machines". After selecting VM, click create. Running down the list of options here, make sure our subscription is the same one we used before. Under that is the Resource group, and we will want to create the one we created, "VM-Test". For name, let's name it VM-Windows-Test. !! MAKE SURE THE REGION IS SET TO THE ONE YOU HAD USED PREVIOUSLY. If it's not, we will run into some issues!! Going down to Image for this one, make sure you select Windows 10 Pro, version 22H2 - x64 Gen2. For size, you'll want something with at least 2 vCPUs and 8 GiB of memory, or else the device will run incredibly slow. For the Username and Password, set something you'll remember and write it down, as we will need it for later. I will use the username "labuser" and the password "Azurelab123!" Without the "". Make sure you select the checkbox for "I confirm I have an eligible Windows 10/11 license with multi-tenant hosting rights" at the bottom. Your settings should look like this.

![image](https://github.com/user-attachments/assets/405dcb50-d3b7-46a2-a00e-f37ab29c73e3)
![image](https://github.com/user-attachments/assets/983b2ece-9748-45cf-9757-d29d0d906a85)




 
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
