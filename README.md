<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022 (Domain Controller)
- Windows 10 (21H2) (Client Machine)

<h2>Lab Overview</h2>
In this lab, we simulate a real-world enterprise environment by setting up Active Directory Domain Services (AD DS) using two virtual machines hosted in Azure.


Lab Objectives:
- Configure the Windows Server VM as a Domain Controller.

- Promote it to a domain using Active Directory and DNS.

Configure the Windows 10 client to:

- Join the domain.

- Authenticate using domain user accounts.

Set the DNS server on the client machine to point to the DC's private IP.
- By setting the client’s DNS server to the DC’s IP, we ensure the client uses internal DNS resolution for domain-based login and communication.

- This simulates a real network where all client machines rely on the internal DNS provided by the DC.

- Because of this, the client no longer uses Azure's default DNS to resolve external domain names (like google.com). Instead, it tries to route DNS queries through the DC first.

<img src="https://i.imgur.com/46ZxkYP.png" alt="lab overview"/>


<h2>In-Depth Deployment and Configuration Steps</h2>
Once Active Directory Domain Services is installed and the VM is promoted to be the DC, "mydomain.com" was configured as a new forest. After restarting and logging back into the DC VM as "mydomain.com\labuser", you should have access to AD Users and Computers. 


<p>
<img src="https://i.imgur.com/XeKEhk2.png" height="80%" width="80%" alt="AD-users&computers"/>
</p>
<p>
Now we will start creating Organizational Units or "OUs". The first set of OU's will be "_EMPLOYEES" and "_ADMINS". To do that you will right-click on the domain name, select New, then Organizational Unit.

In the "_ADMINS" OU, right-click -> new -> User and create the user "Jane Doe". For the user login name, insert "jane_admin". Once that is done, add Jane to the domain admins security group. 
</p>
<br />

<p>
<img src="https://i.imgur.com/jBgCBrs.png" height="80%" width="80%" alt="AD-adminCreation"/>
</p>
<p>
Next we have to join Client-1 machine to the Domain. To do this, right-click the windows icon in the bottom left of the screen. Select system -> Rename this PC (advanced) -> under computer name select change -> domain -> enter "mydomain.com"
</p>
<br />

<p>
<img src="https://i.imgur.com/m8PnNVm.png" height="80%" width="80%" alt="AD-joinClientDomain"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
