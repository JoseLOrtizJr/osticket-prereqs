# osticket-prereqs







<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
In this lab we are going to install osTicket. Since this is for educational purposes I highly recommend installing osTicket in a virtual enviroment. I have used Azure, Hyper-V and VirtualBox to run this lab but we are going to be using VirtualBox since we can enable drag and drop to transfer the installation files to the VM since downloading them can be slow and the first few times running the lab can be time consuming. Also I would recommend taking a snapshot after setting up the enviroment so you can reload and rerun the lab once finished. Taking the snapshot can also be helpful if you run into problems setting up osTicket. If you get stuck you should try and figure it out via google or forums as this will help your intuition for problem solving, but as last resort you can also reload from the snapshot. Now this lab is assuming you already have VirtualBox and a Windows 10 virtual machine setup but will provide a link here when I complete this repository if you need those steps done.


<h3>Environments and Technologies</h3>

- VirtualBox
- Internet Information Services (IIS)
- MySQL

<h3>Operating Systems</h3>

- Windows 10



<h2>List of Prerequisites</h2>

- Download the installation files to your computer from the following links [Google Drive](https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6) & [Heidisql](https://www.heidisql.com/installers/HeidiSQL_12.3.0.6589_Setup.exe)
<img src="https://i.imgur.com/XAaDCdJ.png" height="80%" width="80%" alt="Google Drive"/>
- Enabled drag and drop and shared clipboard to bidirectional or host to guest.
<img src="https://i.imgur.com/1d9HQES.png" height="60%" width="60%" alt="Enable Drag and Drop"/>
- You need to have Guest Additions installed to drag and drop. You can install by going to \Devices\Insert Guest Additions CD image\ on the navigation bar. Then go to \This PC\CD Drive(D)\VirtualBox Guest Additions\. Install VBWindowsAdditions-amd64 if your running a 64-bit operating system or VBWindowsAdditions-x86 in case your machine is a 32-bit system. If you already have it installed skip to next step.
<img src="https://i.imgur.com/JfJrMZp.png" height="80%" width="80%" alt="Guest Additions"/>
<img src="https://i.imgur.com/LjtvoVS.png" height="80%" width="80%" alt="Guest Additions1"/>
<img src="https://i.imgur.com/kH3gJKK.png" height="80%" width="80%" alt="Guest Additions2"/>
- Once the VM is up and running create a folder and name it "osTicket" on the desktop and then drag and drop installation files to the folder.
<img src="https://i.imgur.com/og5IrX1.png" height="80%" width="80%" alt="Drag and Drop Files"/>
- When the files are copied to your VM take a snapshot.
<img src="https://i.imgur.com/WYOAlhb.png" height="80%" width="80%" alt="Take Snapshot"/>
 
<h2>Installation Steps</h2>

-Install/Enable IIS by going to the turn Windows features on or off via Control Panel\All Control Panel Items\Programs and Features
<img src="https://i.imgur.com/seSRaOR.png" height="80%" width="80%" alt="Turn Windows Featues on or off"/>

-Enable IIS Management Console, CGI and Common HTTP Features. Make sure all Common HTTP Features are checked.

<img src="https://i.imgur.com/wktR1fZ.png" height="60%" width="60%" alt="IIS CGI Common HTTP Features"/>
-Verify IIS is installed / enabled by going to the web browser and entering 127.0.0.1 in the address bar. If it displays the IIS page then it was installed properly.
<img src="https://i.imgur.com/PdpE5Uf.png" height="60%" width="60%" alt="Internet Information Services"/>

-Now we can start installing the files. First we install PHP Manager for IIS(PHPManagerForIIS_V1.5.0.msi).
<img src="https://i.imgur.com/H8eqJW4.png" height="80%" width="80%" alt="PHP Manager grid"/>

-Next we install the Rewrite Module(rewrite_amd64_en-US.msi).
<img src="https://i.imgur.com/rERfRrt.png" height="100%" width="100%" alt="Rewrite grid"/>
-Now we create the following folder C:\PHP and we unzip the PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) files and copy the contents to C:\PHP
<img src="https://i.imgur.com/6E9QFgi.png" height="100%" width="100%" alt="Rewrite grid"/>
-Next we install VC_redist.x86.exe
<img src="https://i.imgur.com/YuaHA1c.png" height="100%" width="100%" alt="Rewrite grid"/>
-And now it's time to install MySQL 5.5.62(mysql-5.5.62-win32.msi) which we will do in two phases. In the first phase we are going to choose typical setup.
<img src="https://i.imgur.com/mJx7xbQ.png" height="120%" width="120%" alt="MYSQL grid1"/>
-In the next phase we use the MySQL Instance Configuration Wizard and we are going choose the standard configuration and our root password will be "Password1". As a matter of fact to simplify things all of our passwords will be "Password1" though stronger passwords are recommended in real world scenarios.
<img src="https://i.imgur.com/aCjsLyK.png" height="120%" width="120%" alt="MYSQL grid1"/>
-Now we are going to setup the Internet Information Services (IIS) Manager. We type IIS in the windows search bar and select run as administrator. Once the manager pops up we are going to clcik on PHP Manager and restart it.

<img src="https://i.imgur.com/4pkWh95.png" height="60%" width="60%" alt="IIS manager"/>
<img src="https://i.imgur.com/kfFitbK.png" height="80%" width="80%" alt="IIS manager1"/>
-Next we are going to install osTicket. We extract and copy the "upload" folder to c:\inetpub\wwwroot. Within c:\inetpub\wwwroot we rename the "upload" folder to "osTicket".
<img src="https://i.imgur.com/v7Ix65c.png" height="60%" width="60%" alt="osTicket"/>

-Now we restart the PHP Manager again. Next under Connections on the left we go to Sites>Default Web Site then we to the Actions on the right side and under Browse Website we click on Browse*:80(http). It should load with localhost in the address bar and IIS landing page from before.

<img src="https://i.imgur.com/PiGKR5P.png" height="60%" width="60%" alt="osTicket"/>
<img src="https://i.imgur.com/ZznbiBm.png" height="60%" width="60%" alt="osTicket"/>
-There are some PHP extensions that need to be enabled so we go back to IIS Connections Sites>Default Web Site\osTicket. We will have to click on PHP Manager then Register new PHP version and then we search for the php-cgi.exe file which is in the following folder C:\PHP\php-cgi.exe.
Now we can go to PHP Extensions and enable the following; php_imap.dll, php_intl.dll and php_opcache.dll.
<img src="https://i.imgur.com/mJRxg2O.png" height="80%" width="80%" alt="osTicket"/>
<img src="https://i.imgur.com/Wk0msKg.png" height="80%" width="80%" alt="osTicket"/>
-Now we go back to IIS Connections Sites>Default Web Site\osTicket and to the right under Manager Folder\Browse Folder click on Browse*:80(http) and We should be able to load the osTicket installer page now.

<img src="https://i.imgur.com/4QxRqcT.png" height="60%" width="60%" alt="osTicket"/>
<img src="https://i.imgur.com/KL8Mfog.png" height="60%" width="60%" alt="osTicket"/>
-Before setting up osTicket there are still things to do. We have to rename the following file: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php to ost-config.php. We are going to also change the permissions on ost-config.php. We will go to Advanced Security Settings and disable inheritance and assign new permissions giving full control to everyone.

