
---

# Executive Retail Performance Analytics Dashboard

<img width="1290" height="725" alt="image" src="https://github.com/user-attachments/assets/875f9050-9a88-4f8d-a367-9ba72754425f" />


---

## Navigation

- [Purpose](#purpose) 
- [Business Problem](#business-problem) 
- [Executive Questions](#executive-questions)
- [Dataset](#dataset)
- [Data Preparation](#data-preparation) 
- [Data Model](#data-model)
- [DAX Used (Measures)](#dax-used-measures)
- [Dashboard KPIs](#dashboard-kpis) 
- [Dashboard Design (Business Problem -> Analysis -> Insights & Recommendations -> Action)](#dashboard-design-business-problem---analysis---insights--recommendations---action)
- [Executive Business Insights](#executive-business-insights) 
- [Actionable Business Recommendations](#actionable-business-recommendations) 
- [Business Value Delivered](#business-value-delivered)
- [Tools & Skills Used](#tools--skills-used)

---

## Purpose

An executive-level Power BI dashboard providing retail leadership with consolidated visibility into monitoring sales performance, profit drivers, geographic performance contribution, and customer segment analysis for retail/wholesale operations through KPI-led reporting and interactive geographic/product analysis.

---

## Business Problem

Retail operations generate complex multi-dimensional data across products, geography, and customer segments, but leadership requires a single executive view to monitor performance trends, identify profit centers, and optimize resource allocation.

Retail leadership teams often lack a consolidated view of sales performance versus prior year, profit contribution by product category and geography, and return rates impacting bottom-line performance. This creates blind spots in revenue planning, product portfolio optimization, geographic expansion decisions, and customer segment strategy.

This dashboard delivers KPI-led monitoring of sales/profit versus prior year, product profitability analysis, geographic performance mapping, and segment contribution breakdown.

---

## Executive Questions

- How are sales and profit trending versus prior year performance? What are the percentage changes being observed over year?
- What is the return rate impact on overall business health? Did the return rates peaked or declined as per planning?
- Compare sales performance versus previous year over time ?
- Which product categories and subcategories drive profitability vs losses? Determine the most profitable and the most loss making product?
- Which geographic markets generate strongest profit contribution? Find out the place where most of the profit is happening?
- Which customer segments contribute most to sales revenue?


---

## Dataset

The project is built on the Superstore Dataset, a retail‑sales dataset .

It contains order‑level transaction data with columns such as Order ID, Order Date, Customer Name, Segment, City, State, Region, Product Category, Sub‑Category, Sales, Quantity, Discount, and Profit.

The dataset file is used to answer business questions around sales, profit, returns, and geography.

---

## Data Preparation

Only relevant tables and columns are imported:

- Orders table (fact table with metrics, dates, and dimensions).

- Returns table (filtered to keep only Order ID to flag returned orders).

In Power Query:

- Extra columns that are not needed for the KPIs are removed using “Choose Columns” to keep the model lean.

- The Returns table is cleaned by removing the Returned text column and keeping only Order ID to identify which orders were returned.

Data types are checked in the Orders table (e.g., Order Date as Date, Sales and Profit as Decimal) and left as‑is where they are already correct

---

## Data Model

The data model is built on three main elements:

- Orders (fact table with sales, profit, and dimensional attributes).

- Returns (a return‑flag table, linked to Order ID).

- A custom Date table created using CALENDAR( MIN(Order Date), MAX(Order Date) ) and marked as the Date table for time‑intelligence measures.

Relationships:

- Orders[Order ID] ↔ Returns[Order ID] (many‑to‑many; Returns filters Orders).

- Orders[Order Date] ↔ Date[Date] (fact‑date relationship for year‑over‑year and time‑based analysis).

Measures and organization:

- All key measures are stored in a “Key Measures” table (Sales, Profit, Percentage of Returned Orders, PY Sales/Profit, vs. PY % change).

- Measures are grouped into folders such as Metrics, PY Measures, and vs. PY to keep the model clean and easy to navigate.


**Tables Relationships and Cardinalities**

<img width="987" height="518" alt="image" src="https://github.com/user-attachments/assets/486f18d5-5392-496b-96fd-bf7620963c67" />


---

## DAX Used (Measures)


The dashboard includes the use of calculated tables, columns and measures derived using DAX for the analysis purpose. 


- ###  **Date Table**

  <img width="670" height="824" alt="image" src="https://github.com/user-attachments/assets/db36eecd-ae7f-4296-a637-7fc92a743cb1" />


- ###  **Sales**

<img width="576" height="199" alt="image" src="https://github.com/user-attachments/assets/7333d763-a056-495f-ac07-7d9ab1bc0797" />

- ###  **Profit**

<img width="889" height="305" alt="image" src="https://github.com/user-attachments/assets/fc930693-0fc5-47a3-9484-0d0790b500e9" />

- ###  **% Returned Orders**

  <img width="893" height="360" alt="image" src="https://github.com/user-attachments/assets/c25c1957-7431-455d-bc8a-620a4b338db9" />

- ###  **Sales PY** 

<img width="896" height="310" alt="image" src="https://github.com/user-attachments/assets/60676094-79d4-4733-bbd2-775efef2dfb6" />

- ###  **Profit PY** 

<img width="889" height="314" alt="image" src="https://github.com/user-attachments/assets/e66763f0-4938-4da7-a7c2-e18e94510b2c" />

- ###  **% Returned Orders PY**

<img width="413" height="130" alt="image" src="https://github.com/user-attachments/assets/18320934-e583-4505-88fc-c01d0632d34c" />

- ###  **Sales vs PY** 

<img width="897" height="308" alt="image" src="https://github.com/user-attachments/assets/8964e703-e02c-4b12-841b-78ecf671e498" />

- ###  **Profit vs PY** 

<img width="893" height="297" alt="image" src="https://github.com/user-attachments/assets/1ca609c3-191f-4278-a748-bfc65e6911f2" />

- ###  **% Returned Orders vs PY**

  <img width="894" height="314" alt="image" src="https://github.com/user-attachments/assets/ca192bab-520f-4f8c-99f0-e6f61fc2a885" />


These Dax functions helps in providing the base for drilling into more structured, detailed and specific analysis directed towards problem statement at hand.


---

## Dashboard KPIs

The dashboard includes 9 primary KPI cards to provide an at-a-glance view of business performance:

<img width="543" height="170" alt="image" src="https://github.com/user-attachments/assets/82f5086a-128b-4e93-bbbc-271daf2fe62e" />


- ### **Sales** – current sales, previous year sales and percentage change in sales wrto previous year 

<img width="197" height="168" alt="image" src="https://github.com/user-attachments/assets/e9bf1c47-41d9-4066-8079-955096975a13" />

- ### **Profit** – current profit, previous year profit and percentage change in profit wrto previous year 

<img width="193" height="164" alt="image" src="https://github.com/user-attachments/assets/04c00070-406f-4cc6-8d29-4c68a26672e3" />

- ### **% Returned Orders** – percentage of returned orders, previous year percentage of returned orders and percentage change wrto previous year 

<img width="198" height="164" alt="image" src="https://github.com/user-attachments/assets/6c18a97d-9227-4041-89d1-e7310e022a7e" />


These KPIs provide a leadership-level summary before drilling into more detailed analysis.


---


## Dashboard Design (Business Problem -> Analysis -> Insights & Recommendations -> Action)

### 1. KPI Card – Overall Metrics

- **Business Questions**:  
What are current Sales, Profit, and Percentage of Returned Orders, and how are they changing versus last year?

<img width="543" height="170" alt="image" src="https://github.com/user-attachments/assets/7cc8bf53-c1ec-46ea-8f3e-12f283dcb2ad" />

- **Business Insights**:  
The KPI cards show Sales and Profit along with the percentage of returned orders, including YoY change; negative vs‑PY values in % returned orders highlight improved performance or reducing returns.

- **Executive Decisions**:  
Prioritize improvement actions where Sales/Profit vs‑PY are low/negative or Returned‑Order % is increasing; maintain or scale up what is performing positively.



### 2. Line Chart – Sales vs. Previous Year Over Time

- **Business Questions**:  
How has current‑year sales performance evolved over time compared with the previous year?

<img width="698" height="291" alt="image" src="https://github.com/user-attachments/assets/4156a0ec-771e-4e75-bfb2-6c5f8e2da87a" />

- **Business Insights**:  
The line chart reveals periods where current‑year sales are above or below the previous‑year baseline, exposing growth phases and downturns by month.

- **Executive Decisions**:  
Investigate drivers behind underperforming months (e.g., seasonality, promotions, region issues) and replicate tactics from high‑growth periods.



### 3. Bar Chart – Profit by Product (Category & Sub‑Category)

- **Business Questions**:  
Which products are the most profitable, and which are loss‑making?

<img width="542" height="462" alt="image" src="https://github.com/user-attachments/assets/788e3f72-4c9e-46de-aaef-b444a6d0d9d2" />

- **Business Insights**:  
The chart shows products like Technology → Copiers contributing the highest profit, while others like Furniture → Tables are the most loss‑making

- **Executive Decisions**:  
Increase focus on high‑margin products and reevaluate pricing, stock, or marketing for loss‑making ones; consider discontinued or bundled strategies for the worst‑performing SKUs.

### 4. Map – Profit by State

- **Business Questions**:  
In which states is the company generating the most profit (and the most loss)?

<img width="356" height="337" alt="image" src="https://github.com/user-attachments/assets/448135bb-b16c-4df3-9c82-ff9382799582" />

- **Business Insights**:  
The map highlights states such as California as the most profitable and others like Texas as the most loss‑making, indicating strong regional performance gaps.

- **Executive Decisions**:  
Expand investment and marketing in top‑profit states and diagnose or restructure operations, pricing, or logistics in the most loss‑making states.

### 5. Donut Chart – Sales by Segment

- **Business Questions**:  
How are sales distributed across customer segments (e.g., Consumer, Corporate, Home Office)?

<img width="330" height="340" alt="image" src="https://github.com/user-attachments/assets/269b8ec8-337d-4931-a7b2-d43215ecb194" />

- **Business Insights**:  
The donut chart shows the share of total sales for each segment, indicating which segment contributes the largest portion of revenue.

- **Executive Decisions**:  
Allocate more sales and marketing resources to the highest‑revenue segment, while exploring targeted campaigns to grow smaller but promising segments.


---

## Executive Business Insights

- **Performance Monitoring:** KPI cards provide immediate executive snapshot with prior year comparisons
- **Trend Visibility:** Monthly sales trajectory supports revenue planning and seasonality detection  
- **Product Optimization:** Profit ranking identifies promotion priorities and loss review candidates
- **Geographic Strategy:** Map reveals market profit concentration for resource allocation
- **Segment Focus:** Customer breakdown guides targeted sales and retention efforts

---



## Actionable Business Recommendations

Based on the dashboard structure, the following actions would be relevant for business stakeholders:

1. **Review** monthly sales trends to time promotional campaigns effectively
2. **Promote** top-performing product categories while reviewing loss-making subcategories for pricing/positioning
3. **Monitor** return rates by product/geography to identify quality or fulfillment issues
4. **Invest** in highest-profit geographic markets. Prioritize investment in highest-profit states/provinces revealed by geographic analysis
5. **Target** highest-revenue generating customer segments. Focus sales efforts on these customer segments

---


## Business Value Delivered

This solution transforms transactional retail data into executive decision intelligence, enabling:
- Revenue performance monitoring
- Product portfolio optimization  
- Geographic market prioritization
- Customer segment strategy
- Return rate performance management

---
## Tools & Skills Used

- **Power BI**
- **Power Query**
- **Data Modeling**
- **DAX**
- **KPI Dashboard Design**
- **Business Performance Analysis**
- **Interactive Data Visualization**
- **Visual Story telling**
- **Time-Intelligence DAX**
- **Conditional formatting for storytelling**
- **Visual hierarchy for executive consumption**

---

---
