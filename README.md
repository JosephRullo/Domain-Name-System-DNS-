<p align="center">
<img src="https://i.imgur.com/Mfc8tBk.jpeg" height=100% width=100% alt="Microsoft Active Directory Logo"/>
</p>

<h1> <p align="center"> Domain Name System</h1>
<p align="center"> This tutorial outlines a basic understanding of what DNS is and how it functions as well as some command line prompts for identifying and resolving common issues.<br />
<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Virtual Machines
- Remote Desktop
- Active Directory
- Command Prompt

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Windows Server 2022
<p>
<p>
  <h2>High-Level Configuration Steps</h2>

- Inspect DNS A records on the server (Hostname to IP Address Mappings)
- Create our own A records on the server and observe them on the client
- Delete records from the server and inspect/clear the client dns cache
- Create a "CNAME" record (mapping one hostname to another hostname)
- Discuss what Root Hints are and how they work
<p>
<br> 
<h2>Let's briefly describe what DNS (Domain Name System) is and it's primary use</h2> The Domain Name System (DNS) maps human-readable domain names (in URLs or in email address) to IP addresses. For example, DNS translates and maps the domain www.google.com to the IP address 142.251.40.238. This takes place behind the scenes after you type a URL into a web browser's address bar. Without DNS, navigating the internet wouldn't be easy since we'd have to enter the IP address of each website we want to visit. 
<p>  
<br>  
<br>
For the demonstration below I will use Active Directory that was installed in a Microsoft Azure Virtual Machine running Windows 2022 Sever and it's Client running Windows 10. After joining the Client to the Domain Controller I will login as the Administrator on both VM's to continue with the lab. For a full walkthrough on how to install and configure Active Directory and Azure VM's please view my previous tutorials by clicking on these links:
<p> https://github.com/JosephRullo/Configuring-Active-Directory-within-Azure-VMs/blob/main/README.md</p>
<p> https://github.com/JosephRullo/Azure-Virtual-Machines-and-Networking/blob/main/README.md</p>
<p>
<p>
<h1>Implementation</h1>
<br>
<h2>Step 1.</h2>

**Log in to Domain Controller and Client as the Adminstrator**
<p>
Let's begin with logging in to our Domain Controller and Client VM's as the Administrator using Microsoft Remote Desktop.
<p>
<p> 
<p>
<img src="https://i.imgur.com/nVwElfM.png" alt="Microsoft Active Directory Logo"/> <height="60%" width="60%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/8y5iyce.png" alt="Microsoft Active Directory Logo"/> <height="60%" width="60%" alt="Disk Sanitization Steps"/> 
<p>
<br>
<h2>Step 2.</h2>

**Log in and Check your IP Address**
<p>
Log into the VM via Remote Desktop. Once Window's is done booting, open the web browser and go to this website www.whatismyipaddress.com. This will show you the actual IP Address and region of the VM. Next try going to www.google.com and notice the native language of the region is displayed, in this case Japanese.
<p>
<p>
<img src="https://i.imgur.com/QvpRM8Q.png" alt="Microsoft Active Directory Logo"/> <height="60%" width="60%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/X19xJQN.png" alt="Microsoft Active Directory Logo"/> <height="60%" width="60%" alt="Disk Sanitization Steps"/> 
<p>
<br>
