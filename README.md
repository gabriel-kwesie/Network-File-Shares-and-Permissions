<h1>Network File Shares and Pemissions</h1>
This tutorial provides an overview of implementing Network File Shares and Permissions (Active Directory Setup Required)<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 11 (25H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1: Plan the Share Structure
- Step 2: Create the File Shares
- Step 3: Assign Permissions
- Step 4: Test and Maintain Access

<h2>Deployment and Configuration Steps</h2>

<p>
<img width="1599" height="899" alt="image" src="https://github.com/user-attachments/assets/3943dd0d-0ee4-4d1e-b1d8-8962e88a408d" />
</p>
<p>
Log in to the domain controller VM with the admin username mydomain.com\(adminusername) > Log in to the client VM as a normal user with the username mydomain.com\(user) (Password is Password1)
</p>
<br />

<p>
<img width="1599" height="899" alt="image" src="https://github.com/user-attachments/assets/a42ee1c5-5ada-46cf-b367-1e143638faa7" />
</p>
<p>
Within the domain controller VM, open File Explorer and go to the C:\ drive > create 4 folders named “read-access”, “write-access”, “no-access”, and “accounting.” 
</p>
<br />

<p>
<img width="1599" height="899" alt="image" src="https://github.com/user-attachments/assets/5449dac3-1ee0-4160-8430-6fc2c02b58ea" />
</p>
<p>
First, go to the properties of the read access folder > sharing tab > click share > and type domain users and give them read access > click add > then click share 
<br />

<p>
<img width="1599" height="899" alt="image" src="https://github.com/user-attachments/assets/f1dd8a8f-8252-4867-b282-1d7f5df7b83f" />
</p>
<p>
Next, go to the properties of the write access folder > sharing tab > click share > and type domain users and give them read/write access > click add > then click share 
</p>
<br />

<p>
<img width="1599" height="899" alt="image" src="https://github.com/user-attachments/assets/5c12209e-2aa5-4374-bf0a-4e598bd48b69" />
</p>
<p>
Finally, go to the properties of the no access folder > sharing tab > click share > and type domain admins and give them read/write access > click add > then click share 
</p>
<br />

<p>
<img width="1599" height="899" alt="image" src="https://github.com/user-attachments/assets/95636dd6-a25d-4c1b-a05f-0ece13667f92" />
</p>
<p>
Within the client VM, open File Explorer > in the main search bar \\(domain controller name) > now try to access the folders previously created (Read folder should only let you view) (Write folder should let you view and save things) (No access shouldn’t be accessible in any way)
</p>
<br />

<p>
<img width="1599" height="899" alt="image" src="https://github.com/user-attachments/assets/caada959-8b30-4d20-9330-443558d25c70" />
</p>
<p>
Go back to the domain controller VM > open Active Directory Users and Computers > right click my domain and create a new organizational unit named “_GROUPS” > within the _GROUPS folder, right click the white area on the right, go to New, and create a group named “ACCOUNTANTS” 
</p>
<br />

<p>
<img width="1599" height="899" alt="image" src="https://github.com/user-attachments/assets/acb8c1b5-777d-41cc-9531-9a1fe593d9d1" />
</p>
<p>
Now go back to the C drive, go to the properties of the accounting folder > sharing tab > click share > and type “ACCOUNTANTS” and give them read/write access > click add > then click share 
</p>
<br />

<p>
<img width="1599" height="899" alt="image" src="https://github.com/user-attachments/assets/1784f81d-1d5e-4cd8-a4a2-788f8f9f612a" />
</p>
<p>
Go into the client VM and refresh the folder with the previously created folders and try to access the accounting folder (you shouldn’t be able to interact with it in any way)
</p>
<br />

<p>
<img width="1599" height="899" alt="image" src="https://github.com/user-attachments/assets/b6d13578-06b3-4efd-a2bc-86d6d10bbbaf" />
</p>
<p>
Log out of the client VM and go back to the domain controller VM > Within Active Directory Users and Computers, go to the accountants group and double click on it > go to members and add the user you signed into the client VM to the group > click apply and ok 
</p>
<br />

<p>
<img width="1599" height="899" alt="image" src="https://github.com/user-attachments/assets/5262cd7e-4e04-4c31-a401-9e5f7bef2b49" />
</p>
<p>
Now log back into the client VM with the user > open File Explorer > Type \\(domain controller name) in the larger search bar > now try accessing the accounting folder (you should be able to view the folder and save things)
</p>
<br />
