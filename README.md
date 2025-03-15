
# osTicket: Prerequisites and Installation

## Project Overview
This project demonstrates the installation and configuration of osTicket, an open-source help desk ticketing system, using Microsoft Azure and Windows 10.

## Environments and Technologies Used
- Microsoft Azure (Virtual Machines)
- Windows 10 (21H2)
- Internet Information Services (IIS)
- MySQL 5.5.62
- PHP 7.3.8
- osTicket v1.15.8

## Prerequisites
- Azure subscription
- Understanding of Windows OS
- Basic knowledge of web servers

## Implementation Steps

### 1. Create Azure Virtual Machine
- Created a Windows 10 VM (4 vCPUs) named "osticket-vm"
- Username: labuser
- Password: osTicketPassword1! (would use more secure passwords in production)

![Azure VM Creation](https://i.imgur.com/5HzGhsb.png)

### 2. Install Internet Information Services (IIS)
- Enabled IIS in Windows WITH CGI
- Installed World Wide Web Services -> Application Development Features -> CGI

![IIS Installation](https://i.imgur.com/OFaZmGi.png)

### 3. Install Supporting Software
From the osTicket Installation Files:
- Installed PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)
- Installed Rewrite Module (rewrite_amd64_en-US.msi)
- Created directory C:\PHP
- Extracted PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) to C:\PHP
- Installed VC_redist.x86.exe
- Installed MySQL 5.5.62 (mysql-5.5.62-win32.msi)
  - Typical Setup
  - Standard Configuration
  - Set Root Password: root (would use more secure passwords in production)

![PHP Installation](https://i.imgur.com/vvKaUKL.png)

### 4. Configure IIS
- Registered PHP from within IIS using PHP Manager
- Set path to C:\PHP\php-cgi.exe
- Restarted IIS

### 5. Install osTicket
- Extracted osTicket v1.15.8 from the installation files
- Copied "upload" folder to c:\inetpub\wwwroot
- Renamed folder to "osTicket"
- Restarted IIS

![osTicket Files](https://i.imgur.com/tVJpMCs.png)

### 6. Configure Required PHP Extensions
- Accessed the osTicket installer at http://localhost/osTicket/setup
- Enabled the following PHP extensions through IIS PHP Manager:
  - php_imap.dll
  - php_intl.dll
  - php_opcache.dll

### 7. Configure osTicket Files
- Renamed ost-sampleconfig.php to ost-config.php:
  - From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
  - To: C:\inetpub\wwwroot\osTicket\include\ost-config.php
- Set permissions on ost-config.php:
  - Disabled inheritance
  - Added "Everyone" with "All" permissions (would restrict further in production)

![File Permissions](https://i.imgur.com/yCY1oM7.png)

### 8. Set Up Database
- Installed HeidiSQL from the installation files
- Created a new database session with:
  - Username: root
  - Password: root
- Created a new database called "osTicket"

![HeidiSQL Database](https://i.imgur.com/YXTtzrX.png)

### 9. Complete osTicket Installation
- Configured basic settings:
  - Helpdesk Name: Zach's Help Desk
  - Default Email (receives email from customers)
- Configured database settings:
  - MySQL Database: osTicket
  - MySQL Username: root
  - MySQL Password: root
- Installed successfully!

![Installation Success](https://i.imgur.com/h6riq3C.png)

### 10. Clean Up
- Deleted: C:\inetpub\wwwroot\osTicket\setup directory
- Set ost-config.php to "Read Only" permissions:
  - C:\inetpub\wwwroot\osTicket\include\ost-config.php

## Post-Installation Access
- Admin/Analyst Login: http://localhost/osTicket/scp/login.php
- End Users osTicket URL: http://localhost/osTicket/

## Lessons Learned
- Gained experience deploying Windows virtual machines in Azure
- Learned about configuring IIS and PHP for web applications
- Practiced database creation and management with MySQL
- Implemented proper file permissions for security
- Understood the relationships between different web technologies in a WIMP stack
