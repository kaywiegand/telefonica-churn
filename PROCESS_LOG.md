# PROCESS_LOG.md – Telefonica Churn

> Projektverlauf und AI-Kontext-Einstieg.
> Dieses File ist der Einstiegspunkt für neue Claude-Sessions.

---

## Projekt-Übersicht

| Feld | Inhalt |
| :--- | :--- |
| Projektname | Telefonica Churn |
| Erstellt | 2026-07-10 |
| Status | 🟢 Phase 1-3 abgeschlossen, README + Notebook-Formatierung fertig |
| Nächster Schritt | `/project-case check` |

---

## Verlauf

### 2026-07-10 – Projekt aufgesetzt

- Projektstruktur mit wgnd-scaffolding generiert.
- Nächste Schritte: Daten laden, erste EDA.

### 2026-07-11 – Rohnotebook migriert, Content-Audit, Phase 1-3 fertig

- Altes `telefonica-churn/` (Rohnotebook, `.venv`, DB-Files) nach `telefonica-churn-legacy/` gesichert, Ordner neu via `/project-init telefonica-churn data` (DA) gescaffoldet.
- Rohnotebook (Struktur 1-6 aus `infos.md`) auf `notebooks/00_introduction.ipynb` … `04_insights.ipynb` aufgeteilt, alle Notebooks lauffähig (siehe Notebook-Outputs für Zahlen — nicht hier kopiert).
- Content-Audit (Pflichtphase laut Workspace-Memory) fand zwei echte Probleme im Rohnotebook, die das Original nicht entdeckt hatte: einen Bug (undefinierte Variable in der Logistic-Regression-Zelle) und einen Datenfehler (negative Werte in `customer_service_calls` in der Roh-DB) — beide gefixt, Details siehe `01_exploration.ipynb`/`02_preparation.ipynb`.
- Nebenbei: `wgnd-toolkit` hatte einen Bug (`cfg.PALETTE_DIVERGENT`), der lokal schon gefixt aber nie gepusht war — mit Kays Freigabe nach GitHub gepusht (Toolkit-Repo, nicht dieses Projekt).
- `/code-review` (high effort, 3 Subagents) auf dem Diff gelaufen: bestätigte Funde (Deutsch statt Englisch in Code-Zellen, Inkonsistenz zwischen zwei Notebooks bei der Grenzwert-Begründung) gefixt; drei Design-Trade-off-Findings (Notebook-Unabhängigkeit vs. Duplikation, hartcodierte Pfade statt `config.PATHS`) bewusst nicht gefixt, siehe `BACKLOG.md`.
- `/project-review` durchgeführt: Struktur/Git/MD-Kohärenz ✅, README + `public/index.html` als einzige Lücken (Schicht 2, erwartet vor `/project-case`) — Ergebnis "BEDINGT".
- README komplett neu geschrieben (Struktur an `zh-tram-flow`/`us-used-vehicle-resales` angelehnt, auf DA-Umfang gekürzt — kein ML/Dashboard-Abschnitt), mit echten Zahlen aus den Notebooks befüllt.
- Alle 5 Notebooks um Titel+Subtitle+`---` und eine Anchor-Link-TOC ("## Inhalt") ergänzt (Muster aus `zh-tram-flow`); 01–04 zusätzlich um Zweck·Input·Output in der ersten Zelle (CONVENTIONS-Gap aus dem Review geschlossen). Nur Markdown-Änderungen, kein Re-Run nötig.
- Nächster Schritt: `/project-case check`.

---

## 2026-08-27 — Portfolio-Aufbereitung

`/project-case slides` + Build. `public/md/slides.yaml` neu angelegt (25 Slide-Einträge, 6 davon in
mehr als einer View), daraus `overview.html`, `storyview.html`, `techview.html`, `index.html`, die
View-MDs und `slides-matrix.md` generiert. Alter Stand liegt in `public/archive/v1/`.

**View-Rollen (Kay-Vorgabe 27.08.2026):** Overview ist die kürzeste Fassung (7 Slides, Ergebnis und
Empfehlungen, keine Methodik), StoryView die vollständigste (15), TechView rein technisch (9,
Datenbereinigung, Indikatortypen, Regression, Grenzen, ohne Business-Empfehlungen).

**Zwei Fallstricke beim Schreiben der slides.yaml:**
1. `chart_refs.source` erwartet **nur den Dateinamen** — `_img_src()` in `generate_html_from_json.py`
   setzt `img/` selbst davor. Mit `source: "img/datei.png"` entsteht `img/img/datei.png`.
2. `comparison_table` braucht `columns:` (nicht `headers:`) und Zeilen als `- cells: [...]`;
   `box_grid`-Items kennen nur `text` und `highlight` (kein `title`/`sentiment`);
   `recommendations` braucht `points:` als Liste; `contrasts` braucht `assumption`/`finding`.

**PDF-Export der Views (Reveal `?print-pdf` + Chrome headless):** Die Bildschirm-Navigation als
normales Stylesheet ausblenden. Der gelegentliche Hochformat-Fallback (612×792 statt 821×578, Slides
über mehrere Seiten zerlegt) ist ein **Timing-Rennen**, keine CSS-Frage — dieselbe Datei rendert mal
richtig, mal falsch. Lösung: MediaBox prüfen und wiederholen, siehe
`wgnd-skills/project-case/scripts/render_views_pdf.sh`.

**Offen:** kein Git-Remote. Das GitHub-Repo `kaywiegand/telefonica-churn` existiert, ist aber leer
(0 KB). Ohne Push kein GitHub Pages, damit ist der Case noch nicht verlinkbar.


## 2026-08-28 — Layout-Korrekturen nach Kay-Review

Vier Fehler in der ersten `slides.yaml`, alle im Schema, nicht im Inhalt:

1. **`meta:` statt `view_meta:`** — `generate_json_from_slides.py` liest `view_meta`. Mein Block wurde
   still ignoriert, die Views hatten keine Metadaten.
2. **`layout: image_left` gehört auf das `chart_refs`-Item**, nicht auf die Slide. Auf Slide-Ebene
   greift es nicht, dann rendert der Chart über die volle Breite und das Statement darunter statt
   daneben. Richtig ist Chart links, Text rechts.
3. **Closing-Slide:** `role: closing` **plus `layout: split`** ergibt die Kopfzone wie auf der
   Titelslide und darunter zwei Spalten, Text links, Links rechts. Statt drei getrennter Ende-Slides
   jetzt **eine gemeinsame** für alle Views (`views: [overview, storyview, techview]`) — kein Drift.
4. **`statement` braucht `layout: wide`** für volle Breite, sonst bleibt es auf 860px gekappt.

Dazu drei fehlende Abstands-Paare im globalen `slides.css` ergänzt (2em-Konvention):
`.text-lead-copy + .metric-row`, `.box-grid + blockquote.statement`,
`.sections-block + blockquote.statement`.

Alle Statements verdichtet. TechView-Titel: die unsinnige KPI „kein Split" durch „5 nummerierte
Notebooks" ersetzt.
