 #####  Fritz Raluca-Mihaela grupa 243
# Retele 
### Laboratorul 5 


Norme de lucru  `T568A si T568B`:

![](https://media.discordapp.net/attachments/841731398952026133/955544355370856458/unknown.png?width=686&height=371)


Daca la capete exista:
- aceeasi norma => `STRAIGHT-THROUGH`  
- norme diferite => `CROSSOVER` 2-6, 1-3  

![](https://media.discordapp.net/attachments/841731398952026133/955559442152316958/unknown.png?width=328&height=375)

Echipamentele de:
- acelasi tip => `CROSSOVER`  
- tip diferit => `STRAIGHT-THROUGH`  

! intre `Host` si `Router` = conexiune `CROSSOVER`  

---

### `168.163.213.172/18`  
 
`N.A.` = network address  
`B.A.` = broadcast address  
`R.A.` = range address  

![](https://media.discordapp.net/attachments/841731398952026133/955565464162017380/unknown.png?width=552&height=333)

168 - `128` = 40 - `32` = 8 - `8` = 0 => 1010.1000  
163 - `128` = 35 - `32` = 3 - `2` = 1 - `1` = 0 => 1010.0011  
213 - `128` = 85 - `64` = 21 - `16` = 5 - `4` = 1 - `1` = 0 => 1101.0101  
172 - `128` = 44 - `32` = 12 - `8` = 4 - `4` = 0 => 1010.1100  

![](https://media.discordapp.net/attachments/841731398952026133/955567661734043678/unknown.png?width=712&height=173)

`N.A.`=`168.163.192.0/18`  
`B.A.`=`168.163.255.255/18`  
`R.A.`=`168.163.192.1-168.163.255.254/18`  

#### Reguli:
- `N.A.` poate fi `0` sau numar par   
- `B.A.` este intotdeauna numar impar   
- `N.A.` si `B.A.` nu pot fi asignate   

---

### `154.201.110.21/15`  

![](https://media.discordapp.net/attachments/841731398952026133/955569932828020826/unknown.png?width=490&height=293)

154 - `128` = 26 - `16` = 10 - `8` = 2 - `2` = 0 => 1001.1010  
201 - `128` = 73 - `64` = 9 - `8` = 1 - `1` = 0 => 1100.1001  
110 - `64` = 46 - `32` = 14 - `8` = 6 - `4` = 2 - `2` = 0 => 0110.1110  
21 - `16` = 5 - `4` = 1 - `1` = 0 => 0001.0101  

![](https://media.discordapp.net/attachments/841731398952026133/955569964536983682/unknown.png?width=712&height=202)

`N.A.`=`154.200.0.0/15`   
`B.A.`=`154.201.255.255/15`  
`R.A.`=`154.200.0.1-154.201.255.254/15`  

---

### `129.229.139.250/19`  

![](https://media.discordapp.net/attachments/841731398952026133/955576998607077446/unknown.png?width=468&height=297)
![](https://media.discordapp.net/attachments/841731398952026133/955577021856108584/unknown.png?width=712&height=197)
 
`N.A.`=`129.229.128.0/19`  
`B.A.`=`129.229.159.255/19`  
`R.A.`=`129.229.128.1-129.229.159.254/19`  

---

### `194.177.225.155/27`

![](https://media.discordapp.net/attachments/841731398952026133/955577976001548378/unknown.png?width=598&height=375)

`N.A.`=`194.177.225.128/27`  
`B.A.`=`194.177.225.159/27`  
`R.A.`=`194.177.225.129-194.177.225.158/27`  

