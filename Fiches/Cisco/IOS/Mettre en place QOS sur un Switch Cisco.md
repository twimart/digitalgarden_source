

⚠  A détailler!!!
````
SwitchToto>en
Password:
SwitchToto#
SwitchToto#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
SwitchToto(config)#interface fastEthernet 0/1
SwitchToto(config-if)#mls qos ?
  cos            cos keyword
  dscp-mutation  dscp-mutation keyword
  trust          trust keyword

SwitchToto(config-if)#mls qos cos ?
  <0-7>     class of service value between 0 and 7
  override  override keyword

SwitchToto(config-if)#mls qos cos 7
SwitchToto(config-if)#


````
