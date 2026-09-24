\# 🛍️ Day 19: E-Commerce Customer Lifetime Value (CLV), RFM Segmentation \& Cohort Velocity



!\[Dashboard Preview](dashboard\_preview.png)



\## 📌 Executive Overview

This multi-dimensional commercial retail command center evaluates customer acquisition health, order velocity, and customer lifetime value (CLV) across \*\*805,549 verified transactions\*\* and \*\*36,969 purchase orders\*\* generating \*\*$17.74M in gross sales revenue\*\* across 41 global markets. It implements an enterprise \*\*Recency, Frequency, Monetary (RFM)\*\* behavioral segmentation model, isolating high-yield customer cohorts and flagging \*\*$1.65M in at-risk revenue exposure\*\*.



\---



\## 🔑 Core Commercial \& RFM KPIs

\* \*\*Total Sales Revenue:\*\* $17.74M ($17,743,429.18)

\* \*\*Total Dispatched Orders:\*\* 36,969 Purchase Invoices

\* \*\*Total Active Customer Profiles:\*\* 5,878 Accounts

\* \*\*Average Order Value (AOV):\*\* $479.95

\* \*\*Average Spend per Customer:\*\* $3,018.62

\* \*\*Champions Revenue Contribution:\*\* 64.1% ($11.37M across 921 top-tier clients)

\* \*\*At-Risk Revenue Exposure:\*\* $1.65M (742 lapsed repeat buyers)

\* \*\*Primary Geographic Market:\*\* United Kingdom ($14.72M | 83.0% share)



\---



\## 📥 Data Source \& Reproduction Instructions

Due to GitHub file size limits (>25 MB web / >100 MB Git), the raw 94 MB dataset is hosted externally.



\* \*\*Primary Source:\*\* \[Kaggle - Online Retail II UCI Dataset](https://www.kaggle.com/datasets/mashlyn/online-retail-ii-uci)

\* \*\*File Used:\*\* `online\_retail\_II.csv` (1,067,371 rows × 8 features)



\### Local Reproduction Steps:

1\. Download `online\_retail\_II.csv` from the Kaggle link above.

2\. Place the file inside the project directory.

3\. Open `Customer\_Lifetime\_Value\_RFM\_Command.pbix` in \*\*Power BI Desktop\*\*.

4\. If prompted, go to \*\*Transform Data > Data source settings > Change Source\*\* and point to your local file path.



\---



\## 🛠️ Data Architecture \& Star Schema Model

The model structures a high-performance \*\*Star Schema\*\* separating raw transactional logs from analytical dimensions:



```

&#x20;      ┌────────────────────────┐

&#x20;      │        DimDate         │

&#x20;      │  (DAX Generated Table) │

&#x20;      └───────────┬────────────┘

&#x20;                  │ 1

&#x20;                  │ \*

┌──────────────────┴──────────────────┐          ┌────────────────────────┐

│              FactSales              │ \*      1 │      DimCustomer       │

│         (805,549 Records)           ├──────────┤  (DAX Customer Matrix) │

└─────────────────────────────────────┘          └────────────────────────┘

```



\* \*\*Data Hygiene in Power Query:\*\*

&#x20; \* Pruned 243,007 guest checkout records with null `Customer ID` to maintain individual-level tracking.

&#x20; \* Filtered out credit note cancellations (`Invoice` starting with "C") and negative return adjustments (`Quantity` $\\le$ 0, `Price` $\\le$ 0).

&#x20; \* Standardized `InvoiceDate` to discrete Date format to ensure clean 1:\* relational integrity with `DimDate`.



\---



\## 📐 Core Analytical DAX Formulations



\### 1. RFM Behavioral Segmentation (DAX Dimension Table)

```dax

CustomerSegment = 

SWITCH(

&#x20;   TRUE(),

&#x20;   DATEDIFF(\[LastPurchaseDate], DATE(2011, 12, 10), DAY) <= 60 \&\& \[TotalOrders] >= 6 \&\& \[TotalSpend] >= 2500, "Champions",

&#x20;   DATEDIFF(\[LastPurchaseDate], DATE(2011, 12, 10), DAY) <= 120 \&\& \[TotalOrders] >= 3, "Loyal Customers",

&#x20;   DATEDIFF(\[LastPurchaseDate], DATE(2011, 12, 10), DAY) <= 60 \&\& \[TotalOrders] < 3, "New \& Promising",

&#x20;   DATEDIFF(\[LastPurchaseDate], DATE(2011, 12, 10), DAY) > 180 \&\& \[TotalOrders] >= 3, "At Risk",

&#x20;   DATEDIFF(\[LastPurchaseDate], DATE(2011, 12, 10), DAY) > 180 \&\& \[TotalOrders] < 3, "Hibernating / Lost",

&#x20;   "Needs Attention"

)

```



\### 2. Champions Revenue Dominance Share %

```dax

Champions Revenue Share % = 

DIVIDE(

&#x20;   CALCULATE(\[Total Sales Revenue], DimCustomer\[CustomerSegment] = "Champions"),

&#x20;   CALCULATE(\[Total Sales Revenue], ALL(DimCustomer\[CustomerSegment])),

&#x20;   0

)

```



\---



\## 💡 Strategic Executive Insights

1\. \*\*The 64% Champions Concentration:\*\* 15.7% of the customer base (921 accounts) generates \*\*$11.37M\*\* of total revenue. Maintaining service levels and VIP incentives for this core cohort is critical to top-line stability.

2\. \*\*Reactivation Opportunity ($1.65M):\*\* 742 repeat accounts with proven purchasing history have not transacted in over 350 days. Targeting this cohort with automated win-back workflows represents a high-ROI retention initiative.

3\. \*\*Cross-Border Growth Potential:\*\* While domestic UK sales dominate ($14.72M), Western European markets (EIRE at $622K, Netherlands at $554K, Germany at $431K) show consistent repeat order patterns that can be scaled with localized operations.



\---



\## 📂 Repository Contents

\* `Customer\_Lifetime\_Value\_RFM\_Command.pbix` — Interactive Power BI application.

\* `dashboard\_preview.png` — High-resolution executive dashboard screenshot.

\* `README.md` — Project documentation and methodology guide.

