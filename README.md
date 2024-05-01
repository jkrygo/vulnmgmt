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

Once that is finished, I am taken to a Nessus Essentials dashboard. This is where scans will be started and reviewed from. Plugins take some time to compile, so I have to wait a bit even after this dashboard loads.
<img src="https://i.imgur.com/cyuns8T.png" alt="Nessus Dashboard"/>

<h2>Non-Credentialed Scan</h2>
Once the installation is finished, I run a scan by clicking the "New Scan" button. Under Vulnerabilities, I select "Basic Network Scan" and then name the scan Win10. The target of this scan will be this machine, so the Target is set to 172.16.0.100. To run this scan, I click the arrow.
<img src="https://i.imgur.com/2KabAVa.png" alt="New Scan"/>
<img src="https://i.imgur.com/1fMx3z3.png" alt="Run Scan"/>

Scans can take several minutes to complete, and even longer if they're configured beyond the default settings. After a scan is complete, a checkmark will appear. This can be clicked to show the results of the scan.
<img src="https://i.imgur.com/ol15q8o.png" alt="Scan Complete"/>
<img src="https://i.imgur.com/c9EoBQR.png" alt="Results"/>

From this screen, I can see that some vulnerabilities have been detected, with two of them being Medium level. Clicking the Vulnerabilities tab will list each vulnerabilitiy, and clicking on one will display a description of the vulnerability, the solution, as well as some further documentation.

<img src="https://i.imgur.com/d3DJVyp.png" alt="Medium Vulnerability"/>

<h2>Credentialed Scan</h2>
It's time to perform a Credentialed scan. I have to configure this machine to accept authenticated scans. This will allow Nessus to scan with credentials.

There are a few things Tenable recommends doing to allow credentialed scans to run effectively.
* Turning on network discovery and file and printer sharing in Advanced Sharing Settings.
* Enable Remote Registry to allow Nessus to scan the registry
* Create a DWORD in Registry Editor under Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System called LocalAccountTokenFilterPolicy and setting the value to 1.

After all of that is finished, I restart the VM to apply the changes I made.

<img src="https://i.imgur.com/XI9nNCi.png" alt="Discovery"/>
<img src="https://i.imgur.com/frlj9kD.png" alt="Remote Registry"/>
<img src="https://i.imgur.com/u0MzjH6.png" alt="LocalAccountTokenFilterPolicy"/>

I'm ready to run a Credentialed scan now! By selecting the previous scan and clicking More>Configure, I can add a set of Windows credentials under the Credentials tab. After clicking the Windows category, I enter my admin username and password and leave everything else as default, and click save.
<img src="https://i.imgur.com/meWJdY5.png" alt="Credential Scan Menu"/>

This scan is now ready to run, and the process is the exact same as the non-credentialed scan. Normally, there should be more vulnerabilities, but this scan doesn't show anything new.
<img src="https://i.imgur.com/zZL4yTQ.png" alt="Credential Scan"/>

<h2>Issues </h2>

