<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

Azure VM Configuration - A Windows 10 VM with 4 vCPUs named "osticket-vm" must be created in Azure, accessible via RDP with specified credentials (labuser/osTicketPassword1!).

IIS with CGI - Internet Information Services must be installed/enabled with CGI feature under World Wide Web Services -> Application Development Features.

PHP Setup - Requires PHP 7.3.8 extracted to C:\PHP, along with PHP Manager for IIS and the Rewrite Module installed from provided installation files.

MySQL Database - MySQL 5.5.62 must be installed with a root/root account and a database named "osTicket" created using HeidiSQL.

Dependency Installation - VC_redist.x86 runtime and specific PHP extensions (php_imap.dll, php_intl.dll, php_opcache.dll) need to be enabled for osTicket functionality.

<h2>Installation Steps</h2>

<p>
1. Server Environment Setup
  Enable IIS with CGI: Install Internet Information Services (IIS) via Windows Features, ensuring the CGI module is enabled under Application Development Features.

Install Dependencies:

  PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi).

  URL Rewrite Module (rewrite_amd64_en-US.msi).

  Extract PHP 7.3.8 to C:\PHP and register it in IIS using PHP Manager (pointing to php-cgi.exe).

  Install the VC++ runtime (VC_redist.x86.exe) for PHP compatibility.

2. Database Configuration
  Install MySQL 5.5.62: Use the typical setup, then configure with:

  Standard Configuration.

  Username: root, Password: root.

Create osTicket Database:

  Use HeidiSQL to connect to MySQL (credentials root/root).

  Create a new database named osTicket.

3. osTicket Installation & Finalization
Deploy osTicket Files:

  Unzip osTicket-v1.15.8.zip and copy the upload folder to C:\inetpub\wwwroot. Rename it to osTicket.

Configure Permissions:

  Rename ost-sampleconfig.php to ost-config.php in the include folder.

  Assign Full Control permissions to ost-config.php for "Everyone".

Complete Web Setup:

  Access http://localhost/osTicket in your browser.

  Enable required PHP extensions (php_imap.dll, php_intl.dll, php_opcache.dll) via PHP Manager.

  Link the MySQL database (osTicket, root/root) during the web installer.

Post-Installation Security:

 Delete the setup folder in C:\inetpub\wwwroot\osTicket.

 Restrict ost-config.php to Read-only permissions.
</p>
<br />
