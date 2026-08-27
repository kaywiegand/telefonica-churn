# Project

**Projekt:** N/A
**Beschreibung:** N/A
**Autor:** N/A
**Zielgruppe:** N/A
**Dauer:** N/A Minuten
**Zeitraum:** N/A
**GitHub:** [N/A](https://github.com/)

---


---

### Einstieg

# Telefonica Churn

**Telefonica Churn | Zielgruppen für zwei Kundenbindungs-Kampagnen**
**Abwanderungsanalyse für einen Markteintritt in Florida**

* **37** — Zeilen mit negativem Anrufzähler
* **350,74** — Minuten, 50-Prozent-Schwelle
* **0,052** — Pseudo-R² der Regression
* **kein Split** — bewusst ohne Train/Test-Split

## Inhaltsübersicht
*Datenaufbereitung, Indikatortypen und Methodik*

1. Daten und Qualität
2. Indikatortypen
3. Methodik
4. Grenzen


---

### Daten

## Zwei Tabellen, ein Join
*SQLite-Datenbank aus dem StackFuel-Abschlussprojekt*

> Querschnittsaufnahme ohne Datumsspalte. Es gibt keinen Zeitverlauf, jede Aussage bezieht sich auf einen Stand.

## Ein Zähler, der nicht negativ sein kann
*Was die Prüfung der Rohdaten zutage gefördert hat*

> Der negative Anrufzähler war in der ursprünglichen Musterlösung nicht aufgefallen. Er verschiebt genau den Indikator, auf dem später eine der drei Empfehlungen beruht.


---

### Analyse

## Drei Datentypen, drei Auswertungswege
*Warum nicht jede Spalte gleich behandelt wird*

> Bei einer stetigen Größe gibt es keine natürlichen Gruppen. Eine Schwelle per Augenmaß wäre willkürlich, deshalb kommt hier die Regression zum Einsatz und nicht bei den anderen beiden.


---

### Methodik

## Die Regression im Detail
*statsmodels Logit auf total_day_minutes*

> Ein einzelner Prädiktor, gerechnet auf dem vollständigen Datensatz. Der 50-Prozent-Punkt liegt bei 350,74 Minuten. Das Pseudo-R² von 0,052 sagt zugleich, dass die Tagesminuten allein den Großteil der Abwanderung nicht erklären.

## Bewusst ohne Train/Test-Split
*Schwellenwert bestimmen statt generalisieren*

> Ein Split würde die Datenbasis für diese Herleitung nur verkleinern, ohne die Aussage zu verbessern. Entsprechend gibt es keine Testmetrik. Die Prüfung liegt in der Datenqualität und in der Frage, wie viele Kunden ein Indikator tatsächlich trifft.


---

### Grenzen

## Was diese Analyse nicht kann
*Aussagegrenzen, offen benannt*



---

### Ende

## Methodisch schlicht, dafür überprüfbar
*Reproduzierbar über fünf nummerierte Notebooks*

> Jeder Bereinigungsschritt, jede Schwelle und jede Aussagegrenze ist im Notebook nachvollziehbar dokumentiert. Wo eine Zahl nicht trägt, steht das dabei.
