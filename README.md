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

-- Step 1 -- 
<h2>Create Azure Virtual Machine</h2>
<p>Create Windows 10 VM (4 vCPUs).</p>
<p>VM Name: osticket-vm</p>
<p>Username/Password: labuser / osTicketPassword1!</p>
<p>Log in via Remote Desktop.</p>
<p><!-- Add description/commentary for Step 1 photos here --></p>

-- Step 2 --
<h2>Prepare Installation Files</h2>
<p>Download osTicket-Installation-Files.zip to VM desktop.</p>
<p>Unzip folder to osTicket-Installation-Files.</p>
<p><!-- Add description/commentary for Step 2 photos here --></p>

-- Step 3 --
<h2>Install IIS with CGI</h2>
<p>Open “Add Roles and Features.”</p>
<p>Enable IIS → World Wide Web Services → Application Development Features → CGI.</p>
<p><!-- Add description/commentary for Step 3 photos here --></p>

-- Step 4 --
<h2>Install PHP Manager and Rewrite Module</h2>
<p>Run PHPManagerForIIS_V1.5.0.msi.</p>
<p>Run rewrite_amd64_en-US.msi.</p>
<p><!-- Add description/commentary for Step 4 photos here --></p>

-- Step 5 --
<h2>Prepare PHP and Dependencies</h2>
<p>Create folder C:\PHP.</p>
<p>Unzip php-7.3.8-nts-Win32-VC15-x86.zip into C:\PHP.</p>
<p>Install VC_redist.x86.exe.</p>
<p><!-- Add description/commentary for Step 5 photos here --></p>

-- Step 6 --
<h2>Install MySQL</h2>
<p>Run mysql-5.5.62-win32.msi.</p>
<p>Typical setup → Launch Configuration Wizard → Standard Configuration.</p>
<p>Root username/password: root/root.</p>
<p><!-- Add description/commentary for Step 6 photos here --></p>

-- Step 7 --
<h2>Configure IIS for PHP</h2>
<p>Open IIS as Admin.</p>
<p>Register PHP: PHP Manager → C:\PHP\php-cgi.exe.</p>
<p>Reload IIS (Stop → Start).</p>
<p><!-- Add description/commentary for Step 7 photos here --></p>

-- Step 8 --
<h2>Install osTicket</h2>
<p>Unzip osTicket-v1.15.8.zip → copy upload to C:\inetpub\wwwroot.</p>
<p>Rename folder: upload → osTicket.</p>
<p>Reload IIS.</p>
<p><!-- Add description/commentary for Step 8 photos here --></p>

-- Step 9 --
<h2>Enable PHP Extensions</h2>
<p>Open IIS → Sites → Default → osTicket → PHP Manager.</p>
<p>Enable extensions: php_imap.dll, php_intl.dll, php_opcache.dll.</p>
<p>Refresh osTicket in browser.</p>
<p><!-- Add description/commentary for Step 9 photos here --></p>

-- Step 10 --
<h2>Configure osTicket</h2>
<p>Rename ost-sampleconfig.php → ost-config.php.</p>
<p>Assign permissions to ost-config.php (Everyone → All).</p>
<p>Continue setup in browser (Helpdesk name, default email).</p>
<p><!-- Add description/commentary for Step 10 photos here --></p>

-- Step 11 --
<h2>Setup Database with HeidiSQL</h2>
<p>Install and open HeidiSQL.</p>
<p>Create new session → root/root → connect.</p>
<p>Create database osTicket.</p>
<p><!-- Add description/commentary for Step 11 photos here --></p>

-- Step 12 --
<h2>Final Browser Setup</h2>
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
