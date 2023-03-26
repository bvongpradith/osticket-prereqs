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
<img src="https://i.imgur.com/PZ3BXsF.png"/>
</p>
<p>
Download and install VC_redist.x86.exe.

Download and install mysql-5.5.62-win32.msi
- Typical Setup ->
- Launch Configuration Wizard (after install) ->
- Standard Configuration ->
- Next ->
- Password1 (root will be the username, but you don't need to set that up) ->
- Execute 

</p>
<br />

<p>
<img src="https://i.imgur.com/kfk7PPp.png"/>
</p>
<p>
Open IIS as administrator as shown above.
</p>
<br />

<p>
<img src="https://i.imgur.com/QnWyh4t.png"/>
</p>
<p>
After opening IIS Manager as admin, click on the "PHP Manager" icon", hit "Register new PHP version". 

Browse files and find the PHP folder we made earlier and select "php-cgi" and hit open.
</p>
<br />

<p>
<img src="https://i.imgur.com/7nygYZ7.png"/>
</p>
<p>
Restart the IIS server as per the image above.
</p>
<br />

<p>
<img src="https://i.imgur.com/VCrGYgY.png"/>
</p>
<p>
Now open two separate file explorer windows and on one navigate to the downloads folder and click on osTicket-v1.15.8, and on the other window open up your C:/ drive.
</p>
<br />

<p>
<img src="https://i.imgur.com/izvuG0n.png"/>
</p>
<p>
In that C:/ window, navigate to "inetpup" -> "wwwroot" and move in the "upload" folder from the osTicket zip and let it finish copying. Then rename the "upload" folder to "osTicket".
</p>
<br />

<p>
<img src="https://i.imgur.com/RxeVUCO.png"/>
</p>
<p>
Restart the IIS server.
</p>
<br />

<p>
<img src="https://i.imgur.com/fm1ZFgU.png"/>
</p>
<p>
Close and reopen IIS manager as admin again, on the left expand the menus osTicket-VM -> Sites -> Default Web Site -> then click on osTicket.

On the right hit Browse *:80 and you should see the osTicket installer open inside of your default browser.
</p>
<br />

<p>
<img src="https://i.imgur.com/QqUA0PL.png"/>
</p>
<p>
Go back to IIS Manager, osTicket-VM -> Sites -> Default Web Site -> click osTicket, then click on "Enable or disable an extension".
</p>
<br />

<p>
<img src="https://i.imgur.com/PTOgAhg.png"/>
</p>
<p>
Locate "php_imap.dll", "php_intl.dll", and "php_opcache.dll". Enable them all by right-clicking.
</p>
<br />

<p>
<img src="https://i.imgur.com/W67FgEV.png"/>
</p>
<p>
Refresh the osTicket installer page and observe the changes, it should match the picture above.
</p>
<br />

<p>
<img src="https://i.imgur.com/uEMoIah.png"/>
</p>
<p>
In file explorer go to C: -> inetpub-> wwwroot -> osTicket -> include, then locate ost-sampleconfig.php at the bottom.
</p>
<br />

<p>
<img src="https://i.imgur.com/T4CBoq4.png"/>
</p>
<p>
Then rename the file form "ost-sampleconfig.php" to "ost-config.php"
</p>
<br />

<p>
<img src="https://i.imgur.com/Xto4OTI.png"/>
</p>
<p>
Then right click on that file got to Properties -> Security -> Disable inheritance -> Remove all
</p>
<br />

<p>
<img src="https://i.imgur.com/KTIJ5J0.png"/>
</p>
<p>
Then click Add -> Select a principal -> In the object box type "Everyone" and check for names -> click OK
</p>
<br />

<p>
<img src="https://i.imgur.com/7Tpm1LY.png"/>
</p>
<p>
Select Full control and hit OK -> click Apply -> OK -> OK
</p>
<br />

<p>
<img src="https://i.imgur.com/9Bf1IuO.png"/>
</p>
<p>
Now go back into the osTicket installer in the browser and click continue.
</p>
<br />

<p>
<img src="https://i.imgur.com/3uOvZ8X.png"/>
</p>
<p>
For the name I just did "Helpdesk" and for the email I did "john@helpdesk.com", then I set the Admin User credentials, write these down if you made up your own. 

Now just leave this page be and go onto the next step in this tutorial.
</p>
<br />

<p>
<img src="https://i.imgur.com/3d9To5Z.png"/>
</p>
<p>
Download HeidiSQL form the Drive folder, it will download as a word doc and open it, then click the link to download the HeidiSQL Setup. 

Then install it.

Once it opens, click the green new button in the bottom left of the window, the username should be "root" and the password should be "Password1" if you set them to those earlier in this tutorial, then hit open.
</p>
<br />

<p>
<img src="https://i.imgur.com/8IMqLza.png"/>
</p>
<p>
In HeidiSQL, right click Unnamed -> Create new -> Database, name it "osTicket" and click OK
</p>
<br />

<p>
<img src="https://i.imgur.com/qmZlp4P.png"/>
</p>
<p>
Going back into the osTicket installer in the browser, put in the username and password for MySQL (should be "root" and "Password1" if you set them to those) and click install.
</p>
<br />

<p>
<img src="https://i.imgur.com/hoVuqRf.jpg"/>
<img src="https://i.imgur.com/I8ZApOx.png"/>
</p>
<p>
Now that it has installed, open up both of these urls in your VM's browser

- Help desk login page (login with the credentials that you set for the admin user for osTicket): http://localhost/osTicket/scp/login.php

- End Users osTicket URL: http://localhost/osTicket/ 
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
