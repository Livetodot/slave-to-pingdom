# slave-to-pingdom

A script to present the status of MySQL replication from a slave to Pingdom in XML form

## Installation

These instructions assume a CentOS 6-like environment. Please adapt them for your own.
Run the following commands on the MySQL slave server

     yum install httpd php php-mysql
     cd /var/www/html
     touch index.html
     git clone https://github.com/CatN/slave-to-pingdom.git
     cd slave-to-pingdom
     cp config.template.inc.php config.inc.php
     mysql
     mysql> GRANT REPLICATION CLIENT ON *.* TO 'slave-to-pingdom'@'localhost' IDENTIFIED BY 'random_password_here';
     mysql> \q
     ( edit config.inc.php and update it with the correct details)

Then setup your monitoring in Pingdom using Check type "HTTP Custom" and enter the URL to XML file as 
http://your-slave.example.com/slave-to-pingdom/
