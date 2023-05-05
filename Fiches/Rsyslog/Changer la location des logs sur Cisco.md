---
dg-publish: true
---
Pour ce TP nous utilisons un serveur RSysLog hébergé par une machine debian.

```ios
Switch> en
Switch# conf t
Switch(config)# logging <@_IP_RSysLog>
```

Vos log serons hébergé par le serveur RSysLog!
Voici ce que vous devriez voir sur votre serveur Rsyslog (si vous avez suivi mon tuto [[Mettre en place Rsyslog |ici]]):

```bash
cat /var/log/Switch/forwarded-logs.log
Jan  6 13:24:16 172.25.193.35 34: Jan  6 12:24:15.205: %LINK-5-CHANGED: Interface FastEthernet0/20, changed state to administratively down
Jan  6 13:24:17 172.25.193.35 35: Jan  6 12:24:16.211: %SYS-6-LOGGINGHOST_STARTSTOP: Logging to host 172.25.193.34 Port 514 started - CLI initiated
```

- [[Mettre en place Rsyslog]]

#cisco 