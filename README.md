<h1>Netwrok File Shares and Pemissions</h1>
This tutorial provides an overview of implementing Group Policy and managing user accounts within a domain controller<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1: Create and Organize User Accounts and Groups
- Step 2: Define and Configure Group Policy Objects (GPOs)
- Step 3: Link GPOs to Organizational Units (OUs)
- Step 4: Monitor, Update, and Maintain Policies and Accounts

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Log in to the domain controller VM with the admin username mydomain.com\(adminusername) > Log in to the client VM as a normal user with the username mydomain.com\(user) (Password is Password1)
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Within the domain controller VM, open File Explorer and go to the C:\ drive > create 4 folders named “read-access”, “write-access”, “no-access”, and “accounting.” 
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
First, go to the properties of the read access folder > sharing tab > click share > and type domain users and give them read access > click add > then click share 
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next, go to the properties of the write access folder > sharing tab > click share > and type domain users and give them read/write access > click add > then click share 
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Finally, go to the properties of the no access folder > sharing tab > click share > and type domain admins and give them read/write access > click add > then click share 
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Within the client VM, open File Explorer > in the main search bar \\(domain controller name) > now try to access the folders previously created (Read folder should only let you view) (Write folder should let you view and save things) (No access shouldn’t be accessible in any way)
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go back to the domain controller VM > open Active Directory Users and Computers > right click my domain and create a new organizational unit named “_GROUPS” > within the _GROUPS folder, right click, go to New, and create a group named “ACCOUNTANTS” 
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now go back to the C drive, go to the properties of the accounting folder > sharing tab > click share > and type “ACCOUNTANTS” and give them read/write access > click add > then click share 
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go into the client VM and refresh the folder with the previously created folders and try to access the accounting folder (you shouldn’t be able to interact with it in any way)
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Log out of the client VM and go back to the domain controller VM > Within Active Directory Users and Computers, go to the accountants folder and double click on it > go to members and add the user you signed into the client VM to the group > click apply and ok 
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now log back into the client VM with the user > open File Explorer > Type \\(domain controller name) in the larger search bar > now try accessing the accounting folder (you should be able to view the folder and save things)
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
