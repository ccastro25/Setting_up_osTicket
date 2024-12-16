# Setting_up_osTicket
This guide details the requirements and steps for installing the open-source help desk ticketing system, osTicket
Absolutely, here's a well-formatted version for your `README.md` on GitHub:

---

# Setting Up Localhost

## Steps:

### 1. Enable IIS on Windows
1. Go to `Control Panel > Programs > Programs and Features`.
2. Click on `Turn Windows features on or off`.
3. Expand `Internet Information Services`.
4. Expand `Web Management Tools` and select `IIS Management Console`.
5. Expand `World Wide Web Services`, then:
   - Expand `Application Development Features` and select `CGI`.
   - Expand `Common HTTP Features` and select all.

### 2. Test Localhost
- Open any browser and type `localhost` or `127.0.0.1`. You should see the IIS welcome page.
![iis welcome screen](https://github.com/user-attachments/assets/134ff0c0-a897-435b-ab28-744507391d56)

---

### 3. Download and Install PHP
1. Visit [PHP Downloads](https://windows.php.net/download#php-8.2).
2. Download `PHP 8.2 (8.2.26) VS16 x64 Non Thread Safe`.
3. Extract files:
   - Right-click the downloaded ZIP file and select `Extract All`.
   - Create a folder `C:\php` and extract the files there.
![create php folder](https://github.com/user-attachments/assets/8ac62f73-3216-4eb4-84aa-1cbde2f96176)

### 4. Install PHP Manager
- Download PHP Manager from [Google Drive](https://drive.google.com/file/d/1qyZMk_YTizMGJMVULN_TtCwVY9sxw9lz/view?usp=sharing%3Eis).
![PhpManager](https://github.com/user-attachments/assets/0a01c983-4d3a-4aa6-9b2b-c4a180643e90)
### 5. Install URL Rewrite Module
- Download from [Microsoft IIS](https://www.iis.net/downloads/microsoft/url-rewrite) and select the `x64 installer`.
![UrlRewrite](https://github.com/user-attachments/assets/3b58f585-36a8-4205-a52b-8041f4cb5004)


### 6. Install Microsoft Visual C++ Redistributable
- Visit [Microsoft Visual C++ Redistributable](https://learn.microsoft.com/en-gb/cpp/windows/latest-supported-vc-redist?view=msvc-170) and download the latest `x64` version.
![UrlRewrite](https://github.com/user-attachments/assets/6ad6a738-953b-4040-aa1e-85a03d40badb)

### 7. Download MySQL Community Edition
1. Go to [MySQL Downloads](https://dev.mysql.com/downloads/file/?id=536356).
2. Select `Custom` setup.
3. Expand `MySQL Servers` > `MySQL Server` and select `MySQL Server 8.0.40 - x64`.
4. Add `MySQL Workbench 8.0.40 - x64`.
5. Follow the installation steps, setting up the root password when prompted.

---

### 8. Setup Database for osTicket
1. Once MySQL Workbench is open, create a schema named `osticket`.

### 9. Download and Configure osTicket
1. Download osTicket from [GitHub](https://github.com/osTicket/osTicket/releases/tag/v1.18.1).
2. Unzip and move the `upload` folder to `C:\inetpub\wwwroot\osTicket`.
3. Rename `ost-sampleconfig.php` to `ost-config.php`:
   - Set permissions: Disable inheritance, remove all inherited permissions, add `Everyone` with `Full Control`.

---

### 10. Register PHP in IIS
1. Search for IIS, right-click and run as Admin.
2. Double-click `PHP Manager`, click `Register new PHP version`, and select `php-cgi.exe` from the `C:\php` directory.
3. Restart the server.

### 11. Install osTicket
1. In IIS, expand `Sites` and navigate to `Default Web Site`.
2. Click on `osTicket` and browse to `http://localhost/osTicket/setup/install.php`.

### 12. Enable PHP Extensions
- Enable `PHP IMAP`, `Intl`, and `Zend OPcache` extensions through PHP Manager.

### 13. Finish osTicket Setup
1. Complete the web-based setup, providing database and admin information.

---

### Cleanup
1. Delete the `setup` folder from `C:\inetpub\wwwroot\osTicket`.
2. Set `ost-config.php` permissions to read-only for `Everyone`.

---

That should set you up nicely! If there's anything else you need, feel free to ask. Happy coding! 📚💻
