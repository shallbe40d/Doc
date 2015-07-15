# Install mysql on osx yosemite

Make sure macports is installed and upgraded to the latest version:
		sudo port selfupdate

Then install mysql server 5.6:
		sudo port install mysql56-server mysql56

MacPorts installs MySQL and its derivatives in a way that they don’t conflict with each other and can be installed at the same time. That includes putting the mysql binary in non-standard paths. You can locate your binary using:
		port contents mysql56 | grep -E '/s?bin/'

Which should spit out paths pointing at /opt/local/lib/mysql56/bin/.

MacPorts also comes with a selection mechanism that creates symlinks for your convenience in /opt/local/bin. To make MySQL 5.6 your default, run:
		sudo port select --set mysql mysql56

Setup default database by running:
		sudo -u _mysql mysql_install_db

Configure MySql server by editing the my.cnf file:
		sudo vi /opt/local/etc/mysql56/my.cnf

By default, MySql server does not allow network connections. Read more by typing:

port notes mysql56

To allow network connection comment out the following line:

		\#!include /opt/local/etc/mysql56/macports-default.cnf

Also add your custom config to this file.

Then start the mysql database server:
		sudo -u _mysql mysqld_safe &

Set the mysql root password:
		mysqladmin -u root password 'new-password'

Check if mysql server is alive:
		mysqladmin -u root -p ping

To stop the mysql databse server:
		mysqladmin -u root shutdown -p

To start the server and ensure it is running after a reboot, you can use MacPorts’ daemon control functions (that are a frontend to launchd):
		sudo port load mysql56-server

To undo that and stop the server:
		sudo port unload mysql56-server
