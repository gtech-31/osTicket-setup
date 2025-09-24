<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<body>

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">

</head>
<body>

<h1>osTicket Installation Tutorial</h1>

<h2>Step 1. Create Azure Virtual Machine</h2>
<p align="center">
  <img src="Images/canvas (4).png" width="200"/>
  <img src="Images/canvas (3).png" width="200"/>
  <img src="Images/canvas (5).png" width="200"/>
  <img src="Images/Screenshot (50).png" width="200"/>
</p>
<p>First, log into or create a Microsoft Azure account, then navigate to the Virtual Machines tab and create a new Resource Group named after your project. Create a Windows 10 VM named osticket-vm, set the size to 4 vCPUs / 16 GiB memory, and configure a username (labuser) and password (osTicketPassword1!) for RDP access. Check the licensing box, then click Review + Create to deploy the VM. Once created, confirm it is running under the Virtual Machines tab, and copy its Public IP Address for the RDP connection. Using Remote Desktop, log into the VM with the credentials you set, then download the osTicket-Installation-Files.zip inside the VM and unzip it to your desktop. The extracted folder, osTicket-Installation-Files, will be used for installing osTicket and its dependencies.<p>
<ul>
<li>Create an Azure Virtual Machine Windows 10, 4 vCPUs</li>
<li>Reasource Group name: osTicket-vm-rg</li>
<li>VM Name: osticket-vm</li>
<li>Username: labuser</li>
<li>Password: Password1!</li>
<li>Log into the VM with Remote Desktop</li>
  <li>My VM IP Address: 172.184.157.175 (Yours will be different)</li>
</ul>

<h2>Step 2. Prepare Installation Files</h2>
<p>Download osTicket-Installation-Files.zip inside the VM desktop. Copy the link below then paste into google inside the VM.</p>
<p>All OsTicket Installation Files = https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD </p>
<p>Unzip folder osTicket-Installation-Files to desktop.</p>
<p align="center">
  <img src="Images/canvas (6).png" width="200"/>
  <img src="Images/canvas (7).png" width="200"/>
</p>
<ul>
<li>Download osTicket-Installation-Files.zip inside the VM we created "osticket-vm".</li>
<li>Unzip the downloaded folder onto our desktop</li>
</ul>


<h2>Step 3. Install IIS with CGI</h2>
<p>Open “Add Roles and Features.”</p>
<p>Enable IIS → World Wide Web Services → Application Development Features → CGI.</p>
<p><p>Inside the VM, install and enable Internet Information Services (IIS) on Windows, which will act as the web server for osTicket. To do this, open Windows Features and navigate to World Wide Web Services → Application Development Features, then check CGI. Make sure to also check all the required boxes needed to fully install IIS, including the basic Web Server, Common HTTP Features, Security, Performance Features, and Management Tools. IIS will allow your VM to host and serve web applications like osTicket, and handle incoming HTTP requests, essentially turning your VM into a functioning web server.</p>
  <p align="center">
  <img src="Images/canvas (8).png" width="200"/>
  <img src="Images/canvas (9).png" width="200"/>
  <img src="Images/canvas (10).png" width="200"/>
  <img src="Images/canvas (11).png" width="200"/>
</p>
<ul>
<li>Enable Internet Information Services (IIS) and check all required boxes.</li>
<li>Under Application Development Features, check CGI for PHP support.</li>
</ul>


<h2>Step 4. Install PHP Manager and Rewrite Module</h2>
<p>Run PHPManagerForIIS_V1.5.0.msi.</p>
<p>Run rewrite_amd64_en-US.msi.</p>
<p>Open the Installation Files Folder on our desktop and go ahead and locate the first two installations we will be taking care of.</p>
<p align="center">
  <img src="Images/canvas (13).png" width="200"/>
  <img src="Images/canvas (14).png" width="200"/>
</p>
<ul>
<li>Install and agree with Licensce Agreement to install "PHPManagerForIIS_V1.5.0.msi." file.</li>
<li>Install and agree with Licensce Agreement for "rewrite_amd64_en-US.msi." file as well.</li>
</ul>


