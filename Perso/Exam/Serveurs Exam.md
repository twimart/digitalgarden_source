
## DHCP ##
nano /etc/dhcp/dhcpd.conf

nano /etc/default/isc-dhcp-server

systemctl restart isc-dhcp-server.service


## NTP ##
nano /etc/chrony/chrony.conf

systemctl restart chrony

```
ntp server <@ip_ntp>
clock set hh:mm:ss dd mm yyyy
```

## TFTP ##

nano /etc/xinetd.d/tftp

sudo /etc/init.d/xinetd restart

```
copy running-config tftp
```


## RSYSLOG ##

nano /etc/rsyslog.conf 

```
Switch> en
Switch# conf t
Switch(config)# logging <@ip_RSysLog>
```