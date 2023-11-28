---
dg-publish: true
---
### Prérequis
Avoir un server LAMP fonctionnel. J'ai une note [[Créer un serveur LAMP sur Debian |ici]]. 

Installez d'abord quelques dépendances pour GLPI :
```
apt install php-mysqli php-mbstring php-curl php-gd php-simplexml php-intl php-ldap php-apcu php-xmlrpc php-cas php-zip php-bz2 php-imap -y
```

### Création de la base de données

Connectez vous à votre instance MariaDB:

```
mariadb -u root -p
```

Puis on va créer la base de données ainsi que l'utilisateur qui va l'administrer : 

```
create database db_glpi;  
grant all privileges on db_glpi.* to admindb_glpi@localhost identified by `"MDP"`;  
exit
```

### Paramétrage d'Apache2

Modifiez le fichier de configuration du site web par défaut d'Apache:

```
nano /etc/apache2/sites-available/000-default.conf
```

Ajoutez les lignes suivantes en dessous de  `DocumentRoot` :

```
<Directory /var/www/html>  
Options Indexes FollowSymLinks  
AllowOverride All  
Require all granted  
</Directory>
```

Redémarrez Apache:

```
service apache2 restart
```


### Installation de GLPI

Téléchargez l'archive GLPI:

```
cd /tmp  
wget https://github.com/glpi-project/glpi/releases/download/9.5.2/glpi-9.5.2.tgz  
```

Décompressez l'archive de GLPI:

```
tar -xvzf glpi-9.5.2.tgz
```

Supprimez le contenu de `/var/www/html/` :

```
rm /var/www/html/index.html  
cp -r glpi/* /var/www/html/
```

Donnez les permissions nécessaires sur le dossier `html/`:

```
chown -R www-data /var/www/html
```

Puis continuez l'installation sur votre navigateur !

```
http://ip-de-votre-machine-GLPI
```

- [[Créer un serveur LAMP sur Debian]]
- [[Installer WordPress sur un serveur Apache]]
