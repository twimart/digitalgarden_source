---
dg-publish: true
---

![[nat réseau.png]]

*Dans ce shéma, Router1 symbolise Internet, le seul "vrai" routeur est Router0, c'est sur lui qu'on va configurer le NAT.*

Le Network Address Translation (NAT) est une technique utilisée pour traduire les adresses IP d'un réseau privé en adresses IP publiques. Cette technique permet à un réseau privé d'accéder à Internet en utilisant une seule adresse IP publique.

Dans cet exemple, nous allons configurer le NAT sur un routeur Cisco pour un réseau privé avec l'adresse IP 192.168.53.0/24.

## Étape 1 : Configuration de l'interface du routeur

La première étape consiste à configurer l'interface du routeur qui sera connectée au réseau privé. Nous allons attribuer une adresse IP privée à cette interface.

```
Router(config)# interface GigabitEthernet 0/0
Router(config-if)# ip address 192.168.53.254 255.255.255.0
Router(config-if)# ip nat inside
Router(config-if)# no shutdown 
```


## Étape 2 : Configuration de la translation d'adresse

Maintenant, nous allons configurer la translation d'adresse pour que les adresses IP privées soient traduites en adresses IP publiques. Dans cet exemple, nous allons utiliser une adresse IP publique statique fournie par notre fournisseur d'accès Internet (FAI) pour traduire toutes les adresses IP privées.

```
Router(config)# ip nat inside source list 1 interface GigabitEthernet 0/1 overload
```

Dans cette commande, `list 1` fait référence à une liste d'accès qui spécifie les adresses IP privées à traduire. Dans ce cas, nous allons utiliser une liste d'accès standard qui inclut toutes les adresses IP du réseau privé :

```
Router(config)# access-list 1 permit 192.168.53.0 0.0.0.255
```

## Étape 3 : Configuration de l'interface WAN

Cette étape consiste à configurer l'interface WAN du routeur qui sera connectée à Internet. Nous allons attribuer l'adresse IP publique fournie par notre FAI à cette interface.

```
Router(config)# interface GigabitEthernet 0/1
Router(config-if)# ip address 203.0.113.1 255.255.255.0
Router(config-if)# ip nat outside
Router(config-if)# no shutdown
```

## Étape 4 : Création d'une route par défaut

Il ne nous reste plus qu'à configurer une route par défaut pour que les paquets du réseau privé puissent être acheminés vers Internet via l'interface WAN du routeur. Voici comment configurer cette route:

````
Router(config)# ip route 0.0.0.0 0.0.0.0 203.0.113.1
````

C'est tout ce qu'il faut pour configurer le NAT sur un routeur Cisco. Maintenant, toutes les adresses IP privées du réseau 192.168.53.0/24 seront traduites en adresse IP publique lorsqu'elles accéderont à Internet.

