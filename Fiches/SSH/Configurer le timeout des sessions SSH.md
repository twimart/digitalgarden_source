
---
dg-publish: true
---

Se rendre dans le fichier de configuration de SSH :

```bash
sudo nano /etc/ssh/sshd_conf
```

Puis décommenter les lignes suivantes: 

```bash
ClientAliveInterval 600
ClientAliveCountMax 0
```

-   **ClientAliveInterval** - ceci indique le délai d'attente en secondes. Après x secondes, le serveur SSH enverra un message au client demandant une réponse.

-   **ClientAliveCountMax** - ceci indique le nombre total de messages de vérification envoyés par le serveur SSH sans obtenir de réponse du client SSH.

Puis redémarrer SSH

```bash
service ssh restart
```

#ssh
