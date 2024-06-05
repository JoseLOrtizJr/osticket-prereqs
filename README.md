


<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>


# osTicket - Prerequisites and Installation Guide

In this guide, we'll install osTicket in a virtual environment using VirtualBox. This method allows easy file transfer and is ideal for educational purposes. Snapshots are recommended for troubleshooting and rerunning the lab.

## Required Environments and Technologies

- Oracle VM VirtualBox
- Internet Information Services (IIS)
- MySQL
- Windows 10

## Prerequisites

1. **Download Installation Files:**
   - [Google Drive](https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6)
   - [HeidiSQL](https://www.heidisql.com/installers/HeidiSQL_12.3.0.6589_Setup.exe)
  
   - <img src="https://i.imgur.com/XAaDCdJ.png" height="80%" width="80%" alt="Google Drive"/>

2. **Enable Drag and Drop:**
   - Enable drag and drop and shared clipboard to bidirectional.
  
   - <img src="https://i.imgur.com/1d9HQES.png" height="60%" width="60%" alt="Enable Drag and Drop"/>

3. **Install Guest Additions:**
   - Go to `Devices > Insert Guest Additions CD image` in VirtualBox.
   - Install appropriate version (`VBWindowsAdditions-amd64` for 64-bit or `VBWindowsAdditions-x86` for 32-bit).
  
   - <img src="https://i.imgur.com/JfJrMZp.png" height="80%" width="80%" alt="Guest Additions"/>

4. **Prepare osTicket Folder:**
   - Create a folder named "osTicket" on the VM desktop and drag installation files into it.
   - Take a snapshot of the VM.

## Installation Steps

1. **Enable IIS:**
   - Go to `Control Panel > Programs and Features > Turn Windows features on or off`.
   - Enable `IIS Management Console`, `CGI`, and all `Common HTTP Features`.

<img src="https://i.imgur.com/wktR1fZ.png" height="60%" width="60%" alt="IIS CGI Common HTTP Features"/>

2. **Verify IIS Installation:**
   - Open a web browser and navigate to `127.0.0.1` to check if the IIS page loads.

3. **Install PHP Manager:**
   - Install `PHPManagerForIIS_V1.5.0.msi`.

4. **Install Rewrite Module:**
   - Install `rewrite_amd64_en-US.msi`.

5. **Setup PHP:**
   - Create a folder `C:\PHP`.
   - Unzip `php-7.3.8-nts-Win32-VC15-x86.zip` and copy contents to `C:\PHP`.
   - Install `VC_redist.x86.exe`.

6. **Install MySQL:**
   - Install `mysql-5.5.62-win32.msi` with typical setup.
   - Use MySQL Instance Configuration Wizard with standard configuration and root password `Password1`.

7. **Configure IIS Manager:**
   - Open IIS Manager as Administrator.
   - Click on `PHP Manager` and restart it.
  
   - <img src="https://i.imgur.com/kfFitbK.png" height="80%" width="80%" alt="IIS manager1"/>

8. **Install osTicket:**
   - Extract and copy the `upload` folder to `C:\inetpub\wwwroot` and rename it to `osTicket`.
   - Restart PHP Manager.

9. **Configure PHP Extensions:**
   - In IIS, go to `Sites > Default Web Site > osTicket`.
   - Register new PHP version by selecting `C:\PHP\php-cgi.exe`.
   - Enable the following extensions `php_imap.dll`, `php_intl.dll`, and `php_opcache.dll`.
  
   - <img src="https://i.imgur.com/mJRxg2O.png" height="80%" width="80%" alt="osTicket"/>

   - <img src="https://i.imgur.com/Wk0msKg.png" height="80%" width="80%" alt="osTicket"/>

10. **Complete osTicket Installation:**
    - Browse to `Sites > Default Web Site > osTicket` and click on `Browse *:80 (http)`.
    - Rename `C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php` to `ost-config.php`.
    - Change permissions on `ost-config.php` by disabling inheritance and giving full control to everyone.
   
    - <img src="https://i.imgur.com/4QxRqcT.png" height="60%" width="60%" alt="osTicket"/>

    - Now you should be able to access the osTicket installer page. Follow the on-screen instructions to complete the setup. Remember to write down the username and email you use to signup and use `Password1` as default password.
   
    - <img src="https://github.com/JoseLOrtizJr/osticket-prereqs/blob/main/osticket.png">
    - <img src="https://github.com/JoseLOrtizJr/osticket-prereqs/blob/main/osticket1.png">
    - <img src="https://github.com/JoseLOrtizJr/osticket-prereqs/blob/main/osticket2.png">

    - Install HeidiSQL and create a new database called `osTicket`. We will be using our credentials from MySQL in HeidiSQL and in the database settings, `root` and password `Password1`.
   
    - <img src="https://github.com/JoseLOrtizJr/osticket-prereqs/blob/main/heidisql.png">

    - Congratulations! You just installed osTicket.
   
    - <img src="https://github.com/JoseLOrtizJr/osticket-prereqs/blob/main/congrats.png">
    
    - Finally, perform post-installation cleanup by deleting the `setup` folder and changing the permissions on `ost-config.php` to read & execute and read-only.
   
    - <img src="https://github.com/JoseLOrtizJr/osticket-prereqs/blob/main/setup.png">
    - <img src="https://github.com/JoseLOrtizJr/osticket-prereqs/blob/main/ostconfig.png">
    
    
    ## Conclusion

This lab can be challenging, and issues may arise during the setup. Using VirtualBox is preferable over Azure because you can create and load snapshots, allowing you to quickly restore your environment without needing to reinstall the virtual machine. Additionally, VirtualBox's drag-and-drop feature helps overcome slow download speeds by easily transferring installation files to the VM. Finally, there are no fees associated with using VirtualBox compared to cloud services.
    
