# Day 1: Blinkit Orders Analysis 📊

![Dashboard Preview](Screenshots/Page1_Overview.png)

## 📋 Project Overview
This is **Day 1** of my **30-Day Power BI Challenge**.  
I analyzed Blinkit order data to understand:
- Order volume and revenue trends
- Delivery performance
- Payment method preferences
- Store-wise performance

---

## 📈 Key Metrics
| Metric | Value |
|--------|-------|
| **Total Orders** | 1,285 |
| **Total Revenue** | ₹2.87 Cr |
| **Average Order Value** | ₹22.3K |
| **On-Time Delivery Rate** | 69.96% |

---

## 📊 Dashboard Pages

### Page 1: Overview
![Overview](Screenshots/Page1_Overview.png)

**Visuals:**
- 4 KPI Cards (Orders, Revenue, Avg Order Value, On-Time Rate)
- Delivery Status Breakdown (Donut Chart)
- Revenue by Payment Method (Bar Chart)
- Total Orders by Store (Bar Chart)

### Page 2: Detailed Analysis
![Detailed Analysis](Screenshots/Page2_Detailed.png)

**Visuals:**
- Orders by Year (2023 vs 2024)
- Revenue by Payment Method & Year
- Top Stores by Revenue
- Daily Order Trend

---

## 🔧 Tools Used
| Tool | Purpose |
|------|---------|
| **Power BI Desktop** | Data visualization & dashboard creation |
| **DAX** | Measures & calculated columns |
| **Power Query** | Data cleaning & transformation |

---

## 📐 DAX Measures Created
```dax
// Core Measures
Total Orders = COUNTROWS(blinkit_orders)
Total Revenue = SUM(blinkit_orders[order_total])
Avg Order Value = DIVIDE([Total Revenue], [Total Orders])

// Delivery Metrics
On-Time Rate = 
DIVIDE(
    CALCULATE(COUNTROWS(blinkit_orders), blinkit_orders[delivery_status] = "On Time"),
    [Total Orders]
)

// Payment Analysis
Revenue by Payment = 
SUMX(
    VALUES(blinkit_orders[payment_method]),
    CALCULATE([Total Revenue])
)