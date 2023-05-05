---
dg-publish: true
---
Fail2ban surveille ces journaux pour créer automatiquement une règle iptables, ufw ou autres firewall afin d’ajouter la machine en liste noire et la bloquer totalement.  
Ainsi, fail2ban protège contre les tentatives répétées d’authentification sur le service soit par des attaques par bruteforce ou DoS.

### Etape 1 : Installer Fail2ban

```bash
sudo apt install fail2ban
```

### Etape 2 : Configurer Fail2ban

On conseille de le copier vers /etc/fail2ban/jail.local afin d’apporter les modifications souhaitée.  
Cela afin de ne pas perdre sa configuration lors du mise à jour du système ou du paquet.

```bash
cp /etc/fail2ban/jail.{conf,local}
```

Ensuite, configurer le fichier dans le fichier **/etc/fail2ban/jail.local** : 

```bash
nano /etc/fail2ban/jail.local
```

puis : 

```bash
[default]
# "bantime" is the number of seconds that a host is banned.
bantime  = 10m

# A host is banned if it has generated "maxretry" during the last "findtime"
# seconds.
findtime  = 10m

# "maxretry" is the number of failures before a host get banned.
maxretry = 3

# "maxmatches" is the number of matches stored in ticket (resolvable via tag <matches> in actions).
maxmatches = %(maxretry)s


[sshd]
# To use more aggressive sshd modes set filter parameter "mode" in jail.local:
# normal (default), ddos, extra or aggressive (combines all).
# See "tests/files/logs/sshd" or "filter.d/sshd.conf" for usage example and details.
#mode   = normal
enabled = true
port    = ssh
logpath = %(sshd_log)s
backend = %(sshd_backend)s
bantime = 10m
maxretry = 3
```

Il est possible de mettre des adresses IP en liste blanche :

```bash
ignoreip = 127.0.0.1/8 10.128.31.48
```


### Etape 3 : Vérifier que Fail2ban fonctionne et est actif


- Pensez à redémarrer le service :

```bash
systemctl restart fail2ban
```

- Pour vérifier la prise en compte de la configuration :

```bash
fail2ban-client -d|grep "'sshd', "
```

- pour obtenir des statistiques sur fail2ban SSH :

```
sudo fail2ban-client status sshd
```

```
sudo systemctl status fail2ban
```

#### Points importants 
- Penser à changer la valeur de "`port`" dans le fichier de configuration (en fonction de sa configuration SSH).
- Aussi, en fonction de ses besoins, on prendra garde à modifier les valeurs de `bantime`, `maxretry`, et `findtime`.

### Etape 4 : Tester sa configuration 

Normalement, avec la configuration ci-dessus, un hôte qui essaie de se connecter et qui se trompte 3 fois en 10 minutes, devrai être bannit pendant 10 minutes. Ainsi, il ne pourra pas tenter de se connecter en SSH sur l'hôte distant. 

#ssh