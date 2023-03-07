---
dg-publish: false
---

## Topologie du réseau

![[DMZ.png]]

Dans ce réseau, PC0 fait partis du LAN (172.16.0.0/16). Server0 doit être accessible depuis le LAN, mais aussi depuis Internet, sans que Internet n'est accès au LAN. La création d'une DMZ est donc nécessaire. 

## Étape 1 : Configuration de l'interface du routeur 

*(Si cela est déja fait, passez directement à la 2ieme étape.)*

- Cette interface doit être configurée avec une adresse IP différente de celle utilisée sur l'interface LAN et l'interface WAN.  La commande pour créer une interface est la suivante :

```
Router(config)# interface GigabitEthernet 0/0.1
```

- Configurez l'adresse IP de l'interface DMZ. Utilisez la commande suivante :

```
Router(config-if)# ip address 10.54.0.254 255.255.255.0
```


## Étape 2 : Configuration du NAT

Afin que nos service présent dans la DMZ puissent accèder à Internet et répondre aux requêtes venant d'Internet, il nous faut configurer un NAT sortant. 

 - Définissez une règle de translation NAT dynamique (PAT) pour la DMZ. Cette règle permettra de traduire les adresses IP de la DMZ en une adresses IP publique (celle du routeur) qui peuvent être accessibles depuis Internet. 
  - Les commandes pour configurer une règle de translation NAT dynamique est [[Configuration du NAT avec Cisco |ici]].


*(On refera cette étape de la même manière pour que le LAN aussi puisse sortir du réseau)*

## Étape 3 : Mise en place de la DMZ

Configurez des règles de pare-feu pour la DMZ. Les règles de pare-feu permettent de contrôler le trafic entrant et sortant de la DMZ. 

- Par exemple, pour autoriser le trafic HTTP entrant dans la DMZ, vous pouvez utiliser la commande suivante :

```
Router(config)# access-list 101 permit tcp any 10.54.0.0 0.0.255.255 eq http
```

*(On pourra faire d'autre ACL pour autoriser d'autres protocoles, d'autres ports, ou encore d'autres réseaux)*

- Appliquez les règles de pare-feu à l'interface DMZ en utilisant la commande suivante :

```
Router(config)# interface GigabitEthernet 0/0.1 
Router(config-if)# ip access-group 101 out
```

- Vérifiez la configuration en utilisant la commande `show running-config`. Cette commande affiche la configuration en cours sur le routeur.

## Étape 4 : Mise en place d'un NAT de destination

Dans notre exemple, on veut que Internet ai accès au site disponible sur Server0, présent dans la DMZ.  Notre DMZ est fonctionnelle, mais on doit ajouter un NAT de destination afin qu'Internet puisse s'y rendre.

Voir comment faire [[Configurer un NAT de destination sur Cisco |ici]]. 

Désormais, Internet devrais avoir accès à notre DMZ! 


