# Smart Home

Postavené na Home Assistant + Loxone? Asi, nic lepšího jsem nenašel.

## Postupně nutné

- spotová elektřina a aktuální cena (zapínání bojleru, dobíjení baterií ze sítě, nabíjení EV?)
- dle předpovědi počasí plánovat nutnost nákupu na spotu, šetření (počasí a predikci výroby FVE zvládá Home Assistant + [Forecast Solar](https://www.home-assistant.io/integrations/forecast_solar))
- v koupelně (asi dle rozsvícení + následného zhasnutí / samostatného tlačítka) se zapne na plný výkon odtah z rekuperace (a zůstává běžet nějakou dobu aby vytáhlo vlhkost)
- v kuchyni (asi dle zapnutí digestoře / samostatného tlačítka) se zapne na plno odtah rekuperace
- malé osvětlení na chodbě se zapíná na pohyb a nastavuje intenzitu dle denní hodiny
- dle zvyšující se teploty u krbu (pokud se nezvýšila teplota poslahovky) se zapne nasávání rekuperace na vyšší výkon - doohřev ostatních místností
- dle předpovědi počasí / termostatů se spíná podlahovka 
- vnitřní a venkovní teplota
- vlhkost
- hlídání hladiny v akumulační nádrži (notifikace abychom dopustili z kohoutku na splachování)
- CO2 senzor? Má smysl, když rekuperace jede vlastně nonstop?
- dle predikce výroby FVE nahřívat bojler, baterie, EV

## Hezké

- osvětlení se k večeru mění intenzita (ikea žárovky, Home Assistant nebo ikea režimy) - není nutné mít relátka
- osvětlení kolem domu se zapne se setměním a vypne např. v 11
- 

## Nutno vyřešit

- co zvládne sám Home Assistant
- co všechno na něj půjde napojit
- bude potřeba Loxone a k čemu a kolik extension modulů