# Instructions 
<br><br>
## for Apache, PHP, MySQL and PHPMyAdmin installation on Ubuntu 20.04;

### 1. Apache2 Installation via terminal:
<br>

```
$ sudo apt-get install apache2
```
<br>

### as soon as we are done with installation we can type 'localhost' in the browser and we should
### see the Apache2 Ubuntu Default Page; which means that installation was successful.
<br>

### 2. PHP installation via terminal: 
<br>

```
$ sudo apt-get install php libapache2-mod-php
```
<br>

### after installation we can type 
<br>

```
$ php -v
```
<br>

### in order to check the php version that was previously installed;
### by default it should be the latest version.
<br>

### 3. Navigate to root directory for localhost: 
<br>

```
$ cd /var/www/html/
$ ls -la
```
<br>

### right here we can create index.php file; 
### after creating index.php file, if we navigate to localhost in our web browser
### we cannot see anything because in root directory we have index.html file
### and by default apache looks up for index.html first and index.php second;
### so what we need to do here is actually change this by opening dir.conf file: 
<br>

```
$ sudo gedit /etc/apache2/mods-available/dir.conf
```
<br>

### inside of dir.conf we just need to change the order
### and place the index.html after index.php and save it.
### after that we need to restart apache server: 
<br>

```
$ sudo service apache2 restart
```
<br>

### another thing we need to mention is that every file is owned by root; 
### and when we start working with VS Code it will be impossible to change
### anything inside of this file because VS Code runs with our current user
### which in my case is husein@husein: /var/www/html
### and optimal solution is to run apache with 'husein' user
### and change ownership of the files to 'husein' user; 
<br>

```
$ sudo chown husein:husein -R ./
```
<br>

### and now when we type ls -la; we can see that everything is own by 'husein' user;




[more about web development setup on Linux Ubuntu 20.04](https://www.google.com)

