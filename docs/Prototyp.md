# Kontrolný bod 2. - Prototyp

Cieľom nášho prototypu bolo vytvorenie funkčnej siete kombináciou Mininetu a real IP siete.

## PC0 - Virtuálny stroj - Mininet

Vytvorenie a nastavenie siete realizuje skript create_network.py. IP adresy boli nastavené podľa vedeckého článku, ktoré vidíme v tabuľke 1. Na smerovanie využívame OS Routing, t.j. smerovanie operačného systému Linux. Taktiež sa vyžaduje povolenie forwardingu na OS, aby sme dokázali prepojiť reálnu sieť so sieťou v emulátori mininet. Skript vytvorí TClink link1, pomocou ktorého dokážeme meniť priepustnosť linky. Zmenu v stanovených časových bodoch zabezpečuje framework minievents, do ktorého vstupuje ako argument JSON súbor s názvom bw.json, kde sú špecifikované udalosti „editlink“ a parametre ako linka ktorá sa má meniť, čas, kedy sa má daná udalosť nastať a hodnota priepustnosti, ktorá sa má nastaviť v link1.

## PC1 - Server

Následne sme vytvorili na strane servera DASH obsah pomocou programov x264 a MP4box. 
Zo stránky http://jell.yfish.us sme stiahli video, ktoré slúži na testovanie bitratov. Video bolo rozsegmentované na DASH obsah s bitratmi 4 Mbps, 3 Mbps, 2.4 Mbps. 1.5 Mbps, 1.1 Mbps, 0.8 Mbps a 0.5 Mbps. Segmenty sme nahrali na Apache web server a upravili konfiguračný súbor aby prehrávač dokázal rozoznať a vypýtať segmenty rôznych bitretov.

## PC2 - Klient

Na strane klienta sme prispôsobili bitmovin prehrávač pomocou html a javascriptu. Používame free trial verziu na 30 dní, ktorá postačuje na dodržanie termínu na odovzdanie už finálnej verzie produktu.