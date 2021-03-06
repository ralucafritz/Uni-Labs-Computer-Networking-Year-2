#####  Fritz Raluca-Mihaela grupa 243
# Retele 
### Laboratorul 4

---

In acest laborator o sa lucram cu:
- LAN DONALD
- LAN DUCK
- LAN DAISY
- LAN CHIP

--- 

### LAN DONALD

`LAN DONALD` are urmatoarele componente:

`HOST (PC)` = `DONALD`
`Switch (2960)` = `SwDONALD`
`SERVICE (Laptop)` = `SERVICE`
`Router (2911)` = `RDONALD`

IP CONFIGURATION `DONALD`:

- `192.168.200.36`
- `255.255.255.224`
- `192.168.200.33`
- `209.165.250.46`

Se vor urma urmatorii pasi pentru configurarea `LAN DONALD`:
- se adauga `DONALD` in spatiul de lucru;
- IP configuration si EMAIL configuration pentru `DONALD`;
- se adauga `SwDONALD` in spatiul de lucru;
- se adauga `SERVICE` in spatiul de lucru;
- se configureaza `SwDONALD` [(conform `lab_02`)](lab_02.md) prin `SERVICE`;
- se realizeaza conexiunea dintre `DONALD` si `SwDONALD`:
``` 
    DONALD(G/0) -> SwDONALD(G 0/1)
```
- se adauga `RDONALD` in spatiul de lucru;
- se configureaza `RDONALD` [(conform `lab_03`)](lab_03.md) prin `SERVICE`:
```
    interface giga 0/0 : 192.168.200.33 255.255.255.224
```
- se realizeaza conexiunea dintre `SwDONALD` si `RDONALD`:
```
    SwDONALD(G 0/2) -> RDONALD(G 0/0)
```
![](https://media.discordapp.net/attachments/894378460615680004/961577326871724052/unknown.png?width=374&height=375)

Se testeaza corectitudinea conexiunilor [(conform `lab_03`)](lab_03.md).

!!! A NU SE UITA `exit` DUPA CE SE TESTEAZA CU SUCCES SSH !!!!

---

### LAN DUCK

`LAN DUCK` are urmatoarele componente:

`HOST (SERVER)` = `SERVER`
`Switch (2960)` = `SwDUCK`
`Router (2911)` = `RDONALD`

IP CONFIGURATION `SERVER`:

- `209.165.250.46`
- `255.255.255.240`
- `209.165.250.33`
- `209.165.250.46`

Se vor urma urmatorii pasi pentru configurarea `LAN DUCK`:
- se adauga `SwDUCK` in spatiul de lucru;
- se configureaza `SwDUCK` [(conform `lab_02`)](lab_02.md) prin `SERVICE`;
- se adauga `SERVER` in spatiul de lucru;
- se acceseaza `SERVER`;
- in tabul `Physical` se va opri `SERVER`-ul;
- se va inlocui modulul de retea cu `PT-HOST-NM-1CGE`;
- se va porni `SERVER`-ul;
![](https://media.discordapp.net/attachments/894378460615680004/961577327433769051/unknown.png?width=515&height=223)
- IP CONFIGURATION si EMAIL CONFIGURATION pentru `SERVER` ca la un host(PC);
- se realizeaza conexiunea dintre `SERVER` si `SwDUCK`:
``` 
    SERVER(G/0) -> SwDUCK(G 0/1)
```
- se configureaza `RDONALD` [(conform `lab_03`)](lab_03.md) prin `SERVICE`:
```
    interface giga 0/1 : 209.165.250.33 255.255.255.240
```
- se realizeaza conexiunea dintre `SwDUCK` si `RDONALD`:
```
    SwDUCK(G 0/2) -> RDONALD(G 0/1)
```
![](https://media.discordapp.net/attachments/894378460615680004/961577398372012063/unknown.png?width=537&height=319)

Se testeaza corectitudinea conexiunilor [(conform `lab_03`)](lab_03.md).

!!! A NU SE UITA `exit` DUPA CE SE TESTEAZA CU SUCCES SSH !!!!

Se testeaza `ping` si `ssh` si in `DONALD` si in `SERVER` cu `<default gateway>` ale ambelor HOST-uri

##### EXEMPLU DONALD:

![](https://media.discordapp.net/attachments/894378460615680004/961577421998547034/unknown.png?width=214&height=375)

Se vor face si `ping`-uri intre IPv4 Addess-uri(in `DONALD` cu IPv4 `SERVER`):
![](https://media.discordapp.net/attachments/894378460615680004/961577441489485824/unknown.png?width=340&height=168)

Pentru o verificare a configurarile interface => hover pe `ROUTER`, exemplu:
![](https://media.discordapp.net/attachments/894378460615680004/961577460946829343/unknown.png?width=569&height=185)

---

### SETARE SERVICES 

- se acceseaza `SERVER`;
- se acceseaza tabul `Services`;

#### HTTP SERVICES:

- in sectiunea `HTTP`:
  - se dezactiveaza `HTTP`;
  - ramane activata doar `HTTPS` pentru securitate;
  - exemplu:
![](https://media.discordapp.net/attachments/894378460615680004/961577483210219540/unknown.png?width=463&height=282)

#### DNS SERVICES:

- in sectiunea `DNS`:
  - se activeaza serviciul;
  - se introduce numele domeniului(`info.ro`);
  - se introduce `<DNS Server IP>` => `209.165.250.46`; (in poze am gresit ip-ul)
![](https://media.discordapp.net/attachments/894378460615680004/961577507373608990/unknown.png?width=478&height=303)
  - se apasa pe `Add`;
  - exemplu rezultat final:
![](https://media.discordapp.net/attachments/894378460615680004/961577527980220546/unknown.png?width=420&height=113)

##### TESTARE DNS SERVICES:

Se realizeaza in `DONALD`:

- se acceseaza `DONALD`;
- se acceseaza `Web Browser`;
- la URL introducem una dintre cele 2(de obicei `<domain name>`):
  - `<DNS Server IP>` => `209.165.250.46`;
    - implicit se va folosi `http:/` si trebuie schimba manual in `https:/`;
  - `<domain name>` => `info.ro`;
    - implicit se va folosi `http:/` si trebuie schimba manual in `https:/`;

##### EXEMPLU TEST DESFASURAT CU SUCCES:
![](https://media.discordapp.net/attachments/894378460615680004/961577551183101962/unknown.png?width=553&height=243)

#### EMAIL SERVICES:

- in sectiunea `EMAIL`: 
  - se introduce `<domain name>`: `info.ro` si se apasa pe `SET` => !!! EXTREM DE IMPORTANT ALTFEL DA EROARE LA TESTARE !!!
  - daca `<domain name>` a fost setat cu success, butonul `SET` se va face GRI;
  - se introduce username-ul si parola setate apoi se apasa pe `+` pentru fiecare dintre `HOST`-uri;
  - exemplu:
![](https://media.discordapp.net/attachments/894378460615680004/961577581503709225/unknown.png?width=483&height=373)

##### TESTARE EMAIL SERVICES:

Se realizeaza in `DONALD` si in `SERVER`:

- se acceseaza `DONALD`;
  - se acceseaza `EMAIL`;
  - se apasa pe butonul `Compose`;
    - se introduce email-ul corespunzator `SERVER`-ului;
    - se alege un titlu si un mesaj corespunzator;
    - se apasa pe `SEND` pentru a se trimite mail-ul;
    - exemplu:
![](https://media.discordapp.net/attachments/894378460615680004/961577601170808862/unknown.png?width=419&height=169)
- se acceseaza `SERVER`;
  - se acceseaza `EMAIL`;
  - se apasa pe butonul `Receive`;
  - se verifica daca s-a primit mail-ul;
  - exemplu corect:
![](https://media.discordapp.net/attachments/894378460615680004/961577645282304000/unknown.png?width=472&height=167)

---

### LAN DAISY

`LAN DAISY` are urmatoarele componente:

`HOST (PC)` = `DAISY`
`Switch (2960)` = `SwDAISY`
`Router (2911)` = `RDONALD`

IP CONFIGURATION `DAISY`:

- `192.168.100.136`
- `255.255.255.128`
- `192.168.100.129`
- `209.165.250.46`

Se vor urma urmatorii pasi pentru configurarea `LAN DAISY`:
- se adauga `DAISY` in spatiul de lucru;
- IP configuration si EMAIL configuration pentru `DAISY`;
- se adauga `SwDAISY` in spatiul de lucru;
- se configureaza `SwDAISY` [(conform `lab_02`)](lab_02.md) prin `SERVICE`;
- se realizeaza conexiunea dintre `DAISY` si `SwDAISY`:
``` 
    DAISY(G/0) -> SwDAISY(G 0/1)
```
- se configureaza `RDONALD` [(conform `lab_03`)](lab_03.md) prin `SERVICE`:
```
    interface giga 0/2 : 191.168.100.129 255.255.255.128
```
- se realizeaza conexiunea dintre `SwDAISY` si `RDONALD`:
```
    SwDAISY(G 0/2) -> RDONALD(G 0/2)
```

![](https://media.discordapp.net/attachments/894378460615680004/961577667285639198/unknown.png?width=535&height=320)

Se testeaza corectitudinea conexiunilor prin: `ping` si `ssh`, in `DAISY` cu `SERVER` si `DONALD` si vice-versa.
Se adauga `DAISY` la serviciul  `EMAIL` din `SERVER` si se testeaza serviciul `EMAIL`.
Se testeaza serviciul `DNS`.

---

### LAN CHIP

`LAN CHIP` are componentele:

`HOST (PC)` = `CHIP`
`Switch (2960)` = `SwCHIP`
`Router (2911)` = `RCHIP`

IP CONFIGURATION `CHIP`:

- `192.168.10.10`
- `255.255.255.192`
- `192.168.10.1`
- `209.165.250.46`


Se vor urma urmatorii pasi pentru configurarea `LAN CHIP`:
- se adauga `CHIP` in spatiul de lucru;
- IP configuration si EMAIL configuration pentru `CHIP`;
- se adauga `SwCHIP` in spatiul de lucru;
- se configureaza `SwCHIP` [(conform `lab_02`)](lab_02.md) prin `SERVICE`;
- se realizeaza conexiunea dintre `CHIP` si `SwCHIP`:
``` 
    CHIP(G/0) -> SwCHIP(G 0/1)
```
- se adauga `RCHIP` in spatiul de lucru;
- se configureaza `RCHIP` [(conform `lab_03`)](lab_03.md) prin `SERVICE`:
```
    interface giga 0/0 : 192.168.10.1 255.255.255.192
```
- se realizeaza conexiunea dintre `SwCHIP` si `RCHIP`:
```
    SwCHIP(G 0/2) -> RCHIP(G 0/0)
```

![](https://media.discordapp.net/attachments/894378460615680004/961577691528708157/unknown.png?width=544&height=282)

Se testeaza corectitudinea conexiunilor din `LAN CHIP`[(conform `lab_03`)](lab_03.md).

