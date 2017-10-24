# Analýza
V článku sa zisťuje, ako doručiť obsah založený na DASH cez mininet prostredie. 
Toto prostredie sa dá nakonfigurovať tak, aby spojila reálne aj virtuálne siete. 
Ďalej prezentujú výsledky experimentov zameraných na štúdium  prenesenia streamovaného videa v podmienkach ako je premenlivá šírka prenosového pásma. 
Pri experimentoch boli použité  dva rôzne emulátory sietí: Mininet a Linktropy 5500.   

## Testovanie obsahu článku


### SDN (Software defined network)
Softvér definovaná sieťová technológia (SDN) je prístup k počítačovej sieti, ktorý umožňuje správcom siete programovo inicializovať, riadiť,
 meniť a spravovať chovanie siete dynamicky prostredníctvom otvorených rozhraní.
 Dokáže poskytovať abstrakciu funkcií nižšej úrovne. SDN má za cieľ riešiť skutočnosť, že statická architektúra tradičných sietí nepodporuje potreby modernejších výpočtových prostredí.

 ![trad-SDN](https://github.com/aks-2017/semestralne-zadania-semestralne-zadanie-xbakonyi-xnagya3/blob/master/docs/traditionalvsSND.PNG)

### Apache HTTP Server
Je softwarový webový server s Open source licenciou pre rôzné platformy. 

###MPEG-DASH(Dynamic Adaptive Streaming over HTTP)

je adaptívna technológia streamovania dátového toku, ktorá umožňuje vysoko kvalitné streamovanie mediálneho obsahu cez internet, ktorý je dodávaný z konvenčných webových serverov HTTP. 
Každý segment obsahuje krátky čas prehrávania obsahu, ktorý môže trvať niekoľko hodín, napríklad multimediálny obsah z youtube,netflix,twich. 


### OpenFlow 
Je komunikačný protokol, ktorý umožňuje prístup k prepojovacej rovine sieťového prepínača alebo smerovača cez sieť.
### Mininet 
Je emulátor siete, ktorý vytvára sieť virtuálnych hostiteľov, prepínačov, ovládačov a odkazov. Mininet hostitelia prevádzkujú štandardný sieťový softvér Linux a jeho prepínače podporujú OpenFlow pre vysoko flexibilné vlastné smerovanie a softvérové ​​siete.
*Podporuje ľubovoľné vlastné topológie a obsahuje základnú sadu parametrizovaných topológií
*Poskytuje priamu a rozšíriteľnú Python API pre vytváranie a experimentovanie so sieťami