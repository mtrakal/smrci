# Zapojení Elektřiny

## Požadavky:

- FVE a ČEZ je možné úplně oddělit (v případě poruchy zdroje X přepnout pouze na zdroj Y - bypass zdroje X)
- FVE funguje v hybridním 3f. režimu (může dodávat do sítě, ale nechceme)
- FVE může:
  - nahřívat bojler
  - dobíjet baterie (jde i ze sítě - dle spotu a výhodnosti - Loxone?)
  - dobíjet EV (jde i ze sítě - dle spotu a výhodnosti - Loxone?)
  - provozovat většinu domácnosti (primárně všechno asi krom podlahového vytápění)
- Bateriový systém + EV powerbanka (V2L a V2H)
  - napájí chod domácnosti (omezený rozsah)
    - světla
    - vybrané označené zásuvky
    - smart home / servery / internet
    - lednice
    - Domovní vodárna pro splachování
    - varná deska?
    - rekuperace?
    - ČOV?
  - vypomáhá baterie přes den FVE s vykrytím špiček na fázi (asymetrie střídače, nebo bude brát ze sítě, protože to střídač nedokáže obsloužit)?
  - může v budoucnu dodávat do sítě (není nutné, ani nevím zda žádané)
- Světla
  - rozmyslet, zda se spínají pomocí relé v TM a vypínače jsou pouze tlačítka s UTP/FTP, nebo vypínače na stěně.
  - světla tahat ideálně CYKY 5x1.5mm pro možnost dvou okruhů v jednom místě?
  - LEDky třeba na 24V? Nemusely by jít přes střídač z baterií.
- Rekuperace
  - by měla být zálohována pro případ, že vypadne proud v zimě, tak může rozvádět teplo od kamen (jediný jiný zdroj tepla než elektrický)

## TZB:

- kamerový systém (vlastní na Synology)
- bezpečnostní systém (alarm, okna, má to vůbec smysl)?
- protipožární systém?
- moisture guard ve stěnách?
- [SmartHome](./SmartHome.md)

## Zapojení rozvodů, návrh

```mermaid
classDiagram
  note "Schéma zapojení elektrických rozvodů"
  
  SvodPřepětí --> ZemnicíPásek
  HlavníRozvaděč --> SvodPřepětí
  Splitter --> SvodPřepětí
  Splitter <-- PřívodČEZ
  Splitter <-- FveModuly
  Splitter --> Střídač
  Střídač --> HlavníRozvaděč
  HlavníRozvaděč --> PodlahovéTopeníPR
  HlavníRozvaděč --> Bojler
  
  class HlavníRozvaděč["Hlavní rozvaděč"] {
    Hlavní 3f jistič
    Podlahové topení hlavní jistič
    
    ČOV dmychadlo (zálohované)
    Domovní vodárna pro splachování (zálohované)
    Hlídání stavu vody v retenční nádrži
    
    Pokoj Tobi - zásuvky (zálohováno)
    Pokoj Tobi - světla (zálohováno)
    
    Pokoj Niky - zásuvky (zálohováno)
    Pokoj Niky - světla (zálohováno)

    Ložnice - zásuvky (zálohováno)
    Ložnice - světla (zálohováno)

    Pracovna - zásuvky (zálohováno)
    Pracovna - světla (zálohováno)

    Koupelna malá - zásuvka - nezálohováno
    Koupelna malá - světlo (zálohováno)
    Koupelna malá - odtah vlhkosti (zálohováno)
    Koupelna malá - žebřík / sušák ručníků - nezálohováno

    Koupelna velká - zásuvka - nezálohováno
    Koupelna velká - světlo (zálohováno)
    Koupelna velká - odtah vlhkosti (zálohováno)
    Koupelna velká - sušička - nezálohováno
    Koupelna velká - pračka - nezálohováno
    Koupelna velká - žebřík / sušák ručníků - nezálohováno

    Kuchyň - zásuvky (zálohováno)
    Kuchyň - varná deska 3f. - zálohováno?
    Kuchyň - lednice (zálohováno)
    Kuchyň - trouba
    Kuchyň - světla (zálohováno)
    Kuchyň - digestoř - zálohováno?
    Kuchyň - myčka nádobí - nezálohováno
    
    Obývák - světla (zálohováno)
    Obývák - zásuvky (zálohováno)
    
    Chodba - světla (zálohováno)
    Chodba - zásuvka - nezálohováno
    
    Předsíň - světla (zálohováno)
    Předsíň - zásuvka - nezálohováno
    
    TM - světlo (zálohováno)
    TM - zásuvky (zálohováno)
    TM - rack / internet / smarthome (zálohováno)
    TM - rekuperace (zálohováno)
    TM - Bojler - 2 patrony - FVE + ČEZ - dvoupólový jistič? - nezálohováno
    TM - Sušák na boty - nezálohováno
    
    Spižírna - světla (zálohováno)
    Spižírna - zásuvky - nezálohováno
    
    WallBox 1 (V2L/V2H - může dodávat do domu)
    WallBox 2 (V2L/V2H - může dodávat do domu)
    
    Terasa - osvětlení (zálohováno)
    Terasa - zásuvky (zálohováno)
    
    Půda - osvětlení (zálohováno)
    Půda - zásuvky (zálohováno)
    
    Exteriér - vánoční světýlka s časovačem v HR (nezálohováno) 
    Exteriér - osvětlení kolem domu (zálohováno)
  }
  
  class ZemnicíPásek["Zemnící pásek"]

  class PřívodČEZ["Přívod ČEZ"] {
      samostatně napájená kůlna
      tam už napojení na FVE asi nedává smysl
  }

  class SvodPřepětí["Svod přepětí"]

  class FveModuly["FVE moduly"] {
      Odhadem kolem 30-35 panelů 500 Wp
  }
  
  class Střídač {
      LAN připojení
      Připojení baterií
      Připojení FVE_modulů
      Připojení k síti
      Příprava na V2L/V2H
  }

  note for Splitter "By měl zajišťovat možnost odpojit libovolný možný zdroj." 
  class Splitter {
    Bypass/odpojení zdroje FVE/ČEZ
    Odpojení modulů na střeše
    Odpojení baterií
    Odpojení EV
    Jistič pro střídač
  }

  class Bojler {
    síťová patrona
    FVE patrona
  }

  class PodlahovéTopeníPR["Podlahové topení\npodružný rozvaděč"] {
    Koupelna velká
    Koupelna malá
    Dětský pokoj Niky
    Dětský pokoj Tobík
    Ložnice
    Pracovna
    Obývací pokoj
    Kuchyňě
    Chodba
  }

```

