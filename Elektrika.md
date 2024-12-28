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
  - vypomáhá FVE s vykrytím špiček na fázi (asymetrie střídače)?
  - může v budoucnu dodávat do sítě (není nutné, ani nevím zda žádané)
- Světla
  - rozmyslet, zda se spínají pomocí relé v TM a vypínače jsou pouze tlačítka s UTP/FTP, nebo vypínače na stěně.
  - LEDky třeba na 24V? Nemusely by jít přes střídač z baterií.
- Koupelny
  - zásuvky nezálohováno, ale možná můžeme spojit se světlem a není třeba vlastní jistič/chránič? V tom případě můžeme zálohovat včetně světel (stejně tam v 95 % nic nebude zapojeného)
- Pokoje dětí / ložnice
  - Stejně jako v koupelně, zda nezálohovat zásuvky stejně jako světla? Max tam bude notebook/tablet/mobil a stolní lampička...

## TZB:
- kamerový systém (vlastní na Synology)
- bezpečnostní systém (alarm, okna, má to vůbec smysl)?
- protipožární systém?
- moisture guarg ve stěnách?

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
    
    Pokoj Tobi - zásuvky - nezálohováno
    Pokoj Tobi - světla (zálohováno)
    
    Pokoj Niky - zásuvky - nezálohováno
    Pokoj Niky - světla (zálohováno)

    Ložnice - zásuvky - nezálohováno
    Ložnice - světla (zálohováno)

    Pracovna - zásuvky (zálohováno)
    Pracovna - světla (zálohováno)

    Koupelna malá - zásuvka - nezálohováno
    Koupelna malá - světlo (zálohováno)
    Koupelna malá - odtah vlhkosti (zálohováno)

    Koupelna velká - zásuvka - nezálohováno
    Koupelna velká - světlo (zálohováno)
    Koupelna velká - odtah vlhkosti (zálohováno)
    Koupelna velká - sušička
    Koupelna velká - pračka

    Kuchyň - zásuvky (zálohováno)
    Kuchyň - varná deska 3f. (zálohováno)
    Kuchyň - lednice (zálohováno)
    Kuchyň - světla (zálohováno)
    Kuchyň - digestoř - zálohováno?
    Kuchyň - myčka nádobí - nezálohováno
    
    Obývák - světla (zálohováno)
    Obývák - zásuvky (zálohováno)
    
    Chodba - světla (zálohováno)
    
    Předsíň - světla (zálohováno)
    
    TM - světlo (zálohováno)
    TM - zásuvky (zálohováno)
    TM - rack / internet / smarthome (zálohováno)
    TM - rekuperace (nezálohováno)?
    TM - Bojler - 2 patrony - FVE + ČEZ - dvoupólový jistič? (zálohováno)?
    
    WallBox 1 (zálohováno)?
    WallBox 2 (zálohováno)?
    
    Venkovní osvětlení (nezálohováno)
    
    Terasa - osvětlení (zálohováno)?
    Terasa - zásuvky
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