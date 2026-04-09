Tento doprovodný dokument obsahuje krátký popis procesu tvorby Power BI souboru.

# Návrh datového modelu
## Faktová tabulka
Faktová tabulka F_Sales vznikla načtením a následným upravením zdrojové tabulky v rámci Power Query.
Kromě kosmetických úprav (přejmenování sloupců, změna pořadí sloupců...) došlo k následujícím úpravám:
- sjednocení formátování sloupců s datumy
- odstranění sloupců zbytečných pro účel projektu (jména zákazníků, discount)
- změna datových typů
- přidání vypočítaných sloupců (Profit margin (%))
- oddělení některých sloupců do samostatných dimenzionálních tabulek

## Dimenzionální tabulky
