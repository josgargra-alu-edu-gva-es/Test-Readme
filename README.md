# Installing the Apache HTTP Server, PHP, and MySQL Server on the latest Ubuntu Server 
This document provides instructions for installing the Apache HTTP Server, PHP, and MySQL Server on the latest Ubuntu Server. I assume you have your Ubuntu Server running with a technology such as Docker, AWS, or something similar, and that you also have a connection to it via SSH.
1. Update the server with the command `sudo apt-get update`.
2. Once the update process is complete, install the Apache Web Server with the command `sudo apt-get install apache2`.
3. Check if the server is working by accessing the server address in your local machine's browser.
4. Next, install PHP, the MySQL server, and the required modules for MySQL and PHP for Apache. Depending on the OS, some of them may already be installed or unnecessary, but attempt to install them with the command `sudo apt-get install mysql-server php libapache2-mod-php php-mysql`.
5. Enable the PHP module for Apache (version may differ) with the command `sudo a2enmod php8.1`.
6. Start the MySQL server to change the root user authentication method, but do not set a password for the root user to simplify the connection for the application deployment. Use the following commands:
```
sudo service mysql start
sudo mysql
mysql> USE mysql`
mysql> UPDATE user SET plugin='mysql_native_password' WHERE User='root';
mysql> FLUSH PRIVILEGES;
mysql> exit
sudo service mysql restart
```
7. In summary, your servers are now ready to deploy any application with these requirements.

