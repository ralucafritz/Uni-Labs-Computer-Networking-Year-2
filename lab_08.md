#####  Fritz Raluca-Mihaela grupa 243
#  Retele
### Laboratorul 8

Pe Switch doar `interface vlan` + setare `DGW`  

`IPv4`:`138.149.221.115/15`  

LAN ANGLIA = `4095 U`  
LAN ANDORA = `2047 U`  
LAN WiFi = `31 U`  

3 LAN-uri => 2 legaturi  

#### Pas 1:  

`NA` = `138.148.0.0/15`  
`BA` = `138.149.255.255/15`  
`RA` = `138.148.0.1 - 138.149.255.254/15`  

#### Pas 2:

2<sup>12</sup> < 4095 < 2<sup>13</sup>   
2<sup>11</sup> < 2047 < 2<sup>12</sup>     
2<sup>5</sup> < 31 < 2<sup>6</sup>   
2<sup>1</sup> < 2 < 2<sup>2</sup>     
2<sup>1</sup> < 2 < 2<sup>2</sup>   

#### Pas 3:

R1 = 4095  
masca de retea = 32-13 = 19  

`NA` = `138.148.0.0/19`  
`BA` = `138.148.31.255/19`  
`RA` = `138.148.0.1 - 138.148.31.254/19`  

R1 = 2047  
masca de retea = 32-12 = 20  

`NA` = `138.148.32.0/20`  
`BA` = `138.148.47.255/20`  
`RA` = `138.148.32.1 - 138.148.47.255/20`  

R1 = 31  
masca de retea = 32-6 = 26  

`NA` = `138.148.48.0/26`  
`BA` = `138.148.48.63/26`  
`RA` = `138.148.48.1 - 138.148.48.62/26`  
 
R1 = 2  
masca de retea = 32-2 = 30  

`NA` = `138.148.48.64/30`   
`BA` = `138.148.48.67/30`  
`RA` = `138.148.48.65 - 138.48.48.66/30`  

R1 = 2  

`NA` = `138.148.48.68/30`  
`BA` = `138.148.48.71/30`  
`RA` = `138.148.48.69 - 138.148.48.70/30`

### Configurare wireless router:

