---
dg-publish: false
---

Ce premier concerne la configuration générale qui sera appliquée à l’ensemble des utilisateurs:

````
[general] ; s'applique donc à tous les utilisateurs 
hasvoicemail = yes ; l’utilisateur possède une boîte vocale. 
hassip = yes ; l’utilisateur possède un compte sip.
````


On va maintenant créer un template avec des paramètres qui s'appliquerons à tous les utilisateurs:

````
[template](!)
type = friend ; type d’objet SIP. 
host = dynamic ; l’utilisateur n’est pas associé à une IP fixe. 
dtmfmode = rfc2833 ; mode DTMF. 
disallow = all ; interdit tous les codecs. 
allow = ulaw ; autorise le codec ulaw. 
allow = alaw ; autorise le codec alaw.
````

⚠ Pour la première ligne, on peut remplacer `template` par un nom personnalisé que l'on voudrait donner au template. Le `!` spécifie qu'il sagit d'un template.

````
[1112](template)
fullname = Thomas ;remplacer utilisateur1 par votre prénom
username = 1112
secret = jsp ;le mot de passe est très simple ici et non sécurisé.
mailbox = 1112 ;référence vers la boîte vocale (fichiers voicemail.conf).
context = finance ;l’utilisateur appartient au contexte finance.
 ````
