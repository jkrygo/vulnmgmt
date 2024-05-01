# Vulnerability Management Lab
<h2>Description</h2>
The purpose of this lab is to install Nessus Vulnerability Scanner and analyzing the differences between each scan ran. I will perform a non-credentialed scan, a credentialed scan, another credentialed scan after installing depreciated software, and then remediating critical vulnerabilities found.
<h2>Environments Used</h2>
- <b>Windows 10</b> (22H2) </br>
<h2>Setup</h2>
The first thing I do is boot up a Windows 10 VM and download Nessus Essentials. This requires an activation code which you can get by registering your email on their website. Once that's finished. I download Nessus v10.7.2 for Windows x64.
<img src="https://i.imgur.com/sY8E3ls.png" alt="Nessus"/>

Once downloaded, I install Nessus and accept all of the agreements when prompted. A webpage appears prompting me to Connect via SSL. After clicking through a few prompts, a screen appears asking how I want to deploy Nessus. I select "Register for Nessus Essentials".
<img src="https://i.imgur.com/gt7TkId.png" alt="Register Nessus"/>

I'm prompted for an activation code, which comes from the registration email sent by Tenable. I then create a Nessus administrator user account when asked. Once finished, Nessus begins to initialize. 
<img src="https://i.imgur.com/97uQeG9.png" alt="Initialize Nessus"/>

Once that is finished, I am taken to a Nessus Essentials dashboard. This is where scans will be started and reviewed from. 
<img src="https://i.imgur.com/cyuns8T.png" alt="Nessus Dashboard"/>

<h2>Non-Credentialed Scan</h2>

<h2>Issues </h2>
The main issue I ran into was forgetting that the Notepad++ installer was an .exe and not a .msi. This probably isn't the safest or most ideal way to handle this, but for the purpose of really wanting to do this in a lab environment, I repackaged the .exe as an .msi using WiX Toolset (https://wixtoolset.org/). I've included the WiX Source File in this repo.
