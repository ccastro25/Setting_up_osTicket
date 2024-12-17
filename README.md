# osTicket - Prerequisites and Installation
## This guide covers the necessary prerequisites and steps for installing the open-source help desk ticketing system, osTicket.


### 1. Enable IIS on Windows - Setting Up Localhost


1. Go to **Control Panel > Programs > Programs and Features**.
2. Click on **Turn Windows features on or off**.
3. Expand **Internet Information Services**.
4. Expand **Web Management Tools** and select **IIS Management Console**.
5. Expand **World Wide Web Services**:
   - Expand **Application Development Features** and select **CGI**.
   - Expand **Common HTTP Features** and select all.
![Setting_UP_localhost](https://github.com/user-attachments/assets/2d1a8bf7-a510-46af-973b-25541dac4500)
6. **Testing localhost Setup**: Open any browser and type `localhost` or `127.0.0.1` to see the IIS welcome page.
![showingLocalHost](https://github.com/user-attachments/assets/3f89469a-3991-4415-bc10-52012494bd81)

### 2. Download and Install PHP


1. Visit the [PHP Downloads Page](https://windows.php.net/download#php-8.2).
2. Download the ZIP: **PHP 8.2 (8.2.26) VS16 x64 Non Thread Safe**.
3. Extract the files:
   - Right-click the downloaded ZIP file and select **Extract All**.
   - Create a folder `C:\php` and extract the files there.
![downloadingphp](https://github.com/user-attachments/assets/91adb7d7-14ac-4b6a-9267-e686a5b47244)
### 3. Install PHP Manager


- Download PHP Manager from [Google Drive](https://drive.google.com/file/d/1qyZMk_YTizMGJMVULN_TtCwVY9sxw9lz/view?usp=sharing%3Eis).
![phpManager](https://github.com/user-attachments/assets/36ec2b0b-1a5a-42c1-95a2-9d301a2aa288)
### 4. Install URL Rewrite Module






- Download the URL Rewrite Module from [Microsoft IIS](https://www.iis.net/downloads/microsoft/url-rewrite) and select the `x64 installer`.
![urlrewrite](https://github.com/user-attachments/assets/83b3decf-6768-4264-919c-23a803ccc97c)
### 5. Install Microsoft Visual C++ Redistributable


- Visit the [Microsoft Visual C++ Redistributable Page](https://learn.microsoft.com/en-gb/cpp/windows/latest-supported-vc-redist?view=msvc-170) and download the latest `x64` version.
![redist](https://github.com/user-attachments/assets/59684505-b17d-4049-bcdd-e4790a966e3e)
### 6. Download and Install MySQL Community Edition


1. Go to the [MySQL Downloads Page](https://dev.mysql.com/downloads/file/?id=536356).
![mysqldownloading](https://github.com/user-attachments/assets/cd72bb26-f4ac-4059-82c4-dc3e483a0c97)
2. When the "Choosing setup type" screen pops up, select `Custom`, then click `Next`.
3. At the `Select Products` screen, expand `MySQL Servers > MySQL Server` and select `MySQL Server 8.0.40 - x64`.
4. Click the `->` arrow to add it.
5. Expand `Applications > MySQL Workbench` and add `MySQL Workbench 8.0.40 - x64`.
6. Click `Next`.
7. At the `Installation` screen, click `Execute`.
8. When complete, click `Next`.
9. At `Product Configuration`, click `Next`.
10. At `Type and Networking`, leave the default value and click `Next`.
11. Leave the default selection at `Authentication Method` and click `Next`.
12. Add a password for `root` and click `Next`.
13. At the `Windows Service` screen, leave the default and click `Next`.
14. At `Server File Permissions`, leave the default and click `Next`.
15. At `Apply Configuration`, click `Execute`.
16. Click `Finish` when complete.
![mysqlInstallProcess](https://github.com/user-attachments/assets/d6242071-3ed3-4c98-b72e-19d205cf1a5b)
### 7. Setup Database for osTicket

1. Once the download is complete, open MySQL Workbench or it might open itself.
2. There should be a connection—click it and log in.
3. Once logged in, right in the `Schemas` area, select `Create Schema` and name it `osticket`.
4. Click `Apply`.
5. Click on the `Schema` tab under `Navigator`, and `osticket` should be there.
![creatingdb](https://github.com/user-attachments/assets/a3dbf8cf-9e30-4fab-bead-215680633efd)

### 8. Download and Configure osTicket

1. Download osTicket from [GitHub Releases](https://github.com/osTicket/osTicket/releases/tag/v1.18.1).
2. Unzip and move the `upload` folder to `C:\inetpub\wwwroot\osTicket`.![download osticket](https://github.com/user-attachments/assets/d94cc97c-fcb9-41a5-bb7c-e4e5de22f9d5)

3. Rename `ost-sampleconfig.php` to `ost-config.php`:
   - In File Explore go to `C:\inetpub\wwwroot\osTicket\include`
   - Right-click `ost-config.php` and select `Properties`.
   - Go to the `Security` tab and click `Advanced`.
   - Disable inheritance and select `Remove all inherited permissions from this object`.
   - Click `Add`, then `Select a principal`, enter `Everyone`, and click `OK`.
   - Select `Full control`, click `OK`, apply the changes, and close the properties window.
![permissionand rename ost](https://github.com/user-attachments/assets/819b47f9-2774-41e3-9125-e086605a98b5)

### 9. Register PHP in IIS

1. Search for IIS, right-click, and run as Admin.
2. Double-click `PHP Manager`, click `Register new PHP version`, and select `php-cgi.exe` from the `C:\php` directory.
3. Click `Desktop-G... Home` and then click `Restart` under `Actions/Manage Server`.
![register php manager](https://github.com/user-attachments/assets/35b917e2-7da8-4016-b489-43c44ff30313)


### 10. Enable PHP Extensions
0. go to `http://localhost/osTicket/setup/install.php`. to see missing        extensions
1. Return to IIS Manager.
2. Double-click on `PHP Manager`.
3. Scroll down to `PHP Extensions`.
4. Click `Enable or Disable extension`.
5. Scroll down to the disabled section and enable the following extensions:
   - `php_imap.dll`
   - `php_opcache.dll`
   - `php_intl.dll`
6. Refresh the page for `http://localhost/osTicket/setup/install.php` and ensure all the extensions except APCu have a green check.

### 11. Finish osTicket Setup

1. Navigate back to `http://localhost/osTicket/setup/install.php` webpage.
2. Click the `Continue` button.
3. In the setup form, enter:
   - `Helpdesk Name`
   - `Default Email`
4. Add admin info.
5. Add database info:
   - Leave `Table Prefix` and `Hostname` the same.
   - `MySQL Database`: `osticket`
   - `MySQL Username`: `root`
   - Use the same password you created for MySQL.
6. Click `Install Now`.

If successful, you should see a congratulations window. Go to `http://localhost/osTicket/scp/login.php` and log in using the admin credentials you just created.

### Cleanup

1. Go to `C:\inetpub\wwwroot\osTicket` and delete the `setup` folder.
2. Go to `C:\inetpub\wwwroot\osTicket\include`.
3. Right-click `ost-config.php` and select `Properties`.
4. Go to the `Security` tab and click `Advanced`.
5. Select `Everyone` under permission entries.
6. Click `Edit`, unselect all except `Read` and `Read & execute`, then click `OK`, apply the changes, and close the window.

You can also delete all the ZIP files and folders downloaded during the setup.

---

Happy coding! If you need any further adjustments or additional details, let me know! 🖥️🚀
