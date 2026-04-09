# Harmonogram

```mermaid
%%{init: {'theme':'forest'}}%%
gantt
    title Hrubý harmonogram
    dateFormat YYYY-MM-DD
    section Základová deska
        Výkopové práce: des3, 2026-04-12, 14d
        Betonáž základové desky: des4, after des3, 14d
    section Hrubá stavba
        Montáž dřevěné konstrukce: des5, after des4, 28d
        Instalace střechy: des6, after des5, 28d
        Instalace oken a dveří: des7, after des6, 28d
    section Instalace technologií
        Elektroinstalace: des8, after des7, 28d
        Vodoinstalace: des9, after des8, 28d
        Instalace topení: des10, after des9, 28d
    section Dokončovací práce
        Podlahy a obklady: des11, after des10, 28d
        Malování: des12, after des11, 28d
        Instalace kuchyně: des13, after des12, 28d
        Úpravy okolí domu: des14, after des13, 28d
    section Kolaudace a předání
        Kolaudace: des15, after des14, 28d
        Předání domu: des16, after des15, 14d

```

```mermaid
%%{init: {'theme':'forest'}}%%
gantt
    title Harmonogram detailní
    dateFormat YYYY-MM-DD
    section Stavební povolení
        Arch. studie: done, as, 2024-11-01, 60d
        Koupě pozemku: done, kp, 2024-11-01, 100d
        Projekt pro SP (DSP): done, pdsp, 2025-01-01, 90d
        Stavební povolení: done, dsp, 2025-09-01, 60d

    section Prováděcí studie
        Projekt prováděcí studie: dps, 2025-09-01, 2026-05-31

    section Příprava pozemku
        ČOV a akumulační nádrž: done, pp-cov, 2025-10-01, 180d
        Elektrika: pp-el, 2026-04-01, 30d
        Vodovod: pp-voda, 2026-04-01, 30d
        Odpady: pp-odpad, 2026-04-01, 30d

    section Zemní práce
        Výkop pasů: zp-pasy, 2026-04-12, 14d
        Základová deska + strop sklepu: zp-deska, after zp-pasy, 30d

    section Konstrukce
        Obvodové stěny: k-steny, after zp-deska, 2w
        Strop: k-strop, after k-steny, 1w
        Krov: k-krov, after k-strop, 3w
        Střecha: k-strecha, after k-krov, 4w
        Izolace stěn - vnější: k-izolace, after k-strecha, 2w
        Okna: k-okna, after k-izolace, 1w
        Fasáda: k-fasada, after k-okna, 2w
    section Rozvody
        Voda: r-voda, after k-strecha, 3w
        Vzduchotechnika: r-vzduch, after r-voda, 2w
        Elektro rozvody: r-elektro, after r-vzduch, 4w

```

---

- zemní a výkopové práce (zemní a terénní úpravy, výkopy základů a základových spár, přemístění stržené ornice a uložení
  či odvoz hlušiny)
- budování základů domu (včetně hydroizolací a případné ochrany před zvýšeným radonovým rizikem a prostupů inženýrských
  sítí)
- hrubá spodní stavba (realizace svislých a vodorovných konstrukcí přízemí, vodorovné izolace a případně i zásypy a
  obsypy)
- realizace střechy (střešní konstrukce i krytina včetně doplňků, střechy se rovnou realizují kompletní s výjimkou
  odvádění vody, okapové systémy realizujeme až po případném vnějším zateplení a realizaci fasády)
- realizace nezděných nenosných příček a dalších konstrukcí (třeba sádrokartonové podhledy, příčky včetně osazení
  zárubněmi, …)
- realizace hrubých instalací (rozvody vody, kanalizace, elektřiny, plynu, vzduchotechniky, ústředního topení včetně
  podlahového vytápění – s ním souvisí i podkladové vrstvy podlah, …)
- realizace vnitřních omítek
- realizace podlah a obkladů
- vnitřní malířské a natěračské práce, nášlapné vrstvy podlah, kompletace instalací
- realizace fasády (případně i zateplení fasády a dokončovací klempířské práce – parapety, okapy, …)
- dokončovací práce (venkovní schodiště, chodníky, …)
- kontrola kvality a odevzdání stavby
- úprava terénu a realizace zahrady včetně oplocení včetně bran a branek (pokud nebylo oplocení realizováno již dříve)

---

- Příprava povolení a sítí (Podzim 2025 - Březen 2026) [hotovo]
    - Září-listopad 2025: Stavební povolení
    - Říjen 2025 - březen 2026: Osazení ČOV a akumulační nádrže
- Zemní práce a základy (Duben - Květen 2026)
    - Týden 1-2 (od 12. 4. 2026): Výkop základových pasů
    - Týden 3-6: Základová deska + strop sklepu
- Hrubá konstrukce (Květen - Září 2026)
    - Týden 7-8: Obvodové stěny
    - Týden 9: Strop
    - Týden 10-12: Krov
    - Týden 13-16: Střecha
    - Týden 17-18: Vnější izolace stěn
    - Týden 19: Okna
    - Týden 20-21: Fasáda
- Rozvody (Srpen - Říjen 2026)
    - Týden 17-19: Voda
    - Týden 20-21: Vzduchotechnika
    - Týden 22-25: Elektro rozvody
- Dokončovací práce (Říjen 2026 - Únor 2027)
    - Týden 26-31: Vnitřní omítky, podhledy
    - Týden 32-37: Podlahy a obklady
    - Týden 38-41: Malování a finální úpravy interiéru
    - Týden 42-45: Instalace kuchyně a koupelny
    - Týden 46-48: Úpravy okolí domu (stání, chodník, zarovnání terénu)
- Kolaudace a předání (Březen - Duben 2027)
    - Týden 49-52: Kolaudace a předání domu
