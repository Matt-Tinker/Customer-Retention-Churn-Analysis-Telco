# Customer Retention & Churn Analysis (Telco)

Welcome! This project analyzes customer retention and churn using PostgreSQL → Excel → Tableau on a Telco subscription dataset. It’s structured to read like a real business case and to be portfolio-ready for recruiters.

---

# Project Background

  
**Business:** Subscription telecommunications provider (consumer internet/phone/TV).  
**Model:** Monthly/annual contracts; recurring revenue with optional add-on services.  
**Key Metrics:** Active customers, churn rate, cohort retention, customer lifetime value (LTV), ARPU, discount/contract effects.

Its business model depends on **recurring monthly and annual contracts**, supplemented by optional add-on services.  
Customer churn directly impacts recurring revenue, making retention a top strategic priority.

Insights and recommendations are provided on the following key areas:

- **Cohort Retention & Churn**
- **Customer Lifetime Value (LTV)**
- **Contract & payment risk segments**
- **Payment Friction**


An interactive Tableau dashboard used to report churn and retention trends can be found here: _(insert Tableau Public link)_  

---

# Executive Summary

### Overview of Findings

- **Early lifecycle is high risk.** Customers in their first year churned at **47.4%**, compared to only **6.6%** churn after 5+ years.  
- **Retention multiplies value.** Average LTV increased from **$276** in early cohorts to **$5,181** for long-tenure customers.  
- **Contract & payment type matter most.** **Month-to-month contracts (42.71% churn)** and **Electronic check payments (45.29% churn)** are high-risk segments to prioritize.  

[Visualization: snapshot of Tableau Overview dashboard]

---

# Data Structure & Initial Checks

The company’s main database for this project consisted of one key table: **`telco_customers`** with ~7,043 records.  

A description of the key fields is as follows:
- **Demographics:** `gender`, `SeniorCitizen`, `Partner`, `Dependents` 
- **Tenure & economics:** `tenure` (months), `MonthlyCharges`, `TotalCharges`   
- **Products:** `Phone Service`, `Internet Service`, `Online Security`, `Streaming`  
- **Commercials:** `Contract`, `PaperlessBilling`, `PaymentMethod`  
- **Target:** `Churn` (Yes/No)

Initial data checks:  
- `TotalCharges` was provided as text with blanks; cleaned to numeric with `NULLIF`.  
- Cohorts were constructed using **tenure buckets (0–1 yr, 1–2 yrs, etc.)** due to lack of explicit signup dates.  

---

# Insights Deep Dive

### Category 1: Cohort Retention & Churn

* **First year is most vulnerable.** 0–1 yr customers churn at 47.4%.  
* **Churn declines with tenure.** By 5+ yrs, churn drops to 6.6%.  
* **Tenure averages differ.** Churned customers average 18 months vs 37.6 months for retained.  
* **Retention programs in year 1** could yield outsized impact.  


### Category 2: Customer Lifetime Value (LTV)

* **LTV rises with tenure.** Avg LTV = $276 for 0–1 yr, $5,181 for 5+ yrs.  
* **Value compounds over time.** Retained customers generate significantly higher revenues.  
* **Small early churn reductions** lead to large downstream LTV gains.  
* **Focus on early retention** drives long-term revenue stability.  


### Category 3: Contract Risk Segments

* **Month-to-month contracts:** 42.7% churn.  
* **Annual contracts:** materially lower churn rates.  
* **Longer contracts stabilize retention.**  
* **Contract migration offers** could shift customers to safer cohorts.  


### Category 4: Payment Friction

* **Electronic check:** 45.3% churn, highest risk.  
* **Auto-pay methods (credit/bank transfer):** lower churn.  
* **Friction in payments increases churn risk.**  
* **Campaigns to switch payment methods** could reduce churn significantly.  


---

# Recommendations:

Based on the insights and findings above, I recommend the Retention & Growth team take the following actions:  

* **Onboarding sprints (months 1–6).** Focus on service activation and value education in the early lifecycle.  
* **Contract migration offers.** Incentivize month-to-month → annual contract upgrades. upgrades (credits, device perks) to pull customers into lower-risk cohorts.  
* **Payment optimization campaigns.** Nudge **Electronic check** users to **auto-pay** or **bank transfer** to reduce failed payments and involuntary churn.
* **Segmented outreach.** Combine **Contract + Payment + InternetService** to focus outreach on the highest-risk micro-segments first.  
* **Lifecycle KPIs.** Make early churn reduction **0–1 yr churn** and **1–2 yr LTV growth** executive KPIs; measure weekly.  

---

# Assumptions and Caveats:

Throughout the analysis, the following assumptions were made:  

* **Cohorts defined by tenure** (0–1 yr, 1–2 yrs, etc.) in absence of true signup dates.  
* **TotalCharges blanks cleaned** with `NULLIF` before numeric conversion.  
* **Dataset is a sample** from a single telecom provider; competitor or market shocks are not captured.  
* **Associations, not causation.** Churn correlations (e.g., payment type) require experiments for causal validation.  

---
