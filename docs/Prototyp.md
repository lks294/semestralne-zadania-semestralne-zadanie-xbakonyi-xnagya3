# 2. KONTROLNÝ BOD [ PROTOTYP ]  

Pre tento kontrolný bod sme si vymedzili niekoľko cieľov.

* Inštalácia potrebných koponentov
    * Floodlight v1.1
    * SOFTmon
* Vytvorenie testovacích topológií
* Prepojenie SOFTmon s Floodlight riadiacov jednotkov
* Testovanie SOFTmon meraní nad vytvorenými topológiami

-------------------

## INŠTALÁCIA POTREBNÝCH KOMPONENTOV

Pre správne zapojenie SOFTmon aplikácie do vývojového prostredia je potrebné dodržiavať nasledujúce kroky.

pozn. Kroky sú uvádzané pre operačný systém Windows 

Požadovaný softvér:

* VirtualBox;
* PuTTY;
* MININET 2.2.2 ( 32 bit );
* JAVA v.7;
* Floodlight v.1.1;
* OpenFlow v.1.3.

### MININET INŠTALÁCIA

Podrobný tutoriál je možne nájsť na stránke [MININET](http://mininet.org/download/)


1. Stiahnuť si [Mininet VM Image v.2.2.2 ( 32 bit )](https://github.com/mininet/mininet/wiki/Mininet-VM-Images)
2. Stiahnuť a nainštalovať softvéer na virtualizáciu. Odporúča sa [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
3. Kliknúť na `.ovf` subor v Mininet `.zip`, stiahnutý v kroku 1. a ten sa otvorí vo VirtualBox
4. Nastaviť `Network` v nastaveniach, na `NAT` a `HOST-ONLY`
5. Sputiť Mininet, meno: `mininet`, heslo: `mininnet`
6. Zadať príkaz `sudo dhclient eth1`, ktorý vytvorí nový pristupový bod   
7. Pripojiť sa na mininet pomocou [PuTTY](http://www.putty.org) s povoleným `-X forwarding`


### FLOODLIGHT INŠTALÁCIA

Podrobný tutoriál je možné nájsť na stránke [FLOODLIGHT](https://floodlight.atlassian.net/wiki/spaces/floodlightcontroller/pages/1343544/Installation+Guide)

1. Stiahnuť potrebný softvér pre floodlight pomocou príkazu 
```
$ sudo apt-get update
$ sudo apt-get install build-essential openjdk-7-jdk ant maven python-dev eclipse
```
2. Inštalácia Floodlight
```
$ git clone git://github.com/floodlight/floodlight.git -b v1.1
$ cd floodlight
$ git submodule init
$ git submodule update
$ ant
 
$ sudo mkdir /var/lib/floodlight
$ sudo chmod 777 /var/lib/floodlight
```

3. <a name="flood">Spustenie Flodlight</a>

```
$ cd floodlight
$ java -jar target/floodlight.jar
```

4. Pomocné príkazy v prípade, že niektorý z predchádzajúcich krokov nefungoval

```
$ sudo apt-get update
$ sudo apt-get install software-properties-common
$ java -version
```


### INŠTALÁCIA SOFTmon

pozn. SOFTmon aplikáciu nie je potrebné inštalovať na MininetVM

1. Stiahnuť SOFTmon z git repozitára

```
$ git clone https://github.com/mha-net/SOFTmon
```

2. Spustenie SOFTmon v MININET

```
$ cd SOFTmon/jar
$ java -jar SOFTmon-1.0.8_OF13_WIN.jar &
```

###






## VYTVORENIE TESTOVACÍCH TOPOLÓGIÍ

1. Základná MININET topológia

```
$ sudo mn --controller=remote,ip=<ip adresa riadiacej jednotky>,port:6653 --switch ovsk,protocols=OpenFlow13
```

2. Topológia s hĺbkou 2 a vetvením 3
```python
from mininet.topo import Topo

class MyTopo( Topo ):
    "Topology used in SOFTmon article"
    def __init__( self ):
        "Create sustom topo"
        
        # Initialize topology
        Topo.__init__( self )
        
        # Add host and switches
        h1 = self.addHost( 'h1' )
        h2 = self.addHost( 'h2' )
        h3 = self.addHost( 'h3' )
        h4 = self.addHost( 'h4' )
        h5 = self.addHost( 'h5' )
        h6 = self.addHost( 'h6' )
        h7 = self.addHost( 'h7' )
        h8 = self.addHost( 'h8' )
        h9 = self.addHost( 'h9' )
        s1 = self.addSwitch( 's1' )
        s2 = self.addSwitch( 's2' )
        s3 = self.addSwitch( 's3' )
        s4 = self.addSwitch( 's4' )


        # Add links
        self.addLink( s2, s1 )
        self.addLink( s3, s1 )
        self.addLink( s4, s1 )


        self.addLink( h1, s2 )
        self.addLink( h2, s2 )
        self.addLink( h3, s2 )

        self.addLink( h4, s3 )
        self.addLink( h5, s3 )
        self.addLink( h6, s3 )

        self.addLink( h7, s4 )
        self.addLink( h8, s4 )
        self.addLink( h9, s4 )


topos = { 'mytopo': ( lambda: MyTopo() ) }
```
```
$ sudo mn --custom <cesta k súboru>/<názov súboru>.py --topo mytopo --controller=remote,ip=<ip adresa riadiacej jednotky>,port:6653 --switch ovsk,protocols=OpenFlow13
```

3. Topolopológia ASOK

```python
from mininet.topo import Topo

class MyTopo( Topo ):
    "Topology used in SOFTmon article"
    def __init__( self ):
        "Create sustom topo"
        
        # Initialize topology
        Topo.__init__( self )
        
        # Add host and switches
        asok04 = self.addHost( 'asok04' )
        asok05 = self.addHost( 'asok05' )
        asok06 = self.addHost( 'asok06' )
        asok07 = self.addHost( 'asok07' )
        asok08 = self.addHost( 'asok08' )
        asok13 = self.addHost( 'asok13' )
        asok14 = self.addHost( 'asok14' )
        asok15 = self.addHost( 'asok15' )
        asok16 = self.addHost( 'asok16' )
        nec101 = self.addSwitch( 'nec101' )
        nec301 = self.addSwitch( 'nec301' )
        nec102 = self.addSwitch( 'nec102' )
        nec201 = self.addSwitch( 'nec201' )
        nec302 = self.addSwitch( 'nec302' )
        nec202 = self.addSwitch( 'nec202' )


        # Add links
        self.addLink( nec101, nec301 )
        self.addLink( nec101, nec302 )

        self.addLink( nec102, nec301 )
        self.addLink( nec102, nec302 )

        self.addLink( nec201, nec301 )
        self.addLink( nec201, nec302 )

        self.addLink( nec202, nec301 )
        self.addLink( nec202, nec302 )


        self.addLink( asok04, nec101 )
        self.addLink( asok05, nec101 )
        self.addLink( asok06, nec101 )

        self.addLink( asok07, nec102 )
        self.addLink( asok08, nec102 )

        self.addLink( asok13, nec201 )
        self.addLink( asok14, nec201 )

        self.addLink( asok15, nec202 )
        self.addLink( asok16, nec202 )


topos = { 'mytopo': ( lambda: MyTopo() ) }

``` 
```
$ sudo mn --custom <cesta k súboru>/<názov súboru>.py --topo mytopo --controller=remote,ip=<ip adresa riadiacej jednotky>,port:6653 --switch ovsk,protocols=OpenFlow13
```




## PREPOJENIE SOFTmon A FLOODLIGHT RIADIACOV JEDNOTKOU

Prepojenie v rámci mininetu:

1. Pripojiť sa na mininet pomocou troch inštancií putty
2. Prvá inštancia: Spustenie [FLOODLIGHT](#flood)
3. Druhá inštancia: Spustenie SOFTmon
4. Tretia inštancia: Spustenie topológie
5. `port` pre FLOODLIGHT nastaviť na `8080`, ide o nechránené pripojenie; inak može dojsť k zamietnutiu spojenia

## TESTOVANIE

Testovanie prebiehalo na všetkých vyššie spomínaných topológiach. Meranie bolo odsledované na `ping` funkcii ako aj s `iperf` testovacím nástrojom.

### MERANIA NA ZÁKLADNEJ TOPOLÓGIÍ


Monitorovanie `ping` funkcie. 


```
$ pingall 

```

![](/testing_screens/screen_ping.png)


Monitorovanie TCP spojenia prostredníctvom `iperf` nástroja.

1. Spustiť Server

```
$ iperf -s -w 130k

```
2. Sputiť Client

```
$ iperf -c 10.0.0.1 -w 130k

```

![](/testing_screens/screen_iperf.png)

![](/testing_screens/server_client.png)




### MERANIA NA TOPOLÓGIÍ S HĹBKOU 2 A VETVENÍM 3

Monitorovanie `ping` funkcie. 


```
$ pingall 

```

![](/testing_screens/screen_ping_topology2-3.png)


Monitorovanie TCP spojenia prostredníctvom `iperf` nástroja.

1. Spustiť Server

```
$ iperf -s -w 1250k

```
2. Sputiť Client

```
$ iperf -c 10.0.0.9 -w 1250k

```

![](/testing_screens/screen_iperf_asok_topology2-3.png)

![](/testing_screens/server_client_asok_topology2-3.png)

### MERANIA NA TOPOLÓGIÍ ASOK 

Monitorovanie `ping` funkcie. 


```
$ pingall 

```

![](/testing_screens/screen_ping_asok.png)


Monitorovanie TCP spojenia prostredníctvom `iperf` nástroja.

1. Spustiť Server

```
$ iperf -s -w 1250k

```
2. Sputiť Client

```
$ iperf -c 10.0.0.7 -w 1250k

```

![](/testing_screens/screen_iperf_asok.png)

![](/testing_screens/server_client_asok.png)


### ROZDIELY SO ZDROJOVÝM ČLÁNKOM

Pri implementácii riešenia sme narazili na problémy spojené s verziami softvéru, ktorý pri písaní článku autory využili. Konkrétne sa jedná o verziu mininetu. V zdrojovom článku je MININET v.2.2.1 pričom mi využívame MININET v.2.2.2. V prototype sme využili iba jeden virtuálny stroj, na ktorom súčasne spúšťame všekty potrebné programy, pričom autori článku využili dve virtuálne stroje pod hlavným operačným systémom. Z dôvodu nedostupnosti ASOK clustra sme sa rozhodli simulovať prostredie v MININET a tak sa môže stať, že výsledky sa budú odlišovať, čo ale neznamená, že aplikácia nefunguje správne.     