`Network devices -> Routers -> Wireless Routers -> WRT300N` ![poza networking devices](https://media.discordapp.net/attachments/894378460615680004/962726169294295110/unknown.png?width=31&height=33)
![poza WRT300N](https://media.discordapp.net/attachments/894378460615680004/962726125333786704/unknown.png?width=188&height=86)

Pentru configurarea acestuia, il conectam la laptop-ul `SERVICE` printr-o conexiune de tip `Straight-Through` 
```
SERVICE(FastEthernet0) - WR_EXEMPLU(Ethernet 1)
```
In `SERVICE`:
-  in `IP Configuration` vom configura IP-ul conform setarilor router-ului(initial este configurat automat cu `DGW` = `192.168.0.1`):
   - `192.168.0.2`  
   - `255.255.255.0`  
   - `192.168.0.1`   
    ![poza IP config](https://media.discordapp.net/attachments/894378460615680004/962727970445852682/unknown.png?width=347&height=78)

- in `Browser`:  
  - vom accesa `192.168.0.1` si ne va aparea o fereastra pentru autentificare:  
    ![poza accesare Browser](https://media.discordapp.net/attachments/894378460615680004/962727976666013756/unknown.png?width=532&height=375)
  - username: `admin`  
  - password: `admin`   
  - dupa ce am introdus username si password ne va aparea:  
    ![poza accesare configurare router](https://media.discordapp.net/attachments/894378460615680004/962729010184486942/unknown.png?width=421&height=376)

Aici incepe propriu-zis configurarea router-ului:
#### Setup:
  - Basic Setup:
    - Internet setup: 
      - setam `Internet Connection Type` in `Static IP`
      - introducem :
        - `138.148.48.66`
        - `255.255.255.252`
        - `138.148.48.65`
        - `138.148.47.254`
    - Network setup:
      - Router IP:
        - setam :
          - IP = `138.148.48.1`
          - Subnet Mask = `255.255.255.192` (nu se poate introduce manual, trebuie selectat)
      - DHCP Server Settings:
        - setam:
          - Maximum number of users: `62`
  - SAVE  
  ![](https://media.discordapp.net/attachments/894378460615680004/962732985222844456/unknown.png?width=446&height=375)
  - Dupa ce salvam, vom primi un mesaj cu `CONNECTION TIMEOUT` pentru ca am schimbat setarile router-ului iar acum trebuie sa editam in `IP Configuration` cu un IP din range, noul `Subnet Mask` si `DGW` = `138.148.48.1`:  
  ![poza editare ip config](https://media.discordapp.net/attachments/894378460615680004/962733032169689138/unknown.png?width=328&height=105)
  - Apoi ne intoarcem in `Browser` si accesam `138.148.48.1` si introducem din nou username si parola:  
    ![poza reaccesare config router](https://media.discordapp.net/attachments/894378460615680004/962735092369875115/unknown.png?width=605&height=237)
#### Wireless
  - Basic settings: 
    - setam:
      - `Network name(SSID)`: `SSID` sau `Wi-Fi`, noi am folosit `Wi-Fi` la laborator
      - `Standard Channel`: NEVER on channel 1 => selectam intre channel 6 si 11
    - SAVE   
    ![poza basic settings](https://media.discordapp.net/attachments/894378460615680004/962735906035486770/unknown.png?width=483&height=254)
  - Wireless Security:
    - setam:
      - `Security mode`: `WPA2 Personal`
      - `Encryption`: `AES`
      - `Passphrase`: `SSID-WI-FI`
    - SAVE  
    ![poza wireless security](https://media.discordapp.net/attachments/894378460615680004/962738147081478215/unknown.png?width=448&height=201)
  - Wireless MAC Filter
    - il setam pe ENABLED
    - selecta ori `Permit PCs` ori `Prevent PCs`, in functie de cazurile ulterioare  
    ![poza setari MAC Filter](https://media.discordapp.net/attachments/894378460615680004/962738986143612998/unknown.png?width=341&height=78)
    - vom introduce ulterior o adresa MAC in lista
    - SAVE

#### Aflarea adresei MAC:
Pentru acest pas vom adauga un laptop nou numit `LAP1` si ii vom schimba placa de retea cu placa de retea `WPC300N` pentru access la Wi-Fi

Vom intra in `Desktop`:
  - in `PC Wireless`:
    - intram la `Profiles`, dam click pe `New` pentru a crea un profil nou si ii setam numele `SSID-Wi-Fi`  
    ![poza adaugare profil](https://media.discordapp.net/attachments/894378460615680004/962740250529124352/unknown.png?width=517&height=319)
    - vom intra in `Advanced Setup`  
    ![poza advanced setup](https://media.discordapp.net/attachments/894378460615680004/962740293793366016/unknown.png?width=84&height=35)
    - introducem la `Wireless Network name` numele selectat in sectiunea [Wireless](#wireless), in cazul de fata, `Wi-Fi`  
    ![poza setare nume](https://media.discordapp.net/attachments/894378460615680004/962740844258033694/unknown.png?width=479&height=238)
    - dam next de 2 ori pana ajungem la setarea `Wireless Security` unde selectam `WPA2 Personal`  
    ![poza wireless security](https://media.discordapp.net/attachments/894378460615680004/962741199817551893/unknown.png?width=488&height=198)
    - dam next si introducem parola introdusa in sectiunea [Wireless](#wireless), in cazul de fata: `SSID-WI-FI`  
    ![poza parola](https://media.discordapp.net/attachments/894378460615680004/962743155948654682/unknown.png?width=199&height=60)
    - next => save => connect to network

In momentul de fata conexiunea la Network este imposibila deoarece nu am introdus adresa MAC a `LAP1` in router si avem selectata optiunea `Permit PCs` care lasa doar adresele MAC introduse sa se conecteze la router.

Pentru a afla adresa MAC intram in `LAP1` in `Command Prompt` si introducem comanda `ipconfig /all` si va aparea ceva similar cu:
```
Cisco Packet Tracer PC Command Line 1.0
C:\> ipconfig /all

Bluetooth Connection:(default port)

   Connection-specific DNS Suffix..: 
   Physical Address................: 0000.0C7D.CB7D
   Link-local IPv6 Address.........: ::
   IPv6 Address....................: ::
   IPv4 Address....................: 0.0.0.0
   Subnet Mask.....................: 0.0.0.0
   Default Gateway.................: ::
                                     0.0.0.0
   DHCP Servers....................: 0.0.0.0
   DHCPv6 IAID.....................: 
   DHCPv6 Client DUID..............: 00-01-00-01-8B-67-B9-54-00-02-16-17-28-84
   DNS Servers.....................: ::
                                     0.0.0.0

Wireless0 Connection:

   Connection-specific DNS Suffix..: 
   Physical Address................: 0002.1617.2884
   Link-local IPv6 Address.........: FE80::202:16FF:FE17:2884
```

In cazul de fata, adresa MAC este cea de la sectiunea `Wireless0 Connection` la subsctiunea `Physical Address`: `0002.1617.2884`.

In general adresele MAC pot aparea sub diverse forme:
- `0002.1617.2884`
- `00:02:16:17:28:84`
- `00-02-16-17-28-84`

Acum ne intoarcem in `SERVICE` => `Browser` => Accesam `138.148.48.1` si introducem la MAC Filter, adresa MAC a laptop-ului `LAP1` si salvam. Dupa ce se realizeaza conexiunea, va aparea asa:  
![poza conexiune](https://media.discordapp.net/attachments/894378460615680004/962746060814561440/unknown.png?width=426&height=308)

Testam conexiunea cu `ping DGW` sau `ping IP-SERVICE`, exemplu DGW:  
![poza ping](https://media.discordapp.net/attachments/894378460615680004/962746621928538112/unknown.png?width=372&height=202)