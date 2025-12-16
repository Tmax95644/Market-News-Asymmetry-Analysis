# Market News Coverage Across Bull and Bear Market Conditions  
### S&P 500 News Coverage Analysis (Python / MediaCloud)

---

## Project Overview

This project examines whether **large daily declines in the S&P 500 receive more media coverage than large daily gains**.

The analysis combines:

- **Daily S&P 500 (^GSPC) price data** from Yahoo Finance  
- **Daily financial news article counts** from MediaCloud  

A widely held assumption in financial commentary is tested:

> *“Bad market days attract more news coverage than good market days.”*

Rather than relying on anecdotal evidence, this project evaluates that claim using market data and large-scale news coverage statistics.

---

## Research Question

**Do large negative market moves generate more media coverage than similarly large positive moves?**

---

## Data Sources

### Market Data
- **S&P 500 (^GSPC)** daily prices  
- Source: *Yahoo Finance* (via `yfinance`)  
- Daily return defined as **open-to-close percentage change**

### News Data
- **MediaCloud** daily article counts  
- Query phrases:
  - “stock market”
  - “financial markets”
  - “equity markets”
  - “share market”

> Raw MediaCloud data files are not included due to size and licensing constraints.

---

## Tools & Libraries

- Python  
- pandas  
- matplotlib  
- seaborn  
- yfinance  

---

## Methodology

### 1. Data Preparation
- Parsed and aligned dates across market and news datasets  
- Cleaned MediaCloud output to retain daily article counts  
- Calculated daily S&P 500 returns using:

\[
\text{Return} = \frac{\text{Close} - \text{Open}}{\text{Open}} \times 100
\]

---

### 2. Exploratory Analysis
- Compared article counts on the **20 largest gain days** and **20 largest loss days**
- Results showed strong sensitivity to **outliers**, motivating a more robust comparison framework

---

### 3. Like-for-Like Threshold Analysis
To compare market moves of similar magnitude, trading days were classified using **symmetric thresholds**:

- **Large Loss:** ≤ −3%  
- **Large Gain:** ≥ +3%  

Key metrics evaluated:
- Number of qualifying days  
- Mean article count  
- Median article count  

The analysis was repeated using a **±2.5% threshold** to increase sample size and test robustness.

---

### 4. Lag Analysis
To assess whether media attention peaks *after* large market declines, article volumes were analysed across multiple horizons:

- Same day  
- 1 day after  
- 2 days after  
- 3 days after  

---

## Key Findings

- Both **large gains and large losses** attracted substantially more news coverage than typical trading days  
- Contrary to the initial hypothesis, **large positive market moves often received equal or greater coverage** than large negative moves  
- News coverage peaked **on the same day** as large market losses and declined in subsequent days  
- Results were **consistent across different threshold definitions**

---

## Interpretation

These findings suggest that **media coverage is driven more by market extremity and narrative significance** than by negativity alone.

Large and unusual market moves — regardless of direction — appear to attract disproportionate media attention.

---

## Limitations

- Small sample sizes for extreme market days  
- Article counts do not capture **sentiment or tone**  
- MediaCloud reflects curated sources rather than the full global news ecosystem  
- Daily aggregation obscures intraday timing effects  

---

## SQL Replication & Validation

To ensure these results were not specific to MediaCloud or Python-based processing, the analysis was replicated using **SQL** and an independent dataset:

- **Dataset:** GDELT global news database  
- **Tools:** SQLite  
- **Method:** Identical market thresholds, classification logic, and aggregation methods  

🔗 **Related Project:**  
[S&P 500 News Coverage Asymmetry — SQL / GDELT](https://github.com/Tmax95644/Market-Moves-Media-Coverage-SQL-Replication-Using-GDELT)

The SQL-based replication produced **directionally consistent results**, strengthening confidence in the conclusions.
