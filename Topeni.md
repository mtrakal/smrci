# Vytápění

V RD budeme mít 3 potenciální zdroje tepla. Podlahové elektrické vytápění, krb a rekuperaci.

## Podlahové

- Elektrické rohože těsně pod nášlapnou vrstvou.

#### Krytina:

- [Detail k podlaze](./Podlaha.md)
- Dlažba a lepené dřevěné podlahy.

## Rekuperace

[Předpokládaný návrh zapojení rekuperace. (Figma projekt)](https://www.figma.com/design/HXPyJgDuI7QUvlEugycx2D/Vzduchotchnika?node-id=0-1&t=dSRtvnLBsCDfXFPA-1)

Je potřeba počítat, že odtah rekuperace bude muset být na střechu nebo veden podhledem někam ke kuchyni aby splnil odstup přívodu/výfuku od sebe.

![](./imgs/vzduchotechnika.png "Vzduchotechnika")

E-shopy:

- [rekuperacka.cz](https://www.rekuperacka.cz/)
- [termikoneshop.cz](https://www.termikoneshop.cz/) - nabízí [odkud přebytečného materiálu](https://www.termikoneshop.cz/prebytecny-material--nevadi/)!
- [Ventishop](https://www.ventishop.cz/)

### Požadavky

- Klapky na jednotlivé místnosti (možnost uzavřít pracovnu + obývák a nechat profukovat pouze ložnice v noci)
- naboostovat samostatně wc, koupelnu, digestoř / jednotlivé pokoje pro "přitopení"
- samostatný přícuc tepla od krbových kamen (nemusí jít nutně přes rekuperák, ale klidně napřímo do místností? Výhoda
  asi víc tepla, nevýhoda možného přenosu smradu?)
- sběrnice modbus nebo ideálně vlastní API a LAN konektor / loxone integrace
- tichá
- možnost trošku víc chladit / topit
- nesmí zamrzat (předehřev)
- uhlíkový filtr / filtr mikročástic - Brink Pure Induct před jakoukoliv reku? Dávalo by smysl?

[Jak vybrat komponenty pro rozvody vzduchu](https://www.termikoneshop.cz/kompletni-navod--jak-vybrat-komponenty-pro-rozvody-vzduchu/)

### Nice to have

- možnost napojit na chlazení / ohřev (vzduch-vzduch, musí být příprava z TM ven na tepelko!)

### Modely

#### [Atrea Duplex 360 Pro-V - SVT33621](https://atrea.eu/cs/vyrobky/duplex-pro-pro-v/) (56 000 Kč)

#### [Atrea Rx5](https://atrea.eu/cs/vyrobky/duplex-r5/) (105 000 Kč)

- [technický list](https://atrea.eu/_files/documents/253_LgLEGA5F.pdf)
- rozvody čistého vzduchu 200mm, špinavého 160mm
- modbus TCP, webserver s XML se všemi daty
- napojení na loxone přes modbus
  a [vodníci konfigy](https://www.vodnici.net/community/diy-navody-loxone-arduino/riadenie-rekuperacie-atrea-z-loxone/paged/2/)
- Přístup do servisního menu (Odkaz na servisni menu je na strance uzivatelskeho menu vpravo dole.) je tří místné a je
  to číslo dne v týdnu, číslo zítra a číslo pozítří. Např. v úterý je to 234, v pátek je to 567, v neděli je to 712, ...
  ....tak už jsem na to přišel....ono totiž heslo nejde zadat v microsoft edge a to na PC ani na mobilu...čili budete-li
  mít někdo stejný problém jako já, použijte chrome
- [čtení dat z XML](https://forum.tzb-info.cz/133605-atrea-data-logging-monitoring-cez-webserver)
- [Ofiko Loxone modul](https://library.loxone.com/detail/atrea-rd5-1295/overview)
- [Home Assistant integrace](https://github.com/JurajNyiri/HomeAssistant-Atrea)

#### [Zehnder ComfoAir Q350 TR](https://www.zehnder-rekuperace.cz/zehnder-comfoair-q350-tr/) (108 263 Kč)

#### [Brink Flair 325](https://www.storc.cz/cs/produkt/flair-325400) 90 000 Kč

#### [Brink Renovent Sky 350](https://www.storc.cz/cs/produkt/renovent-sky-300) 65 000 Kč

#### [Nilan Comfort 350 TOP Polar](https://nilan.cz/comfort-350-top/) (72 500 Kč)

- [technický list](https://nilan.cz/wp-content/uploads/2023/05/Comfort-350-Top-Produktovy-list.pdf)

#### [Nilan VPL 10 TOP](https://nilan.cz/vpl-15-top/) (99 500 Kč)

Aktivní rekuperace (používá tepelné čerpadlo), takže vlastně už ani není moc standardní reku, jak ji známe, jako spíš malé samotné tepelko vzduch/vzduch.

- [technický list](https://nilan.cz/wp-content/uploads/2023/03/PL2303_VPL-15-TOP.pdf)

#### [Regulus Sentinel Advance SX](https://www.regulus.cz/cz/rekuperacni-jednotka-sentinel-advance-sx-svt-9238) (105 754 Kč)

### Finální výběr

#### Jednotka

Rekuperační jednotka od [Atrea Ra5](https://atrea.eu/cs/vyrobky/duplex-r5/) zvolena jako asi nejlepší možná volba s přihlédnutím na:

- pořizovací cenu
- pravidelné náklady (filtry)
- možnost sehnat někoho na servis / údržbu
- poměr cena/výkon/hlučnost

#### Rozvody

- [Kulaté 90mm](https://www.termikoneshop.cz/90mm-system-potrubi/) (ploché [Zehnder 51mm](https://www.termikoneshop.cz/ploche-potrubi/) jsou zbytečně drahé, blbě se budou čistit)
- koncovky Zehnder ComfoValve Luna S125 (přívod) / Luna E125 (odvod) nebo jiné kvalitní co nebudou "ofukovat" pod výustkem

## Krbová kamna (kachlová)

- nezapomenout na nezávislý přívod vzduchu!!!

Nejspíš [Hass+Sohn Treviso Mini](https://www.haassohn-rukov.cz/produkty/krbova-kamna/04343-kachlova-kamna-treviso-mini) / [Loreto](https://www.haassohn-rukov.cz/produkty/archiv/krbova-kamna/03314-1-kachlova-kamna-loreto) / [Laguno](https://www.haassohn-rukov.cz/produkty/archiv/krbova-kamna/03314-kachlova-kamna-lugano)

Něco jako
[![](https://www.van2o.lt/cache/images_product_S_1_1000x500/treviso%20ii%20-%20papildoma.jpg)](https://www.van2o.lt/krosneles-zidiniai/kieto-kuro-krosneles/plienine-krosnele-haas-sohn-treviso-ii-8-kw.html?keyword=pl)

## Elektrické žebříky

- Elektrické žebříky / přímotopy v koupelnách na ručníky
- sušák na boty v TM