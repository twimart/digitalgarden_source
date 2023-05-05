
##### Commande pour les service:

Avant de commencer nous allons voir ce qu'il y a comme service sur la machine.
Pour cela nous allons utiliser la commande:
~~~~
service --status-all
~~~~

 Cette commande va lister tous les services de la machines et nous montrer si oui ou non le service est démarrer. (Le + veut dire que la machine est en route et le - veut dire que la machine n'est pas en route)

**Pour vérifier le statut d’un service spécifique :**
~~~~
service [Nom service] status
~~~~

**Pour démarrer et stopper un service:**
~~~~
service [Nom service] start
~~~~
~~~~
service [Nom service] stop
~~~~

**Pour redémarrer un service:**
~~~~
service [Nom service] restart
~~~~

##### Commande avec le systemctl:

La commande de base est:
~~~~
systemctl [commande] [Nom service]
~~~~

Afficher et lister les services:
~~~~
systemctl list-unit-files --type service -all
~~~~

Voir le status d'un service,Démarrer, stopper, redémarrer un service:
~~~~

systemctl status [Nom service]


systemctl start [Nom service]


systemctl stop [Nom service]


systemctl restart [Nom service]
~~~~

Source: https://www.malekal.com/comment-demarrer-arreter-redemarrer-un-service-sur-linux/

- [[Configuration d'un serveur Asterisk]]
- [[Voir les logs]]
- [[Vérifier les ports utilisés sur Linux]]