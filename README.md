# Vulnerability Management Lab
<h2>Description</h2>
The purpose of this lab is to install Nessus Vulnerability Scanner and analyzing the differences between each scan ran. I will perform a non-credentialed scan, a credentialed scan, another credentialed scan after installing depreciated software, and then remediating critical vulnerabilities found.
<h2>Environments Used</h2>
- <b>Windows 10</b> (22H2) </br>
<h2>Group Policy Configuration Walkthrough</h2> 
To start, I create a folder named Share containing a Notepad++ installer and image on the Domain Controller. I configure Share Permissions to allow Authenticated Users to read from the folder, and to allow Domain Admins to have Full Control. When I check into my Windows 10 client, the Share folder appears when accessing \\DC\.
<img src="https://i.imgur.com/dpfEvRd.png" alt="Share"/>
<img src="https://i.imgur.com/J1EY5LN.png" alt="Share"/>
<br/>
Now that the installer is accessable, I create a GPO link for my _DOMAIN_COMPUTERS Organizational Unit (OU) called Notepad++ Install. Under Group Policy Management Editor, I created a package that points to the N++ installer in the network share. I then run /gpupdate on the client to initiate the Group Policy update.
<img src="https://i.imgur.com/rlsYGrN.png" alt="GPO Link"/>
<img src="https://i.imgur.com/yVq0tlW.png" alt="GPME Package"/>
<img src="https://i.imgur.com/g7RTKef.png" alt="/gpupdate force"/>
<br/>
After restarting, I'm able to log in and verify Notepad++ is installed to the client.
<img src="https://i.imgur.com/CBM2u7O.png" alt="Notepad++"/>
<br/>
Now that Notepad++ is installed, I created another GPO that changes the desktop wallpaper to another image. I linked it to the _USERS OU so it will apply to every user that isn't the admin. I ran gpupdate /force and restart the client.
<img src="https://i.imgur.com/knc61v0.png" alt="Desktop Wallpaper GPO"/>
<img src="https://i.imgur.com/WdWgCNP.png" alt="GPO Linked to _USERS"/>
<img src="https://i.imgur.com/6yQdste.jpeg" alt="Bliss"/>
<br/>
<h2>Issues </h2>
The main issue I ran into was forgetting that the Notepad++ installer was an .exe and not a .msi. This probably isn't the safest or most ideal way to handle this, but for the purpose of really wanting to do this in a lab environment, I repackaged the .exe as an .msi using WiX Toolset (https://wixtoolset.org/). I've included the WiX Source File in this repo.
