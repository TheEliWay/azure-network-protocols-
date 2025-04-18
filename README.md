
<![image](https://github.com/user-attachments/assets/7e283f2f-5787-4639-a16f-7cb02386d7fa) 
>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we will be observing various network traffic to and from Azure Virtual Machines with Wireshark. Also we will be experimenting with Network Security Groups. <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute).
- Remote Desktop.
- Various Command-Line Tools.
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP).
- Wireshark (Protocol Analyzer).

<h2>Operating Systems Used </h2>

- Windows 10 (21H2).
- Ubuntu Server 20.04.

<h2>Prerequisites </h2>

- Create Windows 10 (21H2) and Ubuntu Server 20.04 vitrual machine on Microsoft Azure.

<h2>High-Level Steps</h2>

- Observe ICMP Traffic.
- Observe SSH Traffic.
- Observe DHCP Traffic.
- Observe DNS Traffic.
- Observe RDP Traffic.

<h2>Actions and Observations</h2>

![image](https://github.com/user-attachments/assets/3a3f70df-c69a-4057-9250-98069d2209b8)

</p>
<p>
<h3>Observe ICMP Traffic</h3>

- Use Remote Desktop to connect to your Windows 10 Virtual Machine.
- Within your Windows 10 Virtual Machine, Install Wireshark.
- Open Wireshark and filter for ICMP traffic only.
- Retrieve the private IP address of the Ubuntu VM and attempt to ping it from within the Windows 10 VM.
   - Observe ping requests and replies within WireShark.
- From The Windows 10 VM, open command line or PowerShell and attempt to ping a public website (such as www.google.com) and observe the traffic in WireShark.
- Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM.
   - Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic.
   - Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity.
   - Re-enable ICMP traffic for the Network Security Group your Ubuntu VM is using.
   - Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity (should start working).
   - Stop the ping activity.

</p>
<br />

![image](https://github.com/user-attachments/assets/f6dd01dc-7fc4-4531-a33d-f51adafbc31c)

</p>
<p>
<h3>Observe SSH Traffic</h3>

- Back in Wireshark, filter for SSH traffic only.
- From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address).
   - Type commands (username, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark.
   - Exit the SSH connection by typing ‘exit’ and pressing [Enter].

</p>
<br />

![image](https://github.com/user-attachments/assets/4f85ed4b-182d-4357-8694-9f3d56480a25)

</p>
<p>
<h3>Observe DHCP Traffic</h3>

- Back in Wireshark, filter for DHCP traffic only.
- From your Windows 10 VM, attempt to issue your VM a new IP address from the command line (ipconfig /renew).
   - Observe the DHCP traffic appearing in WireShark.

</p>
<br />

![image](https://github.com/user-attachments/assets/55ca3439-27a3-4154-b440-f9feb45302b5)

</p>
<p>
<h3>Observe DNS Traffic</h3>

- Back in Wireshark, filter for DNS traffic only.
- From your Windows 10 VM within a command line, use nslookup to see what google.com and disney.com’s IP addresses are.
   - Observe the DNS traffic being show in WireShark.
