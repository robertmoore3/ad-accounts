<p align="center">
<img src="https://github.com/user-attachments/assets/2a666083-7f44-48eb-ab51-728daafd40dd" />
</p>

<h1>Enabling and Unlocking Accounts and Restting Passwords</h1>
This tutorial outlines how to manage accounts in Active Directory<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)
- Windows Server 2022

<h2>Configuring Group Policy</h2>
<p>
<img src="https://github.com/user-attachments/assets/66a48859-1d86-484c-832b-110e31cf8062"/>
</p>
First we need to setup a Group Policy to lockout accounts that recieve bad passwords too many times.
<ol>
  <li>login in to dc-1</li>
  <li>Open Group Policy Management Console(GPMC) by typing 'gpmc.msc' into start → search bar</li>
  <li>Create or Edit a Group Policy Object (GPO)</li>
  <b>open Forest:mydomain.com → domains → mydomain.com → group policy objects → right click → new</b>
  <li>Configue GPO settings </li>
  • In the Group Policy Management Editor, expand the following:
  <b>Computer Configuration → Policies → Windows Settings → Security Settings → Account Policies → Account Lockout Policy</b>
  <p>• Define the Account Lockout Threshold policy set to 5.</p>
  <li>Link the GPO to an Organizational Unit (OU)</li>
  <b>In the GPMC, right-click _EMPLOYEES → select Link an Existing GPO</b>
  <li>Update Group Policy</li>
  <b>login to client-1 → open Command Prompt → run gpupdate /force</b>
</ol>
<br />

<h2>Account Lockouts</h2>
<p>
<img src="https://github.com/user-attachments/assets/3a4e5bbc-0397-4629-aaae-bee11cc6cd22"/>
</p>
<ol>
  <li>Navigate to the _EMPLOYEES organizatiional unit on dc-1. We'll use one of these accounts that we previously automatically generated for testing.</li>
  <li>Attempt to log-in to client-1 as one of the employees 6 times with a bad password</li>
  <li>Observe that the account has been locked out within Active Directory</li>
  <b>_EMPLOYEES → double-click your employee's account → Account tab → unlock the account</b>
  • to reset the password, simply left click the employee within _EMPLOYEES
  <li>Attempt to log-in again with a new password</li>
</ol>
<br />

<h2>Enabling and Disabling Accounts</h2>
<ol>
  <li>Disable the same account in Active Directory</li>
  <b>left click employee's account → disable </b>
  <li>Attempt to login with it, observe the error message</li>
  <li>Re-enable the account and attempt to login with it.</li>
</ol>
<br />

<h2>Observing Logs</h2>
<p>
<img src="https://github.com/user-attachments/assets/9737a13b-6c5c-4043-8588-3dc1547bd344"/>
</p>
To observe the logs, type 'eventvwr.msc' into start → search bar. Expand the Windows Logs and click Security. From here you can observe all the security events that took place in the domain, such as all the bad password attempts or the successful login attempts. 
<ol>
  <li>Observe the Logs on DC-1</li>
  <li>Observe the Logs on Client-1 (run as an Admin)</li>
</ol>
<br />

