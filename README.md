# 📊 User Referral Program Analysis

> **An end-to-end data analytics project** evaluating the effectiveness of a user referral program launched on October 31, 2015 — analyzing user growth, transaction volumes, spend behavior, and program economics using statistical hypothesis testing.

[![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python)](https://python.org)
[![Pandas](https://img.shields.io/badge/Pandas-2.0+-blue?logo=pandas)](https://pandas.pydata.org)
[![SciPy](https://img.shields.io/badge/SciPy-Stats-blue?logo=scipy)](https://scipy.org)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)](https://jupyter.org)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

---

## 📌 Project Overview

Company XYZ launched a referral program offering existing users **$10 in credit** when a referred user completes a purchase. After nearly one month of operation, the Growth Product Manager needed a data-driven assessment to present to leadership.

This project performs a full pre/post analysis of the program's impact, comparing key metrics before and after launch, segmenting by referral status and country, and applying statistical hypothesis testing to validate findings.

---

## 🎯 Business Questions

1. Did the referral program drive meaningful user growth?
2. Do referred users spend more than non-referred users?
3. Did overall platform spend increase after launch?
4. Is the $10 credit economically justified?
5. Which markets show the strongest referral adoption?

---

## 📁 Dataset

| Column | Description |
|--------|-------------|
| `user_id` | Unique identifier for each user |
| `date` | Date of the purchase transaction |
| `country` | User's country based on IP address |
| `money_spent` | Amount spent in USD |
| `is_referral` | Binary flag (1 = referred, 0 = organic) |
| `device_id` | Device used to make the purchase |

- **Total records:** 97,341
- **Date range:** October 3 – November 27, 2015
- **Countries:** CA, CH, DE, ES, FR, IT, MX, UK, US

---

## 🔍 Analysis Workflow

### 1. Data Cleaning & EDA
- Identified and removed exact duplicate records
- Converted date column to datetime
- Verified referral/non-referral distribution (71% / 29%)
- Assessed device_id cardinality (17,887 unique — excluded from analysis)

### 2. Pre/Post Split
- **Pre-launch:** October 3 – October 30
- **Post-launch:** November 1 – November 27
- ~4 weeks each — symmetric comparison window

### 3. Spend & Volume Analysis
- Time series: avg daily spend by referral status (pre and post)
- **Line chart: daily transaction volume pre vs post launch (with Oct 31 launch marker)**
- Bar chart: avg spend by country and referral status
- Bar chart: overall avg spend pre vs post launch
![Pre vs Post Refferal Transaction Volumne]("visuals/daily-pre-vs-post-transaction.png")

### 4. Country Analysis
- Referral adoption rate by country
- Avg spend comparison across markets

### 5. Statistical Hypothesis Testing

**H1 — Referral vs Non-Referral Spend (Post-Launch)**
- H₀: Mean spend is equal for referral and non-referral users
- H₁: Mean spend is greater for referral users
- Result: t=0.865, p=0.19 — **Fail to reject H₀**

**H2 — Daily User Growth**
- H₀: Mean daily unique users pre-launch = post-launch
- H₁: Mean daily unique users increased after launch
- Result: t=1.586, p=0.059 — **Fail to reject H₀ (borderline)**

**H3 — Overall Spend Lift**
- H₀: Mean spend per transaction pre-launch = post-launch
- H₁: Mean spend increased after launch
- Result: t=30.89, p≈0.000 — **Reject H₀**

### 6. Program Economics
- Total referral transactions: 28,015
- Total credit cost: $280,150
- Incremental spend (referral vs non-referral): $0.19
- **Net per referral transaction: -$9.81**

---

## 📈 Key Findings

1. **Referred users do not spend more** — Only $0.19 incremental spend vs non-referred users (p=0.19), insufficient to justify the $10 credit cost
2. **Program is running at a loss** — Net loss of $9.81 per referral transaction, $280,150 total credit cost in month one
3. **User growth is promising but unconfirmed** — Positive trend at p=0.059, just short of significance; needs 8–12 weeks of data to confirm
4. **Overall spend lifted significantly** — $42.39 → $46.96 avg spend (p≈0.000), but both referral and non-referral users lifted equally, pointing to November seasonality as the driver
5. **Top referral markets:** IT, MX, ES, FR (~31% adoption); **Weakest:** DE, CH (~23%)

---

## 💡 Recommendations

1. **Do not scale yet** — Reduce credit from $10 to $5 or make it conditional on the referred user's second purchase
2. **Run a proper A/B test** — Current analysis cannot isolate program impact from seasonal factors
3. **Retest user growth at 8–12 weeks** — More data needed for a conclusive result
4. **Analyze lifetime value** — Referred users may retain better over time, potentially justifying acquisition cost
5. **Focus on high-adoption markets** — Double down on IT, MX, ES, FR; investigate barriers in DE and CH
6. **Test alternative incentive structures** — Tiered credits, dual-sided rewards, or non-monetary incentives

---

## 🛠 Tech Stack

- **Python** — pandas, numpy, scipy, matplotlib, seaborn
- **Jupyter Notebook** — analysis and visualization
- **Statistical Testing** — independent samples t-test (scipy.stats)

---

## 🚀 Getting Started

```bash
# Clone the repo
git clone https://github.com/tbhatti211-wq/referral-program-analysis.git
cd referral-program-analysis

# Install dependencies
pip install -r requirements.txt

# Launch notebook
jupyter notebook referral_analysis.ipynb
```

---

## 📂 Project Structure

```
referral-program-analysis/
│
├── data/
│   └── referral.csv          # Raw dataset
│
├── referral_analysis.ipynb   # Main analysis notebook
├── requirements.txt          # Python dependencies
└── README.md
```

---

## 👤 Author

**Talib Hussain**
- GitHub: [@tbhatti211-wq](https://github.com/tbhatti211-wq)
- Email: tbhatti211@gmail.com