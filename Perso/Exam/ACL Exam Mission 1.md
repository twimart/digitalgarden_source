
### !Bloquer SSH de la DMZ vers le Serveur

access-list 100 deny tcp  (réseau DMZ masque inverse)  (réseau Serveur masque inverse) eq 22
access-list 100 permit tcp any any 


### Où définir cette ACL ?

On va la définir en entrée, à la sous-interface de la DMZ:

```
interface Gigabitethernet 0/0.3
```

puis


```
ip access-group 100 in
```
