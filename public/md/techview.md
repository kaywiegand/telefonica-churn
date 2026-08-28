# Telefonica Churn

**Projekt:** Telefonica Churn
**Beschreibung:** Technischer Deep Dive
**Autor:** Kay Wiegand
**Zielgruppe:** Data Scientists · Tech Leads · Interviewer
**Dauer:** 8 Minuten
**Zeitraum:** StackFuel Capstone
**GitHub:** [kaywiegand/telefonica-churn](https://github.com/kaywiegand/telefonica-churn)

---


---

### Einstieg

# Telefonica Churn

**Telefonica Churn | Zielgruppen für zwei Kundenbindungs-Kampagnen**
**Abwanderungsanalyse für einen Markteintritt in Florida | StackFuel Capstone**

* **37** — Zeilen mit negativem Anrufzähler
* **350,74** — Minuten, 50-Prozent-Schwelle
* **0,052** — Pseudo-R² der Regression
* **5** — nummerierte Notebooks, durchgehend reproduzierbar

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

> Querschnittsaufnahme ohne Datumsspalte. Jede Aussage bezieht sich auf einen Stand, nicht auf einen Verlauf.

## Ein Zähler, der nicht negativ sein kann
*Was die Prüfung der Rohdaten zutage gefördert hat*

> Der negative Anrufzähler blieb in der Musterlösung unentdeckt. Er verschiebt genau den Indikator, auf dem eine der Empfehlungen beruht.


---

### Analyse

## Drei Datentypen, drei Auswertungswege
*Warum nicht jede Spalte gleich behandelt wird*

> Eine stetige Größe hat keine natürlichen Gruppen. Eine Schwelle per Augenmaß wäre willkürlich, deshalb hier die Regression.


---

### Methodik

## Die Regression im Detail
*statsmodels Logit auf total_day_minutes*

> Ein Prädiktor auf dem vollen Datensatz. 50-Prozent-Punkt bei 350,74 Minuten. Pseudo-R² 0,052 heißt zugleich, dass die Tagesminuten den Großteil der Abwanderung nicht erklären.

## Bewusst ohne Train/Test-Split
*Schwellenwert bestimmen statt generalisieren*

> Ein Split würde die Datenbasis nur verkleinern, ohne die Aussage zu verbessern. Geprüft wird stattdessen die Datenqualität und wie viele Kunden ein Indikator trifft.


---

### Grenzen

## Was diese Analyse nicht kann
*Aussagegrenzen, offen benannt*



---

### Ende

## Telefonica Churn
*Abwanderungsanalyse für einen Markteintritt in Florida<br>Data-Analysis-Projekt | StackFuel Capstone*

> Sorgfalt schlägt Modellkomplexität
