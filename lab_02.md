#####  Fritz Raluca-Mihaela grupa 243
# Retele
### Laboratorul 2 

---

##  Configurarea unui host

### Pasul 1 (Adaugarea unui host si redenumirea acestuia)

- stanga jos => Selectam `[END DEVICES]` 
![](https://media.discordapp.net/attachments/894378460615680004/961572595407409162/unknown.png?width=178&height=58)  

- adaugam un Host de tip `PC` ![](https://media.discordapp.net/attachments/894378460615680004/961572615678468146/unknown.png?width=42&height=40)  

- ii dam drag and drop in partea de jos a spatilui liber ![](https://media.discordapp.net/attachments/894378460615680004/961572632472469584/unknown.png?width=44&height=59)

- click pe `PC0` si schimbam numele in `Info243` ![](https://media.discordapp.net/attachments/894378460615680004/961572649614598194/unknown.png?width=49&height=61)

### Pasul 2 (Schimbarea placii de retea)

- click pe `PC`  
- inchidem PC-ul din preview apasand pe butonul rosu: ![](https://media.discordapp.net/attachments/894378460615680004/961572673870245898/unknown.png?width=29&height=31)  
- dam scroll pana vedem placa de retea ![](https://media.discordapp.net/attachments/894378460615680004/961572990691196938/unknown.png?width=82&height=34)
- drag and drop placii de retea in cadranul cu module
- drag and drop placii `1CGE` (Cisco 1CGE de 1 GB) in locul celei vechi
- pornim PC-ul 

### Pasul 3 (Asignarea IP-ului)

- selectam tab-ul `Desktop`  
- selectam `IP Configuration` 
- setam IPv4 Configuration
  - IPv4 Address: `192.168.100.10`
  - Subnet Mask: `255.255.255.128`
  - Default Gateway: `192.168.100.1`
  - DNS Server: `209.165.200.254`  
![](https://media.discordapp.net/attachments/894378460615680004/961573174313627668/unknown.png?width=391&height=376)
- iesim din IP Configuration apasand pe X: 
### Pasul 4 (Configurarea serviciului de mail)

- selectam `Email` din tab-ul `Desktop`
- User Information
  - Name: `Info243`
  - Email Address: `info243@info.ro`
- Server Information
  - Incoming Mail Server: `209.165.200.254`
  - Outgoing Mail Server: `209.165.200.254`
- Logon Information
  - Username: `info243`
  - Password: `123456`
- save 
![](https://media.discordapp.net/attachments/894378460615680004/961573113311690752/unknown.png?width=472&height=375)
- pentru a verifica daca datele introduse sunt corecte -> apasam pe `Configure Mail` si se deschide fereastra precedenta

---

## Reguli si sintaxa Switch 

Useful terms:
- usermode: `Switch> `
- privileged mode: `Switch#` / `SwInfo# `
- global config mode: `Switch(config)#` / `SwInfo(config)#`
- line config mode: `SwInfo(config-line)#`
- `exit`


        Switch>                                             -> usermode
        Switch> enable                                      -> intrare in Switch privileged mode

        Switch# configure terminal                          -> intrare in Switch global config mode

        Switch(config)# no ip domain-lookup                 -> pentru a preveni erorile
        Switch(config)# hostname SwInfo                     -> intrare in SwInfo global config mode 

        SwInfo(config)# no cdp run                          -> inchiderea serviciului pentru a preveni atacuri
        
- `cdp` = cisco discovery protocol  
    
        SwInfo(config)# service password-encryption         -> toate parolele vor fi criptate

        SwInfo(config)# enable secret ciscosecpa55          -> password 1      
        SwInfo(config)# enable password ciscoenapa55        -> password 2
        SwInfo(config)# banner motd $Vineri la ora 14:00 serverul va fi oprit$

- `motd` = message of the day

        SwInfo(config)# line console 0                      -> intrare in SwInfo line config mode

        SwInfo(config-line)# password ciscoconpa55
        SwInfo(config-line)# login
        SwInfo(config-line)# logging synchronous
        SwInfo(config-line)# exec-timeout 25 40             -> inactivitate timp de 25 minute si 40 de secunde => return to Switch> enable
        
        SwInfo(config-line)# exit                           -> intoarcere in  SwInfo(config)#

        SwInfo(config)# line vty 0 15
        SwInfo(config-line)# password ciscovtypa55
        SwInfo(config-line)# login
        SwInfo(config-line)# logging synchronous
        SwInfo(config-line)# exec-timeout 25 40 
        
        SwInfo(config-line)# exit                           -> intoarcere in  SwInfo(config)#
        SwInfo(config)# exit                                -> intoarcere in  SwInfo#
        
        SwInfo# clock set 16:56:20 21 FEB 2022              -> sincrozinare cu ora si data actuala

- `NTP` = network time protocol
  
        SwInfo# configure terminal
        SwInfo(config)# ip domain-name info.ro
        SwInfo(config)# username Admin01 privilege 15 secret Admin01pa55
        SwInfo(config)# line vty 0 15
        SwInfo(config-line)# transport input ssh
        SwInfo(config-line)# login local

        SwInfo(config-line)# exit

        SwInfo(config)# crypto key generate rsa             -> ENTER -> 2048 -> ENTER

---

- stanga jos => `[Network Devices]`  ![](https://media.discordapp.net/attachments/894378460615680004/961574108712300604/unknown.png?width=105&height=63)


- selectare `Switches` (a doua optiune de pe randul al 2-lea) ![](https://media.discordapp.net/attachments/894378460615680004/961574185233174538/unknown.png?width=172&height=78)


- introducem un switch `2960` ![](https://media.discordapp.net/attachments/894378460615680004/961574260147638302/unknown.png?width=50&height=44)


- il denumim `SwInfo` ![](https://media.discordapp.net/attachments/894378460615680004/961574284566884392/unknown.png?width=49&height=55)


- adaugam un Laptop pe care il denumim `SERVICE` ![](https://media.discordapp.net/attachments/894378460615680004/961574301524426752/unknown.png?width=52&height=64)


- adaugam o conexiune ![](https://media.discordapp.net/attachments/894378460615680004/961574324597293116/unknown.png?width=162&height=49) de tip `Console`(cea albastra)![](https://media.discordapp.net/attachments/894378460615680004/961574353571545118/unknown.png?width=25&height=24) intre `SERVICE`(de tip `RS232`) si `SwInfo`(de tip `Console`)  


- daca conexiunea este reusita, ambele capete vor avea un cerc negru: 
 ![](https://media.discordapp.net/attachments/894378460615680004/961574370617208862/unknown.png?width=247&height=129)


- click pe `SERVICE` -> tab-ul `Desktop` -> `Terminal` -> OK -> ENTER -> configuram `SwInfo`  
![](https://media.discordapp.net/attachments/894378460615680004/961574399151071242/unknown.png?width=360&height=375)

---

Pentru a salva:

- scriem:
    `SwInfo# copy running-config startup-config `
- alegem unde sa salvam, in cazul nostru dam direct enter
  ![](https://media.discordapp.net/attachments/894378460615680004/961574431761760296/unknown.png?width=249&height=67)

---

- adaugam un PC nou: `Info243.1` -> setam placa de retea si configuram IP: IPv4 = `192.168.100.11`, in rest identic `Info243`
- adaugam un switch nou: `SwInfo.1` si il configuram
- adaugam o conexiune de tip STRAIGHT-THROUGH intre `Info243 (GigabitEthernet0)` si `SwInfo (GigabitEthernet0/1)`
- adaugam o conexiune de tip STRAIGHT-THROUGH intre `Info243.1 (GigabithEthernet0)` si `SwInfo.1 (GigabitEthernet0/1)`
- adaugam o conexiune CROSSOVER intre `SwInfo` si `SwInfo.1` -> `GigabitEthernet0/2`
- toate conexiunile devin verzi:

![](https://media.discordapp.net/attachments/894378460615680004/961574452074807306/unknown.png?width=457&height=220)

- click pe `Info243` -> `Desktop` -> `Command Prompt`
- dam ping ip-ului PC-ului `Info243.1` -> `ping 192.168.100.11` 
- daca primim 4 reply-uri (pong-uri) => e OK

![](https://media.discordapp.net/attachments/894378460615680004/961574475629989939/unknown.png?width=375&height=315)