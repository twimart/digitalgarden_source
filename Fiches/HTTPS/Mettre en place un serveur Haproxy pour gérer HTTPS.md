---
dg-publish: true
---

### Installation de Haproxy

Mettez à jour votre machine 

```
apt-get update && apt-get upgrade -y
```

Installer HaProxy:

```
apt-get install haproxy
```

Démarrer le service:

```
service haproxy status
service haproxy start
```

Créez une copie du fichier de configuration par défaut au cas où:

```
cd /etc/haproxy
cp haproxy.cfg haproxy.cfg.bak
```

Modifier le fichier de configuration:

```
cd /etc/haproxy
nano haproxy.cfg
```

Ajoutez les parties `frontend` et `backend`:

```
frontend https-in
    bind *:443 ssl crt /etc/haproxy/cert/ no-sslv3
    mode http
    option httplog
    default_backend be_servers

backend be_servers
    mode http
    balance roundrobin 
    server server1 192.168.1.1:80 check 
    server server2 192.168.1.2:80 check
```

### Explication du fichier Haproxy.conf

On a ici spécifié que le certficat SSL se trouvait dans le dossier `/etc/haproxy/cert/`. Vous pouvez changer la localisation du certificat si vous le désirer, mais assurez-vous que HaProxy a un accés au dossier. Le certificat doit être un fichier `.pem`, et il doit contenir la clé ET le certificat (voir ma note sur  [[Générer une autorité de certification et un certificat auto-signé avec XCA |XCA]]) .

Pour la parties `backend`, vous pensez à modifier `server1` et `server2`, qui sont les nom des serveurs, ainsi que leurs adresses IP.


### ⚠️ Haproxy et Apache sur le même serveur

Si vous désirer utliser Haproxy sur un serveur Apache (pour gérer facilement un certificat SSL par exemple), il y a un risque de conflit entre les deux. 
En effet, HaProxy et Apache écoutent tout les deux le port 443. Or, on veut seulement que HaProxy écoute sur ce port (car c'est lui qui s'occupe de gérer HTTPS): il nous faut donc modifier les ports d'écoute d'Apache:

```
cd /etc/apache2/
nano ports.conf
```

Puis modifier le fichier (vous pouvez laisser le port 80 pour HTTP, c'est 443 qui nous pose problème):

```
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default.conf

Listen 80

<IfModule ssl_module>
        Listen 8443
</IfModule>

<IfModule mod_gnutls.c>
        Listen 8443
</IfModule>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet

```

J'ai changé les valeurs 443 pour 8443, ainsi, Haproxy et Apache ne sont plus en conflit de ports!

- [[Générer une autorité de certification et un certificat auto-signé avec XCA]]