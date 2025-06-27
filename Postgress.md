# Postgres on Ubuntu:

## Install dependency

	apt update 
	sudo apt install software-properties-common apt-transport-https wget -y
	sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
	wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -

## Install Postgres

	sudo apt  update
	sudo apt  -y install postgresql
	sudo apt -y install postgresql-13 postgresql-13-pgqr postgresql-13-cron postgresql-13-postgis-3

## Check Postgres Status and Enable services

	sudo systemctl status postgresql
	sudo systemctl enable postgresql

## Create DB

	sudo -u postgres psql
	SELECT version();
	ALTER USER postgres PASSWORD 'postgres';

## Exit from DB

	\q
	exit ()


## Check Status DB
	
	ss -nlt

## Change DB parameter to access outside of server

	sudo vi /etc/postgresql/13/main/postgresql.conf
	#listen_addresses = 'localhost' 
	listen_addresses = '*' 

	sudo systemctl restart postgresql


	ss -nlt
	sudo vi /etc/postgresql/13/main/pg_hba.conf 
	
	host    all          all            0.0.0.0/0  md5
	host    replication     all         0.0.0.0/0           md5

	sudo systemctl restart postgresql
