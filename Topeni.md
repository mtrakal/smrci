# Vytápění

V RD budeme mít 3 potenciální zdroje tepla. Podlahové/stropní elektrické vytápění, krb a rekuperaci.

## Podlahové / stropní elektrické

#### Krytina:

- vybírejte podlahovou krytinu s tepelným odporem menším než 0,15 m2.K/W.
- Ideální krytinou je pro podlahové topení dlažba, má totiž vysokou míru tepelné vodivosti a bude tedy dobře předávat
  teplo. Vhodná je však i řada dalších materiálů, například laminátové a dřevěné krytiny nebo PVC
- Pokud se rozhodnete pro tuto (laminát, dřevěná), je důležité dodržovat maximální výkon topení 100 W/m2, aby
  nedocházelo k tepelné roztažnosti podlahy.

| Typ podlahové krytiny a pořadí vrstev konstrukce                                                                | tloušťka     | tepelná vodivost | odpor kladený vedení tepla  | tloušťka celé konstrukce |
|-----------------------------------------------------------------------------------------------------------------|--------------|------------------|-----------------------------|--------------------------|
|                                                                                                                 | D            | λ                | R λ B                       | dWD                      |
| jednotky                                                                                                        | mm           | W/mK             | m2 K/W                      | mm                       |
| Textilní podlahová krytina                                                                                      | 10           | 0,07             | max 0,15                    | 10                       |
| Parkety<br>Lepící hmota<br>Celkový tepelný odpor konstrukce                                                     | 8<br>2       | 0,2<br>0,2       | 0,04<br>0,01<br>0,05        | 10                       |
| Plastová podlahová krytina např\.PVC                                                                            | 5            | 0,23             | 0,022                       | 5                        |
| Novilon Nova                                                                                                    | 3,2          | 0,25             | 0,0352                      | 3,2                      |
| Novilon Viva                                                                                                    | 2,4          | 0,25             | 0,0264                      | 2,4                      |
| Novilon Prima                                                                                                   | 2,0          | 0,25             | 0,0264                      | 2,0                      |
| Novilux Structura                                                                                               | 2,2          | 0,25             | 0,022                       | 2,2                      |
| Novilux Trafic                                                                                                  | 3,0          | 0,25             | 0,03                        | 3,0                      |
| Marmoleum                                                                                                       | 9,8          | 0,17<br>0,25     | 0,037                       |                          |
| Keramická dlažba<br>Tenké maltové lože<br>Celkový tepelný odpor konstrukce                                      | 10<br>2      | 1<br>1,4         | 0,01<br>0,001<br>0,011      | 12                       |
| Keramická dlažba<br>Maltové lože<br>Celkový tepelný odpor konstrukce                                            | 10<br>10     | 1<br>1,4         | 0,01<br>0,007<br>0,017      | 20                       |
| Korková podlaha                                                                                                 | 10,5         |                  | 0,114                       |                          |
| Desky přírodního nebo umělého kamene v tomto případě mramor<br>Maltové lože<br>Celkový tepelný odpor konstrukce | 15<br><br>10 | 3,5<br><br>1,4   | 0,004<br><br>0,007<br>0,011 | 25                       |
|                                                                                                                 |              |                  |                             |                          |

## Rekuperace

### Požadavky

- Klapky na jednotlivé místnosti (možnost uzavřít pracovnu + obývák a nechat profukovat pouze ložnice v noci)
- naboostovat samostatně wc, koupelnu, digestoř / jednotlivé pokoje pro "přitopení"
- samostatný přícuc tepla od krbových kamen (nemusí jít nutně přes rekuperák, ale klidně napřímo do místností? Výhoda
  asi víc tepla, nevýhoda možného přenosu smradu?)
- sběrnice modbus nebo ideálně vlastní API a LAN konektor / loxone integrace

### Nice to have

- možnost napojit na chlazení / ohřev (vzduch-vzduch, musí být příprava z TM ven na tepelko!)

## Modely

### Atrea Rx5

- modbus TCP, webserver s XML se všemi daty
- napojení na loxone přes modbus
  a [vodníci konfigy](https://www.vodnici.net/community/diy-navody-loxone-arduino/riadenie-rekuperacie-atrea-z-loxone/paged/2/)
- Přístup do servisního menu (Odkaz na servisni menu je na strance uzivatelskeho menu vpravo dole.) je tří místné a je
  to číslo dne v týdnu, číslo zítra a číslo pozítří. Např. v úterý je to 234, v pátek je to 567, v neděli je to 712, ...
  ....tak už jsem na to přišel....ono totiž heslo nejde zadat v microsoft edge a to na PC ani na mobilu...čili budete-li
  mít někdo stejný problém jako já, použijte chrome
- [čtení dat z XML](https://forum.tzb-info.cz/133605-atrea-data-logging-monitoring-cez-webserver)
- [Ofiko Loxone modul](https://library.loxone.com/detail/atrea-rd5-1295/overview)

## Krbová kamna kachlovás

- nezapomenout na nezávislý přívod vzduchu!!!
- Nejspíš [Hass+Sohn Treviso Mini](https://www.haassohn-rukov.cz/produkty/krbova-kamna/04343-kachlova-kamna-treviso-mini) / [Loreto](https://www.haassohn-rukov.cz/produkty/archiv/krbova-kamna/03314-1-kachlova-kamna-loreto) / [Laguno](https://www.haassohn-rukov.cz/produkty/archiv/krbova-kamna/03314-kachlova-kamna-lugano)

Něco jako 
[![](https://www.van2o.lt/cache/images_product_S_1_1000x500/treviso%20ii%20-%20papildoma.jpg)](https://www.van2o.lt/krosneles-zidiniai/kieto-kuro-krosneles/plienine-krosnele-haas-sohn-treviso-ii-8-kw.html?keyword=pl)

## Elektrické žebříky

- Elektrické žebříky / přímotopy v koupelnách na ručníky
- sušák na boty v TM