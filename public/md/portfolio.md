# Portfolio Summary — Telefonica Churn
<!-- Interface-Datei: Wird von /project-case story befüllt.
     Einzige Zahlenquelle für /project-case report und /project-case slides.
     KEINE Inhalte aus Notebooks kopieren — nur kuratierte Kernaussagen.
-->

---

## Project

```
name:       Telefonica Churn
slug:       telefonica-churn
type:       DA
stage:      Phase 3 complete — analysis + insights done, portfolio prep in progress
target:     churn (0/1) — used for threshold/indicator analysis, not predicted via ML model
stack:      Python · pandas · SQLAlchemy · statsmodels · Matplotlib/Seaborn · Jupyter
period:     cross-sectional snapshot — no date column
rows:       3,333 (cleaned, from 3,349 raw)
notebooks:  5
findings:   6
dashboard:  — (not built for this project)
```

---

## Storyline

```
thesis:     Three independently-evaluated indicators — one strong contract feature, one clean
            behavioral threshold, one statistically valid but weak-alone metric — are enough to
            target both retention campaigns without building a predictive model.
hook:       The content audit found and fixed a real data-quality bug (37 rows with negative
            customer_service_calls) that the original coursework solution never caught.
proof:      City ranking (60.9% of churn in 4 districts) → three indicators evaluated
            independently against the full dataset → combined coverage (954/3,333 customers
            flagged by at least one indicator).
so_what:    Well-audited EDA + simple thresholds can answer a business-targeting question
            without a predictive model — rigor is in the data quality checks, not model complexity.
```

---

## Problem

```
kpi_name:   Churn rate
kpi_ist:    14.49%
kpi_soll:   not specified — the brief asks who to target, not what rate to hit
kpi_gap:    n/a (targeting problem, not a rate-reduction target)
problem_statement: |
  Teleconfia enters the Florida market with a subsidized first year; some customers churn anyway.
  Two retention campaigns need concrete targets: a poster campaign for the highest-churn city
  districts, and individual outreach for customers likely to leave. The core question is which
  columns actually indicate churn risk and where to set the contact threshold — with the float
  threshold derived from a logistic regression rather than a rule of thumb.
```

---

## Key Findings
<!-- Max 6 Findings — jeweils mit konkreter Zahl und Quelle-Notebook -->

### F1 — City concentration
```
finding:   4 city districts account for the large majority of all churn
number:    Jacksonville (29.82%), Orlando1 (23.67%), Cape Coral (21.78%), Orlando2 (19.08%) = 60.9% of all churn
source:    03_analysis.ipynb
```

### F2 — International plan is the strongest categorical signal
```
finding:   Customers with an international plan churn at nearly 4x the rate of those without
number:    42.4% vs. 11.5% — 323 customers affected
source:    03_analysis.ipynb
```

### F3 — Customer service calls: sharp inflection point
```
finding:   Churn rate jumps sharply once a customer has called support 4+ times
number:    ~10% (0-3 calls) -> 45.8% (4 calls) -- contact threshold set at 3 calls (696 customers)
source:    03_analysis.ipynb
```

### F4 — Logistic regression threshold is clean but weak alone
```
finding:   The 50%-probability threshold for total_day_minutes is statistically derived but affects very few customers
number:    350.74 minutes, pseudo-R² 0.052, only 4 customers above it
source:    03_analysis.ipynb
```

### F5 — Data quality bug found and fixed
```
finding:   37 rows had negative customer_service_calls values in the raw database -- impossible for a call counter, undetected by the original coursework solution
number:    37 rows (-1, -2), clipped to 0
source:    01_exploration.ipynb / 02_preparation.ipynb
```

### F6 — Combined indicator coverage
```
finding:   Nearly a third of all customers trigger at least one of the three risk indicators
number:    954 of 3,333 customers (28.6%)
source:    03_analysis.ipynb
```

---

## Model Results
<!-- n.a. — DA-Projekt, kein Predictive Model. Ziel ist Schwellenwert-Identifikation, nicht Generalisierung. -->

n.a. — this project deliberately has no train/test split or predictive model (see `02_preparation.ipynb`, "Train Test Split" section). The logistic regression in F4 is used to derive a threshold on the full dataset, not evaluated for generalization.

---

## Figures
<!-- Alle relevanten Exports in public/img/ — für Report und Slides -->

```yaml
city:
  - img/city_churn_ranking.png            # Top-4 cities by absolute churn count

categorical:
  - img/international_plan_churn.png      # Churn rate by international plan (0 vs. 1)

behavioral:
  - img/customer_service_calls_churn.png  # Churn rate by number of customer service calls

statistical:
  - img/logit_total_day_minutes.png       # Logistic regression curve + 50%-threshold
```

---

## Recommendations

```
r1:
  title:  Poster campaign in the top-4 churn districts
  detail: Jacksonville, Orlando1, Cape Coral, Orlando2 — together account for 60.9% of all churn.

r2:
  title:  Individual outreach for international-plan customers
  detail: 323 customers at 42.4% churn rate — offer special international-call conditions before they leave.

r3:
  title:  Early-warning contact at 3+ customer service calls
  detail: 696 customers — churn rate jumps to 45.8% by the 4th call, so contacting at 3 gives a buffer.

r4:
  title:  Use the total_day_minutes threshold only as a secondary criterion
  detail: Statistically clean (350.74 min) but affects only 4 customers alone — combine with r2/r3, don't rely on it standalone.
```

---

## Status

```
generated_by:   /project-case story
generated_at:   2026-07-12
summary_version: 1
portfolio_check: ⚠️ partial (public/index.html + portfolio.md were the two open gaps -- portfolio.md now closed by this file)
report_html:    ❌ pending
slides_html:    ❌ pending
dashboard:      ❌ not deployed (not planned for this project)
```
