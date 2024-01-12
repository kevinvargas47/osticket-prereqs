<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1 align = "center">osTicket - Prerequisites and Installation</h1>
</p>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />



<h3>Environments and Technologies</h3>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h3>Operating Systems</h3>

- Windows 10</b> (21H2)

<h3>List of Prerequisites</h3>
<ol>
<li> Azure Virtual Machine</li>
<li> Internet Information Services (IIS) </li>
<li> PHP Manager </li>
<li> Rewrite Manager </li>
<li> VC Redist </li>
<li> MySQL </li>
<li> Heidi SQL </li>
<li> osTicket v1.15.8 </li>
<li>Link to Downloads: https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6 </li>

</ul>

<br />

<h3>Installation Steps </h3>

<p>


1.) The first thing you are going to want to do is create a virtual machine by going to https://portal.azure.com/. Setup your virtual machine with Windows 10 Pro, version 22H2. Note, you will want to create a virtual machine with at least 2 vcpus and 16 gbs of memory.

2.) Once you have created your virtual machine you will want to connect to it by using the public ip address the vm is setup with. You will connect using the remote desktop connection app.

3.) Copy and paste the simple list and installation files from the lab into the virtual machine. Once you have connected you will want to go to your control panel, from the control panel open up programs. Select, Turn Windows features on and off.

4.) You will want to install/enable IIS in Windows with CGI and Common HTTP Features

</p>
<br />

<p>
<img src="https://i.imgur.com/1DzWDl2.png" height="35%" width="35%" alt="Disk Sanitization Steps"/>
</p>
<img src="https://i.imgur.com/T3Qk4M2.png" height="35%" width="35%" alt="Disk Sanitization Steps"/>
</p>
<img src="https://i.imgur.com/FJToamx.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
Make sure that all Common HTTP features are checked. To make sure IIS is installed / enabled go to a browser of choice and search for 127.0.0.1. If it displays the IIS page then you did it correctly.
  


</ul>

</br>

<h3>Installing Files for osTicket</h3>
<p>

1.) Now that the IIS is enabled, From the Installation Files, download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi) Go through the install wizard and complete the install.

2.) Next from the Installation Files, download and install the Rewrite Module (rewrite_amd64_en-US.msi)

3.) Create a folder in the C drive called PHP.

4.) From the Installation Files, download PHP 7.3.8 (php-7.3.88-nts-Win32-VC15-x86.zip) and unzip the contents into C:\PHP
</p>
Attention: If this appears, choose to “Keep” the file:
</p>
<img src="https://imgur.com/xZv1Yhw.png" height="30%" width="30%" alt="Disk Sanitization Steps"/>
</p>
<p>

<img src="https://imgur.com/YwBhqo0.png" height="30%" width="30%" alt="Disk Sanitization Steps"/>
<p>
5.) Once you have downloaded and extracted the zip file into the PHP folder on the C drive, download and install the VC_redist.x86.exe from the installation files. Go through the setup wizard to finish setting up and installing the VC_redist.x86.exe.

6.) Download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi) Run the setup wizard: Typical Setup -> Launch Configuration Wizard (after install) -> Standard Configuration -> Make the new root password: Password1. Execute the process on the next page. 
<p>
Now that we have the files downloaded and installed we will want to search for IIS in the windows search bar. Open IIS as an administrator.
The program should look like this.  
<p>
<img src="https://imgur.com/rgdZwmM.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
7.) We will now want to register PHP from within IIS.
<p>
I.) Click on PHP Manager
<p>
II.) Register New PHP Version
<p>
III.) You will want to provide a path to the php executable file (php-cgi.exe). Go to C Drive, then PHP, and click on php-cgi file.
<p>
IV.) Restart the IIS Server
</p>
<p>
</ul>

</br>

<h3>Installing osTicket</h3>

<p>
Install osTicket v1.15.8, Download osTicket from the Installation Files Folder. Extract and copy "upload" folder to c:\inetpub\wwwroot. Within c:\inetpub\root, Rename "upload" to "osTicket". Reload IIS again.
<p>
On IIS go to sites > Default > osTicket On the right, click “Browse *:80”. Some extensions are not enabled on the osTicket browser
<p>
<img src="https://imgur.com/eJIsGTn.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
<p>
To enable the extensions: Go back to IIS, sites > Default > osTicket - Double click PHP manager. Click "Enable or disable an extension". We will want to enable three extensions from here
<p>
1.) php_imap.dll
 
2.) php_intl.dll
  
3.) php_opcache.dll
<p>
Once we have those extensions enabled in IIS, we are going to want to rename one of the files in our osTicket folder.
Go into the file explorer and search for C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
<p>
We are going to rename the ost-sampleconfig.php to ost-config.php. Now that we have renamed the files, right click on the file and go to properties. From there click security, click on advance, and disable the inheritance. We will select Remove all inherited permissions from this object.
<p>
Now we will add new permissions. 1) Click Add, 2) Select a Principal, 3) Type "Everyone" in the box. Make sure Full Control and the other boxes are checked. Click Apply and Ok
<p>
Once that is done we will continue to setup osTicket in the browser. Click Continue on the osTicket browser page.
Fill out the page as required except the Database Settings at the bottom of the page. We will get to that. 
<p>  
We will want to download and install HeidiSQL from the Installation Files. 
<p>
<img src="https://imgur.com/i7a4gWC.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
When the program is open we will create a new session in it.
<p>
<img src="https://imgur.com/g5M1i61.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>  
We want to make sure the username is root and the password is Password1.  
<p>
<img src="https://imgur.com/LEAZNOc.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>  
Once we are connected to the session we will go back to the browser to finish setting everything up. Under the Database Settings in the browser the username will be root and the password will be Password1.
<p></p>
We will now create a new database within HeidiSQL. In Heidi right click on the left side where is says "Unnamed", select "create new", and then select "database". Name the new database osTicket. Once we have the new database setup go back to the osTicket browser and under MySQL Database type in osTicket.  
<p>
<img src="https://imgur.com/0rG1AJm.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
</ul>

</br>

<h3>Clean Up</h3>

<p>

The last step is to do some clean up. We will want to delete the setup folder in our system.
<p>
Delete: C:\inetpub\wwwroot\osTicket\setup. Only delete the setup folder and nothing else. We then will want to set the permissions back to "Read" only in the ost-config.php file.  
<p>
<img src="https://imgur.com/wFr0pkK.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>  
<p>
<img src="https://imgur.com/jsJOPyn.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>  
The last step after that is to login to osTicket on the browser.  
<p>
<img src="https://imgur.com/uHVdDsx.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
<p>
<img src="https://i.imgur.com/QIZWPlD.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
<p>
This is the conclusion of the setup of the lab
