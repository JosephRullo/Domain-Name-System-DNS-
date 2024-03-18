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
<h2>Let's briefly describe what DNS (Domain Name System) is and it's primary use</h2> The Domain Name System (DNS) maps human-readable domain names (in URLs or in email address) to IP addresses. For example, DNS translates and maps the domain www.google.com to the IP address 142.251.40.238. This takes place behind the scenes after you type a URL into a web browser's address bar. Without DNS, navigating the internet wouldn't be easy since we'd have to enter the IP address of each website we want to visit. In a sense it acts like the phone book of the internet.
<p>  
<br>  
<br>
<h2>Important Note</h2>
  
For the demonstration below I will use Active Directory that was installed in a Microsoft Azure Virtual Machine running Windows 2022 Sever and it's Client running Windows 10 on another VM. After joining the Client to the Domain Controller I will login as the Administrator on both VM's to continue with the lab. For a full walkthrough on how to install and configure Active Directory and Azure VM's please view my previous tutorials by clicking on these links:
<p> https://github.com/JosephRullo/Configuring-Active-Directory-within-Azure-VMs/blob/main/README.md</p>
<p> https://github.com/JosephRullo/Azure-Virtual-Machines-and-Networking/blob/main/README.md</p>
<p>
<p>
<h1>Implementation</h1>
<br>
<h2>Step 1.</h2>

**Test Pinging a Hostname and Check Local Cache**
<p>
  
Let's begin with logging in to our Domain Controller and Client VM's as the Administrator using Microsoft Remote Desktop. ** **Note** ** The Client is using the Domain as it's **DNS server**. This means that it is relying on the Domain for all of it's Hostname to IP Address translations. Now on the Client VM, lets open the Command Prompt and type "ping mainframe". You will get a message saying it cannot find the hostname "mainframe". The Client will first check it's local cache to see if it already knows this hostname. If it fails to locate it there, next it will check it's local host file. Let's right click on the start menu and and select the run command. Type the following "c:\windows\system\32\drivers\etc\hosts" to open the local host file (use Notepad to open the file when it prompts you). After checking the local host file for hostnames that are stored on this computer we will not find it there either. Lastly the Client will check it's DNS server. It cannot be found by the Client because the A record for the hostname "mainframe" does not exist yet on the DNS server which is located on the Domain Controller as we configured it.
<p>
<p> 
<p>
<img src="https://i.imgur.com/pT2SjA3.png"/> <height="60%" width="60%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/uW6unAJ.png"/> <height="60%" width="60%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/4uV5tlt.png"/> <height="60%" width="60%" alt="Disk Sanitization Steps"/> 
<p>
<br>
<h2>Step 2.</h2>

**Create A record on the DNS server**
<p>

<br>
