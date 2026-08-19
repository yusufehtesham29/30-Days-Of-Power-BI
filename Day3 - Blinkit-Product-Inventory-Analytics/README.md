# 🛒 Day 3: Blinkit Product Catalog & Inventory Analytics

![Dashboard Preview](dashboard_preview.png)

## 📌 Project Overview
An operational product catalog and inventory analytics dashboard for **Blinkit (Quick Commerce)**. This project evaluates category-level profit margins, shelf-life perishability risks, and stock-level safety buffers across 268 active SKUs to optimize merchandising and dark store inventory workflows.

---

## 📊 Executive Summary & Key KPIs
* **Total SKUs:** 268
* **Total Categories:** 11
* **Average Selling Price:** ₹488.36
* **Average Profit Margin:** 27.8%
* **Average Shelf Life:** 231.8 Days

---

## 💡 Strategic Business Insights
1. **High-Margin Value Drivers:** **Instant & Frozen Food** yields the highest gross margin (**40.0%**), followed closely by **Personal Care**, **Pet Care**, and **Snacks & Munchies** (**35.0%** each).
2. **High-Perishability Fast Movers:** **Fruits & Vegetables** (3-day shelf life) and **Dairy & Breakfast** (7-day shelf life) require strict Just-In-Time (JIT) replenishment and automated markdown schedules to minimize stock shrinkage.
3. **Inventory Buffer Optimization:** Minimum safety stock thresholds average ~20 units with maximum capacity capped at ~75 units across categories, balancing order fulfillment rates with dark store holding capacity.
4. **Stable Low-Margin Anchors:** Essential staples like **Grocery & Staples** operate on thinner margins (**15.0%**) but provide consistent repeat volume and low perishability risk (365-day shelf life).

---

## 🛠️ Technical Stack & Implementation

### 1. Data Transformation (Power Query / M)
* Cleaned whitespace across category and brand names.
* Applied explicit typing (IDs as Text, Quantities as Whole Numbers).
* Set price metrics (`price`, `mrp`) to Fixed Decimal Number (`Currency - INR ₹`).

### 2. DAX Calculations
* **Total SKUs:**
  ```dax
  Total Products = DISTINCTCOUNT(blinkit_products[product_id])

## 🛠️ Key DAX Measures

```dax
Total Products = DISTINCTCOUNT(blinkit_products[product_id])
```

```dax
Avg Selling Price = AVERAGE(blinkit_products[price])
```

```dax
Avg Margin % = AVERAGE(blinkit_products[margin_percentage]) / 100
```