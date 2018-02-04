# Udacity Server Project
This is info for the udacity grader to access and test the practice server

### Server Info

* IP: 35.170.221.248
* SSH Port: 2200
* URL: www.t1update.com

### Apache Config

* Close all connections to git repo

```<Directorymatch "^/.*/\.git/">
Order deny,allow
Deny from all
</Directorymatch>
```

* Open files in app
```
<Directory /var/www/html>
Order allow,deny
Allow from all
</Directory>
```
* Change name of app in WSGI
```
WSGICallableObject app
```
* Run in Daemon mode and include python path to allow relative paths in code
```
WSGIDaemonProcess catalog python-path=/var/www/html home=/var/www/html
```
* Link WSGI to app
```
WSGIScriptAlias / /var/www/html/catalog.wsgi process-group=catalog application-group=%{$
```

### Users

* created user grader
* added grader to sudoers

### Postgres

* Modify pg_hba.conf to trust localhost connections

#### Firewall

* Default all to blocked except 80, 2200, 123

### Third Party Resources

I did a ton of troubleshooting and research on Stackexchange, Postgres website, etc. 

Server runs on Amazon Lightsail. Apache, Python, Postgres, Ubuntu.
