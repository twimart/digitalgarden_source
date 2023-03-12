---
dg-publish: true
---

Un serveur LAMP (Linux Apache MaraDB PHP) est un serveur qui va nous permettre d'hébèrger un site web. 

### 1ere étape: Installation d'Apache

On commence par mettre à jour les paquets:
```
sudo apt-get update
```

puis on les installe :

```
sudo apt-get upgrade
```

Nous devons ensuite installer notre 1er composant, Apache:

```
sudo apt-get install -y apache2
```

On peut ensuite activer Apache au démarage du serveur:

```
sudo systemctl enable apache2
```

Maitenant, on peut accècder à la page par défaut d'Apache. Pour cela, récupérer l'adresse IP de votre serveur:

```
ip address
```

Puis rentrer cette adresse sur une machine équipé d'un navigateur :

```
http://192.168.0.33
```

Vous devriez accèder à la page par défaut d'Apache.

Nous allons maintenant activer quelques modules important pour que Apache fonctionne correctement: 

```
sudo a2enmod rewrite
sudo a2enmod deflate
sudo a2enmod headers
sudo a2enmod ssl
```

Vous pouvez ensuite redémarrer Apache:
```
sudo systemctl restart apache2
```

Les fichiers de configuration de Apache se trouve dans `/etc/apache2/apache2.conf` .

### 2ieme étape: Intaller PHP

On commence par installer PHP:

```
sudo apt-get install -y php
```

Installez aussi quelques paquets importants pour notre serveur:

```
sudo apt-get install -y php-pdo php-mysql php-zip php-gd php-mbstring php-curl php-xml php-pear php-bcmath
```

Pour nous assurer que l'instalation est effective, nous allons créer un fichier:

```
sudo nano /var/www/html/phpinfo.php
```

Mettez les lignes suivantes dans ce fichier:

```
<?php
phpinfo();
?>
```

Enregistrez et rentrez l'IP de votre serveur suivi de  `phpinfo.php` : 

```
	http://192.168.0.33/phpinfo.php
```

Vous devriez accèder à une page qui donne toutes les infos sur votre configuration PHP. **Ne laissez pas cette page accessible par n'importe qui.**

### 3ieme étape: Installer MariaDB

Installer MariaDB:
```
udo apt-get install -y mariadb-server
```

Accèder à votre instance MariaDB (dans mon cas root n'as pas de mdp)

```
sudo mariadb -u root -p
```

Vous pouvez saisir la commande suivante afin de voir toute les bases de données créées.

```
show databases;
```
 
Puis tapez `exit` pour sortir de la console. 

Pensez à redémarrer MariaDB!

```
systemctl restart mariadb
```

Et voila, votre serveur LAMP est fonctionnel! 