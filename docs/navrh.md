# Návrh

V zadaní plánujeme postupovať podľa metodológií v článku, na ktoré sa zadanie odvoláva. Taktiež použijeme totožnú konfiguráciu a parametre pre DASH doručovania obsahu. Experimentálna zostava pozostáva z nasledujúcich elementov: 
* Apache HTTP Server (verzia httpd-2.4.29)
* Mininet network emulator (verzia 2.2.1)
* Klient PC s MPEG-DASH prehrávačom
* Prispôsobený web rozhranie
* MySQL RDBMS

![topology](https://github.com/aks-2017/semestralne-zadania-semestralne-zadanie-xbakonyi-xnagya3/blob/master/docs/topology.png)

## Príprava DASH obsahu

DASH obsah sa vygeneruje pomocou bitcodin služby, ktorá zakóduje súbor „nieconajdeme.mkv“ do formátu MPEG-DASH, ktorá má široký výber bitových rýchlostí. Pre streamovanie videa použijeme nasledujúce bitové rýchlosti: 4 Mbps, 3 Mbps, 2.4 Mbps, 1.5 Mbps, 1.1 Mbps, 0.8 Mbps a 0.5 Mbps. Súbory sa nahrajú na Apache server a následne sa prenesú cez HTTP protokol. 