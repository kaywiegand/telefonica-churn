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

> Welche Spalten zeigen tatsächlich ein Abwanderungsrisiko an, und wo setzt man die Schwelle für eine Kontaktaufnahme. Der Auftrag nennt keine Zielquote, er fragt nach Adressaten.
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

> Querschnittsaufnahme ohne Datumsspalte. Es gibt keinen Zeitverlauf, jede Aussage bezieht sich auf einen Stand.

## Ein Zähler, der nicht negativ sein kann
*Was die Prüfung der Rohdaten zutage gefördert hat*

> Der negative Anrufzähler war in der ursprünglichen Musterlösung nicht aufgefallen. Er verschiebt genau den Indikator, auf dem später eine der drei Empfehlungen beruht.


---

### Exploration

## Die Ausgangslage
*Was der Datensatz hergibt und was nicht*

* **14,49 %** — Abwanderungsrate als Vergleichsmaßstab
* **1 Zeile** — je Kunde, keine Verlaufsdaten
* **0** — Datumsspalten im Datensatz
> Ohne Zeitachse lässt sich kein Verlauf modellieren. Die Frage nach Zielgruppen ist damit eine Frage nach Merkmalen, die im Bestand sichtbar sind, nicht nach einem Vorhersagemodell.


---

### Analyse

## Vier Stadtteile tragen die Mehrheit
*Zielgebiete für die Plakatkampagne*

> Jacksonville mit 29,82 Prozent, Orlando1 mit 23,67, Cape Coral mit 21,78 und Orlando2 mit 19,08 kommen zusammen auf 60,9 Prozent aller Abwanderungen. Vier von zwölf Stadtteilen reichen damit für die Plakatkampagne.

## Der internationale Tarif
*Das stärkste kategoriale Signal*

> Kunden mit internationalem Tarif wandern zu 42,4 Prozent ab, ohne den Tarif zu 11,5 Prozent. Das ist knapp das Vierfache und betrifft 323 Kunden, eine Gruppe, die sich einzeln ansprechen lässt.

## Der vierte Anruf
*Ein klarer Knick statt eines gleichmäßigen Anstiegs*

> Bis zum dritten Anruf liegt die Abwanderung bei rund 10 Prozent, beim vierten springt sie auf 45,8 Prozent. Die Kontaktschwelle wurde deshalb auf drei Anrufe gesetzt, um vor dem Knick zu liegen. Das betrifft 696 Kunden.

## Eine Schwelle statt einer Faustregel
*Logistische Regression auf den Tagesminuten*

> Für die stetige Größe wurde die Schwelle nicht geschätzt, sondern gerechnet. Bei 350,74 Tagesminuten liegt die Abwanderungswahrscheinlichkeit bei 50 Prozent. Sauber hergeleitet, aber nur vier Kunden liegen darüber.


---

### Ergebnis

## Knapp ein Drittel der Kunden ist adressierbar
*Abdeckung der drei Indikatoren zusammen*

* **954** — von 3.333 Kunden mit mindestens einem Signal
* **28,6 %** — Anteil am Bestand
* **60,9 %** — der Abwanderung in vier Stadtteilen
> Beide Kampagnen haben damit eine konkrete Zielgruppe, ohne dass ein Vorhersagemodell nötig war. Die Sorgfalt steckt in der Datenprüfung, nicht in der Modellkomplexität.


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

## Sorgfalt statt Modellkomplexität
*Was dieses Projekt zeigt*

> Drei unabhängig geprüfte Indikatoren reichen aus, um beide Kampagnen zu adressieren. Der entscheidende Beitrag war nicht ein Modell, sondern die Prüfung der Datenbasis und die ehrliche Einordnung, welcher Indikator trägt und welcher nicht.
