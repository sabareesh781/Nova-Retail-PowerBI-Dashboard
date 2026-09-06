# Nova Retail — Sales Performance & Profitability Dashboard

## Project Overview

Nova Retail is a fictional Indian retail business created for portfolio and analytical practice.

This project transforms raw transactional sales data into an interactive three-page Power BI dashboard for analysing sales performance, profitability, customers, products, regions, and salespeople.

**Tools:** Power BI | Power Query | DAX | Data Modelling

---

## Business Objectives

The dashboard was designed to answer the following business questions:

1. How much revenue and profit is Nova Retail generating?
2. How is revenue changing over time?
3. Which regions contribute the most revenue?
4. Which product categories generate the highest profit?
5. Which individual products generate the most revenue?
6. Which products generate the highest profit?
7. Which customers contribute the most revenue?
8. Are there high-revenue products with relatively low profit margins?
9. Which salespeople generate the highest revenue?
10. How can management use these insights to improve sales and profitability?

---

## Dataset

The project uses five related tables:

| Table | Purpose |
|---|---|
| Sales_Raw | Transaction-level sales, quantity, revenue, cost, discount, and IDs |
| Customers | Customer details and regional information |
| Products | Product names and categories |
| Salespersons | Salesperson information |
| Calendar | Date dimension covering 2024–2025 |

The `Sales_Raw` table acts as the central fact table, while `Customers`, `Products`, `Salespersons`, and `Calendar` function as dimension tables.

**Note:** The dataset is synthetic and was created specifically for portfolio and learning purposes.

---

## Data Cleaning & Transformation

Data preparation was performed using Power Query.

Key activities included:

- Removing duplicate transaction rows.
- Correcting data types, including `OrderDate`.
- Reviewing missing values in key fields.
- Standardising inconsistent text values using trimming.
- Reviewing negative quantities and zero-price records as data-quality issues.
- Preparing the tables for reliable relationships and analysis.

---

## Data Model

The report uses a **star-schema** structure.

### Fact Table

**Sales_Raw**

Contains transactional information including:

- OrderID
- OrderDate
- CustomerID
- ProductID
- SalespersonID
- Quantity
- UnitPrice
- Discount
- Sales
- Cost

### Dimension Tables

- **Customers**
- **Products**
- **Salespersons**
- **Calendar**

The dimension tables have one-to-many relationships with the `Sales_Raw` fact table.

---

## DAX Measures

The main measures created for the analysis were:

```DAX
Total Revenue = SUM(Sales_Raw[Sales])

Total Cost = SUM(Sales_Raw[Cost])

Total Orders = DISTINCTCOUNT(Sales_Raw[OrderID])

Total Profit = [Total Revenue] - [Total Cost]

Profit Margin = DIVIDE([Total Profit], [Total Revenue], 0)
```
