

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
From here, we will need to create our first Windows Virtual Machine! Back in the search bar, type "Virtual machines". After selecting VM, click create. Running down the list of options here, make sure our subscription is the same one we used before. Under that is the Resource group, and we will want to select the one we created, "VM-Test". For name, let's name it VM-Windows-Test. !! MAKE SURE THE REGION IS SET TO THE ONE YOU HAD USED PREVIOUSLY. If it's not, we will run into some issues!! Going down to Image for this one, make sure you select Windows 10 Pro, version 22H2 - x64 Gen2. For size, you'll want something with at least 2 vCPUs and 8 GiB of memory, or else the device will run incredibly slow. For the Username and Password, set something you'll remember and write it down, as we will need it for later. I will use the username "labuser" and the password "Azurelab123!" Without the "". Make sure you select the checkbox for "I confirm I have an eligible Windows 10/11 license with multi-tenant hosting rights" at the bottom. Your settings should look like this.

![image](https://github.com/user-attachments/assets/405dcb50-d3b7-46a2-a00e-f37ab29c73e3)
![image](https://github.com/user-attachments/assets/983b2ece-9748-45cf-9757-d29d0d906a85)

Let's now go through and click Networking on the top, and we will need to create a new Virtual Network. We will create a new one, and it should be auto-named already to VM-Windows-Test-vnet if that is what you had named your VM. We don't need to do anything else, so let's just click review and create, then create. From here, we now need to make our Linux machine. So we will go back and select Ubuntu Server 24.04 D4 LTS, and we can name it VM-Test2. Try it out yourself, but I will have an Image below so you can cross-reference if you want to test yourself. Also, as a side note, make sure you put it in the same virtual network as the one that the VM-Windows-Test is in. If you tried it on your own you might notice that you had run into an error about the Key pair name. Let's go ahead and switch the Authentication type to password instead. Now we can enter a Username and password. Your configuration should look something like this. 

![image](https://github.com/user-attachments/assets/c11fe069-607b-4c8b-b23c-6960c6a37552)
![image](https://github.com/user-attachments/assets/f30f9b9f-bf8d-436c-bd09-32e9598ceb6e)
![image](https://github.com/user-attachments/assets/f407e29a-31ae-444b-8a03-a0142eb955cd)


<h2> Remoting Into Our Windows Machine </h2>
With our VM created, let's go back into Resource Groups, and if we click on VM-Test, it should look something like this!

![image](https://github.com/user-attachments/assets/d4f67752-9e54-466d-a712-ce0dc370c18f)


We can see our Resource groups and the two VMs. Nice! You might have noticed that it had also created a Resource group labeled NetworkWatcherRG; we can ignore this as it is not needed for this lab, but if you are interested, I would recommend doing some solo research on it. Next, we are going to Remote in to our Windows VM. Click on VM-Windows-Test and take a look at the public IP address.
![image](https://github.com/user-attachments/assets/d210b3a3-0181-484f-9f7c-62c919d93782)

Copy that IP address and in our Windows search bar on the bottom left, search for RDP, and Remote Desktop Connection will show up. Open that. 

![image](https://github.com/user-attachments/assets/0b0f3591-240f-4156-8602-07434021a73a)

Go ahead and show options. You'll see now you can enter a username. This will be the username we had set back when we were creating our Virtual Machine. For me, that is "labuser". From here, go ahead and enter the public IP address of the VM-Windows-Test for my case, which is 20.3.232.55. This will probably be different for you. Click connect, and it should ask you for a password. Mine is Azurelab123!. After that, click yes, and your remote session should start. Once you get to the screen that says Choose privacy settings for your device, go ahead and disable them all, although it doesn't matter for this.. Congratulations! You just started your first remote session! (You can also click no on shareable networks as well, once on the main desktop.)
 
</p>
<br />
<h2>Observing ICMP Traffic</h2>
<p>
Once we are on the VM, go ahead and go to Microsoft Edge, and we are going to download a tool called <a href="https://www.wireshark.org"> Wireshark</a>. Go ahead and download the Windows version. Open it up and click Next, Noted, Next, Next, until you get to install, then click on install. (It will probably install Npcap, we dont need this, so we can skip this, but it's already installing, no harm, no foul. Open up Wireshark, and it should look something like this. 

 ![image](https://github.com/user-attachments/assets/b6f47a56-65c4-4a7a-83b8-1429016a59f4)

Wireshark will allow us to filter through tons of network traffic like SSH, DHCP, ICMP, RDP, and even DNS. Neat. For the sake of this lab, though, we will be monitoring ICMP, so to start, go ahead and click that shark icon in the top right. As soon as you do so, you should notice that you're seeing all real-time traffic, and there is a lot of spam. This doesn't help us as we only want to see ICMP, so when we ping our Ubuntu's public IP, we can see it. On the top bar, you should see something that says, "Apply a display filter." Click on that and type "icmp" without the "" and yes, CAPS matter. Hit enter on your keyboard, and we will see a pure white box where all the spam traffic used to be. From here, let's open up PowerShell, and your setup should look something like this.

![image](https://github.com/user-attachments/assets/fd674e9d-facc-496a-ad33-e661d67dc7fb)

Now, go ahead and grab the Ubuntu server's PRIVATE IP address from Azure, same way we grabbed the Public IP from the Windows VM, but we will be selecting VM-Test2, our Ubuntu server VM. It'll just be a little below the public IP address. Once we get that, let's go back into our Remote session, and in PowerShell, we will use the ping command so that we can observe our Windows VM being able to communicate with our Ubuntu VM. So, for my case, ping 10.0.0.5. And look at that, we are communicating with the Ubuntu Server. Awesome!

![image](https://github.com/user-attachments/assets/119f77e5-8935-40d7-ba7a-030b29670417)

As you can see in Wireshark, we can see that the packet was sent, and the Ubuntu server responded to the Windows VM, saying that it had received it. NOTE: If you got an error, make sure that both devices are on and running and that they are on the same Region and Virtual Network that we had created. Now, what if we disable inbound ICMP traffic? What do you think would happen? Let's try it and see!. Back in Azure, let's click on VM-Test2. Under Networking on the left-hand side, select Network settings. From here, select "+ create port rule", "Inbound port rule", Source will be Any, and select the ICMPV4 Protocol's radio button. Under action, select Deny. It should look something like this.

![image](https://github.com/user-attachments/assets/75542a2d-a60b-47c7-b73f-8a58beaa2405)

Click Add, and a new security rule will be added. Going back to our Remote session, if we try to ping that same private IP address, you'll see that the Request has timed out. Since we had disabled the inbound ICMP protocol on our Ubuntu server, it is blocking any and all pings from our Windows VM. You can even see that in Wireshark, it had sent a ping request, but it tells us that there was no response seen.

![image](https://github.com/user-attachments/assets/ebae898a-ea07-40f1-816f-0eb22bf8d093)

If we remove the rule that we previously added, we will be able to ping our Server again! neat!
</p>
<br />

<h3>Lab Cleanup</h3>
<p>
 Now that we are done, let's go ahead and clean up the lab. Still in the remote session, we can exit by right-clicking the Windows icon, then selecting disconnect under sign out. Back in Azure, go to your Resource Groups and select the VM-test that we had created. Once we are in the RG, we can select on the top bar, Delete resource group. In here, select the Checkbox for Apply force delete for selected Virtual machines and Virtual machine scale sets. Under that, you'll have to put in the name of the Resource Group you are trying to delete. Select Delete. It should look something like this,

![image](https://github.com/user-attachments/assets/bfdb470c-1033-48f4-9c3e-6302d81dd67a)

After we have done that, we will have officially deleted everything that we created for this lab! You can also delete NetworkWatchersRG.
</p>
