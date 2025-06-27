# Install MySQL on ubuntu

## OS Update

	sudo apt update

## Install MySQL 

	sudo apt install mysql-server -y 
	mysqld –version 
	sudo systemctl start mysql.service
	sudo ss -tap | grep mysql

## Configure DB

	sudo mysql_secure_installation

	sudo mysql -u root
	sudo mysql
	create database wpdwptest;
	show databases;

	CREATE USER 'dbuser'@'localhost' IDENTIFIED BY 'fVMXH#';
	GRANT ALL PRIVILEGES ON dwpcaresdb.* TO 'dbuser'@'localhost';
	FLUSH PRIVILEGES;