
Afin de durcir la sécurité de notre serveur SSH, nous allons **autoriser seulement la connexion par clé publique/privée**. Décommentez la ligne suivante dans le fichier et changer la valeur du paramètre "**PasswordAuthentication**" de **yes à no** :

```bash
sudo nano /etc/ssh/sshd_config
```

```bash
PasswordAuthentication no
```

Puis, redémarrez le service SSH.

```bash
sudo systemctl restart ssh
```

#ssh 