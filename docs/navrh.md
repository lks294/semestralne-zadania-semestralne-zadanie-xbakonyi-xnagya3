# Návrh

V zadaní plánujeme postupovať podľa metodológií v článku, na ktoré sa zadanie odvoláva. Taktiež použijeme totožnú konfiguráciu a parametre pre DASH doručovania obsahu. Experimentálna zostava pozostáva z nasledujúcich elementov: 
* Webserverebserver
* Mininet network emulator
* Klient PC s MPEG-DASH prehrávačom
* Prispôsobený web rozhranie
* Databáza

![topology](https://github.com/aks-2017/semestralne-zadania-semestralne-zadanie-xbakonyi-xnagya3/blob/master/docs/topology.png)

## Príprava DASH obsahu

DASH obsah sa vygeneruje pomocou bitcodin služby, ktorá zakóduje súbor „nieconajdeme.mkv“ do formátu MPEG-DASH, ktorá má široký výber bitových rýchlostí. Pre streamovanie videa použijeme nasledujúce bitové rýchlosti: 4 Mbps, 3 Mbps, 2.4 Mbps, 1.5 Mbps, 1.1 Mbps, 0.8 Mbps a 0.5 Mbps. Súbory sa nahrajú na Apache server a následne sa prenesú cez HTTP protokol. 

## Mininet prostredie a siete

Mininet spustíme na virtuálnom stroji, ktorý beží na reálnom notebooku dvoma sieťovými rozhraniami, ktoré nakonfigurujeme na mód „premostenia“. K PC s VM sa následne pripoja ďalšie stroje ako server a klient. 
Z webserveru sa následne cez HTTP protokol prenesie streamovaný obsah na klienta.

## Obmeňovanie šírky pásma

Náš program bude schopní ladiť šírku pásma medzi virtuálnou a reálnou sieťou v špecifikovaných časoch. Toto dosiahneme vytvorením json súborov, v ktorých špecifikujeme udalosti a časy, kedy majú nastať zmeny pásmovej šírky. 
Zmeny sa budú vytvárať v istom vzore.

![bandwidthShaping](https://github.com/aks-2017/semestralne-zadania-semestralne-zadanie-xbakonyi-xnagya3/blob/master/docs/bandwidthShaping.PNG)

## Klient

Na klientovom stroji bude bežať MPEG-DASH prehrávač. Nakonfiguruje sa tak, aby posielal aktuálnu bitovú rýchlosť prehrávaného segmentu videa. 

## Návrh experimentov

Prvým krokom je zvoliť si čas trvania experimentov. V zdrojovom článku si vybrali čas 120 sekúnd a skonštatovali, že je postačujúci na merania. My navrhujeme použiť 360 sekúnd, kvôli presnejším meraniam. Každých 30 sekúnd zmeníme pásmovú šírku a sledujeme, ako sa sieť dokáže prispôsobiť zmenám.
Na overenie relevancie experimentov zoberieme výsledky zo zdrojového článku a porovnáme ich s našimi výsledkami.  

