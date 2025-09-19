<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<body>

<h1>osTicket Installation Tutorial</h1>

<-- Step 1 -->
<h2>Create Azure Virtual Machine</h2>
<p>Create Windows 10 VM (4 vCPUs)</p>
<img src="./images/part1-step1.png" alt="Azure VM Creation" width="80%">
<p>VM Name: osticket-vm</p>
<p>Username/Password: labuser / osTicketPassword1!</p>
<p>Log in via Remote Desktop</p>
<img src="./images/part1-step2.png" alt="Remote Desktop Login" width="80%">

<!-- Step 2 -->
<h2>Prepare Installation Files</h2>
<p>Download osTicket-Installation-Files.zip to VM desktop</p>
<img src="./images/part2-step1.png" alt="Download osTicket Files" width="80%">
<p>Unzip folder to osTicket-Installation-Files</p>
<img src="./images/part2-step2.png" alt="Unzip osTicket Files" width="80%">

<!-- Step 3 -->
<h2>Install IIS with CGI</h2>
<p>Open “Add Roles and Features”</p>
<p>Enable IIS → World Wide Web Services → Application Development Features → CGI</p>
<img src="./images/part3-step1.png" alt="Enable IIS CGI" width="80%">

<!-- Step 4 -->
<h2>Install PHP Manager and Rewrite Module</h2>
<p>Run PHPManagerForIIS_V1.5.0.msi</p>
<img src="./images/part4-step1.png" alt="Install PHP Manager" width="80%">
<p>Run rewrite_amd64_en-US.msi</p>
<img src="./images/part4-step2.png" alt="Install Rewrite Module" width="80%">

<!-- Step 5 -->
<h2>Prepare PHP and Dependencies</h2>
<p>Create folder C:\PHP</p>
<img src="./images/part5-step1.png" alt="Create PHP Folder" width="80%">
<p>Unzip php-7.3.8-nts-Win32-VC15-x86.zip into C:\PHP</p>
<img src="./images/part5-step2.png" alt="Unzip PHP" width="80%">
<p>Install VC_redist.x86.exe</p>
<img src="./images/part5-step3.png" alt="Install VC++ Redistributable" width="80%">

<!-- Step 6 -->
<h2>Install MySQL</h2>
<p>Run mysql-5.5.62-win32.msi</p>
<img src="./images/part6-step1.png" alt="Install MySQL" width="80%">
<p>Typical setup → Launch Configuration Wizard → Standard Configuration</p>
<p>Root username/password: root/root</p>
<img src="./images/part6-step2.png" alt="MySQL Configuration" width="80%">

<!-- Step 7 -->
<h2>Configure IIS for PHP</h2>
<p>Open IIS as Admin</p>
<p>Register PHP: PHP Manager → C:\PHP\php-cgi.exe</p>
<img src="./images/part7-step1.png" alt="Register PHP in IIS" width="80%">
<p>Reload IIS (Stop → Start)</p>
<img src="./images/part7-step2.png" alt="Reload IIS" width="80%">

<!-- Step 8 -->
<h2>Install osTicket</h2>
<p>Unzip osTicket-v1.15.8.zip → copy upload to C:\inetpub\wwwroot</p>
<img src="./images/part8-step1.png" alt="Copy osTicket Upload Folder" width="80%">
<p>Rename folder: upload → osTicket</p>
<img src="./images/part8-step2.png" alt="Rename Folder" width="80%">
<p>Reload IIS</p>
<img src="./images/part8-step3.png" alt="Reload IIS" width="80%">

<!-- Step 9 -->
<h2>Enable PHP Extensions</h2>
<p>Open IIS → Sites → Default → osTicket → PHP Manager</p>
<p>Enable extensions: php_imap.dll, php_intl.dll, php_opcache.dll</p>
<img src="./images/part9-step1.png" alt="Enable PHP Extensions" width="80%">
<p>Refresh osTicket in browser</p>
<img src="./images/part9-step2.png" alt="Refresh Browser" width="80%">

<!-- Step 10 -->
<h2>Configure osTicket</h2>
<p>Rename ost-sampleconfig.php → ost-config.php</p>
<img src="./images/part10-step1.png" alt="Rename Config File" width="80%">
<p>Assign permissions to ost-config.php (Everyone → All)</p>
<img src="./images/part10-step2.png" alt="Assign Permissions" width="80%">
<p>Continue setup in browser (Helpdesk name, default email)</p>
<img src="./images/part10-step3.png" alt="Continue Setup" width="80%">

<!-- Step 11 -->
<h2>Setup Database with HeidiSQL</h2>
<p>Install and open HeidiSQL</p>
<img src="./images/part11-step1.png" alt="Open HeidiSQL" width="80%">
<p>Create new session → root/root → connect</p>
<img src="./images/part11-step2.png" alt="Create New Session" width="80%">
<p>Create database osTicket</p>
<img src="./images/part11-step3.png" alt="Create Database" width="80%">

<!-- Step 12 -->
<h2>Final Browser Setup</h2>
<p>Input database details in osTicket installer:</p>
<ul>
  <li>MySQL Database: osTicket</li>
  <li>MySQL Username: root</li>
  <li>MySQL Password: root</li>
</ul>
<img src="./images/part12-step1.png" alt="Database Details" width="80%">
<p>Complete installation</p>
<img src="./images/part12-step2.png" alt="Complete Installation" width="80%">
<p>Access Helpdesk: <a href="http://localhost/osTicket/scp/login.php">http://localhost/osTicket/scp/login.php</a></p>
<img src="./images/part12-step3.png" alt="Access Helpdesk" width="80%">
<p>End users: <a href="http://localhost/osTicket/">http://localhost/osTicket/</a></p>
<img src="./images/part12-step4.png" alt="End Users URL" width="80%">

</body>
</p>
<br />
