---
dg-publish: false
---

## users.conf


[general] ;s'applique donc à tous les utilisateurs

hasvoicemail = yes ;l’utilisateur possède une boîte vocale.

hassip = yes ;l’utilisateur possède un compte sip


[template](!) ;notre template s’appelle template. Le ! Indique qu’il s’agit d’un template.

type = friend ;type d’objet SIP.

host = dynamic ;l’utilisateur n’est pas associé à une IP fixe.

dtmfmode = rfc2833 ;mode DTMF.

disallow = all ;interdit tous les codecs.

allow = ulaw ;autorise le codec ulaw.

allow = alaw ;autorise le codec alaw.

  

[1111](template) ;1101 est le numéro de téléphone. On précise ensuite le template.

fullname = Thomas;remplacer utilisateur1 par votre prénom

username = 1111

secret = jsp ;le mot de passe est très simple ici et non sécurisé.

mailbox = 1199 ;référence vers la boîte vocale (fichiers voicemail.conf).

context = finance ;l’utilisateur appartient au contexte finance.

## extensions.conf

[general]

static = yes ;le DialPlan est statique.

writeprotect = yes ;On ne peut pas le modifier depuis le CLI.

clearglobalvars = yes ;les variables sont effacées et recalculées à chaque redémarrage d’Asterisk.

  

[finance] ;Attention, ici XX est un caractère générique à ne pas remplacer, mais

; 11 est à adapter à votre équipement éventuellement.

;plan de numérotation du contexte finance

exten => _11XX,1,DIAL(SIP/${EXTEN},20)

exten => _11XX,2,Voicemail(${EXTEN}@finance)

;consultation des boîtes vocales du contexte finance.

exten => 1199,1,Answer()

exten => 1199,2, VoiceMailMain(${CALLERID(num)}@finance)

;jonction entre les utilisateurs des contextes finance et compta.

exten => _12XX,1,Goto(compta,${EXTEN},1)

  

[compta] ;Attention, ici XX est un caractère générique à ne pas remplacer, mais

; 11 est à adapter à votre équipement éventuellement.

;plan de numérotation du contexte finance

exten => _11XX,1,DIAL(SIP/${EXTEN},20)

exten => _11XX,2,Voicemail(${EXTEN}@compta)

;consultation des boîtes vocales du contexte finance.

exten => 1199,1,Answer()

exten => 1199,2, VoiceMailMain(${CALLERID(num)}@compta)

;jonction entre les utilisateurs des contextes finance et compta.

exten => _12XX,1,Goto(finance,${EXTEN},1)

## voicemail.conf

[general]

maxmsg = 100 ;nombre maximum de messages de la boîte vocale.

maxsecs = 360 ;durée maximum d’un message. Le 0 indique l’absence de limite.

minsecs = 0 ;durée minimum d’un message.

maxlogins = 3 ;nombre maximum d’erreur de login.

review = no ;permet à l’appelant de réécouter son message avant de le laisser sur la boîte vocale.

saycid = no ;dicte le numéro de l’appelant avant l’écoute du message.

  

[finance]

1111 => 1199, Thomas

  

[compta]

1201 => , Utilisateur5