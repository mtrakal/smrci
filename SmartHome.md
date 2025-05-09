# Smart Home

Postavené na Home Assistant + Loxone? Asi, nic lepšího jsem nenašel.

## Postupně nutné

- **MoistureGuard (nebo obdoba) - měření vlhkosti konstrukce**
- spotová elektřina a aktuální cena (zapínání bojleru, dobíjení baterií ze sítě, nabíjení EV?)
- dle předpovědi počasí plánovat nutnost nákupu na spotu, šetření (počasí a predikci výroby FVE zvládá Home Assistant + [Forecast Solar](https://www.home-assistant.io/integrations/forecast_solar))
- v koupelně (asi dle rozsvícení + následného zhasnutí / samostatného tlačítka) se zapne na plný výkon odtah z rekuperace (a zůstává běžet nějakou dobu aby vytáhlo vlhkost). Případně čidlo vlhkosti?
- v kuchyni (asi dle zapnutí digestoře / samostatného tlačítka) se zapne na plno odtah rekuperace
- malé osvětlení na chodbě se zapíná na pohyb a nastavuje intenzitu dle denní hodiny, nebo prostě svítí tlumenou žlutou
- dle zvyšující se teploty u krbu (pokud se nezvýšila teplota poslahovky) se zapne nasávání rekuperace na vyšší výkon - doohřev ostatních místností a utlumí podlahovka
- dle předpovědi počasí / termostatů se spíná podlahovka (a v závislosti na krbu/rekuperaci)
- vnitřní a venkovní teplota
- vlhkost
- hlídání hladiny v akumulační nádrži (ovládání ventilu, aby se dopustila z kohoutku na splachování). Vyřešit pomocí [hlídače hladiny 12V](https://www.laskakit.cz/xh-m203-hlidac-hladiny-vody-12v--230vac/) + 2× [plovákového senzoru](https://www.laskakit.cz/arduino-plovakovy-senzor-vodni-hladiny/) + libovolný [elektromagnetický ventil NC, 12V](https://www.elventil.cz/elektromagneticky-ventil-0-10bar-g3/8-12v-nc-f.s.a.)
- CO2 senzor? Má smysl, když rekuperace jede vlastně nonstop?
- dle predikce výroby FVE nahřívat bojler, baterie, EV
- hlásiče požáru (počítám, že musí být už dneska běžně) - [AQARA Smoke Detector (SD-S01D)](https://oleje-pema.cz/zbozi/aqara-smoke-detector-sd-s01d-zigbee-3-0-kourovy-senzor_773495?srsltid=AfmBOorhxFq5qiRyybxDnX2qB8aJBxmoy74xMB4spCe94HRBJHkdtUwz) jde napojit do HA/Zigbee, 10 let baterie, nemusí mít nějaké certifikáty/homologace od hasičů apod?
- Spot umí řídit i pro Solax a další střídače např. [Proteus od DeltaGreen](https://www.deltagreen.cz/proteus).
- Vytěžovač FVE [WATTrouter MX](https://solarcontrols.cz/cz/wattrouter_mx.html) + spínací relátka/pwm. Případně udělat přes Loxone / HA / ESP32 (ale asi zbytečně moc práce co se nezaplatí)

## Hezké

- osvětlení se k večeru mění intenzita (ikea žárovky, Home Assistant nebo ikea režimy) - není nutné mít relátka ani stmívače
- osvětlení kolem domu se zapne se setměním a vypne např. v 11
- vánoční osvětlení se zapne v prosinci a skoncí koncem ledna? (To už jsou fakt kraviny na Home assistanta / loxone)
- [meteostanice](https://homeassistant-cz.cz/viewtopic.php?t=1349&start=50) Sencor SWS12500 / SWS 16600 WiFi SH

## Nutno vyřešit

- co zvládne sám Home Assistant
- co všechno na něj půjde napojit
- bude potřeba Loxone a k čemu a kolik extension modulů

## Dostupné varianty

- Home Assistant (řeší pouze SW stránku)
  - ale má [ESPHome](https://esphome.io/) pro integraci pomocí ESP32 mikrokontrollerů snad na cokoliv
  - [SmLight SLZB-06](https://smlight.tech/manual/slzb-06/) zigbee / mqtt brána (LAN + wifi)
  - Ikea Smart home + ZHA / Home Assistant
    - [Senzor úniku vody](https://www.ikea.com/cz/cs/p/-60504352)
    - [Pohybový senzor](https://www.ikea.com/cz/cs/p/-90504341)
    - [Senzor okenní / dveřní](https://www.ikea.com/cz/cs/p/-80504308)
    - [Senzor kvality vzduchu](https://www.ikea.com/cz/cs/p/-80515910) + [ESP32 od Lásky](https://www.laskakit.cz/laskakit-esp-vindriktning-esp-32-i2c/#relatedFiles) + [CO2 senzor](https://www.laskakit.cz/laskakit-scd41-senzor-co2--teploty-a-vlhkosti-vzduchu/)
  - Tuya 
    - [časovače wifi relé Tuya](https://allegro.cz/nabidka/wifi-rele-16a-s-merenim-proudu-tuya-smart-14206911149) funguje ale potřebuje Token z Tuya aplikace
    - [Tuya Zigbee WiFi Temperature And Humidity Sensor](https://www.aliexpress.com/item/1005006534648116.html) funguje krásně přes SLZB-06 bránu
    - [Tuya senzor na okna/dveře - zigbee](https://www.aliexpress.com/item/1005008154245742.html)
  - Lidl Livarno (je rebrandovaná Tuya)
    - Světla i ovladač funguje přes Tuya app, nejspíš půjde napojit i napřímo, protože jede na Zigbee (nezkoušel jsem zatím)
  - [Dingtian relé deska s DI](https://www.dingtian-tech.com/en_us/index.html) - až 32 vstupů a relé výstupů, má podporu pro HA, Loxone, ... [na aliexpressu](https://dtwonder.aliexpress.com/store/1228401)
- Loxone - drahý jak prase, ale obecně funkční, uzavřený systém, velká komunita na [Vodnici.net](https://www.vodnici.net/community/main-category/)
- Siemens LOGO Home (výrazně levnější varianta Loxonu - původně z průmyslu, 24V systém, PLCčka)
- Pro světla DALI sběrnice?
- [Logic machine](https://openrb.com/logicmachine5/) a [diskuze odtud](https://www.vodnici.net/community/vse-o-stavbe-domu/elektro-rozvadec/paged/84/)
- [Teco Foxtrot](https://www.tecomat.cz/products/cat/cz/plc-tecomat-foxtrot/foxtrot-2-zakladni-moduly-a-prislusenstvi-100/)