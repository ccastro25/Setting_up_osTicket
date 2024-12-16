Setting Up Localhost
Steps
1. Enable IIS on Windows
Go to Control Panel > Programs > Programs and Features.

Click on Turn Windows features on or off.

Expand Internet Information Services.

Expand Web Management Tools and select IIS Management Console.

Expand World Wide Web Services:

Expand Application Development Features and select CGI.

Expand Common HTTP Features and select all.

Open any browser and type localhost or 127.0.0.1 to see the IIS welcome page.

2. Download and Install PHP
Visit the PHP Downloads Page.

Download the ZIP: PHP 8.2 (8.2.26) VS16 x64 Non Thread Safe.

Extract the files:

Right-click the downloaded ZIP file and select Extract All.

Create a folder C:\php and extract the files there.

3. Install PHP Manager
Download PHP Manager from Google Drive.

4. Install URL Rewrite Module
Download the URL Rewrite Module from Microsoft IIS and select the x64 installer.

5. Install Microsoft Visual C++ Redistributable
Visit the Microsoft Visual C++ Redistributable Page and download the latest x64 version.

6. Download and Install MySQL Community Edition
Go to the MySQL Downloads Page.

When the "Choosing setup type" screen pops up, select Custom, then click Next.

At the Select Products screen, expand MySQL Servers > MySQL Server and select MySQL Server 8.0.40 - x64.

Click the -> arrow to add it.

Expand Applications > MySQL Workbench and add MySQL Workbench 8.0.40 - x64.

Click Next.

At the Installation screen, click Execute.

When complete, click Next.

At Product Configuration, click Next.

At Type and Networking, leave the default value and click Next.

Leave the default selection at Authentication Method and click Next.

Add a password for root and click Next.

At the Windows Service screen, leave the default and click Next.

At Server File Permissions, leave the default and click Next.

At Apply Configuration, click Execute.

Click Finish when complete.

7. Setup Database for osTicket
Once the download is complete, open MySQL Workbench or it might open itself.

There should be a connection—click it and log in.

Once logged in, right in the Schemas area, select Create Schema and name it osticket.

Click Apply.

Click on the Schema tab under Navigator, and osticket should be there.

8. Download and Configure osTicket
Download osTicket from GitHub Releases.

Unzip and move the upload folder to C:\inetpub\wwwroot\osTicket.

Rename ost-sampleconfig.php to ost-config.php:

Right-click ost-config.php and select Properties.

Go to the Security tab and click Advanced.

Disable inheritance and select Remove all inherited permissions from this object.

Click Add, then Select a principal, enter Everyone, and click OK.

Select Full control, click OK, apply the changes, and close the properties window.

9. Register PHP in IIS
Search for IIS, right-click, and run as Admin.

Double-click PHP Manager, click Register new PHP version, and select php-cgi.exe from the C:\php directory.

Click Desktop-G... Home and then click Restart under Actions/Manage Server.

10. Install osTicket
In IIS, expand Sites and navigate to Default Web Site.

Click on osTicket and browse to http://localhost/osTicket/setup/install.php.

11. Enable PHP Extensions
Return to IIS Manager.

Double-click on PHP Manager.

Scroll down to PHP Extensions.

Click Enable or Disable extension.

Scroll down to the disabled section and enable the following extensions:

php_imap.dll

php_opcache.dll

php_intl.dll

Refresh the page for http://localhost/osTicket/setup/install.php and ensure all the extensions except APCu have a green check.

12. Finish osTicket Setup
Navigate back to http://localhost/osTicket/setup/install.php webpage.

Click the Continue button.

In the setup form, enter:

Helpdesk Name

Default Email

Add admin info.

Add database info:

Leave Table Prefix and Hostname the same.

MySQL Database: osticket

MySQL Username: root

Use the same password you created for MySQL.

Click Install Now.

If successful, you should see a congratulations window. Go to http://localhost/osTicket/scp/login.php and log in using the admin credentials you just created.

Cleanup
Go to C:\inetpub\wwwroot\osTicket and delete the setup folder.

Go to C:\inetpub\wwwroot\osTicket\include.

Right-click ost-config.php and select Properties.

Go to the Security tab and click Advanced.

Select Everyone under permission entries.

Click Edit, unselect all except Read and Read & execute, then click OK, apply the changes, and close the window.

You can also delete all the ZIP files and folders downloaded during the setup.
