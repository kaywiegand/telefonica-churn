# BACKLOG.md – Telefonica Churn

Projektspezifische offene Tasks und Todos.
Nie mitten in einer Session den Kontext wechseln — hier notieren, gesammelt abarbeiten.

Prio: `1` = hoch · `2` = mittel · `3` = niedrig

---

| # | Beschreibung | Prio | Entdeckt in |
| :--- | :--- | :--- | :--- |
| 1 | Notebooks nutzen hartcodierte relative Pfade (`Path('../data/raw')` etc.) statt `PATHS` aus `telefonica_churn.config` — arbeitsverzeichnis-abhaengig, stammt aus dem wgnd-scaffolding-Template selbst (kein projektspezifisches Problem) | 3 | code-review nach Notebook-Migration |
| 2 | `03_analysis` und `04_insights` berechnen SQL-Query bzw. Logistic Regression jeweils unabhaengig neu statt Ergebnisse weiterzureichen — bewusster Trade-off fuer unabhaengig lauffaehige Notebooks, aber Drift-Risiko falls `02_preparation` sich aendert | 3 | code-review nach Notebook-Migration |
| 3 | `04_insights` Executive Summary nennt Zahlen (z.B. "350.74 Minuten") als Prosa statt sie live aus dem Code-Cell zu referenzieren — konsistent mit dem Key-Findings-Muster in `01_exploration`, aber gleiche Kopplungs-Problematik wie #2 | 3 | code-review nach Notebook-Migration |
