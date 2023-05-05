---
 dg-publish: true
---
Avant tout il faut savoir que RSysLog est natif sur debian donc pas besoin de l'installer.  
Il faut juste le configurer le fichier `<rsyslog.conf>` pour ca nous allons nous rendre dans le dossier `<etc>`.

```shell
sudo nano /etc/rsyslog.conf 
```

Le fichier va s'afficher il faudra donc modifier les lignes suivantes :

```shell
#provides UDP syslog reception
#module(load="imudp")
#input(type="imudp" port="514")

#provides TCP syslog reception
#module(load="imtcp")
#input(type="imtcp" port="514")
```

il faut décommanter les lingnes suivantes :

```shell
module(load="imudp")
input(type="imudp" port="514")

module(load="imtcp")
input(type="imtcp" port="514")
```

Une fois cela il faut rajouter une ligne avant la catégorie `<RULES>`.

```shell
$template DynamicFile,"/var/log/<Nom_que_vous_voulez>/forwarded-logs.log"
*.* -?DynamicFile
```

**Pensez à créer le dossier dans lequel vos logs seront stockés.**

Puis activer et redémarrer Rsyslog:

```
systemctl enable rsyslog
systemctl restart rsyslog
```

Penser à [[Changer la location des logs sur Cisco]] pour vérifier que votre serveur est fonctionnel!

- [[Changer la location des logs sur Cisco]]