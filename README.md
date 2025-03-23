

<p align="center">
 <img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
 <img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
 </p>
 
 <h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
 In this lesson, we observe various network traffic to and from Azure Virtual Machines with Wireshark, with our focus on the different protocols like ICMP, DNS, SSH, DHCP, & RDP.
 We further our lesson with the Network Security Groups (NSGs) and how they control inbound and outbound traffic, with an emphasis on security rules that are created that can
 permit or restrict access between the different types of traffic between the virtual machines.<br />



 ***(Video forthcoming)***
 
 <h2>Environments and Technologies Used</h2>
 
 - Microsoft Azure (Virtual Machines/Compute)
 - Remote Desktop
 - Various Command-Line Tools
 - Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
 - Wireshark (Protocol Analyzer)
 
 <h2>Operating Systems Used </h2>
 
 - Windows 10 (21H2)
 - Ubuntu Server 20.04
 
 <h2>Create Work Environment</h2>
 
 - Step 1: Create Resource Group In Azure
 - Step 2: Create a Windows 10 Virtual Machine and place it in the Resource Group created earlier. Also, this will allow for the creation of the Vnet and Subnet
 - Step 3: Create the Linux-Ubuntu Virtual Machine, and place it in the Resource Group created earlier. 

 
 <h2>Observation 1: ICMP Traffic</h2>

 - Remote Desktop into the Windows 10 VM
 - Install Wireshark within the Windows 10 VM
 - Open Wireshark and filter ICMP traffic 
 - Copy the private IP address from the Linux-Ubuntu VM, attempt to ping it from the Windows 10 VM, and observe the Windows 10 VM ping request and 
 replies in Wireshark.
 - In the Windows 10 VM, open Powershell and ping a public website (in this case, www.google.com).
 - In the Azure Portal, access the NSG in the Linux-Ubuntu VM, and disable all ICMP inbound traffic. Now, observe how all ICMP traffic stops in Wireshark and the command line
 due to the rule change that blocks all traffic. 
 - Return to the Linux-Ubuntu VM, delete the NSG rule, and re-enable all ICMP traffic. Now, we see how all ICMP traffic is working again in Wireshark and
 the command line. 
 - With all ICMP traffic observed, we stopped the continuous ping in the Windows 10 VM. 


 <h2>Observation 2: SSH Traffic</h2>

 - In Wireshark, filter for SSH Traffic
 - From the Windows 10 VM, establish an SSH connection to the Linux-Ubuntu VM by its private IP address. 
 - Type the commands (i.e., username & password) into the Linux SSH connection and observe SSH traffic in Wireshark
 - Once completed, exit the SSH connection by typing 'exit' and pressing enter. 


 <h2>Observation 3: DHCP Traffic</h2>

 - Back in Wireshark, filter for DHCP Traffic
 - In the Windows 10 VM, attempt to issue the VM a new IP address from the command line by typing in ipconfig /renew
 - Observe DHCP traffic in Wireshark

 <h2>Observation 4: DNS Traffic</h2>

 - Back in Wireshark, filter for DNS traffic
 - In the Windows 10 VM, use nslookup in the command line to see what 
 google.com and disney.com IP addresses are
 - Observe DNS traffic in Wireshark

 <h2>Observation 5: RDP Traffic</h2>

 - Back in Wireshark, filter for RDP traffic (tcp.port ==3389)
 - Observe the traffic is non-stop between the Windows 10 VM and the local machine
 - The reason for this is that RDP continuously transmits data from one computer to another to keep things updated in real-time


<h2>Conclusion</h2>

In this lab, we analyzed network traffic between two Azure Virtual Machines and Wireshark. We used the protocols of ICMP, SSH, DHCP, DNS, and RDP to 
explore how each strand of network data was filtered throughout the Windows VM command line and Wireshark. We also observed when the flow of ICMP traffic was controlled by a rule
created in the Network Security Group (NSG) of the Linux-Ubuntu VM and the effects that the rule had on ICMP traffic as a whole. We did further analysis on DHCP traffic where we 
had to attempt to have the VM issue a new IP address to observe the overall effects of DHCP traffic. All in all, this lab gives us the necessary know-how on how network traffic 
flows between the virtual machines, plus how the security controls are implemented to manage traffic efficiently. 

 
 

 
