# Restaurant Menus Application - Final Project (Udacity)

## Brief Description

Final Project for Udacity Full Stack Web Development Course.

The goal was to create a working Auth2.0 web application using modern frameworks in a custom configured server in the cloud on AWS.

This is a full CRUD capable application, to demonstrate understanding of how using the Python Flask Framework & WSGI hosted on custom configured Ubuntu instance in the cloud on AWS on a custom configured instance of a server (Ubuntu 18.04) on AWS lightsail.

The application has multiple easy to use API endpoints to expose the data in the PSQL database underlying the site, and allows any user with a Google account to create custom lists of restaurants (along with menus, prices, food characteristics) all on their own.

## Logging into the Restaurant Menu App Server Ubuntu 18.04 on AWS LightSail.

<<<<<<< HEAD
Type **ssh grader@99.79.159.214 -i /c/Users/calvi/.ssh/LightSailKey**, along with the secret passphrase. This will log your terminal into the virtual machine on AWS so long as you have the correct pub key and password, When you want to log out, type **exit** at the shell prompt. Authentication is enforced on SSH key public & private.
=======
Type **ssh USER@PORT -i /c/Users/calvi/.ssh/LightSailKey -p=PORTNUM**, along with the secret passphrase. This will log your terminal into the virtual machine on AWS so long as you have the correct pub key and password, When you want to log out, type **exit** at the shell prompt. Authentication is enforced on SSH key public & private.
>>>>>>> 78b23f0c1e1877d9703438e8bceb6f581cb0a1d9

Now that you have Vagrant up and running type **vagrant ssh** to log into your VM.  change to the /vagrant directory by typing **cd /vagrant**. This will take you to the shared folder between your virtual machine and host machine.

Type **ls** to ensure that you are inside the directory that contains project.py, database_setup.py, and two directories named 'templates' and 'static'

Now type **python database_setup.py** to initialize the database.

Type **python lotsofmenus.py** to populate the database with restaurants and menu items. (Optional)

