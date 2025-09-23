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
<p><p align="center">
  <img src="Images/canvas (6).png" width="200"/>
  <img src="Images/canvas (7).png" width="200"/>
</p></p>
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



<h2>Step 4. Install PHP Manager and Rewrite Module</h2>
<p>Run PHPManagerForIIS_V1.5.0.msi.</p>
<p>Run rewrite_amd64_en-US.msi.</p>
<p><!-- Add description/commentary for Step 4 photos here --></p>



<h2>Step 5. Prepare PHP and Dependencies</h2>
<p>Create folder C:\PHP.</p>
<p>Unzip php-7.3.8-nts-Win32-VC15-x86.zip into C:\PHP.</p>
<p>Install VC_redist.x86.exe.</p>
<p><!-- Add description/commentary for Step 5 photos here --></p>



<h2>Step 6. Install MySQL</h2>
<p>Run mysql-5.5.62-win32.msi.</p>
<p>Typical setup → Launch Configuration Wizard → Standard Configuration.</p>
<p>Root username/password: root/root.</p>
<p><!-- Add description/commentary for Step 6 photos here --></p>




<h2>Step 7. Configure IIS for PHP</h2>
<p>Open IIS as Admin.</p>
<p>Register PHP: PHP Manager → C:\PHP\php-cgi.exe.</p>
<p>Reload IIS (Stop → Start).</p>
<p><!-- Add description/commentary for Step 7 photos here --></p>




<h2>Step 8. Install osTicket</h2>
<p>Unzip osTicket-v1.15.8.zip → copy upload to C:\inetpub\wwwroot.</p>
<p>Rename folder: upload → osTicket.</p>
<p>Reload IIS.</p>
<p><!-- Add description/commentary for Step 8 photos here --></p>


<h2>Step 9. Enable PHP Extensions</h2>
<p>Open IIS → Sites → Default → osTicket → PHP Manager.</p>
<p>Enable extensions: php_imap.dll, php_intl.dll, php_opcache.dll.</p>
<p>Refresh osTicket in browser.</p>
<p><!-- Add description/commentary for Step 9 photos here --></p>



<h2>Step 10. Configure osTicket</h2>
<p>Rename ost-sampleconfig.php → ost-config.php.</p>
<p>Assign permissions to ost-config.php (Everyone → All).</p>
<p>Continue setup in browser (Helpdesk name, default email).</p>
<p><!-- Add description/commentary for Step 10 photos here --></p>




<h2>Step 11. Setup Database with HeidiSQL</h2>
<p>Install and open HeidiSQL.</p>
<p>Create new session → root/root → connect.</p>
<p>Create database osTicket.</p>
<p><!-- Add description/commentary for Step 11 photos here --></p>




<h2>Step 12. Final Browser Setup</h2>
<p>Input database details in osTicket installer:</p>
<ul>
  <li>MySQL Database: osTicket</li>
  <li>MySQL Username: root</li>
  <li>MySQL Password: root</li>
</ul>

<p>Complete installation.</p>
<p>Access Helpdesk: http://localhost/osTicket/scp/login.php</p>
<p>End users: http://localhost/osTicket/</p>
<p><!-- Add description/commentary for Step 12 photos here --></p>

</body>
</html>


</body>
</p>
<br />
