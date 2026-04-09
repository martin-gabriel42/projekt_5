Tento doprovodný dokument obsahuje krátký popis návrhu a procesu tvorby Power BI souboru.

# Návrh datového modelu
## Faktová tabulka
Faktová tabulka F_Sales vznikla načtením a následným upravením zdrojové tabulky v rámci Power Query.
Kromě kosmetických úprav (přejmenování sloupců, změna pořadí sloupců...) došlo k následujícím úpravám:
- sjednocení formátování sloupců s datumy (DD-MM-YYYY -> DD/MM/YYYY)
- odstranění sloupců zbytečných pro účel projektu (customer_name, discount)
- úprava datových typů
- přidání vypočítaných sloupců (Days to ship)
- oddělení některých sloupců do samostatných dimenzionálních tabulek

## Dimenzionální tabulky
Dimenzionální tabulky vznikly oddělením sloupců nebo skupin sloupců z faktové tabulky za účelem přehlednější agregace a filtrování. Dimenzionální model odpovída principu star schema.
Byly vytvořeny následující dimenzionální tabulky:
- D_Time - časová dimenze
- D_Product - informace o produktu, kategorie a podkategorie produktu
- D_Geography - geografická dimenze (trhy, země, administrativní jednotky)
- D_Segment - segmenty zboží
- D_Ship_mode - druhy doručení
- D_Order_priority - priority doručení

U tabulek D_Time, D_Geography a D_Product byly navíc vytvořeny vhodné hierarchie pro podporu drill-down analýzy

# Vizuály reportu
## 1. stránka: Overview KPIs
Tato stránka obsahuje grafy a hodnoty klíčových výkonnostních ukazatelů (KPI) celého podniku. Z této stránky je možné vyčíst následující údaje:
- celkový prodej (obrat) za dané období
- celkový zisk za dané období
- celkový počet prodaných kusů zboží
- celková marže
- vývoj zisku a obratu během času (čárový graf)
- obrat podle trhu (koláčový graf)
- obrat podle segmentu (sloupcový graf)

Všechny vizuály této stránky lze filtrovat pomocí průřezů (slicerů).

## 2. stránka: Product performance
Stránka je zaměřena na analýzu výkonnosti produktů.
Obsahuje vizualizace klíčových metrik:
- obrat
- zisk
- počet prodaných jednotek
Tyto metriky lze přepínat pomocí průřezu Key metrics.
Dále je možné data analyzovat podle:
- segmentu
- druhu doručení
- priority objednávky
Stránka umožňuje:
- porovnání výkonu kategorií a podkategorií produktů
- detailní pohled na jednotlivé produkty v různých dimenzích

## 3. stránka: Geography
Hlavním prvkem je mapa zobrazující vybranou metriku podle geografické jednotky.
Funkcionality stránky:
- přepínání granularity (market → country → administrative sub-unit)
- filtrování konkrétních geografických oblastí
- časové filtrování
Uživatel může analyzovat:
- obrat podle geografické jednotky
- zisk podle geografické jednotky
- počet prodaných jednotek
Všechny metriky lze dále členit podle segmentu.

## 4. stránka: Operational KPIs
Stránka se zaměřuje na provozní ukazatele.
Sledované metriky:
- průměrné náklady na doručení objednávky (Average cost of shipping per order)
- průměrná doba expedice (Average days to ship per order)
Data jsou zobrazena pomocí sloupcových grafů a lze je analyzovat podle:
- priority objednávky
- způsobu doručení
- geografické oblasti
K dispozici jsou průřezy pro filtrování a výběr konkrétního ukazatele (Operational indicators).
