# Telefonica Churn

**Projekt:** Telefonica Churn
**Beschreibung:** Der komplette Projektverlauf
**Autor:** Kay Wiegand
**Zielgruppe:** Data Peers · Portfolio
**Dauer:** 12 Minuten
**Zeitraum:** StackFuel Capstone
**GitHub:** [kaywiegand/telefonica-churn](https://github.com/kaywiegand/telefonica-churn)

---


---

### Einstieg

# Telefonica Churn

**Abwanderungsanalyse für einen Markteintritt in Florida**
**Data-Analysis-Projekt | StackFuel Capstone**

* **3.333** — Kunden (aus 3.349 Rohzeilen)
* **14,49 %** — Basis-Abwanderungsrate
* **3** — unabhängig geprüfte Indikatoren
* **954** — Kunden für gezielte Ansprache

## Inhaltsübersicht
*Der komplette Weg von den Rohdaten zu den Kampagnen-Zielgruppen*

1. Problem
2. Daten und Qualität
3. Exploration
4. Analyse
5. Ergebnis
6. Empfehlungen
7. Grenzen


---

### Problem

## Markteintritt mit subventioniertem ersten Jahr
*Teleconfia testet den US-Markt mit Florida als Pilotregion*

> Nicht alle Neukunden sind geblieben
* **14,49 %** — Abwanderung über alle Kunden
* **3.333** — Kunden im Datensatz
* **12** — Stadtteile in Florida

## Die Leitfrage
*Zielgruppen bestimmen, nicht eine Quote senken*

> Der Auftrag nennt keine Zielquote, er fragt nach Adressaten. Welche Spalten zeigen ein Risiko, und wo liegt die Kontaktschwelle.
* **Plakatkampagne**
  - Zielgebiete sind Stadtteile, nicht einzelne Kunden.
  - Gesucht ist eine Rangfolge der zwölf Distrikte.
* **Persönliche Ansprache**
  - Zielgruppe sind einzelne Kunden mit erkennbarem Risiko.
  - Gesucht sind Merkmale und eine Kontaktschwelle.


---

### Daten

## Zwei Tabellen, ein Join
*SQLite-Datenbank aus dem StackFuel-Abschlussprojekt*

> Querschnittsaufnahme ohne Datumsspalte. Jede Aussage bezieht sich auf einen Stand, nicht auf einen Verlauf.

## Ein Zähler, der nicht negativ sein kann
*Was die Prüfung der Rohdaten zutage gefördert hat*

> Der negative Anrufzähler blieb in der Musterlösung unentdeckt. Er verschiebt genau den Indikator, auf dem eine der Empfehlungen beruht.


---

### Exploration

## Die Ausgangslage
*Was der Datensatz hergibt und was nicht*

* **14,49 %** — Abwanderungsrate als Vergleichsmaßstab
* **1 Zeile** — je Kunde, keine Verlaufsdaten
* **0** — Datumsspalten im Datensatz
> Ohne Zeitachse kein Verlauf. Die Zielgruppenfrage wird damit zur Frage nach Merkmalen im Bestand, nicht nach einem Vorhersagemodell.


---

### Analyse

## Vier Stadtteile tragen die Mehrheit
*Zielgebiete für die Plakatkampagne*


## Der internationale Tarif
*Das stärkste kategoriale Signal*


## Der vierte Anruf
*Ein klarer Knick statt eines gleichmäßigen Anstiegs*


## Eine Schwelle statt einer Faustregel
*Logistische Regression auf den Tagesminuten*



---

### Ergebnis

## Knapp ein Drittel der Kunden ist adressierbar
*Abdeckung der drei Indikatoren zusammen*

* **954** — von 3.333 Kunden mit mindestens einem Signal
* **28,6 %** — Anteil am Bestand
* **60,9 %** — der Abwanderung in vier Stadtteilen
> Beide Kampagnen haben eine konkrete Zielgruppe, ohne Vorhersagemodell.


---

### Empfehlungen

## Vier Maßnahmen
*Direkt aus den drei Indikatoren abgeleitet*



---

### Grenzen

## Was diese Analyse nicht kann
*Aussagegrenzen, offen benannt*



---

### Ende

## Telefonica Churn
*Abwanderungsanalyse für einen Markteintritt in Florida<br>Data-Analysis-Projekt | StackFuel Capstone*

> Sorgfalt schlägt Modellkomplexität