<h2>Step 5. Prepare PHP and Dependencies</h2>
<p>First, create a new folder called (PHP) in our C Drive directory. Next, go to the osTicket-Installation-Files folder and extract the PHP 7.3.8 zip file (php-7.3.8-nts-Win32-VC15-x86.zip) into the C:\PHP directory/folder(PHP) we just created. After that, run VC_redist.x86.exe from the osTicket Installation folder to install the required Microsoft Visual C++ Redistributable, which is necessary for PHP to run properly on Windows.</p>
<p align="center">
  <img src="Images/canvas (15).png" width="200"/>
  <img src="Images/canvas (16).png" width="200"/>
  <img src="Images/canvas (17).png" width="200"/>
  <img src="Images/canvas (18).png" width="200"/>
</p>
<ul>
<li>Create new folder in our (C) Drive as showed here.  C:\PHP.</li>
<li>Unzip php-7.3.8-nts-Win32-VC15-x86.zip into C:\PHP.</li>
<li>Install VC_redist.x86.exe. and agree with Licensce Agreement to proceed.</li>
</ul>



<h2>Step 6. Install MySQL</h2>
<p>Begin by running the installer (mysql-5.5.62-win32.) and launch the MySQL Instance Configuration Wizard after finished downlaoding and choose Standard Configuration, and set the default credentials with the username root and password root to complete the setup.</p>
<p align="center">
  <img src="Images/canvas (21).png" width="200"/>
  <img src="Images/canvas (22).png" width="200"/>
  <img src="Images/canvas (23).png" width="200"/>
  <img src="Images/canvas (24).png" width="200"/>
  <img src="Images/canvas (25).png" width="200"/>
</p>

<ul>
<li>Run mysql-5.5.62-win32.msi.</li>
<li>Typical setup → Launch Configuration Wizard → Standard Configuration.</li>
<li>Root username/password: root/root.</li>
</ul>




<h2>Step 7. Configure IIS for PHP</h2>
<p>Open IIS as an Administrator, then register PHP by pointing IIS to the PHP executable located at C:\PHP\php-cgi.exe through PHP Manager. Then go ahead and reload IIS by stopping and starting the server to apply the changes.</p>

<p align="center">
  <img src="Images/canvas (26).png" width="200"/>
  <img src="Images/canvas (27).png" width="200"/>
  <img src="Images/canvas (28).png" width="200"/>
  <img src="Images/canvas (29).png" width="200"/>
  <img src="Images/canvas (30).png" width="200"/>
  <img src="Images/canvas (32).png" width="200"/>
</p>
<ul>
<li>Open IIS as Admin.</li>
<li>Register PHP: PHP Manager → C:\PHP\php-cgi.exe.</li>
<li>Reload IIS (Stop → Start).</li>
</ul>




<h2>Step 8. Install osTicket</h2>
<p>Unzip osTicket-v1.15.8.zip file located in the osTicket-Installation-Files folder. After extracting, copy the upload folder into the directory C:\inetpub\wwwroot. Once copied, rename the upload folder to "osTicket" *IMPORTANT NOTE* Make sure 'osTicket' is written exactly the same way as shown for IIS can recognize it as the application directory. Finally, reload IIS by opening it and performing a stop and start of the server to apply the changes and prepare osTicket for configuration.</p>
<p align="center">
  <img src="Images/canvas (33).png" width="200"/>
  <img src="Images/canvas (34).png" width="200"/>
  <img src="Images/canvas (35).png" width="200"/>
  <img src="Images/canvas (36).png" width="200"/>
  <img src="Images/canvas (37).png" width="200"/>
</p>
<ul>
<li>Unzip osTicket-v1.15.8.zip → copy upload to C:\inetpub\wwwroot</li>
<li>Rename folder: upload → osTicket</li>
<li>Reload IIS (Stop → Start).</li>
</ul>


