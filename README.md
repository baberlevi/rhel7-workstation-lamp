macports-lamp
=============

Builds a LAMP stack on RHEL 7.1 
Specifically tailored for luggage development

Please read this README all the way through before beginning.

Why
---
Need a dev environment on my laptop

Prerequisites
-------------


Read Through the Script
-----------------------

Note that it will set your MySQL root password to "password" unless you
change this in the expect heredoc (ca. lines 36, 39).

Default Virtual Host
--------------------

The script will create the following virtual host which can be reached by
going to http://local.dev/ after the script completes.

```
NameVirtualHost *:80
<VirtualHost *:80>
    ServerName local.dev
    DocumentRoot /home/username/Sites
    <Directory /home/username/Sites>
      Options Indexes FollowSymLinks
      DirectoryIndex index.php index.html
      Order deny,allow
      Require ip 127.0.0.1
      AllowOverride All
    </Directory>
</VirtualHost>
```

Shortcuts
---------

The following functions will be installed in ~/.profile. I find them useful
at the command line:

```
te - tail Apache error log
ta - tail Apache access log
tp - tail PHP error log
acr - apachectl restart
```

Running the Scripts
-------------------

```
sudo ./build_lamp
sudo ./build_mysql
```

Drush
-----

If you need [Drush](http://drush.ws) (used for Drupal development):

```
sudo ./install_drush
```

Note: this will install Drush 5, which is in its golden years. You probably
want a newer Drush than this.

Reference
---------
https://github.com/clouseau/macports-lamp

