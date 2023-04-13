# LAMP

### Prérequis
* Server Unbuntu 22.04

### Installation
* Téléchatger PHP APACHE2 et MARIABD


```bash
sudo apt install apache2 php libapache2-mod-php mysql-server php-mysql
```
* Plus les dependence
```bash
sudo apt install php-curl php-gd php-intl php-json php-mbstring php-xml php-zip
```

* Création d'un hôte virtuel
* Créé un dossier /etc/apache2/sites-available/example.com.conf

example.com.conf
```apacheconf
<VirtualHost *:80>
	ServerName example.com
	ServerAlias www.example.com
	DocumentRoot "/var/www/example"
	<Directory "/var/www/example">
		Options FollowSymLinks
		AllowOverride all
		Require all granted
	</Directory>
	ErrorLog /var/log/apache2/error.example.com.log
	CustomLog /var/log/apache2/access.example.com.log combined
</VirtualHost>
```
* On déploiera ici les fichiers du site dans le répertoire /var/www/example
* Puis on active l'hôte virtuel et on recharge la configuration d'Apache : 

```bash
sudo a2ensite example.com
sudo systemctl reload apache2
```
* Création de la base de donnée
```mysql
CREATE DATABASE example;
CREATE USER 'userExample'@'localhost' IDENTIFIED BY 'mot_de_passe';
GRANT ALL PRIVILEGES ON example.* TO 'userExample'@'localhost';
FLUSH PRIVILEGES;
QUIT;
```
