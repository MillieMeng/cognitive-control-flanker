# Behavioral Data Analysis — Eriksen Flanker Task

End-to-end R pipeline · 8,000+ behavioral observations · NYU PSYCH-UA 300, Spring 2026

---

## Overview

This project applies a complete data analysis workflow to trial-level behavioral experiment data. Starting from raw observations, the pipeline covers data cleaning, long-to-wide reshaping, individual-level aggregation, visualization across experimental conditions, and regression modeling. The focus is on producing reproducible, documented findings — not just results.

---

## Research Question

Does trial congruency affect reaction time and error rate in a cognitive interference task? Do performance patterns differ between a clinical test group and healthy controls?

---

## Dataset

| Variable | Type | Description |
|---|---|---|
| `subject` | ID | Participant identifier |
| `group` | Independent | `control` vs. `test` |
| `congruency` | Independent | `congruent` vs. `incongruent` trial |
| `result` | Dependent | `correct`, `incorrect`, or `timeout` |
| `rt` | Dependent | Reaction time (seconds) |

**Scale:** ~8,000 behavioral observations · Trial-level (long format)  
**Task:** Eriksen Flanker Task (Eriksen & Eriksen, 1974) — participants identify a central arrow while suppressing flanking distractors

---

## Analytical Workflow

**1. Cleaning and validation**  
Inspected distributions, handled timeout responses, verified variable types and structure.

**2. Visualization**  
Four publication-ready plots built in `ggplot2`:
- Reaction time distribution (overall)
- RT by congruency condition
- RT by response accuracy
- RT by congruency × accuracy (faceted; timeouts excluded)

**3. Data reshaping**  
Converted trial-level long format to participant-level wide format using `pivot_wider()` and `unite()`. Computed individual mean RT for congruent and incongruent conditions using `rowMeans()`.

**4. Data joining**  
Merged individual averages back into the long-format dataset via `left_join()`. Identified participants with missing demographic records using `anti_join()`.

**5. Descriptive statistics**  
Summarized mean RT and accuracy rate by congruency condition using `group_by()` and `summarize()`.

**6. Regression modeling**  
Applied LOESS regression to identify non-linear trends in response time across trial sequences.

---

## Key Findings

Incongruent trials produced consistently slower reaction times and higher error rates than congruent trials. This reflects the Flanker Effect: conflicting distractors increase the cognitive cost of response selection, raising both latency and error probability. LOESS modeling confirmed non-linear trends in response time across trial sequences.

---

## Repository Structure

```
cognitive-control-flanker/
├── README.md
├── analysis/
│   └── flanker_analysis.Rmd        ← Fully annotated R Markdown, end-to-end
└── data/
    ├── flanker_task.csv             ← Raw data (long format, trial-level)
    └── flank_wide.csv               ← Processed data (wide format, participant-level)
```

---

## Reproducibility

All analysis is contained in a single annotated `.Rmd` file. To reproduce:

```r
install.packages("tidyverse")
# Open analysis/flanker_analysis.Rmd in RStudio and knit
```

---

## Technologies

`R` · `tidyverse` · `ggplot2` · `dplyr` · `tidyr` · `RMarkdown`

---

## Reference

Eriksen, B. A., & Eriksen, C. W. (1974). Effects of noise letters upon the identification of a target letter in a nonsearch task. *Perception & Psychophysics*, 16(1), 143–149. https://doi.org/10.3758/BF03203267

---

*Millie Meng · New York University · Spring 2026*
