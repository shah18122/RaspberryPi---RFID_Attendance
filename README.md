# RaspberryPi---RFID_Attendance
This Project is a attendace system based on Raspberry Pi


Before we get started with installing MySQL to our Raspberry Pi, we must first update our package list and all installed packages.
#sudo apt update
#sudo apt upgrade
#sudo apt install mariadb-server
#sudo mysql_secure_installation
#sudo mysql -u root -p
#sudo apt install phpmyadmin
#sudo mysql -u root -p
--------------------
GRANT ALL PRIVILEGES ON *.* TO 'username'@'localhost' IDENTIFIED BY 'password' WITH GRANT OPTION;
---------------------(replace "password" with your password)
#sudo nano /etc/apache2/apache2.

Now we need to add the following line to the bottom of this file.
Include /etc/phpmyadmin/apache.conf
#sudo service apache2 restart
#sudo ln -s /usr/share/phpmyadmin /var/www/html


Now time to build your Raspberry Pi RFID Attendance System
Notice

You have to need read this  tutorial for  how to Building the RFID RC522 Reader Circuit and how to Enabling the SPI interface go to 

How to interface RFID-RC522 with Raspberry Pi

The first thing you need to do is move on from the link above and gain an idea about the RFID.

Raspberry pi to RFID-RC522 wiring
SDA connects to Pin 24.
SCK connects to Pin 23.
MOSI connects to Pin 19.
MISO connects to Pin 21.
GND connects to Pin 6.
RST connects to Pin 22.
3.3v connects to Pin 1.
RFID attendance system 

Now your job is to create a database for the RFID attendance system. 
Now it is time to load up into the MYSQL command-line tool by running the following command

#sudo mysql -u root -p
Now you need to create a database according to the command line given below

We will be naming this database, “attendancesy_stem“. To create this database, run the following command

CREATE DATABASE attendance_system;
With our database created, let’s now create a user called “attendance_admin” we will utilize this user in our Python scripts to read from our newly created database.

Make sure you set the password for this to something unique and hard to guess. For our example, we will be just using “your_password” as the password

CREATE USER 'attendance_admin'@'localhost' IDENTIFIED BY 'your_password';
Now that we have created our user we need to give it the rights to access our “attendancesy_stem” database.

We can do this by running the following command. This command will give our “attendance_admin” user full privileges on any table within our database.

GRANT ALL PRIVILEGES ON attendance_system.* TO 'attendance_admin'@'localhost';
 Before we create our tables, we need to utilize the “use” command so that we are directly interacting with the “attendance_system” database.

Begin interacting with the database by running the following command.

use attendance_system;
Now that we are dealing directly with the database that we want to utilize we can now start creating the tables where all our data will be stored

You can leave the MYSQL tool by entering exit;

Recording a User in the Attendance System 
Before we get writing our attendance system scripts, we need first to install the Python “MYSQL Connector” using pip.

Install the connector library by running the following command on your Pi.

sudo pip3 install mysql-connector-python
Recording a User in the Attendance System Code

Recording Attendance

Now you can check your Database for update
