
### !Accès Internet à partir du LAN
access-list 101 permit tcp(réseau LAN masque inverse) any eq 53
access-list 101 permit udp (réseau LAN masque inverse) any eq 53
access-list 100 permit tcp any eq 53 (réseau LAN masque inverse)
access-list 100 permit udp any eq 53 (réseau LAN masque inverse)
access-list 101 permit tcp (réseau LAN masque inverse) any eq 443
access-list 101 permit tcp (réseau LAN masque inverse) any eq 80
access-list 100 permit tcp any eq 443 (réseau LAN masque inverse)
access-list 100 permit tcp any eq 80 (réseau LAN masque inverse) 

### !Accès SSH à partir du LAN vers la DMZ 
access-list 101 permit tcp  (réseau LAN masque inverse)  (réseau DMZ masque inverse) eq 2222
access-list 102 permit tcp  any (réseau DMZ masque inverse) eq 2222
access-list 103 permit tcp  (réseau DMZ masque inverse) eq 2222 any
access-list 100 permit tcp (réseau DMZ masque inverse) eq 2222 (réseau LAN masque inverse)

### !Accès SSH à mon routeur à partir du LAN
access-list 101 permit tcp  (réseau LAN masque inverse) host (adresse routeur LAN) eq 22
access-list 100 permit tcp host (adresse routeur LAN) eq 22 (réseau LAN masque inverse)

### !Accès SSH à mon routeur à partir de la DMZ
access-list 103 permit tcp (réseau DMZ masque inverse)  host (adresse routeur DMZ) eq 22
access-list 102 permit tcp host (adresse routeur DMZ) eq 22 (réseau DMZ masque inverse)

### !Accès SSH à partir d'Internet vers la DMZ
access-list 102 permit tcp  any  (réseau DMZ masque inverse) eq 2222
access-list 103 permit tcp (réseau DMZ masque inverse) eq 2222 any

### !Accès Internet à partir de la DMZ
access-list 102 permit tcp  any (réseau DMZ masque inverse) eq 53
access-list 102 permit udp  any (réseau DMZ masque inverse) eq 53
access-list 102 permit tcp  any eq 53 (réseau DMZ masque inverse) 
access-list 102 permit udp  any eq 53 (réseau DMZ masque inverse) 
access-list 103 permit tcp (réseau DMZ masque inverse) eq 53 any
access-list 103 permit udp (réseau DMZ masque inverse) eq 53 any
access-list 103 permit tcp (réseau DMZ masque inverse) any eq 53
access-list 103 permit udp (réseau DMZ masque inverse) any eq 53
access-list 102 permit tcp  any (réseau DMZ masque inverse)eq 443
access-list 103 permit tcp (réseau DMZ masque inverse) eq 443 any
   

### !Avoir des logs
access-list 103 deny tcp any any log
access-list 103 deny udp any any log
access-list 100 deny tcp any any log
access-list 100 deny udp any any log
access-list 101 deny tcp any any log
access-list 101 deny udp any any log
access-list 102 deny tcp any any log
access-list 102 deny udp any any log


### Voirs les logs si jamais

show log 

- [[ACL Exam Mission 1]]
- [[BTS épreuve pratique Mission 1]]
- [[BTS épreuve pratique Mission 2]]
- [[Ordre prises armoire A]]
- [[Serveurs Exam]]
