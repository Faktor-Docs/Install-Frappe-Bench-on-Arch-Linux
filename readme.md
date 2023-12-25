### Guide to install Frappe Bench version-15 on Arch Linux
###### Can be used for both Version-14 and Version-15
###### Presuming git is already installed or install using 'pacman -S git'
##### 1. Check python version
	python --version
##### If python not available (For latest stable version)
	sudo pacman -S python
##### 2. Install python pip
	sudo pacman -S python-pip
##### 3. Install python setuptools
	sudo pacman -S python-setuptools
##### 4. Install mariadb
	sudo pacman -S mariadb
##### 5. Install mysql
	sudo pacman -S mysql
##### 6. Setup mariadb
	sudo mariadb-install-db --user=mysql --basedir=/usr --datadir=/var/lib/mysql
##### 7. Start mysql service
	sudo systemctl start mysql
##### 8. Enable mysql service
	sudo systemctl enable mysql
##### 9. Setup mysql
	sudo mysql_secure_installation
##### 10. Install mysqlclient
	pip3 install mysqlclient --break-system-packages
##### 11. Mysql Configuration
	sudo nano /etc/my.cnf.d/50-server.cnf
###### If nano is not installed: sudo pacman -S nano
##### 12. Paste lines below to the file and save
	[client]
	default-character-set = utf8mb4

	[mariadb]
	collation_server = utf8mb4_unicode_ci
	character_set_server = utf8mb4

	[mariadb-client]
	default-character-set = utf8mb4

	[server]
	user = mysql
	pid-file = /run/mysqld/mysqld.pid
	socket = /run/mysqld/mysqld.sock
	basedir = /usr
	datadir = /var/lib/mysql
	tmpdir = /tmp
	lc-messages-dir = /usr/share/mysql
	bind-address = 127.0.0.1
	query_cache_size = 16M
##### 13. Retstart mysql service
	sudo systemctl restart mysql.service
##### 14. Install Redis
	sudo pacman -S redis
##### 15. Install Nodejs
	sudo pacman -S nodejs
##### 16. Install npm
	sudo pacman -S npm
##### 17. Install Yarn
	sudo npm install -g yarn
##### 18. Install Cron
	sudo pacman -S cron
##### 19. Install wkhtmltopdf
##### Download arch linux package of wkhtmltopdf from
	https://wkhtmltopdf.org/downloads.html
 
##### Extract package and install
	cd Downloads
	sudo pacman -U wkhtmltox-package_name.pkg.tar.xz
	sudo pacman -Sy --overwrite '/usr/lib/*' openssl-1.1
##### 20. Install frappe bench
	sudo -H pip3 install frappe-bench --breake-system-packages
##### 21. Initialize new bench
	bench init frappe-bench --frappe-branch version-15
