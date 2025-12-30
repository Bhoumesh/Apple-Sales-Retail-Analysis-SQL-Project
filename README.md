# SQL Sales Analysis Project (PostgreSQL)

## 📌 Project Overview
This project focuses on analyzing sales data using PostgreSQL to identify:
- Highest profit-generating products
- Country-wise profit performance
- Advanced SQL concepts such as window functions

---

## 🗂 Database Schema
The following Entity Relationship Diagram (ERD) represents the database structure used in this project:

![Database Schema](entity-relationship-diagram.png)

---

## 🎯 Problem Statement
**Write an SQL query to find the product with the highest profit in each country.**

---

## 🧠 SQL Concepts Used
- JOINs
- GROUP BY
- Aggregate Functions (`SUM`)
- Window Functions:
  - `RANK()`
  - `DENSE_RANK()`
- Subqueries

---

## 🧾 SQL Query

```sql
SELECT *
FROM (
    SELECT
        s1.country,
        p.product_name,
        SUM(profit) AS profit,
        DENSE_RANK() OVER (
            PARTITION BY s1.country
            ORDER BY SUM(profit) DESC
        ) AS d_ranks
    FROM sales s
    JOIN store s1 ON s.store_id = s1.store_id
    JOIN products p ON s.product_id = p.product_id
    GROUP BY 1, 2
) AS new_table
WHERE d_ranks = 1;


🛠 Tools & Technologies

**PostgreSQL

**SQL

**Git & GitHub


---


If you want, I can:
- Improve this README for **ATS & recruiters**
- Convert this into a **portfolio-level SQL project**
- Help you write **resume bullet points** from this project

Just tell me what you want next.
