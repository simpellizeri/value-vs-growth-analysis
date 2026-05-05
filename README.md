[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/-q-Ajsn4)
[![Open in Codespaces](https://classroom.github.com/assets/launch-codespace-2972f46106e565e64193e422d61a12cf1da4916b45550586e14ef0a7c637dd04.svg)](https://classroom.github.com/open-in-codespaces?assignment_repo_id=23439876)
# Value vs. Growth Through Time
### FIN 4975 — Data Analysis in Finance
**Student:** Samantha Impellizeri  
**Professor:** Adam Aiken  
**Date:** May 2026  

---

## Research Question
How do different definitions of value — Book-to-Market (BM) and Earnings-to-Price 
(EP) — compare in their ability to predict stock returns, and has the relative 
performance of these measures changed over time?

---

## Motivation
Value investing — buying stocks that are cheap relative to their fundamentals — 
is one of the most studied strategies in finance. Fama and French (1993) 
documented that high Book-to-Market stocks consistently outperform low 
Book-to-Market stocks. However, in recent decades this "value premium" has 
weakened significantly, particularly after the 2008 financial crisis.

This project investigates two questions:
1. Does the value premium still exist?
2. Does it matter how you define "value"?

We compare two measures — BM and EP — across five notebooks covering 
descriptive analysis, regression testing, factor models, and macro analysis.

---

## Data Sources
- **Open Asset Pricing** — Quintile portfolio returns for BM and EP signals  
  (Chen & Zimmermann, 2022)
- **Fama-French Data Library** — Three-factor model returns (Mkt-RF, SMB, HML)  
  (Fama & French, 1993)
- **FRED** — 10-year Treasury yield (GS10) and VIX (VIXCLS)

---

## Repository Structure
| Notebook | Description |
|---|---|
| `01_data.ipynb` | Download and clean BM, EP, and Fama-French data |
| `02_charts.ipynb` | Bar charts, cumulative returns, rolling spreads |
| `03_regression.ipynb` | Time trend and post-2007 OLS regressions |
| `04_factor_model.ipynb` | Fama-French three-factor regressions |
| `05_macro.ipynb` | FRED macro data and interest rate regressions |

---

## How to Reproduce
1. Clone this repository
2. Install dependencies: `pip install openassetpricing pandas-datareader 
   fredapi statsmodels matplotlib seaborn python-dotenv`
3. Add your FRED API key to a `.env` file: `FRED_API_KEY=your_key_here`
4. Run notebooks in order from 01 to 05

---

## Key Findings

### 1. The Value Premium Exists But Has Weakened
Both BM and EP show higher average returns for value stocks (Q5) vs growth 
stocks (Q1) over the full sample. However, Chart 3 shows that the value 
premium has become increasingly unreliable since 2007, with extended periods 
where growth stocks outperform.

### 2. The Decline is Statistically Significant for BM — But Not EP
Our time trend regression shows that the BM value premium has declined 
significantly over time (t = -2.342, p = 0.019). The post-2007 dummy 
confirms this collapse was concentrated after the financial crisis 
(coefficient = -0.81%, t = -3.077, p = 0.002).

EP tells a different story — neither the time trend nor the post-2007 
dummy is statistically significant, suggesting EP has been a more 
stable value measure.

### 3. BM Generates Alpha Beyond the Fama-French Factors
Our factor model regression shows BM generates statistically significant 
alpha of 0.40% per month (t = 3.684, p = 0.000) even after controlling 
for market, size, and value risk. EP generates no significant alpha 
(t = 0.507, p = 0.613).

### 4. Rising Interest Rates Benefit the BM Value Premium
When the 10-year Treasury yield rises by 1%, the BM value spread increases 
by 0.02 per month (t = 2.640). This supports the theory that the prolonged 
low interest rate environment after 2008 contributed to value underperformance. 
EP shows no significant relationship with macro variables.

---

## Conclusion
The value premium is real but fragile. How you define value matters enormously:

- **BM** has weakened significantly since 2008, correlates with interest rates, 
  but still generates alpha — suggesting it captures something real but 
  increasingly noisy.
- **EP** is more stable over time but doesn't generate independent alpha — 
  its returns are fully explained by known risk factors.

For a hedge fund considering a value strategy today, EP may be the more 
reliable signal given its stability, while BM's sensitivity to interest 
rates makes it more useful as a macro-timing tool.

---

## References
- Chen, A., & Zimmermann, T. (2022). Open asset pricing. *Journal of 
  Financial Economics*, 145(2), 795–817.
- Fama, E. F., & French, K. R. (1993). Common risk factors in the returns 
  on stocks and bonds. *Journal of Financial Economics*, 33(1), 3–56.
- Lakonishok, J., Shleifer, A., & Vishny, R. W. (1994). Contrarian 
  investment, extrapolation, and risk. *Journal of Finance*, 49(5), 1541–1578.