---
dg-publish: true
---

## Topologie du réseau ##

![[stick réseau.png]]

## 1ere étape : Mettre en place SSH sur les équipement

Je vous invite à suivre le tutoriel que j'ai fait une note [[Paramètrer une connexion SSH sur un appareil Cisco|ici]].

## 2ieme étape: Paramétrer un VLAN sur le Switch 

On créer un VLAN et l'on lui attribue une adresse IP: 

- [[Créer un VLAN sur IOS]]
- [[Donner une addresse IP à un VLAN sur IOS]]

On va ensuite affecter un port à notre VLAN. J'ai fait une note [[Affecter un port à un VLAN |ici]]. 

Puis on définit l'interface relié au routeur en mode trunk, voir ma note [[Définir un port en mode Trunk |ici]].

Ne pas oublier d'indiquer au Switch sa passerelle par défaut: 

 ````
 Switch(config)# ip default-gateway 192.168.254.254
````


## 3ieme étape: Configurer le routeur

On va tout d'abord créer des sous-interfaces (ou interfaces virtuelles), afin que l'interface physique du routeur (Gb 0/0) puisse écouter plusieurs VLANs. 

Création de l'interface virtuelle:
```
R1(config)# interface g0/0.1 
```

On active le protocole 802.q et on lui dit d'écouter le VLAN 10:
```
R1(config-subif)# encapsulation dot1Q 10
```

On lui assigne une adresse IP et son masque. 
```
R1(config-subif)# ip address 192.168.254.254 255.255.255.0
```


***Vous pouvez répéter la 2ieme et 3ième étape autant de fois que vous avez de VLANs.***

#cisco 





