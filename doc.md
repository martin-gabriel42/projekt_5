Tento doprovodný dokument obsahuje krátký popis návrhu a procesu tvorby Power BI souboru.

# Návod na spuštění

Po otevření Power BI projektu je nutné přejít do Power Query. Ve skupině PATH se nachází parametr BasePath, který je nutné přenastavit na složku projektu (např. "C:\Users\gabma\Documents\Programming\ENGETO\projekt_5 - volby\"). Toto by mělo zaručit správné načtení zdrojových tabulek.

Dále je pro správné fungování Shape Map vizuálů na 1. a 3. straně je nutné použít soubor "cz topoJSON", který se nachází ve složce "Zdroje dat". Po označení proveďte následující kroky:

- kliknutí na "Visualizations"
- kliknutí na "Format your visual"
- kliknutí na "Map settings"
- nastavení "Map type" na "Custom"
- nastavení "Add a map type" na "cz topoJSON.json" (soubor se nachází ve složce "Zdroje dat")

# Návrh datového modelu

Datový model byl navrhunt tak, aby bylo možné pohodlně používat filtrování vizuálů.

Tabulky byly vytvořeny a upraveny pro vypočítání hodnot a tvorbu measures do vizuálů.

Běžné úpravy zahrnují:

- úpravu datových typů
- odstranění sloupců
- pivot / unpivot
- slučování tabulek
- použití podmíněných a vypočítaných sloupců

## Faktové tabulky

Faktové tabulky vznikly úpravou zdrojových CSV souborů do podoby lépe použitelné k vizualizaci dat.

### F_Hlasy_pro_strany

- počet hlasů pro jednotlivé strany v okresech

### F_Hlasy_v_okresech

- počet hlasů v okresech
- počet voličů v okresech
- vydané obálky v okresech
- odevzdané obálky v okresech
- platné hlasy v okresech

### F_Mandaty_a_hlasy

- přehled o počtu získaných mandátů, a konečném pořadí stran

### F_Vitez_kraje

- přehled o vítězích v krajích, použito pro mapové vizuály

### Mapa - pomocna tabulka

- přehled o rozložení voličů jednotlivých stran
- pomocná tabulka pro mapové vizuály


## Dimenzionální tabulky
Dimenzionální tabulky vznikly oddělením sloupců nebo skupin sloupců z faktové tabulky, nebo přímým načtení ze zdrojových souborů, za účelem přehlednější agregace a filtrování. Dimenzionální model odpovídá principu star schema.
Byly vytvořeny následující dimenzionální tabulky:

- D_Strany - dimenze politických stran
- D_Lokace - přehled o krajích a okresech

U tabulky D_Lokace byla vytvořena hierarchie Kraj -> Okres

# Vizuály reportu
## 1. stránka: Přehled
Tato stránka obsahuje základní přehled o vítězi voleb, klíčových hodnot a výsledků jednotlivých stran. Slouží zejména k rychlému zjištění nejdůležitějších hodnot a výsledků voleb.

## 2. stránka: Volební účast
Tato stránka obsahuje přehled volební účasti. Je možné agregovat přes jednotlivé kraje a okresy, nebo zjistit exaktní hodnoty z tabulky.

## 3. stránka: Přehled dle strany
Tato stránka umožňuje zjišťovat detaily o výsledcích jednotlivých stran. Je zaměřená na výkon stran ve volbách a rozložení voličů jednotlivých stran.
