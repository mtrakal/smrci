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
  - LEDky třeba na 24V? Nemusely by jít přes střídač z baterií.
- Rekuperace
  - by měla být zálohována pro případ, že vypadne proud v zimě, tak může rozvádět teplo od kamen (jediný jiný zdroj tepla než elektrický)

## TZB:
- kamerový systém (vlastní na Synology)
- bezpečnostní systém (alarm, okna, má to vůbec smysl)?
- protipožární systém?
- moisture guard ve stěnách?

## Zapojení rozvodů, návrh

```mermaid
classDiagram
  note "Schéma zapojení elektrických rozvodů"
  
  SvodPřepětí --> ZemnicíPásek
  Hlavní_Rozvaděč --> SvodPřepětí
  Splitter --> SvodPřepětí
  Splitter <-- PřívodČEZ
  Splitter <-- FVE_Moduly
  Splitter --> Střídač
  Střídač --> Hlavní_Rozvaděč
  Hlavní_Rozvaděč --> Podlahové_Topení_PR
  Hlavní_Rozvaděč --> Bojler
  
  class Hlavní_Rozvaděč {
    Hlavní 3f jistič
    Podlahové topení hlavní jistič
    
    ČOV (zálohované)
    Domovní vodárna pro splachování (zálohované)
    
    Pokoj Tobi - zásuvky - nezálohováno?
    Pokoj Tobi - světla (zálohováno)
    
    Pokoj Niky - zásuvky - nezálohováno?
    Pokoj Niky - světla (zálohováno)

    Ložnice - zásuvky - nezálohováno?
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
    Kuchyň - varná deska 3f. (zálohováno)
    Kuchyň - lednice (zálohováno)
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
    
    Spižírna - světla (zálohováno)
    Spižírna - zásuvky - nezálohováno
    
    WallBox 1 (V2L/V2H - může dodávat do domu)
    WallBox 2 (V2L/V2H - může dodávat do domu)
    
    Venkovní osvětlení - nezálohováno
    
    Terasa - osvětlení (zálohováno)?
    Terasa - zásuvky - nezálohováno
  }
  
  class ZemnicíPásek

  class PřívodČEZ {
      samosttaně napájená kůlna
      tam už napojení na FVE asi nedává smysl
  }

  class SvodPřepětí

  class FVE_Moduly {
      Odhadem kolem 30-35 panelů 500 Wp
  }
  
  class Střídač {
      LAN připojení
      Připojení baterií
      Připojení FVE_modulů
      Připojení k síti
      Příprava na V2L/V2H
  }

  class Splitter {
  %% By měl zajišťovat možnost odpojit libovolný možný zdroj.
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

  class Podlahové_Topení_PR {
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
- Očekávaný příjem FVE (denní) v **letních měsících: 60 kW**.
- Očekávaný příjem FVE (denní) v **jarních/podzimních měsících: 30 kW**.
- Očekávaný příjem FVE (denní) v **zimních měsících: 15 kW**.

### Graf výroby FVE podle měsíců ve Smrčí při sklonu střechy 40° a otočení na jih.
![Graf ](imgs\fve_15kwp.svg)

## Odhadovaná spotřeba domu (denní, kW)

```mermaid
sankey-beta

%% source,target,value
"Nutna spotreba","Osvetleni",2
"Nutna spotreba","Vareni",3
"Nutna spotreba","COV",2
"Nutna spotreba","Ohrev vody",3
"Nutna spotreba","Rekuperace",2
"Nutna spotreba","Smart home / internet / apod.",3
"Nutna spotreba","Drobne spotrebice",2
"Nutna spotreba","Kuchynske spotrebice",1
"Nutna spotreba","Lednice",1.5
"Nutna spotreba","Mycka",1
"Nutna spotreba","TV",0.5
"Nutna spotreba","Pracka + susicka",3
"FVE","Dobiti baterioveho uloziste",8
"Topeni","El. podl. topeni", 50
"EV","Elektroauta", 50

"Odhadovana spotreba","Nutna spotreba", 24
"Odhadovana spotreba","FVE", 8
"Odhadovana spotreba","EV", 50
"Odhadovana spotreba","Topeni", 50
```

Z grafu je vidět, že 15 kWp od jara do podzimu bez problémů zvládá kompletní chod domácnosti s přebytkem i včetně nabíjení bateriového úložiště.

Zbývá i něco málo pro dobíjení elektroaut (pokud někdy budou).

Zimu je potřeba hodně dotovat ze sítě, hlavně kvůli topení. Běžný chod domácnosti by se z velké části dal vykrýt i v zimě.