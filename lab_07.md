#####  Fritz Raluca-Mihaela grupa 243
#  Retele
### Laboratorul 7

- `IPv4` - 4 octeti
- `IPv6` - 8 hexteti: 
  - 10<sup>36</sup>
  - ex: `2001:ACAD:DB8:200:...`
    /128
    /64 - realitate

Configurare Switch pentru `IPv6` include si urmatorii pasi:
```
Switch(config)# sdm prefer dual-ipv4-and-ipv6 default       -> permite ipv4 si ipv6
Switch(config)# interface vlan 1
Switch(config-if)# description ...
Switch(config-if)# ipv6 address 2001:ACAD:DB8:10::2/64
Switch(config-if)# no shutdown
```

`IPv6`: `2001:ACAD:DB8:10::10/64`
`Default Gateway(DGW)`: `2001:ACAD:DB8:10::1`
`DNS`: `1000:2000:0:0:1::FFFE`

`IPv4`: `156.166.177.211/20`

LAN 1 = `1023 H`
LAN 2 = `511 H`
LAN 3 = `63 H`

3 LAN-uri => 2 legaturi

#### Pas 1: 

`NA` = `156.166.176.0/20`
`BA` = `156.166.191.255/20`
`RA` = `156.166.176.1 - 156.166.191.254/20`


Ulterior, vom introduce aceste IP-uri calculate, in Switch, iar `DGW` este primul IP din range, in cazul acesta `156.166.176.1`, iar IP-ul pe care il introducem noi este `DGW+1`, in cazul nostru `156.166.175.2`.
```
Switch(config)# interface vlan 1
Switch(config-if)# ip address 156.166.176.2 255.255.248.0
Switch(config-if)# no shutdown
Switch(config-if)# exit
Switch(config)# ip default-gateway 156.166.176.1
```

#### Pas 2:

2<sup>10</sup> < 1023 < 2<sup>11</sup>   
2<sup>9</sup> < 511 < 2<sup>10</sup>  
2<sup>6</sup> < 63 < 2<sup>7</sup> 

Avem 2 legaturi, deci se adauga si:

2<sup>1</sup> < 2 < 2<sup>2</sup>   
2<sup>1</sup> < 2 < 2<sup>2</sup>   

#### Pas 3:

R1 = 1023
masca de retea = 32-11 = 21

`NA` = `156.166.176.0/21`
`BA` = `156.166.183.255/21`
`RA` = `156.166.176.1 - 156.166.183.254/21`

R1 = 511
masca de retea = 32-10 = 22

`NA` = `156.166.184.0/22`
`BA` = `156.166.187.255/22`
`RA` = `156.166.184.1 - 156.166.187.254/22`

R1 = 63
masca de retea = 32-7 = 25

`NA` = `156.166.188.0/25`
`BA` = `156.166.188.127/25`
`RA` = `156.166.188.1 - 156.166.188.126/25`

R1 = 2
masca de retea = 32-2 = 30

`NA` = `156.166.188.128/30`
`BA` = `156.166.188.131/30`
`RA` = `156.166.188.129 - 156.166.188.130/30`

R1 = 2

`NA` = `156.166.188.132/30`
`BA` = `156.166.188.135/30`
`RA` = `156.166.188.133 - 156.166.188.34/30`


!!! Pe Switch doar `interface vlan` + setare `DGW`  