[Here's the real website, Check it out!](http://99.254.130.8.xip.io)


## Instructions for upping venv for python 2.7 within server to make any needed changes to the packages that the python instance on the VM uses to run the app.

> source venv/bin/activate

## Database is PostGres SQL

Schema:

|                                         | 
|-----------------------------------------| 
| List of relations                       | 
|  Schema |    Name    | Type  |  Owner   | 
| --------+------------+-------+--------- | 
|  public | menu_item  | table | catalog  | 
|  public | restaurant | table | catalog  | 
|  public | user       | table | catalog  | 
| (3 rows)                                | 


catalog-# \ds

|                                                   | 
|---------------------------------------------------| 
| List of relations                                 | 
|  Schema |       Name        |   Type   |  Owner   | 
| --------+-------------------+----------+--------- | 
|  public | menu_item_id_seq  | sequence | catalog  | 
|  public | restaurant_id_seq | sequence | catalog  | 
|  public | user_id_seq       | sequence | catalog  | 
| (3 rows)                                          | 


## Linux conf setup on WSGI

> sudo apt-get update
> sudo apt-get install apache2 apache2-utils ssl-cert

### Now, install mod_wsgi Apache module by running the following command:

> sudo apt-get install libapache2-mod-wsgi

### Restart Apache service to get mod_wsgi to work.

sudo systemctl restart apache2

### Copy of conf file:

<VirtualHost *:80>
    ServerName 35.183.175.71
    ServerAdmin admin@35.183.175.71
    WSGIDaemonProcess Catalog python-path=/var/www/Catalog:/var/www/Catalog/catalog/venv/local/lib/python2.7/site-packages
    WSGIProcessGroup Catalog
    WSGIScriptAlias / /var/www/Catalog/catalog.wsgi
    <Directory /var/www/Catalog/catalog/>
        Order allow,deny
        Allow from all
    </Directory>
    Alias /static /var/www/Catalog/catalog/static
    <Directory /var/www/Catalog/catalog/static/>
        Order allow,deny
        Allow from all
    </Directory>
    ErrorLog ${APACHE_LOG_DIR}/error.log
    LogLevel warn
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>


## Python Dependencies

### (Python 2.7 libs) in the VM now

Package         Version
--------------- ---------

1. certifi         2019.6.16
2. chardet         3.0.4
3. Click           7.0
4. Flask           1.0.3
5. Flask-SeaSurf   0.2.2
6. httplib2        0.13.0
7. idna            2.8
8. itsdangerous    1.1.0
9. Jinja2          2.10.1
10. MarkupSafe      1.1.1
11. oauth2client    4.1.3
12. pip             19.1.1
13. psycopg2-binary 2.8.3
14. pyasn1          0.4.5
15. pyasn1-modules  0.2.5
16. requests        2.22.0
17. rsa             4.0
18. setuptools      41.0.1
19. six             1.12.0
20. SQLAlchemy      1.3.5
21. urllib3         1.25.3
22. Werkzeug        0.15.4
23. wheel           0.33.4

### Git

If you don't already have Git installed, [download Git from git-scm.com.](http://git-scm.com/downloads) Install the version for your operating system.

On Windows, Git will provide you with a Unix-style terminal and shell (Git Bash).  
(On Mac or Linux systems you can use the regular terminal program.)

You will need Git to install the configuration for the VM. If you'd like to learn more about Git, [take a look at our course about Git and Github](http://www.udacity.com/course/ud775).


## Additional References

References:

[UFW docs](https://help.ubuntu.com/community/UFW)
[How to setup PostgresQL](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-16-04)
[Virtual Environments](https://modwsgi.readthedocs.io/en/develop/user-guides/virtual-environments.html)
[Flask uswgi and nginx](https://www.digitalocean.com/community/tutorials/how-to-serve-flask-applications-with-uwsgi-and-nginx-on-ubuntu-16-04)
[Flask app - deploy a flask app](https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps)
[PSQL to Markdown Converter](https://donatstudios.com/CsvToMarkdownTable)


## Ubuntu Packages Installed:

* accountsservice/bionic,now 0.6.45-1ubuntu1 amd64 [installed]
* acl/bionic,now 2.2.52-3build1 amd64 [installed]
* acpid/bionic,now 1:2.0.28-1ubuntu1 amd64 [installed]
* adduser/bionic,now 3.116ubuntu1 all [installed]
* apache2/bionic-updates,bionic-security,now 2.4.29-1ubuntu4.6 amd64 [installed]
* apache2-bin/bionic-updates,bionic-security,now 2.4.29-1ubuntu4.6 amd64 [installed,automatic]
* apache2-data/bionic-updates,bionic-security,now 2.4.29-1ubuntu4.6 all [installed,automatic]
* apache2-utils/bionic-updates,bionic-security,now 2.4.29-1ubuntu4.6 amd64 [installed,automatic]
* apparmor/bionic-updates,bionic-security,now 2.12-4ubuntu5.1 amd64 [installed]
* apport/bionic-updates,now 2.20.9-0ubuntu7.6 all [installed]
* apport-symptoms/bionic,now 0.20 all [installed]
* apt/bionic-updates,now 1.6.11 amd64 [installed]
* apt-utils/bionic-updates,now 1.6.11 amd64 [installed]
* at/bionic,now 3.1.20-3.1ubuntu2 amd64 [installed]
* base-files/bionic-updates,now 10.1ubuntu2.4 amd64 [installed]
* base-passwd/bionic,now 3.5.44 amd64 [installed]
* bash/bionic-updates,now 4.4.18-2ubuntu1.1 amd64 [installed]
* bash-completion/bionic,now 1:2.8-1ubuntu1 all [installed]
* bc/bionic,now 1.07.1-2 amd64 [installed]
* bcache-tools/bionic,now 1.0.8-2build1 amd64 [installed]
* bind9-host/bionic-updates,bionic-security,now 1:9.11.3+dfsg-1ubuntu1.8 amd64 [installed]
* binutils/bionic-updates,bionic-security,now 2.30-21ubuntu1~18.04.2 amd64 [installed,automatic]
* binutils-common/bionic-updates,bionic-security,now 2.30-21ubuntu1~18.04.2 amd64 [installed,automatic]
* binutils-x86-64-linux-gnu/bionic-updates,bionic-security,now 2.30-21ubuntu1~18.04.2 amd64 [installed,automatic]
* bsdmainutils/bionic,now 11.1.2ubuntu1 amd64 [installed]
* bsdutils/bionic-updates,now 1:2.31.1-0.4ubuntu3.3 amd64 [installed]
* btrfs-progs/bionic,now 4.15.1-1build1 amd64 [installed]
* btrfs-tools/bionic,now 4.15.1-1build1 amd64 [installed]
* build-essential/bionic,now 12.4ubuntu1 amd64 [installed,automatic]
* busybox-initramfs/bionic-updates,bionic-security,now 1:1.27.2-2ubuntu3.2 amd64 [installed]
* busybox-static/bionic-updates,bionic-security,now 1:1.27.2-2ubuntu3.2 amd64 [installed]
* byobu/bionic,now 5.125-0ubuntu1 all [installed]
* bzip2/bionic-updates,bionic-security,now 1.0.6-8.1ubuntu0.1 amd64 [installed]
* ca-certificates/bionic,bionic-updates,now 20180409 all [installed]
* cloud-guest-utils/bionic,now 0.30-0ubuntu5 all [installed]
* cloud-init/bionic-updates,now 19.1-1-gbaa47854-0ubuntu1~18.04.1 all [installed]
* cloud-initramfs-copymods/bionic-updates,now 0.40ubuntu1.1 all [installed]
* cloud-initramfs-dyn-netconf/bionic-updates,now 0.40ubuntu1.1 all [installed]
* command-not-found/bionic-updates,now 18.04.5 all [installed]
* command-not-found-data/bionic-updates,now 18.04.5 amd64 [installed]
* console-setup/bionic-updates,now 1.178ubuntu2.9 all [installed]
* console-setup-linux/bionic-updates,now 1.178ubuntu2.9 all [installed]
* coreutils/bionic,now 8.28-1ubuntu1 amd64 [installed]
* cpio/bionic,now 2.12+dfsg-6 amd64 [installed]
* cpp/bionic-updates,bionic-security,now 4:7.4.0-1ubuntu2.3 amd64 [installed,automatic]
* cpp-7/bionic-updates,bionic-security,now 7.4.0-1ubuntu1~18.04.1 amd64 [installed,automatic]
* cron/bionic,now 3.0pl1-128.1ubuntu1 amd64 [installed]
* cryptsetup/bionic-updates,now 2:2.0.2-1ubuntu1.1 amd64 [installed]
* cryptsetup-bin/bionic-updates,now 2:2.0.2-1ubuntu1.1 amd64 [installed]
* curl/bionic-updates,bionic-security,now 7.58.0-2ubuntu3.7 amd64 [installed]
* dash/bionic,now 0.5.8-2.10 amd64 [installed]
* dbus/bionic-updates,bionic-security,now 1.12.2-1ubuntu1.1 amd64 [installed]
* debconf/bionic-updates,now 1.5.66ubuntu1 all [installed]
* debconf-i18n/bionic-updates,now 1.5.66ubuntu1 all [installed]
* debianutils/bionic,now 4.8.4 amd64 [installed]
* diffutils/bionic,now 1:3.6-1 amd64 [installed]
* dirmngr/bionic-updates,bionic-security,now 2.2.4-1ubuntu1.2 amd64 [installed]
* distro-info-data/bionic-updates,bionic-security,now 0.37ubuntu0.5 all [installed]
* dmeventd/bionic,now 2:1.02.145-4.1ubuntu3 amd64 [installed]
* dmidecode/bionic,now 3.1-1 amd64 [installed]
* dmsetup/bionic,now 2:1.02.145-4.1ubuntu3 amd64 [installed]
* dns-root-data/bionic,now 2018013001 all [installed]
* dnsmasq-base/bionic,now 2.79-1 amd64 [installed]
* dnsutils/bionic-updates,bionic-security,now 1:9.11.3+dfsg-1ubuntu1.8 amd64 [installed]
* dosfstools/bionic,now 4.1-1 amd64 [installed]
* dpkg/bionic-updates,now 1.19.0.5ubuntu2.1 amd64 [installed]
* dpkg-dev/bionic-updates,now 1.19.0.5ubuntu2.1 all [installed,automatic]
* e2fsprogs/bionic-updates,now 1.44.1-1ubuntu1.1 amd64 [installed]
* eatmydata/bionic,now 105-6 all [installed]
* ebtables/bionic-updates,now 2.0.10.4-3.5ubuntu2.18.04.3 amd64 [installed]
* ed/bionic,now 1.10-2.1 amd64 [installed]
* eject/bionic,now 2.1.5+deb1+cvs20081104-13.2 amd64 [installed]
* ethtool/bionic,now 1:4.15-0ubuntu1 amd64 [installed]
* fakeroot/bionic,now 1.22-2ubuntu1 amd64 [installed,automatic]
* fdisk/bionic-updates,now 2.31.1-0.4ubuntu3.3 amd64 [installed]
* file/bionic-updates,bionic-security,now 1:5.32-2ubuntu0.2 amd64 [installed]
* findutils/bionic,now 4.6.0+git+20170828-2 amd64 [installed]
* finger/bionic,now 0.17-15.1 amd64 [installed]
* fonts-ubuntu-console/bionic,now 0.83-2 all [installed]
* friendly-recovery/bionic-updates,now 0.2.38ubuntu1 all [installed]
* ftp/bionic,now 0.17-34 amd64 [installed]
* fuse/bionic,now 2.9.7-1ubuntu1 amd64 [installed]
* g++/bionic-updates,bionic-security,now 4:7.4.0-1ubuntu2.3 amd64 [installed,automatic]
* g++-7/bionic-updates,bionic-security,now 7.4.0-1ubuntu1~18.04.1 amd64 [installed,automatic]
* gawk/bionic,now 1:4.1.4+dfsg-1build1 amd64 [installed]
* gcc/bionic-updates,bionic-security,now 4:7.4.0-1ubuntu2.3 amd64 [installed,automatic]
* gcc-7/bionic-updates,bionic-security,now 7.4.0-1ubuntu1~18.04.1 amd64 [installed,automatic]
* gcc-7-base/bionic-updates,bionic-security,now 7.4.0-1ubuntu1~18.04.1 amd64 [installed,automatic]
* gcc-8-base/bionic-updates,bionic-security,now 8.3.0-6ubuntu1~18.04.1 amd64 [installed]
* gdisk/bionic,now 1.0.3-1 amd64 [installed]
* geoip-database/bionic,now 20180315-1 all [installed]
* gettext-base/bionic-updates,bionic-security,now 0.19.8.1-6ubuntu0.3 amd64 [installed]
* gir1.2-glib-2.0/bionic,now 1.56.1-1 amd64 [installed]
* git/bionic-updates,bionic-security,now 1:2.17.1-1ubuntu0.4 amd64 [installed]
* git-man/bionic-updates,bionic-security,now 1:2.17.1-1ubuntu0.4 all [installed]
* gnupg/bionic-updates,bionic-security,now 2.2.4-1ubuntu1.2 amd64 [installed]
* gnupg-l10n/bionic-updates,bionic-security,now 2.2.4-1ubuntu1.2 all [installed]
* gnupg-utils/bionic-updates,bionic-security,now 2.2.4-1ubuntu1.2 amd64 [installed]
* gpg/bionic-updates,bionic-security,now 2.2.4-1ubuntu1.2 amd64 [installed]
* gpg-agent/bionic-updates,bionic-security,now 2.2.4-1ubuntu1.2 amd64 [installed]
* gpg-wks-client/bionic-updates,bionic-security,now 2.2.4-1ubuntu1.2 amd64 [installed]
* gpg-wks-server/bionic-updates,bionic-security,now 2.2.4-1ubuntu1.2 amd64 [installed]
* gpgconf/bionic-updates,bionic-security,now 2.2.4-1ubuntu1.2 amd64 [installed]
* gpgsm/bionic-updates,bionic-security,now 2.2.4-1ubuntu1.2 amd64 [installed]
* gpgv/bionic-updates,bionic-security,now 2.2.4-1ubuntu1.2 amd64 [installed]
* grep/bionic,now 3.1-2 amd64 [installed]
* groff-base/bionic,now 1.22.3-10 amd64 [installed]
* grub-common/bionic-updates,now 2.02-2ubuntu8.13 amd64 [installed,automatic]
* grub-gfxpayload-lists/bionic,now 0.7 amd64 [installed,automatic]
* grub-legacy-ec2/bionic,now 1:1 all [installed]
* grub-pc/bionic-updates,now 2.02-2ubuntu8.13 amd64 [installed,automatic]
* grub-pc-bin/bionic-updates,now 2.02-2ubuntu8.13 amd64 [installed,automatic]
* grub2-common/bionic-updates,now 2.02-2ubuntu8.13 amd64 [installed,automatic]
* gzip/bionic,now 1.6-5ubuntu1 amd64 [installed]
* hdparm/bionic,now 9.54+ds-1 amd64 [installed]
* hibagent/bionic,now 1.0.1-0ubuntu1 all [installed]
* hostname/bionic,now 3.20 amd64 [installed]
* htop/bionic,now 2.1.0-3 amd64 [installed]
* info/bionic,now 6.5.0.dfsg.1-2 amd64 [installed]
* init/bionic,now 1.51 amd64 [installed]
* init-system-helpers/bionic,now 1.51 all [installed]
* initramfs-tools/bionic-updates,now 0.130ubuntu3.8 all [installed]
* initramfs-tools-bin/bionic-updates,now 0.130ubuntu3.8 amd64 [installed]
* initramfs-tools-core/bionic-updates,now 0.130ubuntu3.8 all [installed]
* install-info/bionic,now 6.5.0.dfsg.1-2 amd64 [installed]
* iproute2/bionic,now 4.15.0-2ubuntu1 amd64 [installed]
* iptables/bionic,now 1.6.1-2ubuntu2 amd64 [installed]
* iputils-ping/bionic,now 3:20161105-1ubuntu2 amd64 [installed]
* iputils-tracepath/bionic,now 3:20161105-1ubuntu2 amd64 [installed]
* irqbalance/bionic-updates,now 1.3.0-0.1ubuntu0.18.04.1 amd64 [installed]
* isc-dhcp-client/bionic-updates,bionic-security,now 4.3.5-3ubuntu7.1 amd64 [installed]
* isc-dhcp-common/bionic-updates,bionic-security,now 4.3.5-3ubuntu7.1 amd64 [installed]
* iso-codes/bionic,now 3.79-1 all [installed]
* kbd/bionic,now 2.0.4-2ubuntu1 amd64 [installed]
* keyboard-configuration/bionic-updates,now 1.178ubuntu2.9 all [installed]
* klibc-utils/bionic,now 2.0.4-9ubuntu2 amd64 [installed]
* kmod/bionic-updates,now 24-1ubuntu3.2 amd64 [installed]
* krb5-locales/bionic-updates,bionic-security,now 1.16-2ubuntu0.1 all [installed]
* landscape-common/bionic-updates,now 18.01-0ubuntu3.3 amd64 [installed]
* language-selector-common/bionic-updates,now 0.188.2 all [installed]
* less/bionic,now 487-0.1 amd64 [installed]
* libaccountsservice0/bionic,now 0.6.45-1ubuntu1 amd64 [installed]
* libacl1/bionic,now 2.2.52-3build1 amd64 [installed]
* libalgorithm-diff-perl/bionic,now 1.19.03-1 all [installed,automatic]
* libalgorithm-diff-xs-perl/bionic,now 0.04-5 amd64 [installed,automatic]
* libalgorithm-merge-perl/bionic,now 0.08-3 all [installed,automatic]
* libapache2-mod-wsgi/bionic,now 4.5.17-1 amd64 [installed]
* libapparmor1/bionic-updates,bionic-security,now 2.12-4ubuntu5.1 amd64 [installed]
* libapr1/bionic,now 1.6.3-2 amd64 [installed,automatic]
* libaprutil1/bionic,now 1.6.1-2 amd64 [installed,automatic]
* libaprutil1-dbd-sqlite3/bionic,now 1.6.1-2 amd64 [installed,automatic]
* libaprutil1-ldap/bionic,now 1.6.1-2 amd64 [installed,automatic]
* libapt-inst2.0/bionic-updates,now 1.6.11 amd64 [installed]
* libapt-pkg5.0/bionic-updates,now 1.6.11 amd64 [installed]
* libargon2-0/bionic,now 0~20161029-1.1 amd64 [installed]
* libasan4/bionic-updates,bionic-security,now 7.4.0-1ubuntu1~18.04.1 amd64 [installed,automatic]
* libasn1-8-heimdal/bionic,now 7.5.0+dfsg-1 amd64 [installed]
* libassuan0/bionic,now 2.5.1-2 amd64 [installed]
* libatm1/bionic,now 1:2.5.1-2build1 amd64 [installed]
* libatomic1/bionic-updates,bionic-security,now 8.3.0-6ubuntu1~18.04.1 amd64 [installed,automatic]
* libattr1/bionic,now 1:2.4.47-2build1 amd64 [installed]
* libaudit-common/bionic,now 1:2.8.2-1ubuntu1 all [installed]
* libaudit1/bionic,now 1:2.8.2-1ubuntu1 amd64 [installed]
* libbind9-160/bionic-updates,bionic-security,now 1:9.11.3+dfsg-1ubuntu1.8 amd64 [installed]
* libbinutils/bionic-updates,bionic-security,now 2.30-21ubuntu1~18.04.2 amd64 [installed,automatic]
* libblkid1/bionic-updates,now 2.31.1-0.4ubuntu3.3 amd64 [installed]
* libbsd0/bionic,now 0.8.7-1 amd64 [installed]
* libbz2-1.0/bionic-updates,bionic-security,now 1.0.6-8.1ubuntu0.1 amd64 [installed]
* libc-bin/bionic,now 2.27-3ubuntu1 amd64 [installed]
* libc-dev-bin/bionic,now 2.27-3ubuntu1 amd64 [installed,automatic]
* libc6/bionic,now 2.27-3ubuntu1 amd64 [installed]
* libc6-dev/bionic,now 2.27-3ubuntu1 amd64 [installed,automatic]
* libcap-ng0/bionic,now 0.7.7-3.1 amd64 [installed]
* libcap2/bionic,now 1:2.25-1.2 amd64 [installed]
* libcap2-bin/bionic,now 1:2.25-1.2 amd64 [installed]
* libcc1-0/bionic-updates,bionic-security,now 8.3.0-6ubuntu1~18.04.1 amd64 [installed,automatic]
* libcilkrts5/bionic-updates,bionic-security,now 7.4.0-1ubuntu1~18.04.1 amd64 [installed,automatic]
* libcom-err2/bionic-updates,now 1.44.1-1ubuntu1.1 amd64 [installed]
* libcryptsetup12/bionic-updates,now 2:2.0.2-1ubuntu1.1 amd64 [installed]
* libcurl3-gnutls/bionic-updates,bionic-security,now 7.58.0-2ubuntu3.7 amd64 [installed]
* libcurl4/bionic-updates,bionic-security,now 7.58.0-2ubuntu3.7 amd64 [installed]
* libdb5.3/bionic-updates,bionic-security,now 5.3.28-13.1ubuntu1.1 amd64 [installed]
* libdbus-1-3/bionic-updates,bionic-security,now 1.12.2-1ubuntu1.1 amd64 [installed]
* libdebconfclient0/bionic,now 0.213ubuntu1 amd64 [installed]
* libdevmapper-event1.02.1/bionic,now 2:1.02.145-4.1ubuntu3 amd64 [installed]
* libdevmapper1.02.1/bionic,now 2:1.02.145-4.1ubuntu3 amd64 [installed]
* libdns-export1100/bionic-updates,bionic-security,now 1:9.11.3+dfsg-1ubuntu1.8 amd64 [installed]
* libdns1100/bionic-updates,bionic-security,now 1:9.11.3+dfsg-1ubuntu1.8 amd64 [installed]
* libdpkg-perl/bionic-updates,now 1.19.0.5ubuntu2.1 all [installed,automatic]
* libdrm-common/bionic-updates,now 2.4.97-1ubuntu1~18.04.1 all [installed]
* libdrm2/bionic-updates,now 2.4.97-1ubuntu1~18.04.1 amd64 [installed]
* libdumbnet1/bionic,now 1.12-7build1 amd64 [installed]
* libeatmydata1/bionic,now 105-6 amd64 [installed]
* libedit2/bionic,now 3.1-20170329-1 amd64 [installed]
* libelf1/bionic-updates,bionic-security,now 0.170-0.4ubuntu0.1 amd64 [installed]
* liberror-perl/bionic,now 0.17025-1 all [installed]
* libestr0/bionic,now 0.1.10-2.1 amd64 [installed]
* libevent-2.1-6/bionic,now 2.1.8-stable-4build1 amd64 [installed]
* libexpat1/bionic-updates,bionic-security,now 2.2.5-3ubuntu0.1 amd64 [installed]
* libexpat1-dev/bionic-updates,bionic-security,now 2.2.5-3ubuntu0.1 amd64 [installed,automatic]
* libext2fs2/bionic-updates,now 1.44.1-1ubuntu1.1 amd64 [installed]
* libfakeroot/bionic,now 1.22-2ubuntu1 amd64 [installed,automatic]
* libfastjson4/bionic,now 0.99.8-2 amd64 [installed]
* libfdisk1/bionic-updates,now 2.31.1-0.4ubuntu3.3 amd64 [installed]
* libffi6/bionic,now 3.2.1-8 amd64 [installed]
* libfile-fcntllock-perl/bionic,now 0.22-3build2 amd64 [installed,automatic]
* libfreetype6/bionic,now 2.8.1-2ubuntu2 amd64 [installed,automatic]
* libfribidi0/bionic,now 0.19.7-2 amd64 [installed]
* libfuse2/bionic,now 2.9.7-1ubuntu1 amd64 [installed]
* libgcc-7-dev/bionic-updates,bionic-security,now 7.4.0-1ubuntu1~18.04.1 amd64 [installed,automatic]
* libgcc1/bionic-updates,bionic-security,now 1:8.3.0-6ubuntu1~18.04.1 amd64 [installed]
* libgcrypt20/bionic-updates,bionic-security,now 1.8.1-4ubuntu1.1 amd64 [installed]
* libgdbm-compat4/bionic,now 1.14.1-6 amd64 [installed]
* libgdbm5/bionic,now 1.14.1-6 amd64 [installed]
* libgeoip1/bionic,now 1.6.12-1 amd64 [installed]
* libgirepository-1.0-1/bionic,now 1.56.1-1 amd64 [installed]
* libglib2.0-0/bionic-updates,bionic-security,now 2.56.4-0ubuntu0.18.04.3 amd64 [installed]
* libglib2.0-data/bionic-updates,bionic-security,now 2.56.4-0ubuntu0.18.04.3 all [installed]
* libgmp10/bionic,now 2:6.1.2+dfsg-2 amd64 [installed]
* libgnutls30/bionic-updates,bionic-security,now 3.5.18-1ubuntu1.1 amd64 [installed]
* libgomp1/bionic-updates,bionic-security,now 8.3.0-6ubuntu1~18.04.1 amd64 [installed,automatic]
* libgpg-error0/bionic,now 1.27-6 amd64 [installed]
* libgpm2/bionic,now 1.20.7-5 amd64 [installed]
* libgssapi-krb5-2/bionic-updates,bionic-security,now 1.16-2ubuntu0.1 amd64 [installed]
* libgssapi3-heimdal/bionic,now 7.5.0+dfsg-1 amd64 [installed]
* libhcrypto4-heimdal/bionic,now 7.5.0+dfsg-1 amd64 [installed]
* libheimbase1-heimdal/bionic,now 7.5.0+dfsg-1 amd64 [installed]
* libheimntlm0-heimdal/bionic,now 7.5.0+dfsg-1 amd64 [installed]
* libhogweed4/bionic,now 3.4-1 amd64 [installed]
* libhx509-5-heimdal/bionic,now 7.5.0+dfsg-1 amd64 [installed]
* libicu60/bionic,now 60.2-3ubuntu3 amd64 [installed]
* libidn11/bionic-updates,now 1.33-2.1ubuntu1.2 amd64 [installed]
* libidn2-0/bionic,now 2.0.4-1.1build2 amd64 [installed]
* libip4tc0/bionic,now 1.6.1-2ubuntu2 amd64 [installed]
* libip6tc0/bionic,now 1.6.1-2ubuntu2 amd64 [installed]
* libiptc0/bionic,now 1.6.1-2ubuntu2 amd64 [installed]
* libirs160/bionic-updates,bionic-security,now 1:9.11.3+dfsg-1ubuntu1.8 amd64 [installed]
* libisc-export169/bionic-updates,bionic-security,now 1:9.11.3+dfsg-1ubuntu1.8 amd64 [installed]
* libisc169/bionic-updates,bionic-security,now 1:9.11.3+dfsg-1ubuntu1.8 amd64 [installed]
* libisccc160/bionic-updates,bionic-security,now 1:9.11.3+dfsg-1ubuntu1.8 amd64 [installed]
* libisccfg160/bionic-updates,bionic-security,now 1:9.11.3+dfsg-1ubuntu1.8 amd64 [installed]
* libisl19/bionic,now 0.19-1 amd64 [installed,automatic]
* libisns0/bionic,now 0.97-2build1 amd64 [installed]
* libitm1/bionic-updates,bionic-security,now 8.3.0-6ubuntu1~18.04.1 amd64 [installed,automatic]
* libjson-c3/bionic,now 0.12.1-1.3 amd64 [installed]
* libk5crypto3/bionic-updates,bionic-security,now 1.16-2ubuntu0.1 amd64 [installed]
* libkeyutils1/bionic,now 1.5.9-9.2ubuntu2 amd64 [installed]
* libklibc/bionic,now 2.0.4-9ubuntu2 amd64 [installed]
* libkmod2/bionic-updates,now 24-1ubuntu3.2 amd64 [installed]
* libkrb5-26-heimdal/bionic,now 7.5.0+dfsg-1 amd64 [installed]
* libkrb5-3/bionic-updates,bionic-security,now 1.16-2ubuntu0.1 amd64 [installed]
* libkrb5support0/bionic-updates,bionic-security,now 1.16-2ubuntu0.1 amd64 [installed]
* libksba8/bionic,now 1.3.5-2 amd64 [installed]
* libldap-2.4-2/bionic-updates,now 2.4.45+dfsg-1ubuntu1.2 amd64 [installed]
* libldap-common/bionic-updates,now 2.4.45+dfsg-1ubuntu1.2 all [installed]
* liblocale-gettext-perl/bionic,now 1.07-3build2 amd64 [installed]
* liblsan0/bionic-updates,bionic-security,now 8.3.0-6ubuntu1~18.04.1 amd64 [installed,automatic]
* liblua5.2-0/bionic,now 5.2.4-1.1build1 amd64 [installed,automatic]
* liblvm2app2.2/bionic,now 2.02.176-4.1ubuntu3 amd64 [installed]
* liblvm2cmd2.02/bionic,now 2.02.176-4.1ubuntu3 amd64 [installed]
* liblwres160/bionic-updates,bionic-security,now 1:9.11.3+dfsg-1ubuntu1.8 amd64 [installed]
* liblxc-common/bionic-updates,now 3.0.3-0ubuntu1~18.04.1 amd64 [installed]
* liblxc1/bionic-updates,now 3.0.3-0ubuntu1~18.04.1 amd64 [installed]
* liblz4-1/bionic,now 0.0~r131-2ubuntu3 amd64 [installed]
* liblzma5/bionic,now 5.2.2-1.3 amd64 [installed]
* liblzo2-2/bionic,now 2.08-1.2 amd64 [installed]
* libmagic-mgc/bionic-updates,bionic-security,now 1:5.32-2ubuntu0.2 amd64 [installed]
* libmagic1/bionic-updates,bionic-security,now 1:5.32-2ubuntu0.2 amd64 [installed]
* libmnl0/bionic,now 1.0.4-2 amd64 [installed]
* libmount1/bionic-updates,now 2.31.1-0.4ubuntu3.3 amd64 [installed]
* libmpc3/bionic,now 1.1.0-1 amd64 [installed,automatic]
* libmpdec2/bionic,now 2.4.2-1ubuntu1 amd64 [installed]
* libmpfr6/bionic,now 4.0.1-1 amd64 [installed]
* libmpx2/bionic-updates,bionic-security,now 8.3.0-6ubuntu1~18.04.1 amd64 [installed,automatic]
* libmspack0/bionic-updates,bionic-security,now 0.6-3ubuntu0.2 amd64 [installed]
* libncurses5/bionic-updates,now 6.1-1ubuntu1.18.04 amd64 [installed]
* libncursesw5/bionic-updates,now 6.1-1ubuntu1.18.04 amd64 [installed]
* libnetfilter-conntrack3/bionic,now 1.0.6-2 amd64 [installed]
* libnettle6/bionic,now 3.4-1 amd64 [installed]
* libnewt0.52/bionic,now 0.52.20-1ubuntu1 amd64 [installed]
* libnfnetlink0/bionic,now 1.0.1-3 amd64 [installed]
* libnghttp2-14/bionic,now 1.30.0-1ubuntu1 amd64 [installed]
* libnih1/bionic,now 1.0.3-6ubuntu2 amd64 [installed]
* libnpth0/bionic,now 1.5-3 amd64 [installed]
* libnss-systemd/bionic-updates,now 237-3ubuntu10.24 amd64 [installed]
* libntfs-3g88/bionic-updates,bionic-security,now 1:2017.3.23-2ubuntu0.18.04.2 amd64 [installed]
* libnuma1/bionic-updates,now 2.0.11-2.1ubuntu0.1 amd64 [installed]
* libp11-kit0/bionic,now 0.23.9-2 amd64 [installed]
* libpam-cap/bionic,now 1:2.25-1.2 amd64 [installed]
* libpam-modules/bionic-updates,now 1.1.8-3.6ubuntu2.18.04.1 amd64 [installed]
* libpam-modules-bin/bionic-updates,now 1.1.8-3.6ubuntu2.18.04.1 amd64 [installed]
* libpam-runtime/bionic-updates,now 1.1.8-3.6ubuntu2.18.04.1 all [installed]
* libpam-systemd/bionic-updates,now 237-3ubuntu10.24 amd64 [installed]
* libpam0g/bionic-updates,now 1.1.8-3.6ubuntu2.18.04.1 amd64 [installed]
* libparted2/bionic-updates,now 3.2-20ubuntu0.2 amd64 [installed]
* libpcap0.8/bionic,now 1.8.1-6ubuntu1 amd64 [installed]
* libpci3/bionic-updates,now 1:3.5.2-1ubuntu1.1 amd64 [installed]
* libpcre3/bionic,now 2:8.39-9 amd64 [installed]
* libperl5.26/bionic-updates,bionic-security,now 5.26.1-6ubuntu0.3 amd64 [installed]
* libpipeline1/bionic,now 1.5.0-1 amd64 [installed]
* libplymouth4/bionic-updates,now 0.9.3-1ubuntu7.18.04.2 amd64 [installed]
* libpng16-16/bionic-updates,bionic-security,now 1.6.34-1ubuntu0.18.04.2 amd64 [installed]
* libpolkit-agent-1-0/bionic-updates,bionic-security,now 0.105-20ubuntu0.18.04.5 amd64 [installed]
* libpolkit-backend-1-0/bionic-updates,bionic-security,now 0.105-20ubuntu0.18.04.5 amd64 [installed]
* libpolkit-gobject-1-0/bionic-updates,bionic-security,now 0.105-20ubuntu0.18.04.5 amd64 [installed]
* libpopt0/bionic,now 1.16-11 amd64 [installed]
* libpq5/bionic-updates,bionic-security,now 10.9-0ubuntu0.18.04.1 amd64 [installed,automatic]
* libprocps6/bionic-updates,bionic-security,now 2:3.3.12-3ubuntu1.1 amd64 [installed]
* libpsl5/bionic,now 0.19.1-5build1 amd64 [installed]
* libpython-all-dev/bionic,now 2.7.15~rc1-1 amd64 [installed,automatic]
* libpython-dev/bionic,now 2.7.15~rc1-1 amd64 [installed,automatic]
* libpython-stdlib/bionic,now 2.7.15~rc1-1 amd64 [installed,automatic]
* libpython2.7/bionic-updates,now 2.7.15-4ubuntu4~18.04 amd64 [installed,automatic]
* libpython2.7-dev/bionic-updates,now 2.7.15-4ubuntu4~18.04 amd64 [installed,automatic]
* libpython2.7-minimal/bionic-updates,now 2.7.15-4ubuntu4~18.04 amd64 [installed,automatic]
* libpython2.7-stdlib/bionic-updates,now 2.7.15-4ubuntu4~18.04 amd64 [installed,automatic]
* libpython3-stdlib/bionic-updates,now 3.6.7-1~18.04 amd64 [installed]
* libpython3.6/bionic-updates,now 3.6.8-1~18.04.1 amd64 [installed]
* libpython3.6-minimal/bionic-updates,now 3.6.8-1~18.04.1 amd64 [installed]
* libpython3.6-stdlib/bionic-updates,now 3.6.8-1~18.04.1 amd64 [installed]
* libquadmath0/bionic-updates,bionic-security,now 8.3.0-6ubuntu1~18.04.1 amd64 [installed,automatic]
* libreadline5/bionic,now 5.2+dfsg-3build1 amd64 [installed]
* libreadline7/bionic,now 7.0-3 amd64 [installed]
* libroken18-heimdal/bionic,now 7.5.0+dfsg-1 amd64 [installed]
* librtmp1/bionic,now 2.4+20151223.gitfa8646d.1-1 amd64 [installed]
* libsasl2-2/bionic,now 2.1.27~101-g0780600+dfsg-3ubuntu2 amd64 [installed]
* libsasl2-modules/bionic,now 2.1.27~101-g0780600+dfsg-3ubuntu2 amd64 [installed]
* libsasl2-modules-db/bionic,now 2.1.27~101-g0780600+dfsg-3ubuntu2 amd64 [installed]
* libseccomp2/bionic-updates,bionic-security,now 2.4.1-0ubuntu0.18.04.2 amd64 [installed]
* libselinux1/bionic,now 2.7-2build2 amd64 [installed]
* libsemanage-common/bionic,now 2.7-2build2 all [installed]
* libsemanage1/bionic,now 2.7-2build2 amd64 [installed]
* libsensors4/bionic,now 1:3.4.0-4 amd64 [installed,automatic]
* libsepol1/bionic,now 2.7-1 amd64 [installed]
* libsigsegv2/bionic,now 2.12-1 amd64 [installed]
* libslang2/bionic,now 2.3.1a-3ubuntu1 amd64 [installed]
* libsmartcols1/bionic-updates,now 2.31.1-0.4ubuntu3.3 amd64 [installed]
* libsqlite3-0/bionic-updates,bionic-security,now 3.22.0-1ubuntu0.1 amd64 [installed]
* libss2/bionic-updates,now 1.44.1-1ubuntu1.1 amd64 [installed]
* libssl1.0.0/bionic-updates,bionic-security,now 1.0.2n-1ubuntu5.3 amd64 [installed]
* libssl1.1/bionic-updates,now 1.1.1-1ubuntu2.1~18.04.3 amd64 [installed]
* libstdc++-7-dev/bionic-updates,bionic-security,now 7.4.0-1ubuntu1~18.04.1 amd64 [installed,automatic]
* libstdc++6/bionic-updates,bionic-security,now 8.3.0-6ubuntu1~18.04.1 amd64 [installed]
* libsystemd0/bionic-updates,now 237-3ubuntu10.24 amd64 [installed]
* libtasn1-6/bionic,now 4.13-2 amd64 [installed]
* libtext-charwidth-perl/bionic,now 0.04-7.1 amd64 [installed]
* libtext-iconv-perl/bionic,now 1.7-5build6 amd64 [installed]
* libtext-wrapi18n-perl/bionic,now 0.06-7.1 all [installed]
* libtinfo5/bionic-updates,now 6.1-1ubuntu1.18.04 amd64 [installed]
* libtsan0/bionic-updates,bionic-security,now 8.3.0-6ubuntu1~18.04.1 amd64 [installed,automatic]
* libubsan0/bionic-updates,bionic-security,now 7.4.0-1ubuntu1~18.04.1 amd64 [installed,automatic]
* libudev1/bionic-updates,now 237-3ubuntu10.24 amd64 [installed]
* libunistring2/bionic-updates,now 0.9.9-0ubuntu2 amd64 [installed]
* libunwind8/bionic,now 1.2.1-8 amd64 [installed]
* libusb-1.0-0/bionic,now 2:1.0.21-2 amd64 [installed]
* libutempter0/bionic,now 1.1.6-3 amd64 [installed]
* libuuid1/bionic-updates,now 2.31.1-0.4ubuntu3.3 amd64 [installed]
* libwind0-heimdal/bionic,now 7.5.0+dfsg-1 amd64 [installed]
* libwrap0/bionic,now 7.6.q-27 amd64 [installed]
* libx11-6/bionic-updates,now 2:1.6.4-3ubuntu0.2 amd64 [installed]
* libx11-data/bionic-updates,now 2:1.6.4-3ubuntu0.2 all [installed]
* libxau6/bionic,now 1:1.0.8-1 amd64 [installed]
* libxcb1/bionic-updates,now 1.13-2~ubuntu18.04 amd64 [installed]
* libxdmcp6/bionic,now 1:1.1.2-3 amd64 [installed]
* libxext6/bionic,now 2:1.3.3-1 amd64 [installed]
* libxml2/bionic-updates,bionic-security,now 2.9.4+dfsg1-6.1ubuntu1.2 amd64 [installed]
* libxmlsec1/bionic,now 1.2.25-1build1 amd64 [installed]
* libxmlsec1-openssl/bionic,now 1.2.25-1build1 amd64 [installed]
* libxmuu1/bionic,now 2:1.1.2-2 amd64 [installed]
* libxslt1.1/bionic-updates,bionic-security,now 1.1.29-5ubuntu0.1 amd64 [installed]
* libxtables12/bionic,now 1.6.1-2ubuntu2 amd64 [installed]
* libyaml-0-2/bionic,now 0.1.7-2ubuntu3 amd64 [installed]
* libzstd1/bionic,now 1.3.3+dfsg-2ubuntu1 amd64 [installed]
* linux-aws/bionic-updates,bionic-security,now 4.15.0.1043.42 amd64 [installed]
* linux-aws-headers-4.15.0-1021/bionic-updates,bionic-security,now 4.15.0-1021.21 all [installed]
* linux-aws-headers-4.15.0-1041/bionic-updates,bionic-security,now 4.15.0-1041.43 all [installed,automatic]
* linux-aws-headers-4.15.0-1043/bionic-updates,bionic-security,now 4.15.0-1043.45 all [installed,automatic]
* linux-base/bionic,now 4.5ubuntu1 all [installed]
* linux-headers-4.15.0-1021-aws/bionic-updates,bionic-security,now 4.15.0-1021.21 amd64 [installed]
* linux-headers-4.15.0-1041-aws/bionic-updates,bionic-security,now 4.15.0-1041.43 amd64 [installed,automatic]
* linux-headers-4.15.0-1043-aws/bionic-updates,bionic-security,now 4.15.0-1043.45 amd64 [installed,automatic]
* linux-headers-aws/bionic-updates,bionic-security,now 4.15.0.1043.42 amd64 [installed]
* linux-image-4.15.0-1021-aws/bionic-updates,bionic-security,now 4.15.0-1021.21 amd64 [installed]
* linux-image-4.15.0-1041-aws/bionic-updates,bionic-security,now 4.15.0-1041.43 amd64 [installed,automatic]
* linux-image-4.15.0-1043-aws/bionic-updates,bionic-security,now 4.15.0-1043.45 amd64 [installed,automatic]
* linux-image-aws/bionic-updates,bionic-security,now 4.15.0.1043.42 amd64 [installed]
* linux-libc-dev/bionic-updates,bionic-security,now 4.15.0-54.58 amd64 [installed,automatic]
* linux-modules-4.15.0-1021-aws/bionic-updates,bionic-security,now 4.15.0-1021.21 amd64 [installed]
* linux-modules-4.15.0-1041-aws/bionic-updates,bionic-security,now 4.15.0-1041.43 amd64 [installed,automatic]
* linux-modules-4.15.0-1043-aws/bionic-updates,bionic-security,now 4.15.0-1043.45 amd64 [installed,automatic]
* locales/bionic,now 2.27-3ubuntu1 all [installed]
* login/bionic-updates,now 1:4.5-1ubuntu2 amd64 [installed]
* logrotate/bionic,now 3.11.0-0.1ubuntu1 amd64 [installed]
* lsb-base/bionic,now 9.20170808ubuntu1 all [installed]
* lsb-release/bionic,now 9.20170808ubuntu1 all [installed]
* lshw/bionic-updates,now 02.18-0.1ubuntu6.18.04.1 amd64 [installed]
* lsof/bionic,now 4.89+dfsg-0.1 amd64 [installed]
* ltrace/bionic,now 0.7.3-6ubuntu1 amd64 [installed]
* lvm2/bionic,now 2.02.176-4.1ubuntu3 amd64 [installed]
* lxcfs/bionic-updates,now 3.0.3-0ubuntu1~18.04.1 amd64 [installed]
* lxd/now 3.0.1-0ubuntu1~18.04.1 amd64 [installed,upgradable to: 3.0.3-0ubuntu1~18.04.1]
* lxd-client/now 3.0.1-0ubuntu1~18.04.1 amd64 [installed,upgradable to: 3.0.3-0ubuntu1~18.04.1]
* make/bionic,now 4.1-9.1ubuntu1 amd64 [installed,automatic]
* man-db/bionic-updates,now 2.8.3-2ubuntu0.1 amd64 [installed]
* manpages/bionic,now 4.15-1 all [installed]
* manpages-dev/bionic,now 4.15-1 all [installed,automatic]
* mawk/bionic,now 1.3.3-17ubuntu3 amd64 [installed]
* mdadm/bionic-updates,now 4.1~rc1-3~ubuntu18.04.2 amd64 [installed]
* mime-support/bionic,now 3.60ubuntu1 all [installed]
* mlocate/bionic,now 0.26-2ubuntu3.1 amd64 [installed]
* mount/bionic-updates,now 2.31.1-0.4ubuntu3.3 amd64 [installed]
* mtr-tiny/bionic,now 0.92-1 amd64 [installed]
* multiarch-support/bionic,now 2.27-3ubuntu1 amd64 [installed]
* nano/bionic,now 2.9.3-2 amd64 [installed]
* ncurses-base/bionic-updates,now 6.1-1ubuntu1.18.04 all [installed]
* ncurses-bin/bionic-updates,now 6.1-1ubuntu1.18.04 amd64 [installed]
* ncurses-term/bionic-updates,now 6.1-1ubuntu1.18.04 all [installed]
* net-tools/bionic,now 1.60+git20161116.90da8a0-1ubuntu1 amd64 [installed]
* netbase/bionic,now 5.4 all [installed]
* netcat-openbsd/bionic-updates,now 1.187-1ubuntu0.1 amd64 [installed]
* netplan.io/bionic-updates,now 0.97-0ubuntu1~18.04.1 amd64 [installed]
* networkd-dispatcher/bionic-updates,now 1.7-0ubuntu3.3 all [installed]
* nplan/bionic-updates,now 0.97-0ubuntu1~18.04.1 all [installed]
* ntfs-3g/bionic-updates,bionic-security,now 1:2017.3.23-2ubuntu0.18.04.2 amd64 [installed]
* open-iscsi/bionic-updates,now 2.0.874-5ubuntu2.7 amd64 [installed]
* open-vm-tools/bionic-updates,now 2:10.3.10-1~ubuntu0.18.04.1 amd64 [installed]
* openssh-client/bionic-updates,bionic-security,now 1:7.6p1-4ubuntu0.3 amd64 [installed]
* openssh-server/bionic-updates,bionic-security,now 1:7.6p1-4ubuntu0.3 amd64 [installed]
* openssh-sftp-server/bionic-updates,bionic-security,now 1:7.6p1-4ubuntu0.3 amd64 [installed]
* openssl/bionic-updates,now 1.1.1-1ubuntu2.1~18.04.3 amd64 [installed]
* os-prober/bionic,now 1.74ubuntu1 amd64 [installed,automatic]
* overlayroot/bionic-updates,now 0.40ubuntu1.1 all [installed]
* parted/bionic-updates,now 3.2-20ubuntu0.2 amd64 [installed]
* passwd/bionic-updates,now 1:4.5-1ubuntu2 amd64 [installed]
* pastebinit/bionic,now 1.5-2 all [installed]
* patch/bionic,now 2.7.6-2ubuntu1 amd64 [installed]
* pciutils/bionic-updates,now 1:3.5.2-1ubuntu1.1 amd64 [installed]
* perl/bionic-updates,bionic-security,now 5.26.1-6ubuntu0.3 amd64 [installed]
* perl-base/bionic-updates,bionic-security,now 5.26.1-6ubuntu0.3 amd64 [installed]
* perl-modules-5.26/bionic-updates,bionic-security,now 5.26.1-6ubuntu0.3 all [installed]
* pinentry-curses/bionic,now 1.1.0-1 amd64 [installed]
* plymouth/bionic-updates,now 0.9.3-1ubuntu7.18.04.2 amd64 [installed]
* plymouth-theme-ubuntu-text/bionic-updates,now 0.9.3-1ubuntu7.18.04.2 amd64 [installed]
* policykit-1/bionic-updates,bionic-security,now 0.105-20ubuntu0.18.04.5 amd64 [installed]
* pollinate/bionic-updates,now 4.33-0ubuntu1~18.04.1 all [installed]
* popularity-contest/bionic,now 1.66ubuntu1 all [installed]
* postgresql/bionic,now 10+190 all [installed]
* postgresql-10/bionic-updates,bionic-security,now 10.9-0ubuntu0.18.04.1 amd64 [installed,automatic]
* postgresql-client-10/bionic-updates,bionic-security,now 10.9-0ubuntu0.18.04.1 amd64 [installed,automatic]
* postgresql-client-common/bionic,now 190 all [installed,automatic]
* postgresql-common/bionic,now 190 all [installed,automatic]
* postgresql-contrib/bionic,now 10+190 all [installed]
* powermgmt-base/bionic,now 1.33 all [installed]
* procps/bionic-updates,bionic-security,now 2:3.3.12-3ubuntu1.1 amd64 [installed]
* psmisc/bionic-updates,now 23.1-1ubuntu0.1 amd64 [installed]
* publicsuffix/bionic,now 20180223.1310-1 all [installed]
* python/bionic,now 2.7.15~rc1-1 amd64 [installed]
* python-all/bionic,now 2.7.15~rc1-1 amd64 [installed,automatic]
* python-all-dev/bionic,now 2.7.15~rc1-1 amd64 [installed,automatic]
* python-apt-common/bionic-updates,now 1.6.4 all [installed]
* python-asn1crypto/bionic,now 0.24.0-1 all [installed,automatic]
* python-cffi-backend/bionic,now 1.11.5-1 amd64 [installed,automatic]
* python-crypto/bionic,now 2.6.1-8ubuntu2 amd64 [installed,automatic]
* python-cryptography/bionic-updates,now 2.1.4-1ubuntu1.3 amd64 [installed,automatic]
* python-dbus/bionic,now 1.2.6-1 amd64 [installed,automatic]
* python-dev/bionic,now 2.7.15~rc1-1 amd64 [installed]
* python-egenix-mxdatetime/bionic,now 3.2.9-1 amd64 [installed,automatic]
* python-egenix-mxtools/bionic,now 3.2.9-1 amd64 [installed,automatic]
* python-enum34/bionic,now 1.1.6-2 all [installed,automatic]
* python-gi/bionic-updates,now 3.26.1-2ubuntu1 amd64 [installed,automatic]
* python-idna/bionic,now 2.6-1 all [installed,automatic]
* python-ipaddress/bionic,now 1.0.17-1 all [installed,automatic]
* python-keyring/bionic,now 10.6.0-1 all [installed,automatic]
* python-keyrings.alt/bionic,now 3.0-1 all [installed,automatic]
* python-minimal/bionic,now 2.7.15~rc1-1 amd64 [installed,automatic]
* python-pip/bionic-updates,now 9.0.1-2.3~ubuntu1.18.04.1 all [installed]
* python-pip-whl/bionic-updates,now 9.0.1-2.3~ubuntu1.18.04.1 all [installed,automatic]
* python-pkg-resources/bionic,now 39.0.1-2 all [installed,automatic]
* python-psycopg2/bionic,now 2.7.4-1 amd64 [installed]
* python-secretstorage/bionic,now 2.3.1-2 all [installed,automatic]
* python-setuptools/bionic,now 39.0.1-2 all [installed]
* python-six/bionic,now 1.11.0-2 all [installed,automatic]
* python-wheel/bionic,now 0.30.0-0.2 all [installed,automatic]
* python-xdg/bionic,now 0.25-4ubuntu1 all [installed,automatic]
* python2.7/bionic-updates,now 2.7.15-4ubuntu4~18.04 amd64 [installed,automatic]
* python2.7-dev/bionic-updates,now 2.7.15-4ubuntu4~18.04 amd64 [installed,automatic]
* python2.7-minimal/bionic-updates,now 2.7.15-4ubuntu4~18.04 amd64 [installed,automatic]
* python3/bionic-updates,now 3.6.7-1~18.04 amd64 [installed]
* python3-apport/bionic-updates,now 2.20.9-0ubuntu7.6 all [installed]
* python3-apt/bionic-updates,now 1.6.4 amd64 [installed]
* python3-asn1crypto/bionic,now 0.24.0-1 all [installed]
* python3-attr/bionic,now 17.4.0-2 all [installed]
* python3-automat/bionic,now 0.6.0-1 all [installed]
* python3-blinker/bionic,now 1.4+dfsg1-0.1 all [installed]
* python3-certifi/bionic,now 2018.1.18-2 all [installed]
* python3-cffi-backend/bionic,now 1.11.5-1 amd64 [installed]
* python3-chardet/bionic,now 3.0.4-1 all [installed]
* python3-click/bionic,now 6.7-3 all [installed]
* python3-colorama/bionic,now 0.3.7-1 all [installed]
* python3-commandnotfound/bionic-updates,now 18.04.5 all [installed]
* python3-configobj/bionic,now 5.0.6-2 all [installed]
* python3-constantly/bionic,now 15.1.0-1 all [installed]
* python3-cryptography/bionic-updates,now 2.1.4-1ubuntu1.3 amd64 [installed]
* python3-dbus/bionic,now 1.2.6-1 amd64 [installed]
* python3-debconf/bionic-updates,now 1.5.66ubuntu1 all [installed]
* python3-debian/bionic,now 0.1.32 all [installed]
* python3-distro-info/bionic-updates,now 0.18ubuntu0.18.04.1 all [installed]
* python3-distupgrade/bionic-updates,now 1:18.04.34 all [installed]
* python3-gdbm/bionic-updates,now 3.6.8-1~18.04 amd64 [installed]
* python3-gi/bionic-updates,now 3.26.1-2ubuntu1 amd64 [installed]
* python3-httplib2/bionic-updates,now 0.9.2+dfsg-1ubuntu0.1 all [installed]
* python3-hyperlink/bionic,now 17.3.1-2 all [installed]
* python3-idna/bionic,now 2.6-1 all [installed]
* python3-incremental/bionic,now 16.10.1-3 all [installed]
* python3-jinja2/bionic-updates,bionic-security,now 2.10-1ubuntu0.18.04.1 all [installed]
* python3-json-pointer/bionic,now 1.10-1 all [installed]
* python3-jsonpatch/bionic,now 1.19+really1.16-1fakesync1 all [installed]
* python3-jsonschema/bionic,now 2.6.0-2 all [installed]
* python3-jwt/bionic,now 1.5.3+ds1-1 all [installed]
* python3-markupsafe/bionic,now 1.0-1build1 amd64 [installed]
* python3-minimal/bionic-updates,now 3.6.7-1~18.04 amd64 [installed]
* python3-netifaces/bionic,now 0.10.4-0.1build4 amd64 [installed,automatic]
* python3-newt/bionic,now 0.52.20-1ubuntu1 amd64 [installed]
* python3-oauthlib/bionic,now 2.0.6-1 all [installed]
* python3-openssl/bionic,now 17.5.0-1ubuntu1 all [installed]
* python3-pam/bionic,now 0.4.2-13.2ubuntu4 amd64 [installed]
* python3-pkg-resources/bionic,now 39.0.1-2 all [installed]
* python3-problem-report/bionic-updates,now 2.20.9-0ubuntu7.6 all [installed]
* python3-pyasn1/bionic,now 0.4.2-3 all [installed]
* python3-pyasn1-modules/bionic,now 0.2.1-0.2 all [installed]
* python3-requests/bionic-updates,bionic-security,now 2.18.4-2ubuntu0.1 all [installed]
* python3-requests-unixsocket/bionic,now 0.1.5-3 all [installed]
* python3-serial/bionic,now 3.4-2 all [installed]
* python3-service-identity/bionic,now 16.0.0-2 all [installed]
* python3-six/bionic,now 1.11.0-2 all [installed]
* python3-software-properties/bionic-updates,now 0.96.24.32.9 all [installed]
* python3-systemd/bionic,now 234-1build1 amd64 [installed]
* python3-twisted/bionic,now 17.9.0-2 all [installed]
* python3-twisted-bin/bionic,now 17.9.0-2 amd64 [installed]
* python3-update-manager/bionic-updates,now 1:18.04.11.10 all [installed]
* python3-urllib3/bionic-updates,bionic-security,now 1.22-1ubuntu0.18.04.1 all [installed]
* python3-yaml/bionic,now 3.12-1build2 amd64 [installed]
* python3-zope.interface/bionic,now 4.3.2-1build2 amd64 [installed]
* python3.6/bionic-updates,now 3.6.8-1~18.04.1 amd64 [installed]
* python3.6-minimal/bionic-updates,now 3.6.8-1~18.04.1 amd64 [installed]
* readline-common/bionic,now 7.0-3 all [installed]
* rsync/bionic,now 3.1.2-2.1ubuntu1 amd64 [installed]
* rsyslog/bionic,now 8.32.0-1ubuntu4 amd64 [installed]
* run-one/bionic,now 1.17-0ubuntu1 all [installed]
* screen/bionic-updates,now 4.6.2-1ubuntu1 amd64 [installed]
* sed/bionic,now 4.4-2 amd64 [installed]
* sensible-utils/bionic,now 0.0.12 all [installed]
* shared-mime-info/bionic,now 1.9-2 amd64 [installed]
* snapd/bionic-updates,now 2.39.2+18.04 amd64 [installed]
* software-properties-common/bionic-updates,now 0.96.24.32.9 all [installed]
* sosreport/bionic-updates,now 3.6-1ubuntu0.18.04.2 amd64 [installed]
* squashfs-tools/bionic-updates,now 1:4.3-6ubuntu0.18.04.1 amd64 [installed]
* ssh-import-id/bionic-updates,now 5.7-0ubuntu1.1 all [installed]
* ssl-cert/bionic,now 1.0.39 all [installed,automatic]
* strace/bionic,now 4.21-1ubuntu1 amd64 [installed]
* sudo/bionic,now 1.8.21p2-3ubuntu1 amd64 [installed]
* sysstat/bionic,now 11.6.1-1 amd64 [installed,automatic]
* systemd/bionic-updates,now 237-3ubuntu10.24 amd64 [installed]
* systemd-sysv/bionic-updates,now 237-3ubuntu10.24 amd64 [installed]
* sysvinit-utils/bionic,now 2.88dsf-59.10ubuntu1 amd64 [installed]
* tar/bionic-updates,now 1.29b-2ubuntu0.1 amd64 [installed]
* tcpdump/bionic,now 4.9.2-3 amd64 [installed]
* telnet/bionic,now 0.17-41 amd64 [installed]
* time/bionic,now 1.7-25.1build1 amd64 [installed]
* tmux/bionic-updates,now 2.6-3ubuntu0.1 amd64 [installed]
* tzdata/bionic-updates,bionic-security,now 2019a-0ubuntu0.18.04 all [installed]
* ubuntu-advantage-tools/bionic,now 17 all [installed]
* ubuntu-keyring/bionic-updates,now 2018.09.18.1~18.04.0 all [installed]
* ubuntu-minimal/bionic-updates,now 1.417.1 amd64 [installed]
* ubuntu-release-upgrader-core/bionic-updates,now 1:18.04.34 all [installed]
* ubuntu-server/bionic-updates,now 1.417.1 amd64 [installed]
* ubuntu-standard/bionic-updates,now 1.417.1 amd64 [installed]
* ucf/bionic,now 3.0038 all [installed]
* udev/bionic-updates,now 237-3ubuntu10.24 amd64 [installed]
* ufw/bionic-updates,now 0.36-0ubuntu0.18.04.1 all [installed]
* uidmap/bionic-updates,now 1:4.5-1ubuntu2 amd64 [installed]
* unattended-upgrades/bionic-updates,now 1.1ubuntu1.18.04.11 all [installed]
* update-manager-core/bionic-updates,now 1:18.04.11.10 all [installed]
* update-notifier-common/bionic-updates,now 3.192.1.7 all [installed]
* ureadahead/bionic-updates,now 0.100.0-21 amd64 [installed]
* usbutils/bionic,now 1:007-4build1 amd64 [installed]
* util-linux/bionic-updates,now 2.31.1-0.4ubuntu3.3 amd64 [installed]
* uuid-runtime/bionic-updates,now 2.31.1-0.4ubuntu3.3 amd64 [installed]
* vim/bionic-updates,bionic-security,now 2:8.0.1453-1ubuntu1.1 amd64 [installed]
* vim-common/bionic-updates,bionic-security,now 2:8.0.1453-1ubuntu1.1 all [installed]
* vim-runtime/bionic-updates,bionic-security,now 2:8.0.1453-1ubuntu1.1 all [installed]
* vim-tiny/bionic-updates,bionic-security,now 2:8.0.1453-1ubuntu1.1 amd64 [installed]
* wget/bionic-updates,bionic-security,now 1.19.4-1ubuntu2.2 amd64 [installed]
* whiptail/bionic,now 0.52.20-1ubuntu1 amd64 [installed]
* xauth/bionic,now 1:1.0.10-1 amd64 [installed]
* xdelta3/bionic,now 3.0.11-dfsg-1ubuntu1 amd64 [installed]
* xdg-user-dirs/bionic,now 0.17-1ubuntu1 amd64 [installed]
* xfsprogs/bionic,now 4.9.0+nmu1ubuntu2 amd64 [installed]
* xkb-data/bionic,now 2.23.1-1ubuntu1 all [installed]
* xxd/bionic-updates,bionic-security,now 2:8.0.1453-1ubuntu1.1 amd64 [installed]
* xz-utils/bionic,now 5.2.2-1.3 amd64 [installed]
* zerofree/bionic,now 1.0.4-1 amd64 [installed]
<<<<<<< HEAD
* zlib1g/bionic,now 1:1.2.11.dfsg-0ubuntu2 amd64 [installed]
=======
* zlib1g/bionic,now 1:1.2.11.dfsg-0ubuntu2 amd64 [installed]
>>>>>>> 78b23f0c1e1877d9703438e8bceb6f581cb0a1d9