<h2>Step 9. Enable PHP Extensions</h2>
<p>Navigate in IIS to Sites → Default → osTicket, then on the right panel click *“Browse :80” to open the site in your browser. You may notice that some PHP extensions are not enabled. Go back to IIS, select Sites → Default → osTicket, and double-click PHP Manager. Click “Enable or disable an extension” and enable the following extensions: php_imap.dll, php_intl.dll, and php_opcache.dll.</p>
<p align="center">
  <img src="Images/canvas (38).png" width="200"/>
  <img src="Images/canvas (40).png" width="200"/>
  <img src="Images/canvas (41).png" width="200"/>
  <img src="Images/canvas (42).png" width="200"/>
  <img src="Images/canvas (43).png" width="200"/>
</p>
<ul>
<li>Open IIS → Sites → Default → osTicket → PHP Manager</li>
<li>Enable extensions: php_imap.dll, php_intl.dll, php_opcache.dll</li>
<li>Refresh osTicket in browser</li>
</ul>




<h2>Step 10. Configure osTicket</h2>
<p>Now that the extensions are enabled, configure osTicket by going to this designated path in the C drive to C:\inetpub\wwwroot\osTicket\include\ and rename the file ost-sampleconfig.php to ost-config.php so that osTicket recognizes it as the active configuration. Next, set file permissions by right-clicking ost-config.php, going to Properties → Security → Advanced, disabling inheritance, and removing all inherited permissions. Then, add a new permission for Everyone with full control to ensure IIS and PHP can properly access and modify the configuration file. </p>
<p align="center">
  <img src="Images/canvas (44).png" width="200"/>
  <img src="Images/canvas (45).png" width="200"/>
  <img src="Images/canvas (46).png" width="200"/>
  <img src="Images/canvas (47).png" width="200"/>
  <img src="Images/canvas (48).png" width="200"/>
  <img src="Images/canvas (49).png" width="200"/>
  <img src="Images/canvas (50).png" width="200"/>
  <img src="Images/canvas (51).png" width="200"/>
  <img src="Images/canvas (52).png" width="200"/>
  <img src="Images/canvas (53).png" width="200"/>
  <img src="Images/canvas (54).png" width="200"/>
  <img src="Images/canvas (55).png" width="200"/>
</p>
<ul>
<li>Rename ost-sampleconfig.php → ost-config.php</li>
<li>Assign permissions to ost-config.php (Everyone → All)</li>
<li>Continue setup in browser (Helpdesk name, default email).</li>
</ul>

<h2>Step 11. Setup Database with HeidiSQL</h2>
<p></p>
<p align="center">
  <img src="Images/canvas (56).png" width="200"/>
  <img src="Images/canvas (57).png" width="200"/>
  <img src="Images/canvas (58).png" width="200"/>
  <img src="Images/canvas (59).png" width="200"/>
  <img src="Images/canvas (61).png" width="200"/>
  <img src="Images/canvas (62).png" width="200"/>
  <img src="Images/canvas (64).png" width="200"/>
  <img src="Images/canvas (65).png" width="200"/>
</p>
<p>Install and open HeidiSQL.</p>
<p>Create new session → root/root → connect.</p>
<p>Create database osTicket.</p>
<p><!-- Add description/commentary for Step 11 photos here --></p>




<h2>Step 12. Final Browser Setup</h2>
<p></p>
<p align="center">
  <img src="Images/canvas (66).png" width="200"/>
  <img src="Images/canvas (67).png" width="200"/>
  <img src="Images/canvas (68).png" width="200"/>
  <img src="Images/canvas (69).png" width="200"/>
  <img src="Images/canvas (70).png" width="200"/>
</p>
<p>Input database details in osTicket installer:</p>
<ul>
  <li>MySQL Database: osTicket</li>
  <li>MySQL Username: root</li>
  <li>MySQL Password: root</li>
</ul>

<p>Complete installation.</p>
  <p align="center">
  <img src="Images/canvas (71).png" width="200"/>
  <img src="Images/canvas (72).png" width="200"/>
  <img src="Images/canvas (73).png" width="200"/>
  <img src="Images/canvas (74).png" width="200"/>
  <img src="Images/canvas (75).png" width="200"/>
</p>
<p>Access Helpdesk: http://localhost/osTicket/scp/login.php</p>
<p>End users: http://localhost/osTicket/</p>
<p><!-- Add description/commentary for Step 12 photos here --></p>

</body>
</html>


</body>
</p>
<br />
