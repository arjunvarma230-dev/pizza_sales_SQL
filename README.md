# 🍕 Pizza Sales Analysis — Complete SQL Case Study

A full SQL-driven analysis of a pizza sales dataset using **MySQL**.  
This project contains **13+ SQL files**, organized by topic and difficulty, covering real business questions, revenue analytics, and time-based insights.  
Perfect for showcasing **SQL + Data Analyst skills**.

---

## 📂 Repository Structure


---

## 📊 Dataset Overview

The database consists of the following tables:

| Table | Description |
|-------|-------------|
| **orders** | Stores each order with order timestamp |
| **order_details** | Contains line-items per order |
| **pizzas** | Pizza size, type, and price |
| **pizza_types** | Category and pizza names |

---

## 🎯 Business Questions Answered

### 🔰 **Basic SQL**
- Total number of orders  
- Total revenue generated  
- Highest-priced pizza  
- Most common pizza size  
- Top 5 most ordered pizzas  

### ⚙️ **Intermediate SQL**
- Total quantity per pizza category  
- Orders by hour of the day  
- Revenue per pizza type  
- Category performance breakdown  

### 🚀 **Advanced SQL**
- Percentage contribution of each pizza type to total revenue  
- Multi-table joins across all tables  
- Subqueries for KPI calculations  
- GROUP BY + HAVING filtering  
- Ranking pizzas (if applicable)  

---

## 🧠 SQL Concepts Demonstrated

- **INNER JOIN** across multiple tables  
- **Aggregate functions** (SUM, COUNT, AVG, MAX)  
- **Subqueries** (correlated + non-correlated)  
- **Time functions** (HOUR(), DATE(), etc.)  
- **Category-level insights**  
- **Revenue analysis**  
- **Business logic inside SQL**  

---

## 🧩 Sample Advanced Query

```sql
-- Percentage revenue contribution per pizza type
SELECT 
    pt.name AS pizza_type,
    ROUND(
        SUM(od.quantity * p.price) * 100 /
        (SELECT SUM(od2.quantity * p2.price)
         FROM order_details od2
         JOIN pizzas p2 ON od2.pizza_id = p2.pizza_id),
    2) AS revenue_percentage
FROM order_details od
JOIN pizzas p ON od.pizza_id = p.pizza_id
JOIN pizza_types pt ON p.pizza_type_id = pt.pizza_type_id
GROUP BY pt.name
ORDER BY revenue_percentage DESC;
