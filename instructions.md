# Instructions 

## for Apache, PHP, MySQL and PHPMyAdmin installation on Ubuntu 20.04;

### 1. Apache2 Installation via terminal:
<br>

```
$ sudo apt-get install apache2
```

#### as soon as we are done with installation we can type 'localhost' in the browser and we should see the Apache2 Ubuntu Default Page; which means that installation was successful.
<br>

### 2. PHP installation via terminal: 
<br>

```
$ sudo apt-get install php libapache2-mod-php
```

#### after installation we can type:
<br>

```
$ php -v
```

#### in order to check the php version that was previously installed, by default it should be the latest version.
<br>

### 3. Navigate to root directory for localhost: 
<br>

```
$ cd /var/www/html/
$ ls -la
```

#### right here we can create index.php file; after creating index.php file, if we navigate to localhost in our web browser, we cannot see anything because in root directory we have index.html file;
### and by default apache looks up for index.html first and index.php second, so what we need to do here is actually change this by opening dir.conf file: 
<br>

```
$ sudo gedit /etc/apache2/mods-available/dir.conf
```

#### inside of dir.conf we just need to change the order and place the index.html after index.php and save it, after that we need to restart apache server: 
<br>

```
$ sudo service apache2 restart
```

#### another thing we need to mention is that every file is owned by root; and when we start working with VS Code it will be impossible to change anything inside of this file because VS Code runs with our current user which in my case is husein@husein: /var/www/html; and optimal solution is to run apache with 'husein' user and change ownership of the files to 'husein' user; 
<br>

```
$ sudo chown husein:husein -R ./
```

#### and now when we type ls -la; we can see that everything is own by 'husein' user; we can open everything from terminal in VS code by using command: 
<br>

```
$ code .
```

#### if we make some file right now and save it, it will be owned by www-data; so what we need to do is change settings on our local installation by typing: 
<br>

```
$ sudo gedit /etc/apache2/envvars
```

#### in this file, on lines 16 and 17 we can see:
#### APACHE_RUN_USER=www-data
#### APACHE_RUN_GROUP=www-data
#### and we should modify both so they are equal to our current user, for example:
#### APACHE_RUN_USER=husein
#### APACHE_RUN_GROUP=husein
#### after that we need to restart apache: 
<br>

```
$ sudo service apache2 restart
```

#### now we will not have any permission issues while making some changes in our root folder.

### 4. MySQL Installation: 
<br>

```
$ sudo apt-get install mysql-server
```

#### we can confirm that it's installed by running: 
<br>

```
$ sudo service mysql status
```

### 5. PHPMyAdmin Installation: 
<br>

```
$ sudo apt-get install phpmyadmin
```

#### on the following screen make sure to hit space in order to select apache2; and after that just follow the instructions and type password; when the installation is finished, we just need to open our browser and type: 
<br>

```
localhost/phpmyadmin/
```

#### and we should see the login page of phpmyadmin; We will not be able to login because we need to set the same password on mysql level, for this we will run: 
<br>

```
$ sudo mysql
```

#### and here we can see mysql console where we can run:
<br>

```
mysql> ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'yourPasswordHere';
```

#### hit ctrl + z to exit the console.
#### password that we enter above must match the password we enter within phpmyadmin installation, when we open browser again and this time insert data and click 'Go', we will be able to login to phpmyadmin website.

### 6. Install PHP extension in VS code

#### open VS code, and go to extensions and type 'php IntelliSense', after that just select 'Install'.

### 7. Install Git via terminal: 
<br>

```
$ sudo apt-get install git
```
<br>

[more about web development setup on Linux Ubuntu 20.04](#)
[list of basic Linux commands](https://linoxide.com/linux-command/essential-linux-basic-commands/)

