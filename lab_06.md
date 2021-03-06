#####  Fritz Raluca-Mihaela grupa 243
#  Retele
### Laboratorul 6 


### `152.198.201.105/14`

![](https://media.discordapp.net/attachments/841731398952026133/955579273496887296/unknown.png?width=608&height=375)

`N.A.`=`152.196.0.0/14`  
`B.A.`=`152.199.255.255/14`  
`R.A.`=`152.196.0.1-152.199.255.254/14`  

---

### `176.214.160.191/27` Ce tip de IP este?

![](https://media.discordapp.net/attachments/841731398952026133/955581044831187014/unknown.png?width=660&height=376)

#### IP = B.A. => IP de tip B.A.   

`N.A.`=`176.214.160.160/27`  
`B.A.`=`176.214.160.191/27`  
`R.A.`=`176.214.160.161-176.241.160.190/27`  

---

### `139.230.144.215/18`  

![](https://media.discordapp.net/attachments/841731398952026133/955581714195951676/unknown.png?width=630&height=375)

    Ramura 1: 511 H  
    Ramura 2: 2040 H  
    Ramura 3: 1023 H  
    Ramura 4: 8190 H  
    Ramura 5: 4095 H  
    Ramura 6: 2 H   
    Ramura 7: 2 H  

!! Se iau in considerare si legaturile dintre routere  

`VLSM` = masti de lungime variabila    

#### Pas 1:  

`N.A.`=`139.230.128.0/17`  
`B.A.`=`139.230.255.255/17`  
`R.A.`=`139.230.128.1-139.230.255.254/17`  

#### Pas 2: ORDONARE DE LA MARE LA MIC

2<sup>12</sup> < 8190 < 2<sup>13</sup>  
2<sup>12</sup> < 4095 < 2<sup>13</sup>  
2<sup>10</sup> < 2040 < 2<sup>11</sup>   
2<sup>10</sup> < 1023 < 2<sup>11</sup>   
2<sup>9</sup> < 511 < 2<sup>10</sup>   
2<sup>1</sup> < 2 < 2<sup>2</sup>   
2<sup>1</sup> < 2 < 2<sup>2</sup>   


#### Pas 3:
Ram<sub>4</sub> = 8190  

`N.A.`=`139.230.128.0/19`   
`B.A.`=`139.230.159.255/19`  
`R.A.`=`139.230.128.1-139.230.159.254/19`  

masca de retea = 19 pentru ca 32 - 13 = 19 [----puterea lui 2<sup>13</sup>----]  

Ram<sub>5</sub> = 4095  
 
Pentru `N.A.` utilizam (`B.A`-ul anterior +1) => in cazul asta avem 255+1 ceea ce nu este posibil deci => 0 si adaugam (+1) la 159 => `139.230.160.0/19`  

`N.A.`=`139.230.160.0/19`  
`B.A.`=`139.230.191.255/19`  
`R.A.`=`139.230.168.1-139.230.191.254/19`  

Ram<sub>2</sub> = 2040  

`N.A.`=`139.230.192.0/21`  
`B.A.`=`139.230.199.255/21`  
`R.A.`=`139.230.160.1-139.230.199.254/21`  

masca de retea = 21 pentru ca 32 - 11 = 21 [----puterea lui 2<sup>11</sup>----]  

Ram<sub>3</sub> = 1023  

`N.A.`=`139.230.200.0/21`  
`B.A.`=`139.230.207.255/21`  
`R.A.`=`139.230.200.1-139.230.207.254/21`  

Ram<sub>1</sub> = 511  

`N.A.`=`139.230.208.0/22`  
`B.A.`=`139.230.211.255/22`  
`R.A.`=`139.230.208.1-139.230.211.254/22`  

masca de retea = 22 pentru ca 32 - 10 = 22 [----puterea lui 2<sup>10</sup>----]  

Ram<sub>6</sub> = 2 

`N.A.`=`139.230.212.0/30`  
`B.A.`=`139.230.212.3/30`  
`R.A.`=`139.230.212.1-139.230.212.2/30`  

masca de retea = 30 pentru ca 32 - 2 = 30 [----puterea lui 2<sup>2</sup>----]  

Ram<sub>7</sub> = 2  

`N.A.`=`139.230.212.4/30`  
`B.A.`=`139.230.212.7/30`  
`R.A.`=`139.230.212.5-139.230.212.6/30`  
 
---

### `192.171.231.143/23`

R<sub>1</sub> = 7 H  
R<sub>2</sub> = 31 H  
R<sub>3</sub> = 15 H   
R<sub>4</sub> = 63 H  

#### Pas 1:

![](https://media.discordapp.net/attachments/841731398952026133/955584794991939664/unknown.png?width=664&height=375)

`N.A.`=`192.171.230.0/23`  
`B.A.`=`192.171.231.255/23`  
`R.A.`=`192.171.230.1=192.171.231.254/23`  

#### Pas 2:

2<sup>6</sup> < 63 < 2<sup>7</sup>  
2<sup>5</sup> < 31 < 2<sup>6</sup>  
2<sup>4</sup> < 15 < 2<sup>5</sup>   
2<sup>3</sup> < 7 < 2<sup>4</sup>   
2<sup>1</sup> < 2 < 2<sup>2</sup>   (legatura)  
2<sup>1</sup> < 2 < 2<sup>2</sup>   (legatura)  
2<sup>1</sup> < 2 < 2<sup>2</sup>   (legatura)  

    pentru ca avem legaturi intre cele 4 Ramuri => 3 legaturi cu 2 hosturi  

#### Pas 3:  

R<sub>4</sub> = 63  
`N.A.`=`192.171.230.0/25`   
`B.A.`=`192.171.230.127/25`  
`R.A.`=`192.171.230.1-192.171.230.126/25`  

R<sub>2</sub> = 31  
`N.A.`=`192.171.230.128/26`  
`B.A.`=`192.171.230.191/26`  
`R.A.`=`192.171.230.129-192.171.230.190/26`  

R<sub>3</sub> = 15  
`N.A.`=`192.171.230.192/27`  
`B.A.`=`192.171.230.223/27`  
`R.A.`=`192.171.230.193-192.171.230.222/27`  

R<sub>1</sub> = 7  
`N.A.`=`192.171.230.224/28`  
`B.A.`=`192.171.230.239/28`  
`R.A.`=`192.171.230.225-192.171.230.238/28`  

R<sub>5</sub> = 2 (legatura)  

`N.A.`=`192.171.230.240/30`  
`B.A.`=`192.171.230.243/30`  
`R.A.`=`192.171.230.241-192.171.230.242/30`  

R<sub>6</sub> = 2 (legatura)  

`N.A.`=`192.171.230.244/30`  
`B.A.`=`192.171.230.247/30`  
`R.A.`=`192.171.230.245-192.171.230.246/30`  

R<sub>7</sub> = 2 (legatura)  

`N.A.`=`192.171.230.248/30`  
`B.A.`=`192.171.230.251/30`  
`R.A.`=`192.171.230.249-192.171.230.250/30`  

---

### VLSM 

    A. 0-127/8  10.0.0.0-10.255.255.255/8 -> private
    B. 128-191/16 172.16.0.0-172.16.255.255/12 -> private
    C. 192-223/24 192.168.0.0-192.168.255.255/16 -> private
    D. 224-239 N.A (nealocat)
    E. 240-255 N.A (nealocat)

`CIDR = Classless Inter-Domain Routing`