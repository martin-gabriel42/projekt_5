Tento doprovodný dokument obsahuje krátký popis procesu tvorby Power BI souboru.

# Návrh datového modelu
## Faktová tabulka
Faktová tabulka F_Sales vznikla načtením a následným upravením zdrojové tabulky v rámci Power Query.
Kromě kosmetických úprav (přejmenování sloupců, změna pořadí sloupců...) došlo k následujícím úpravám:
- sjednocení formátování sloupců s datumy (DD-MM-YYYY -> DD/MM/YYYY)
- odstranění sloupců zbytečných pro účel projektu (jména zákazníků, discount)
- změna datových typů
- přidání vypočítaných sloupců (Profit margin (%))
- oddělení některých sloupců do samostatných dimenzionálních tabulek

## Dimenzionální tabulky
Dimenzionální tabulky vznikly oddělením sloupců nebo skupin sloupců z faktové tabulky za účelem přehlednější agregace a filtrování. Dimenzionální model má podobu star schématu.
Byly vytvořeny následující dimenzionální tabulky:
- D_Time - časová dimenze
- D_Product - dimenze produktu, kategorie a podkategorie produktu
- D_Geography - dimenze obsahující hodnoty trhů, zemí a administrativních podjednotkách zemí
- D_Segment - dimenze s hodnotami jednotlivých segmentů zboží
- D_Ship_mode - druhy doručení
- D_Order_priority - priority doručení

K tabulkám D_Time, D_Geography a D_Product byly vytvořeny vhodné hierarchie.

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
Tato stránka obsahuje grafy klíčových metrik (obrat, zisk, počet prodaných jednotek) v závislosti na kategorii / podkategorii produktu. Zobrazené metriky lze přepínat pomocí průřezu Key metrics. Umožňuje tedy porovnání výkonnosti jednotlivých kategorií a podkategorií produktů v klíčových metrikách. Dále je pomcí průřezu Analytical dimension možné jednotlivé hodnoty rozdělit podle segmentu, druhu doručení a prioritz doručení. Na stránce se nacházejí následující vizuály: 
- sloupcový graf zobrazující vybranou klíčovou metriku v závislosti na podkategorii produktu
- graf druhu treemap zobrazující vybranou klíčovou metriku v závislosti na podkategorii produktu
- relevantní filtry

## 3. stránka: Geography

## 4. stránka: Operational KPIs

