# 🏅 Nobel Prize Winners — Exploratory Data Analysis (1901–2023)

> **DataCamp Guided Project — Python, pandas & seaborn**  
> Historical analysis of Nobel Prize laureates from 1901 to 2023 using the official Nobel Prize API dataset.

---

## 📌 Project Overview

The Nobel Prize has been one of the most prestigious international awards since 1901, recognizing achievements in Chemistry, Literature, Physics, Physiology or Medicine, Economics, and Peace. This project explores the full dataset of winners to uncover historical trends in gender, nationality, and repeat laureates.

**Questions answered:**
- Which gender and country have won the most Nobel Prizes?
- In which decade did the United States dominate most?
- When did female winners peak, and in which category?
- Who was the first woman to win — and who has won more than once?

---

## 🗂️ Dataset

**File:** `nobel.csv` — 1,000 rows, 18 columns (1901–2023, Nobel Prize API)

| Column | Description |
|---|---|
| `year` | Year the prize was awarded |
| `category` | Prize category |
| `full_name` | Laureate full name |
| `sex` | Gender of the laureate |
| `birth_country` | Country of birth |
| `organization_name` | Affiliated organization |
| `prize_share` | Share of the prize received |
| `laureate_type` | Individual or Organization |

---

## 🛠️ Tools

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)
![pandas](https://img.shields.io/badge/pandas-2.x-150458?logo=pandas)
![seaborn](https://img.shields.io/badge/seaborn-visualization-4C72B0)
![numpy](https://img.shields.io/badge/numpy-numerical-013243?logo=numpy)

---

## 📊 Key Findings

### Gender & Country Distribution
- **Male laureates dominate** the dataset: 905 men vs. 65 women across all categories and years.
- **United States of America** leads all countries with **291 prizes**, nearly 3× more than the UK (91) and Germany (67).

### US Dominance by Decade
The United States reached its peak proportion of Nobel Prize wins in the **2000s**, claiming approximately **42% of all prizes** awarded that decade — the highest US ratio in the dataset's history.

| Decade | US Share |
|---|---|
| 1900s–1950s | Growing gradually |
| 1960s–1990s | Strong presence |
| **2000s** | **~42% — peak dominance** |

### Female Laureates
- **First woman to win:** **Marie Curie** — Physics, **1903**
- Marie Curie is also a repeat winner (Physics 1903 + Chemistry 1911), one of only four individuals to win the Nobel Prize more than once.

### Repeat Winners
Laureates with 2 or more Nobel Prizes:

| Name | Prizes |
|---|---|
| Marie Curie | 2 (Physics + Chemistry) |
| Linus Carl Pauling | 2 (Chemistry + Peace) |
| John Bardeen | 2 (Physics) |
| Frederick Sanger | 2 (Chemistry) |
| Int'l Committee of the Red Cross | 3 (Peace) |
| UN High Commissioner for Refugees | 2 (Peace) |

---

## 💡 Analysis Approach

```python
import pandas as pd
import numpy as np
import seaborn as sns

# Calculate decade column
nobel_list['decade'] = np.floor(nobel_list['year'] / 10) * 10

# US dominance ratio per decade
us_winners = nobel_list[nobel_list['birth_country'] == 'United States of America']
us_ratio = us_winners.groupby('decade').size() / nobel_list.groupby('decade').size()
max_decade_usa = int(us_ratio.idxmax())

# Female winners — peak decade & category
fem_winners = nobel_list[nobel_list['sex'] == 'Female'].copy()
fem_ratio = fem_winners.groupby(['decade', 'category']).size() / total_by_decade_category
max_female_dict = {peak_decade: peak_category}
```

---

## 📁 Repository Structure

```
nobel-prize-eda/
├── notebook.ipynb
├── README.md
└── data/
    └── nobel.csv
```

---

## 👤 Author

**Leonardo Farfán** · Associate Data Analyst · DataCamp Certified  
[LinkedIn](https://linkedin.com/in/leofarfan) · leofarfan2604@gmail.com

*DataCamp Guided Project — Exploratory Data Analysis with Python*
