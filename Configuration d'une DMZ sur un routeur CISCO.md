
## Étape 1 : Configuration de l'interface du routeur

Cette interface doit être configurée avec une adresse IP différente de celle utilisée sur l'interface LAN et l'interface WAN.  La commande pour créer une interface est la suivante :

```
Router(config)# interface GigabitEthernet 0/0.1
```

2.  Configurez l'adresse IP de l'interface DMZ. Utilisez la commande suivante :

```
Router(config-if)# ip address 10.54.0.254 255.255.255.0
```

3.  Définissez une règle de translation NAT statique pour la DMZ. Cette règle permettra de traduire les adresses IP de la DMZ en adresses IP publiques qui peuvent être accessibles depuis Internet. La commande pour configurer une règle de translation NAT statique est la suivante :

```
Router(config)# ip nat inside source static 10.54.0.0 172.25.0.0
```

4.  Configurez des règles de pare-feu pour la DMZ. Les règles de pare-feu permettent de contrôler le trafic entrant et sortant de la DMZ. Par exemple, pour autoriser le trafic HTTP entrant dans la DMZ, vous pouvez utiliser la commande suivante :

```
Router(config)# access-list 101 permit tcp any 10.54.0.0 0.0.255.255 eq http
```

5.  Appliquez les règles de pare-feu à l'interface DMZ en utilisant la commande suivante :

```
Router(config)# interface GigabitEthernet 0/0.1 
Router(config-if)# ip access-group 101 in
```

6.  Vérifiez la configuration en utilisant la commande `show running-config`. Cette commande affiche la configuration en cours sur le routeur.

Assurez-vous que les règles de pare-feu et les règles de translation NAT statiques ont été correctement configurées.

En suivant ces étapes, vous pouvez configurer une DMZ sur un routeur Cisco pour protéger les serveurs situés dans la zone DMZ tout en leur permettant d'être accessibles depuis Internet.