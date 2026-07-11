# Cognitive Control & the Flanker Effect

**Behavioral data analysis · PSYCH-UA 300 · NYU, Spring 2026**

---

## Overview

This project analyzes data from the **Eriksen Flanker Task** (Eriksen & Eriksen, 1974) to investigate how congruency and response accuracy affect reaction time. The Flanker Task is a classic paradigm in cognitive psychology used to study attention, cognitive control, and interference suppression.

Participants identified the direction of a central arrow while ignoring flanking arrows that were either **congruent** (e.g., `>>>>>`) or **incongruent** (e.g., `>><>>`). Data were collected from both a healthy control group and a test group (participants with a specific medical condition).

---

## Dataset

| Variable | Type | Description |
|---|---|---|
| `subject` | ID | Participant identifier |
| `group` | Independent | `"control"` vs. `"test"` |
| `congruency` | Independent | `"congruent"` vs. `"incongruent"` |
| `result` | Dependent | `"correct"`, `"incorrect"`, or `"timeout"` |
| `rt` | Dependent | Reaction time (seconds) |

---

## Analysis

**1. Data Visualization** — Distributions of reaction time by congruency, accuracy, and their interaction (using `ggplot2`).

**2. Data Reshaping** — Converted long-format trial data to wide format using `pivot_wider()` and `unite()`, enabling individual-level aggregation.

**3. Individual Averages** — Computed each participant's mean RT for congruent and incongruent trials separately using `rowMeans()`.

**4. Data Joining** — Merged averaged data back into the long-format dataset with `left_join()`; identified participants with missing demographic data using `anti_join()`.

**5. Descriptive Statistics** — Summarized mean RT and accuracy by congruency condition using `group_by()` and `summarize()`.

---

## Key Finding

Incongruent trials produced **slower reaction times and higher error rates** than congruent trials — a pattern consistent with the classic Flanker Effect, reflecting the cognitive cost of suppressing conflicting flanking information.

---

## Tools

`R` · `tidyverse` · `ggplot2` · `dplyr` · `tidyr`

---

## Repository Structure

```
cognitive-control-flanker/
│
├── README.md
├── analysis/
│   └── flanker_analysis.Rmd    ← Annotated R Markdown analysis
└── data/
    ├── flanker_task.csv         ← Raw data (long format)
    └── flank_wide.csv           ← Processed data (wide format, exported)
```

---

## Reference

Eriksen, B. A., & Eriksen, C. W. (1974). Effects of noise letters upon the identification of a target letter in a nonsearch task. *Perception & Psychophysics*, 16(1), 143–149. https://doi.org/10.3758/BF03203267

---

*Millie Meng · Psychology B.A. · New York University · Class of 2027*
