<div align="center">

# 🏦 Day 20: Commercial Banking Churn & Capital Risk Intelligence Command

**Financial Risk Analytics, Balance Attrition Modeling & Multi-Product Exposure Dynamics**

[![Power BI](https://img.shields.io/badge/Power_BI-Desktop-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)](https://powerbi.microsoft.com/)
[![DAX](https://img.shields.io/badge/DAX-Financial_Modeling-0078D4?style=for-the-badge&logo=microsoftexcel&logoColor=white)](https://learn.microsoft.com/en-us/dax/)
[![Domain](https://img.shields.io/badge/Domain-Retail_&_Commercial_Banking-0D9488?style=for-the-badge)](https://en.wikipedia.org/wiki/Retail_banking)
[![Dataset](https://img.shields.io/badge/Dataset-Bank_Customer_Churn-20BEFF?style=for-the-badge&logo=kaggle&logoColor=white)](https://www.kaggle.com/)

<br/>

![Dashboard Preview](dashboard_preview.png)

</div>

---

## 📌 Executive Summary

This executive risk command center transitions customer attrition analysis from a simple binary event into a **capital balance exposure framework**. Evaluating **10,000 retail banking accounts** across France, Germany, and Spain representing **$764.86M in total portfolio deposits**, this report isolates liquidity loss, evaluates cross-selling friction across multi-product holdings, and pinpoints regional and demographic vulnerabilities across credit tiers.

> [!IMPORTANT]
> **Key Strategic Risk:** While total customer attrition stands at **20.37% (2,037 accounts)**, the bank has lost **$185.59M in deposits (24.26% of all capital)**. Churned depositors maintain significantly higher account balances (**$91,108.54**) than retained clients (**$72,745.30**), indicating an outflow of affluent capital.

---

## 📊 Core Banking & Risk Economics

| Strategic Banking Metric | Portfolio Value | Operational Risk Interpretation |
| :--- | :---: | :--- |
| **Total Deposited Portfolio** | **`$764.86M`** | Gross liquid deposits held across audited accounts. |
| **Capital Balance at Churn Risk** | **`$185.59M`** | Realized deposit outflow forfeited to competitor institutions. |
| **Retained Deposit Base** | **`$579.27M`** | Core stable liquidity backing commercial and retail operations. |
| **Portfolio Churn Rate %** | **`20.37%`** | Overall account attrition rate across 10,000 customers. |
| **Account Retention Rate %** | **`79.63%`** | Stable customer baseline representing 7,963 accounts. |
| **Mean Churned Account Balance** | **`$91,108.54`** | Average balance surrendered per churned customer. |
| **German Capital Exposure** | **`$97.97M (52.8%)`** | Concentration of all forfeited deposits originating from Germany. |
| **3+ Product Holding Attrition** | **`82.7% – 100.0%`** | Severe attrition cliff observed among accounts with 3 or 4 products. |

---

## 🧱 Data Architecture & Feature Engineering

The underlying model is structured on a clean analytical table (`BankChurn`) enriched via Power Query and DAX:

### ⚙️ Power Query Pipeline & Transformations
* **Dimensional Type Casting:** Converted `customer_id` to text; transformed numeric attributes (`credit_score`, `age`, `tenure`, `products_number`, `balance`, `estimated_salary`) to explicit whole number and fixed decimal types.
* **Credit Score Tiering (FICO Classification):**
  * `Exceptional (800+)`: Prime borrowers with minimal default risk.
  * `Very Good (740-799)` & `Good (670-739)`: Core commercial credit tiers.
  * `Fair (580-669)` & `Poor (<580)`: Elevated monitoring segment.
* **Demographic Age Brackets:** Classified customers into `< 30`, `30 - 39`, `40 - 49`, `50 - 59`, and `60+` to map lifecycle churn.
* **Categorical Feature Decoding:** Mapped binary flags into business labels (`Active Member` vs. `Inactive Member`, `Churned` vs. `Retained`).

---

## 📐 Enterprise DAX Formulations

### 1. Capital Balance at Churn Risk ($)
```dax
Balance at Churn Risk = 
CALCULATE(
    SUM(BankChurn[balance]),
    BankChurn[churn] = 1
)