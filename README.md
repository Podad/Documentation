# GLPI

### Procedure pour une Instataltion

  

### Prérequis

  

   * Serveur Ubuntu 22.04

   * Serveur Web Apache2

   * PHP 8.1

   * MariaDB 10.6

  

### Installation

  

   * Télécharger GLPI

```bash
wget https://github.com/glpi-project/glpi/releases/download/10.0.6/glpi-10.0.6.tgz%
```

   * Décompresser le fichier

```bash
tar -xvf glpi-10.0.6.tgz
```

   * Copier le dossier glpi dans le dossier /var/www/html

```bash
sudo cp -r glpi /var/www/html
```

   * Créer la base de données
  
```mysql
CREATE DATABASE glpi;
```

   * Créer un utilisateur pour la base de données
   
```mysql
CREATE USER 'glpi'@'localhost' IDENTIFIED BY 'glpi';
```

   * Donner les droits à l'utilisateur sur la base de données

```mysql
GRANT ALL PRIVILEGES ON glpi.* TO 'glpi'@'localhost';
```

   * Créer un fichier de configuration

```bash
sudo nano /etc/apache2/sites-available/glpi.conf
```

   * Ajouter le contenu suivant

```bash
    <VirtualHost *:80>
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/html/glpi
        ServerName glpi
        ServerAlias glpi
        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
    </VirtualHost>
```

   * Redémarrer Apache2

```bash
sudo systemctl restart apache2
```

   * Accéder à l'interface web de GLPI

   http://localhost/glpi


![](https://github.com/Podad/GLPI/blob/main/1.png?raw=true)

   * Cliquer sur le bouton "Continuer >"

![](https://github.com/Podad/GLPI/blob/main/2.png?raw=true)

   * Cliquer sur Installer

![](https://github.com/Podad/GLPI/blob/main/3.png?raw=true)

   * Vérifier qui tout est installer sauf les extensions optionnelles

![](https://github.com/Podad/GLPI/blob/main/4.png?raw=true)

   * Remplir les champs avec les informations suivantes mot de passe : glpi

![](https://github.com/Podad/GLPI/blob/main/5.png?raw=true)

   * Cliquer sur le bouton "Continuer >" jusqu'à la fin

   * Se connecter à GLPI

![](https://github.com/Podad/GLPI/blob/main/6.png?raw=true)

   * supprimer le fichier d'installation

```bash
sudo rm -r /var/www/html/glpi/install
```
