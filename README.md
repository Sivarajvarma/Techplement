deploy a monolithic architecture with WordPress and MySQL on Ubuntu.

Step 1: Install MySQL Server
Update the package index:
sudo apt update
Install MySQL Server
sudo apt install mysql-server
During the installation, you'll be prompted to set a root password for MySQL. Choose a strong password and remember it.

Step 2: Secure MySQL Installation
Run the MySQL security script to improve the security of your MySQL installation:
sudo mysql_secure_installation

Step 3: Install Apache, PHP, and other dependencies
Install Apache web server:
sudo apt install apache2
Install PHP and required PHP extensions:
sudo apt install php libapache2-mod-php php-mysql

Step 4: Download and Install WordPress
cd /var/www/html
Download the latest WordPress package:
sudo wget https://wordpress.org/latest.tar.gz
Extract the downloaded archive:
sudo tar -xzvf latest.tar.gz
sudo chown -R www-data:www-data /var/www/html/wordpress
sudo chmod -R 755 /var/www/html/wordpress

Step 5: Create MySQL Database and User for WordPress
Log in to the MySQL server:

sudo mysql -u root -p
Enter the root password you set during MySQL installation.

Create a new database for WordPress:
CREATE DATABASE wordpress_db;
Create a new MySQL user and grant privileges to the WordPress database:

CREATE USER 'wordpress_user'@'localhost' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON wordpress_db.* TO 'wordpress_user'@'localhost';
FLUSH PRIVILEGES;
EXIT;
Replace 'wordpress_db', 'wordpress_user', and 'password' with your desired database name, username, and password.

Step 6: Configure WordPress
Rename the WordPress configuration file:
sudo mv /var/www/html/wordpress/wp-config-sample.php /var/www/html/wordpress/wp-config.php
Open the WordPress configuration file in a text editor:
sudo nano /var/www/html/wordpress/wp-config.php
Update the database connection settings with the MySQL database details:


define( 'DB_NAME', 'wordpress_db' );
define( 'DB_USER', 'wordpress_user' );
define( 'DB_PASSWORD', 'password' );
define( 'DB_HOST', 'localhost' );
Replace 'wordpress_db', 'wordpress_user', and 'password' with your actual database name, username, and password.

Step 7: Complete WordPress Installation
Access your server's public IP address in a web browser.
Follow the WordPress installation wizard to set up your site, including creating an admin account and configuring basic settings.
