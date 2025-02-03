<p align="center">
<img src="https://i.imgur.com/bX8XqFD.jpeg" alt="Traffic Examination"/>
</p>

<h1>Network File Shares and Permissions</h1>
In this tutorial, we are sharing out resources over the network and creating file shares to allow Read, Write, or Deny accesss to individual users or groups. <br />




<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
  

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)

<h2>High-Level Steps</h2>

- Create sample file shares wtih various permissions
- Attempt to access file shares as a normal user
- Create an "ACCOUNTANTS" Security Group, assign permissions, and test access

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/Vkd0Lmm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/jgnhIkf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/OPCBDdM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/05oTGyc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/6Rgy5di.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/cdfF0oO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/chTEemY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/nVL2GBC.png.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


</p>
<p>
-Connect/log into DC-1 as your domain admin account (mydomain.com\jane_admin)
-Connect/log into Client-1 as a normal user (mydomain\<someuser>)
-On DC-1, on the C:\ drive, create 4 folders: “read-access”, “write-access”, “no-access”, “accounting”
-Set the following permissions (share the folder)
-Folder: “read-access”, Group: “Domain Users”, Permission: “Read”
-Folder: “write-access”,  Group: “Domain Users”, Permissions: “Read/Write”
-Folder: “no-access”, Group: “Domain Admins”, “Permissions: “Read/Write”
(Skip accounting for now)
</p>
<br />

<p>
<img src="https://i.imgur.com/JJQINx0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/eFOlVqY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/FvgKAoM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
On Client-1, navigate to the shared folder (start, run, \\dc-1)
Try to access the folders you just created. Which folders can you access? Which folders can you create stuff in? Does it make sense?
</p>
<br />

<p>
<img src="https://i.imgur.com/JJQINx0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/r0gRcCR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/iB5J8ZL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/v3mhKCi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/6edVTys.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/p9u1gLl.pn" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/5gaMhqR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/MWH3aJp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/XIlte0j.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/9dnyFqb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
Go back to DC-1, in Active Directory, create a security group called “ACCOUNTANTS”
On the “accounting” folder you created earlier, set the following permissions:
Folder: “accounting”, Group: “ACCOUNTANTS”, Permissions: “Read/Write”
On Client-1, as  <someuser>, try to access the accountants folder. It should fail. 
Log out of Client-1 as  <someuser>
On DC-1, make <someuser> a member of the “ACCOUNTANTS”  Security Group
Sign back into Client-1 as <someuser> and try to access the “accounting” share in \\DC-1\ - Does it work now?
</p>
<br />
