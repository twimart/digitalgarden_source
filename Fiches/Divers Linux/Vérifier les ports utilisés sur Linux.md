---
dg-publish: true
---

#### Voir tout les ports utilisés

```
netstat -an | grep -i listen
```
  ou
```
netstat -lpn | less
```

#### Voir si un port en particulier est utilisé

(exemple avec le port 443)

```
sudo lsof -i :443
```

- [[Comment démarrer ou stopper un service sur Linux]]
- [[Voir les logs]]
- [[Configuration d'un serveur Asterisk]]