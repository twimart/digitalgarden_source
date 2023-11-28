---
dg-publish: true
---

## Schéma du réseau

![[mission1.png]]


##### A Retenir:

- Réseau SIO (Réseau public) > 172.25.0.0/16
- Passerelle SIO > 172.25.254.254/16
- DNS SIO > 172.25.254.12 et 172.25.254.15

Les machines des réseaux privés (172.16.0.0/16) sortent sur le réseau public avec l’adresse IP du routeur.

***Tester avec des pings et avancer étape par étape.***

***

## Tâches à faire:

### 1ère partie:

#### 1. Reset le switch

[[Reset un Switch Cisco (sans mot de passe)]]

#### 2. Reset le routeur

[[Ordre prises armoire A]]
[[Reset un routeur Cisco (sans mot de passe)]]

#### 3. Etablir une connexion SSH sur les équipements

[[Paramètrer une connexion SSH sur un appareil Cisco]]

#### 4. Configuration du routage *on-a-stick*

[[Mettre en place un Routage on-a-stick]]

#### 5. Mettre en place le NAT dynamique et le NAT de destination

[[Configuration du NAT avec Cisco]]
[[Configurer un NAT de destination sur Cisco]]

***

### 2ième partie:

#### 1. Configurer le service DHCP

[[Serveurs Exam]]

#### 2. Configurer le service Apache2/GLPI 

***A faire sur le serveur WEB !***
[[Serveurs Exam]]

#### 3. Configurer le service NTP 

[[Serveurs Exam]]

#### 4. Configurer le service TFTP

[[Serveurs Exam]]

#### 5. Configurer le service Syslog

[[Serveurs Exam]]

### 3ième partie:

#### 1. Configurer les ACL

[[ACL Exam Mission 1]]

#### 2. Vérifier que les services du Serveur fonctionnent

- Vérifier que les équipements ont une IP du DHCP.
- Vérifier l'heure des équipements avec NTP.
- Vérifier l'envoi de configuration via TFTP.
- Vérifier le stockage des log avec Syslog.

- [[ACL Exam Mission 1]]
- [[ACL Exam Mission 2]]
- [[BTS épreuve pratique Mission 2]]
- [[Ordre prises armoire A]]
- [[Serveurs Exam]]
