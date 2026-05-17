# Global E-Commerce Retention & Growth Analytics Model

A high-performance, single-query SQL data model designed to drive Customer Relationship Management (CRM) and Growth Analytics dashboards. This master query processes raw transactional data into a single, comprehensive dataset (Single Source of Truth) to power dynamic Business Intelligence (BI) tools like Tableau, Power BI, or Looker Studio.

## 📊 Business Problem & Analytics Strategy

In modern e-commerce enterprises, tracking high-level metrics like total sales is no longer enough. The growth team needs to know *how fast customers are returning*, *whether their spending appetite is growing*, and *how to smooth out seasonal purchase anomalies*. 

Instead of running separate resource-heavy scripts, this project utilizes **Advanced Window Functions** and **Analytical Frameworks** to compute multiple critical customer behavioral metrics side-by-side in a single execution.

---

## 📈 Calculated Key Performance Indicators (KPIs)

The master SQL engine delivers three core analytical columns directly on the granular transaction level:

1. **Customer Return Velocity (Retention - `previous_order_date_diff`):**
   * Calculates the exact number of days that elapsed between the customer's previous purchase and their current order using chronologically sequenced time-series delta analysis.
   * *Business Value:* Tracks purchase frequency and provides early churn indicators if the time-to-return gap starts widening.

2. **Basket Growth Rate % (Growth - `previous_order_growth_rate`):**
   * Measures the net financial percentage change (expansion or contraction) of the customer's current basket compared directly to their last order. 
   * Built-in logical guardrails seamlessly handle edge cases (like a customer's first-ever purchase) to prevent `Division by Zero` runtime errors.
   * *Business Value:* Identifies if customer accounts are expanding or shrinking over time, measuring the true impact of cross-selling and upselling strategies.

3. **3-Order Moving Average (Trend Smoothing - `last_three_order_avg`):**
   * Utilizes sliding window frame boundaries to calculate a dynamic average of the customer's spending across their current transaction and the two preceding ones.
   * *Business Value:* Strips away short-term noise and individual outlier spikes to reveal the true trajectory of long-term customer spending behavior.

---

## 🛠️ Advanced SQL Techniques Showcased

- **Analytical Window Functions:** Comprehensive deployment of `LAG()` and `AVG()` partitions.
- **Dynamic Window Framing:** Precise definition of moving boundaries using `ROWS BETWEEN 2 PRECEDING AND CURRENT ROW`.
- **Conditional Data Sanitization:** Complex conditional logic utilizing `CASE WHEN`, `COALESCE()`, and `NULL` pattern matching to handle missing history on initial touchpoints.
- **Multi-Layered Subquery Architecture:** Decoupling raw aggregations from advanced window calculations to optimize performance and readability without using temporary tables.

---

<img width="1405" height="738" alt="Global E-Commerce Retention   Growth Dashboard" src="https://github.com/user-attachments/assets/e1523e78-a2ff-43a3-bb9a-d11442c40f8f" />
