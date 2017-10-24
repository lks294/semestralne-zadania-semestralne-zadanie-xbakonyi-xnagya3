# Analýza
V článku sa zisťuje, ako doručiť obsah založený na DASH cez mininet prostredie. 
Toto prostredie sa dá nakonfigurovať tak, aby spojila reálne aj virtuálne siete. 
Ďalej prezentujú výsledky experimentov zameraných na štúdium  prenesenia streamovaného videa v podmienkach ako je premenlivá šírka prenosového pásma. 
Pri experimentoch boli použité  dva rôzne emulátory sietí: Mininet a Linktropy 5500.   

## Testovanie obsahu článku


### SDN (Software defined network)
Softvér definovaná sieťová technológia (SDN) je prístup k počítačovej sieti, ktorý umožňuje správcom siete programovo inicializovať, riadiť,
 meniť a spravovať chovanie siete dynamicky prostredníctvom otvorených rozhraní.
 Dokáže poskytovať abstrakciu funkcií nižšej úrovne. SDN má za cieľ riešiť skutočnosť, že statická architektúra tradičných sietí nepodporuje potreby modernejších výpočtových prostredí.[^3]

 ![trad-SDN](https://github.com/aks-2017/semestralne-zadania-semestralne-zadanie-xbakonyi-xnagya3/blob/master/docs/traditionalvsSND.PNG)

### Apache HTTP Server
Je softwarový webový server s Open source licenciou pre rôzné platformy.
Apache bol jedným z prvých serverov na podporu virtuálnych hostiteľov založených na IP, ktoré sa nachádzajú priamo mimo škatuľky.
 Verzie 1.1 a novšie verzie Apache podporujú virtuálne hostiteľské počítače založené na protokoloch IP a názvy virtuálnych hostiteľov (virtuálných hostov). 
Druhá verzia virtuálnych hostiteľov sa niekedy nazýva aj virtuálny hostiteľ hostiteľskej alebo non-IP. [4]

###MPEG-DASH(Dynamic Adaptive Streaming over HTTP)

je adaptívna technológia streamovania dátového toku, ktorá umožňuje vysoko kvalitné streamovanie mediálneho obsahu cez internet, ktorý je dodávaný z konvenčných webových serverov HTTP. 
Každý segment obsahuje krátky čas prehrávania obsahu, ktorý môže trvať niekoľko hodín, napríklad multimediálny obsah z youtube,netflix,twich. 
###Bitrate
Bitová rýchlosť udáva, aký objem informácie sa prenesie za jednotku času. 
Základnou jednotkou bitovej rýchlosti je bit za sekundu (bit/s). Jednotka udáva, koľko bitov informácie je prenesených za jednu sekundu. 
Vrámci projektu pomocou bit rate budeme vyhodnocovať výsledok zmeny šírky pásma.
###Šírka pásma

### OpenFlow 
Je komunikačný protokol, ktorý umožňuje prístup k prepojovacej rovine sieťového prepínača alebo smerovača cez sieť.[^2]
### Mininet 
Je emulátor siete, ktorý vytvára sieť virtuálnych hostiteľov, prepínačov, ovládačov a odkazov. Mininet hostitelia prevádzkujú štandardný sieťový softvér Linux 
a jeho prepínače podporujú OpenFlow pre vysoko flexibilné vlastné smerovanie a softvérové ​​siete.[^1]
*Podporuje ľubovoľné vlastné topológie a obsahuje základnú sadu parametrizovaných topológií
*Poskytuje priamu a rozšíriteľnú Python API pre vytváranie a experimentovanie so sieťami




[^1]: https://github.com/mininet/mininet/wiki/Introduction-to-Mininet#what
[^2]: http://archive.openflow.org/documents/openflow-spec-v1.1.0.pdf
[^3]: http://www.opennetworking.org/wp-content/uploads/2013/02/SDN-architecture-overview-1.0.pdf
[^4]: https://httpd.apache.org/docs/current/vhosts/