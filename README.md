<p align="center">
<img src="https://www.synaxiom.com/wp-content/uploads/2016/06/osticket.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites</h1>
This is a tutorial that guides you through the prerequisites and installation of the open source support ticketing system osTicket. As a beginner, you may follow this guide to learn the basics while in a real world scenario you may need to further customize the system to work with your company. We will be deploying osTicket inside of Windows 10 Azure VM, but you can use any machhine that can run a VM. If you have not checked out how to setup a VM in my previous tutorials, there will be a link below where it will guide you step by step.</p>

- [How to Setup VMs and a Virtual Network in Azure](https://github.com/bvongpradith/creating-azure-vm)

Download these files before we begin which contain installion files that we will donwload in the VM later.

- [Google Drive folder](https://drive.google.com/drive/folders/1DABjdlQAXxIvWIURTiBelD0rw6IzLNru)<br />

<h2>Environments and Tech Used</h2>

- Microsoft Azure
- Remote Desktop
- Internet Information Services
- osTicket
- HeidiSQL

<h2>Operating Systems </h2>

- Windows 10</b> (21H2)

<h2>Steps</h2>

- Remote Desktop Connection into your Windows 10 Virtual Machine
- Install / Enable Internet Information Services in Windows WITH CGI
- Download and install PHP Manager for Internet Information Services
- Download and install the Rewrite Module
- Create the directory C:\PHP
- Download PHP 7.3.8 and unzip the contents into C:\PHP
- Download and install VC_redist.x86.exe
- Download and install MySQL 5.5.62
- Open IIS as an Admin and register PHP from within IIS
- Install osTicket v1.15.8
- Download and install HeidiSQL
- Continue setting up osTicket in the browser

<h2>Installation Steps</h2>

<p>
<img src="https://i.imgur.com/Bb7Asf7.png"/>
</p>
<p>
First, we will be connecting to our VM through Remote Desktop Connnection. To do this, go to the VM on the Azure Portal > Copy Public IP Address > Connect with RDC.
</p>
<br />

<p>
<img src="https://i.imgur.com/dV47FKj.png"/>
</p>
<p>
Paste the link into the browser inside of your VM.

- https://drive.google.com/drive/folders/1DABjdlQAXxIvWIURTiBelD0rw6IzLNru
</p>
<br />

<p>
<img src="https://i.imgur.com/DjGPY5A.png"/>
</p>
<p>
Go to the Programs section in Control Panel and click on "Turn Windows features on or off".
</p>
<br />

<p>
<img src="https://i.imgur.com/sPvEkj0.png"/>
</p>
<p>
Next, install and enable IIS in Windows WITH CGI. Check every box shown in the visual step and hit OK to install.
</p>
<br />

<p>
<img src="https://i.imgur.com/2Br2jww.png"/>
</p>
<p>
After you install IIS, open a new browser and type into the search bar "127.0.0.1". The IIS page should pop up but if you do not see it; you will need to go back to control panel to make sure CGI is checked.
</p>
<br />

<p>
<img src="https://i.imgur.com/QmF8rwL.png"/>
</p>
<p>
Download and install PHPManagerForIIS_V1.5.0.msi and rewrite_amd64_en-US.msi from the istall folders in the other web browser.
</p>
<br />

<p>
<img src="https://i.imgur.com/RJUmUcY.png"/>
</p>
<p>
Next, create a new directory in your C drive called PHP or C:\PHP.
</p>
<br />

<p>
<img src="https://i.imgur.com/ubNDqqk.png"/>
</p>
<p>
Now, download and install php-7.3.8-nts-Win32-VC15-x86.zip and then extract all the contents into C:\PHP.
</p>
<br />

<p>
<img src="https://i.imgur.com/6G13Dex.png"/>
</p>
<p>
Download and install VC_redist.x86.exe.

Download and install mysql-5.5.62-win32.msi
- Typical Setup > Launch Wizard > Standard Configuration > Next > Set the password to "Password1" > Execute
</p>
<br />

<p>
<img src="https://i.imgur.com/9z2kuvC.png"/>
</p>
<p>
Search for IIS in the search bar and open it as administrator.
</p>
<br />

<p>
<img src="https://i.imgur.com/PNCSsWD.png"/>
</p>
<p>
After opening IIS Manager as admin, click on "PHP Manager" icon > click on "Register new PHP version" > Browse files > C:\PHP > open "php-cgi"
</p>
<br />

<p>
<img src="https://ihttps://i.imgur.com/nKjcWdB.png"/>
</p>
<p>
Restart the IIS server.
</p>
<br />

<p>
<img src="https://i.imgur.com/vCtQcNC.png"/>
</p>
<p>
Now, download the file osTicket-v1.15.8 from the install files. After it finishes downloading, open two file explorer windows and navigate to the osTicket-v1.15.8.zip folder and "inetpup".
</p>
<br />

<p>
<img src="https://i.imgur.com/q58Kj8z.png"/>
</p>
<p>
In the inetpup folder, go to "wwwroot" and transfer the "upload" folder in from the osTicket zip. After it finishes, rename the "upload" folder to "osTicket". 
</p>
<br />

<p>
<img src="https://i.imgur.com/nKjcWdB.png"/>
</p>
<p>
Restart the IIS server.
</p>
<br />

<p>
<img src="https://i.imgur.com/q2UBV4r.png"/>
</p>
<p>
Restart IIS as admin and expand VM1 on the left menus > Sites > Default Web Sites > Click osTicket. Click on "Browse *.80 which will open web browser that will open a osTicket installer.
</p>
<br />

<p>
<img src="https://i.imgur.com/blmP1hD.png"/>
</p>
<p>
Head back to IIS Manager and into osTicket again. Click on the "PHP Manager" icon and then at the bottom click "Enable or disable an extension".
</p>
<br />

<p>
<img src="https://i.imgur.com/8wk5Tbv.png"/>
</p>
<p>
Enable "php_imap.dll", "php_intl.dll", and "php_opcache.dll" by right clicking and hitting enable.
</p>
<br />

<p>
<img src="https://i.imgur.com/z2GpQ3j.png"/>
</p>
<p>
Refresh the web browser that has the osTicket installer and observe the changes. It should look like the screenshot above.
</p>
<br />

<p>
<img src="https://i.imgur.com/kBCw239.png"/>
</p>
<p>
Open up file explorer and navigate back to osTicket inside of inetpub. Click on include and locate "ost-sampleconfig.php" at the bottom of the list.
</p>
<br />

<p>
<img src="https://i.imgur.com/YRL3v7m.png"/>
</p>
<p>
Then rename the file from "ost-sampleconfig.php" to "ost-config.php"
</p>
<br />

<p>
<img src="https://i.imgur.com/CgHZRpb.png"/>
</p>
<p>
Now, click on that files Properties > Security > Advanced > Disable Inheritance > Remove all.
</p>
<br />

<p>
<img src="https://i.imgur.com/IRbLNbB.png"/>
</p>
<p>
Afterwards, click Add > Select a principle > type "everyone" in the object box > Check name > Press Ok.
</p>
<br />

<p>
<img src="https://i.imgur.com/C0j6tI0.png"/>
</p>
<p>
Check the box for "full control" > press OK > Apply and then OK until the properties window closes.
</p>
<br />

<p>
<img src="https://i.imgur.com/KlhO2v0.png"/>
</p>
<p>
Head back to the osTicket installer and press "Continue".
</p>
<br />

<p>
<img src="https://i.imgur.com/NYqdbCE.png"/>
</p>
<p>
Name your Helpdesk to your liking and a random email. This tutorial will be using the name "Helpdesk" and the email "john@helpdesk.com". You will continue the form by making your own Admin user credentials. I used a random email and created a password; be sure to jot these down if you are forgetful for this tutorial only.
</p>
<br />

<p>
<img src="https://i.imgur.com/YBqFS5x.png"/>
</p>
<p>
Next, download HeidiSQL from the drive folder which contains a word doc with a link to the downloader. Open the installer and click continue all the way through. Once it has installed you will click the "New" button at the bottom of the window > the username should already be set to "root" and type the password that we created "Password1" > press open.
</p>
<br />

<p>
<img src="https://i.imgur.com/riJxLu1.png"/>
</p>
<p>
Inside of HeidiSQL, right click "Unnamed" > Create new > Database > Name it "osTicket"> Click OK.
</p>
<br />

<p>
<img src="https://i.imgur.com/YVmoHK8.png"/>
</p>
<p>
Head back to the osTicket installer and enter the username and password. This should be "root" and "Password1". The hostname should also be "osTicket".
</p>
<br />

</p>
<br />

<p>
<img src="https://i.imgur.com/GanOWok.png"/>
</p>
<p>
We are almost ready to go on to the next tutorial, but first we need to clean some things up.

First browse to the C: drive -> inetpub -> wwwroot -> osTicket -> and delete the "setup" folder.
</p>
<br />

<p>
<img src="https://i.imgur.com/ZEWbk8x.png"/>
</p>
<p>
Now browse to C: -> inetpub -> wwwroot -> osTicket -> include -> and locate ost-config.php

Then on ost-config.php go to Properties -> Security -> Advanced -> click Everyone -> Edit -> and set the permissions to Read and Read & Execute only -> Apply.

Click OK.

Congratulations, you have made it to the end of this part of the tutorial! Now keep the VM and osTicket open, then move on to the post installation setup tutorial.
The link to that tutorial is linked below.

- [osTicket: Post-Installation Configuration](https://github.com/jacksonmalms/post-install-config)
