---
dg-home: false
dg-publish: true
---

Installer Asterisck sur le serveur ( ici une machine Debian):

````
# apt-get install asterisk
````

La configuration d'Asterisck se fera avec les fichiers se trouvant dans le répértoire `/etc/asterisk` .
Il y a déja dans ces fichiers un exemple de configuration, on prendra donc soin de faire une copie d'un fichier original que l'on souhaiterai modifier.

Exemple pour le fichier `users.conf` : 
````
cp users.conf users.conf.sauve
````

On pourra ensuite le contenue de notre fichier: 

````
echo " " > users.conf
````

On va ensuite modifier plusieurs fichiers:

- [[Configuration du fichier users.conf | users.conf ]]
-  extensions.conf
- voicemail.conf
- iax.conf 
