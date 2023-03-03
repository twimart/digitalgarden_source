
## Topologie du réseau ##

![[nat reseau.png]]

### 1ere étape : mettre en place SSH sur les équipement .###

Je vous invite à suivre le tutoriel que j'ai fait une note [[https://www.thomaswimart.fr/fr/notes/cisco-ssh |ici]] .

### 2ieme étape: paramétrer un VLAN sur le Switch. ###

On créer un VLAN afin d'attribuer une adresse IP au Switch:

````
Switch(config)# vlan 10
Switch(config-vlan)# name MANAGEMENT
Switch(config-vlan)# exit
Switch(config)#interface vlan 10
Switch(config-if)# ip address 192.168.0.100 255.255.255.0 
Switch(config-if)# exit
Switch(config)# 
````

On va ensuite affecter un port à notre VLAN. J'ai fait une note [[Affecter un port à un VLAN |ici]]. 

Puis on définit l'interface relié au routeur en mode trunk, voir ma note [[Définir un port en mode Trunk |ici]].

Ne pas oublier d'indiquer au Switch sa passerelle par défaut: 

 ````
 Switch(config)# ip default-gateway 192.168.254.254
````


### 3ieme étape: configurer le routeur. ###

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


***Vous pouvez répéter la 3ième étape autant de fois que vous avez de VLANs.***







