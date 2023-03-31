---
dg-publish: false
dg-home: false
---
## Eteindre le routeur et se brancher en série dessus

Pour cela, débrancher l'alimentation électrique du routeur.

## Reinitialiser le routeur

On va  ici utiliser le logiciel Putty.

Dans les 30 secondes (max) après le redémarrage du router, envoyer une commande `break`

1. Faire un click droit sur la barre en haut de la fenêtre Putty et selectionner  **Special Command > Break**
2. On sera alors sur une invite de commande
3. Tapez dans cette invite : 
```
confreg 0x2142
reset
```

Le routeur va alors redémarrer et il sera réinitialisé! 

