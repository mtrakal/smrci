# Harmonogram

```mermaid
%%{init: {'theme':'forest'}}%%
gantt
    title Hrubý harmonogram
    dateFormat YYYY-MM-DD
    section Příprava pozemku
        Geodetické zaměření: done, des1, 2025-04-01, 14d
        Vyčištění pozemku: des2, after des1, 14d
    section Základová deska
        Výkopové práce: des3, after des2, 14d
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
        Projekt pro SP (DSP): pdsp, after as, 90d
        Stavební povolení: dsp, after pdsp, 60d

    section Prováděcí studie
        Projekt prováděcí studie: dps, after pdsp, 90d

    section Příprava pozemku
        Elektrika: pp-el, after dsp, 30d
        ČOV: pp-cov, after dsp, 30d
        Vodovod: pp-voda, after dsp, 30d
        Odpady: pp-odpad, after dsp, 30d

    section Zemní práce
        Výkop pasů: zp-pasy, after pp-el pp-cov pp-voda pp-odpad, 1w
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

- Příprava pozemku (Duben 2025)
    - Týden 1-2: Vyčištění pozemku, odstranění vegetace a starých staveb
    - Týden 3-4: Geodetické zaměření a příprava stavebního místa
- Základová deska (Květen 2025)
    - Týden 5-6: Výkopové práce a příprava základů
    - Týden 7-8: Betonáž základové desky
- Hrubá stavba (Červen - Říjen 2025)
    - Týden 9-12: Montáž dřevěné konstrukce (stěny, stropy)
    - Týden 13-16: Instalace střechy a krytiny
    - Týden 17-20: Instalace oken a dveří
    - Týden 21-24: Venkovní fasády
- Instalace technologií (Září - Listopad 2025)
    - Týden 21-24: Elektroinstalace a vodoinstalace
    - Týden 25-28: Instalace topení a rekuperace
    - Týden 29-32: Vnitřní omítky, podhledy
- Dokončovací práce (Prosinec 2025 - Březen 2026)
    - Týden 33-36: Podlahy a obklady
    - Týden 37-40: Malování a finální úpravy interiéru
    - Týden 41-44: Instalace kuchyně a koupelny
    - Týden 45-48: Úpravy okolí domu (stání, chodník, zarovnání terénu)
- Kolaudace a předání (Duben 2026)
    - Týden 49-52: Kolaudace a předání domu