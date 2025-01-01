<p align="center">
  <img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
In this home lab, I will install Active Directory Domain Services (AD DS), set up a forest (`mydomain.com`), and use Active Directory Users and Computers (ADUC) to create and assign users to connect to `VM-Client-1` via Remote Desktop (RDP). I will also use PowerShell ISE to run a script that creates randomized users for RDP access.

<h2>Environments and Technologies Used</h2>
<ul>
  <li>Microsoft Azure (Virtual Machines/Compute)</li>
  <li>Remote Desktop</li>
  <li>Active Directory Domain Services</li>
  <li>PowerShell</li>
</ul>

<h2>Operating Systems Used</h2>
<ul>
  <li>Windows Server 2022</li>
  <li>Windows 10 (21H2)</li>
</ul>

<h2>High-Level Deployment and Configuration Steps</h2>

<h3>Part 1: Install Active Directory</h3>
<ol>
  <li>Login to DC-1 and install Active Directory Domain Services</li>
  
![image](https://github.com/user-attachments/assets/d431cf87-0f70-4e93-a2a7-5e0e5eb568af)

  <li>Promote the server as a Domain Controller and set up a new forest as <code>mydomain.com</code></li>

  ![image](https://github.com/user-attachments/assets/34f545d0-6525-4dd6-a972-21dfc35cbe56)

  <li>Restart the server and log in as <code>mydomain.com\labuser</code></li>
  <li>Create Organizational Units (OUs) named <code>_EMPLOYEES</code> and <code>_ADMINS</code></li>
  
![image](https://github.com/user-attachments/assets/79ea811e-7454-4b95-8dd9-f8ea60b37cc6)


  <li>Create a Domain Admin user (<code>jane_admin</code>) in ADUC and add her to the <code>Domain Admins</code> security group</li>
  <li>Log in as <code>mydomain.com\jane_admin</code> for administrative tasks</li>
</ol>

<h3>Join Client-1 to the Domain</h3>
<ol>
  <li>Login to Client-1 as the local admin and join it to the domain <code>mydomain.com</code></li>
  <li>Verify Client-1 appears in ADUC</li>
  
 ![image](https://github.com/user-attachments/assets/d9c53032-3389-43e4-bbc1-c7c7e44a6e26)

  <li>Create a new OU named <code>_CLIENTS</code> and move Client-1 into it</li>
</ol>

<h3>Part 2: Setup Remote Desktop for Non-Administrative Users</h3>
<ol>
  <li>Log in to Client-1 as <code>mydomain.com\jane_admin</code></li>
  <li>Enable Remote Desktop and allow access for domain users</li>

  ![image](https://github.com/user-attachments/assets/657b0725-ca7c-4290-a521-5af06c83e39a)

  <li>Test by logging in as a non-administrative user</li>
</ol>

<h3>Create Randomized Users with PowerShell</h3>
<ol>
  <li>Login to DC-1 as <code>jane_admin</code></li>
  <li>Open PowerShell ISE as an administrator</li>
  <li>Run a PowerShell script to create multiple users for RDP access</li>
  
 ![image](https://github.com/user-attachments/assets/5eade783-d217-4f42-88c0-663b05375a9c)

<h2>Key Takeaways</h2>
<ul>
  <li>Installed and promoted Active Directory Domain Services (AD DS) on a Windows Server 2022 VM, creating a new forest for the domain (`mydomain.com`).</li>
  <li>Created Organizational Units (OUs) and a Domain Admin user, then assigned appropriate security group roles for administrative access.</li>
  <li>Joined a Windows 10 client (Client-1) to the domain and organized it in Active Directory Users and Computers (ADUC).</li>
  <li>Enabled Remote Desktop on Client-1, granting domain users the ability to log in remotely.</li>
  <li>Automated user creation using PowerShell, allowing for bulk user generation to facilitate remote desktop access.</li>
</ul>
