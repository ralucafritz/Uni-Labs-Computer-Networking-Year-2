#####  Fritz Raluca-Mihaela grupa 243
# Retele 
### Laboratorul 3 

---

### Setare Router: 
- se introduce router-ul in spatiul de lucru 
- click pe router
- in tabul Physical 
- Power OFF
![](https://media.discordapp.net/attachments/894378460615680004/961575234027290644/unknown.png?width=338&height=143)
- Drag'n'Drop HWIC-2T in spatiul din dreapta de langa porturi
- Power ON
![](https://media.discordapp.net/attachments/894378460615680004/961575252121485352/unknown.png?width=378&height=162)

---

###  REGULI CONFIGURARE ROUTER 


Useful terms:
- usermode: `Router> `
- privileged mode: `Router#` / `RBON# `
- global config mode: `RBON(config)#` / `RBON(config)#`
- line config mode: `RBON(config-line)#`
- interface config mode: `RBON(config-if)#`
- `exit`  

Inainte de a incepe configurarea `Router`-ului va aparea o interogare la care se va raspunde cu `no`
![](https://media.discordapp.net/attachments/894378460615680004/961575278625321012/unknown.png?width=539&height=35)


##### La inceput este similar cu configurarea `Switch`-urilor

    Router> 
    Router> enable
    Router# configure terminal
    Router(config)# no ip domain-lookup
    Router(config)# hostname <nume>
    <nume>(config)# no cdp run
    <nume>(config)# service password-encryption
        
##### DOAR ROUTER:
```
<nume>(config)# security passwords min-length 10            -> parolele necesita minim 10 caractere

<nume>(config)# login block-for 45 attempts 3 within 15     -> daca se introduc 3 parole gresite in 15 secunde/minute/ore (depinde cum e setat), se blocheaza accessul pentru 45 secunde/minute/ore
```
    <nume>(config)# enable secret ciscosecpa55
    <nume>(config)# enable password ciscoenapa55
##### DOAR ROUTER:
```
<nume>(config)# banner login $Accesul persoanelor neautorizate este strict interzis$
```

[EXEMPLU:]()

![](https://media.discordapp.net/attachments/894378460615680004/961575317787537458/unknown.png?width=390&height=375)

##### AMBELE:
    <nume>(config)# banner motd $..$
    .
    .
    .
    .
    identic SWITCH

Dupa configurarea `router`-ului inainte de a face conexiunile intre componente, in terminalul `SERVICE` pentru `RBON` se introduc urmatoarele instructiuni:
    
    <nume>(config)# interface giga 0/0
    <nume>(config-if)# description Legatura cu LAN X           

`X` = Nume sau IP

    <nume>(config-if)# ip address 192.168.10.1 255.255.255.0 

ip address `default gateway` `subnet mask` 

    <nume>(config-if)# no shutdown
[EXEMPLU:]()

!!! A NU SE UITA `exit` PENTRU A EVITA ACCESUL PERSOANELOR NEAUTORIZATE !!!

![](https://media.discordapp.net/attachments/894378460615680004/961575347038584832/unknown.png?width=533&height=141)

---

Pentru astazi vom lucra cu:

`HOST (PC)` = `BON`
`Switch (2960)` = `SwBON`
`SERVICE (Laptop)` = `SERVICE`
`Router (2911)` = `RBON`

Se seteaza hostul `BON`:
- ip configuration;
- email.

##### IP configuration `BON`:
- `172.32.243.100`
- `255.255.252.0`
- `172.32.243.1`
- `209.165.200.190`

Se configureaza switchul `SwBON` conform regulilor din `lab_02`.

Se configureaza routerul `RBON` conform regulilor din `lab_03(acest document)`. (folosind `SERVICE`)

##### Configurare interfata 0/0 `RBON`

`interface giga 0/0`: `172.32.243.1` `255.255.252.0`

Se realizeaza conexiunile:
   
    BON(G/0) -> SwBON(G 0/1)
    SwBON(G 0/2) -> RBON(G 0/0)

![](https://media.discordapp.net/attachments/894378460615680004/961576025207218206/unknown.png?width=400&height=375)

---

Se testeaza corectitudinea conexiunilor:

- se acceseaza Command Prompt din host
- `ping <default gateway>`
- `ssh -l Admin01 <default gateway>`
- se introduce parola (in cazul nostru `Admin01pa55`)
- `exit`

![](https://media.discordapp.net/attachments/894378460615680004/961576047516729354/unknown.png?width=404&height=375)

---

`HOST (PC)` = `BRAGA`
`Switch (2960)` = `SwBRAGA`

Se seteaza hostul `BRAGA`:
- ip configuration;
- email.

##### IP configuration `BRAGA`:
- `173.16.200.50`
- `255.255.192.0`
- `173.16.200.1`
- `209.165.200.190`

Se configureaza switchul `SwBRAGA` conform regulilor din `lab_02`. (folosind `SERVICE`)

##### Configurare interfata 0/1 `RBON`

`interface giga 0/1`: `173.16.200.1` `255.255.192.0`

![](https://media.discordapp.net/attachments/894378460615680004/961576076759425074/unknown.png?width=414&height=110)

Se realizeaza conexiunile: 
   
    BRAGA(G/0) -> SwBRAGA(G 0/1)
    SwBRAGA(G 0/2) -> RBON(G 0/1)

![](https://media.discordapp.net/attachments/894378460615680004/961576101832966174/unknown.png?width=500&height=362)

Verificare corectitudine:

![](https://media.discordapp.net/attachments/894378460615680004/961576171580031006/unknown.png?width=329&height=375)

!!!!Atentie!!!!! Cand se configureaza interfata 0/1 a `RBON` iti poate cere o parola. Parola in acest caz este corespunzatoare conexiunii folosite -> `ciscoconpa55` (am patit eu la laborator)
