### Etape 1: générer une paire de clés

Ouvrez un terminal et taper la commande suivante:

```
ssh-keygen -t ed25519
```

 Je vous recommande de laisser l'emplacement par défaut pour stocker vos clés en appuyant sur Entrée. Mais vous pouvez changer d'emplacement si vous le dérirez.

```
Generating public/private ed25519 key pair.
Enter file in which to save the key (/home/<user>/.ssh/id_ed25519):
```

Entrez une phrase secrète pour protèger la clé privée:

```
Enter passphrase (empty for no passphrase):
```

Tapez la une seconde fois:

```
Enter same passphrase again:
```

Et vos clés sont maintenant créées!

```
Your identification has been saved in /home/<user>/.ssh/id_ed25519
Your public key has been saved in /home/<user>/.ssh/id_ed25519.pub
The key fingerprint is:
SHA256:EZvGfUbfF9DS/H2gSh1Pe7QdEz1zdw4mGmppw9JST+Y <user>@localhost
The key's randomart image is:
+--[ED25519 256]--+
|        .   ..=oo|
|       ..=+.oo=XB|
|       +*B.+oBo*/|
|      o.O.Eoo o.O|
|       =So .   ..|
|          .      |
|                 |
|                 |
|                 |
+----[SHA256]-----+

```

### Etape 2: Envoyer votre clé publique sur un hôte distant

Allez la où se trouve votre paire de clés puis envoyer la clé publique vers l'hôte distant désiré:

```
cd /home/<user>/.ssh/

ssh-copy-id -i id_ed25519.pub <user_distant>@<hostname>
```

"`-i`" permet de spécifier le fichier qu'on enverra sur l'hôte distant. En l'occurence, il sagit de la clé publique.

Remplacer `hostname` par l'adresse IP ou le nom d'hôte du serveur distant.

### Etape 3: Se connecter en SSH sur l'hôte distant

Connectez vous en SSH avec la commande suivante:

```
ssh <user_distant>@<hostname_distant>
```

Vous devrez alors vous connecter à l'hôte distant afin de copier votre clé publique. A votre prochaine connexion, vous devrez indiquer la phrase secrète  de votre clé. 

Puis vous n'aurez plus besoin de mettre de mot de passe du tout pour vous connecter!