## Odhadovaný výkon FVE

- [Kalkulačka výkonu FVE](https://re.jrc.ec.europa.eu/pvg_tools/en/)
- Očekávaný příjem FVE (měsíční) v **letních měsících: 1800 kW**.
- Očekávaný příjem FVE (měsíční) v **jarních/podzimních měsících: 900 kW**.
- Očekávaný příjem FVE (měsíční) v **zimních měsících: 450 kW**.

### Graf výroby FVE podle měsíců ve Smrčí při sklonu střechy 40° a otočení na jih.

![Graf ](imgs\fve_15kwp.svg)

## Odhadovaná spotřeba domu (měsíční, kWh)

```mermaid
sankey-beta

%% source,target,value
"Nutna spotreba","Osvetleni",60
"Nutna spotreba","Vareni",90
"Nutna spotreba","COV",60
"Nutna spotreba","Ohrev vody",90
"Nutna spotreba","Rekuperace",60
"Nutna spotreba","Smart home / internet / apod.",90
"Nutna spotreba","Drobne spotrebice",60
"Nutna spotreba","Kuchynske spotrebice",30
"Nutna spotreba","Lednice",45
"Nutna spotreba","Mycka",30
"Nutna spotreba","TV",15
"Nutna spotreba","Pracka + susicka",90
"FVE","Dobiti baterioveho uloziste",240
"Topeni","El. podl. topeni", 1500
"EV","Elektroauta", 1500

"Odhadovana spotreba","Nutna spotreba", 720
"Odhadovana spotreba","FVE", 240
"Odhadovana spotreba","EV", 1500
"Odhadovana spotreba","Topeni", 1500
```

Z grafu je vidět, že 15 kWp (450 až 1800kWh) od jara do podzimu bez problémů zvládá kompletní chod domácnosti s přebytkem i včetně nabíjení bateriového úložiště (únor až říjen).

Zbývá i něco málo pro dobíjení elektroaut (pokud někdy budou).

Zimu je potřeba hodně dotovat ze sítě, hlavně kvůli topení. Běžný chod domácnosti by se z velké části dal vykrýt i v zimě.

## Komponenty

- Rozvaděč
  - Silnoproud [cubico-ip40-1800x600x400mm](https://www.schrack.cz/eshop/skrine-pro-rozvadece-a-rozvodnice/skrine-pro-rozvadece-cubico-ip40/skrine-pro-rozvadece-cubico-ip40/skrin-cubico-ip40-1800x600x400mm-1k-ec186040.html) - info z [Vodnici.net](https://www.vodnici.net/community/loxone-a-arduino/jak-zacit-v-novostavbe/#post-40512) jen mi bude stačit tak poloviční než tam má
  - Síťový rozvaděč/rack [Triton 19" 18U/500mm](https://www.bscom.cz/triton-19-rozvadec-jednodilny-18u-500mm-odnimatelne-bocni-kryty-rua-18-as5-cax-a1_d352200/) - 600š×500h×900v
- Relé / časovače
  - [časovače wifi relé Tuya](https://allegro.cz/nabidka/wifi-rele-16a-s-merenim-proudu-tuya-smart-14206911149) na venkovní světla (má Maťo)
- [SmartHome](./SmartHome.md)

## Software

- [SchrackDesign](https://www.schrack.cz/schrack-digital/schrack-design) - návrhy elektrorozvaděčů
- [SchrackDesign katalogy produktů](https://www.schrack.cz/eshop/katalogy/katalogy.html?catId=5267282)