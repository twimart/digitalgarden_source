
## DHCP 

```bash
nano /etc/dhcp/dhcpd.conf

nano /etc/default/isc-dhcp-server

service isc-dhcp-server restart

```

## NTP 
```
nano /etc/chrony/chrony.conf

systemctl restart chrony
service chrony restart
```

```
ntp server <@ip_ntp>
clock set hh:mm:ss dd <month> yyyy
```

## TFTP 

nano /etc/xinetd.d/tftp
service xinetd restart

```
copy running-config tftp
```




## RSYSLOG 

nano /etc/rsyslog.conf  (peut etre ajouter la ligne avec un nouveau fichier)

```
Switch> en
Switch# conf t
Switch(config)# logging <@ip_RSysLog>
```

## Apache/GLPI

cd /etc/apache2/
cd /var/www/html/

[[Installer GLPI sur un serveur LAMP]]

```
service apache2 restart 
```

## DNS

nano  /etc/bind/named.conf.local

renommer et modifier /etc/bind/db.example.com

modifier /etc/bind/named.conf.options

```
systemctl restart bind9
```


## Haproxy 

nano /etc/haproxy/haproxy.conf

mettre le fichier *.pfx* dans /etc/haproxy/cert/

```
service haproxy restart
```

logs: tail /var/log/haproxy.log



