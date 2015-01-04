App vagrant skeleton
=========================
Template for developing applications with LAMP and Vagrant.

Environment
-----------
 * **Ubuntu 14.04 x32**
 * Apache 2.4 (MPM worker,mod_proxy_fcgi)
 * PHP 5.6 (fpm)
 * MySQL 5.6
 * Vagrant/Puphpet (php puppet)

Requirements
------------

 - *VirtualBox 4.3+*

 - *Vagrant 1.6+*

ps. Vagrant box (531mb) - https://atlas.hashicorp.com/puphpet/boxes/ubuntu1404-x32/versions/1.0/providers/virtualbox.box

File structure
--------------
```
apvas
├─── var3w/
│    ├─── vhost1/	
│    ├─── ...
│    └─── vhostX/	
│         ├─── app/
│         ├─── assets/
│         ├─── index.php
│         └─── .htaccess
├─── logs/
└─── vagrant
     ├─── puphpet	
     │     ├─── files/		
     │     ├─── puppet/	
     │     ├─── shell/
     │     └─── config.yaml
     └─── Vagrantfile
```
Explanations
============
var3w
-----
Folder synced to /var/www and contains virtual hosts. Virtual host and it's properties can be set in config(vagrant/puppet/config.yaml).
*VhostX* consists of app, assests, index.php, .htaccess. Where are:

 - **app/** - applications folder

 - **assets/** - container for js, img, css and sass files

 - **index.php** - single access point for application

 - **.htaccess** - folder access restriction, rewrite and redirect rules

Each vhost is separate project managed with git or other CVS. Thus these vhost folder structure are very approximate.

logs
----
Folder synced to /var/log/apache2 and contains apache access, error logs. Usualy error log contains php error messages too.

vagrant
-------
Container for vagrant puppet. The contains of:

 - **files/** - files, executed once, always, at startup; shh rsa keys; handy .bash_aliases, .bash_git, .vim_rc

 - **puppet/** - puppet core and modules

 - **shell/** - shell scripts for puppet

 - **config.yaml** - main configuration file; want to change something -- go here
