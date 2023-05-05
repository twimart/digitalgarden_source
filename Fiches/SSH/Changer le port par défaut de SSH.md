---
dg-publish: true
---


Configurer le fichier de configuration SSH de votre serveur distant:

```bash
sudo nano /etc/ssh/sshd_config
```

Dans ce fichier, recherchez  `Port 22` - *cela pourrait être commenté* - et remplacez le par la valeur désiré. Par exemple:

```bash
Port 2222
```


Sauvegarder les changements et redémarrer SSH :

```bash
systemctl restart ssh
```

- [[Mettre en place une conexion SSH via l'échanges de clés]]
- [[Paramètrer une connexion SSH sur un appareil Cisco]]

#ssh 