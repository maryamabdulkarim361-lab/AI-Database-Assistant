# 🤖 AI Database Assistant

<p align="center">
  <strong>
    Natural Language → SQL → PostgreSQL → Insights
  </strong>
</p>

<p align="center">
  An AI-powered database analytics platform that allows users to explore PostgreSQL data using natural language, generated SQL, and interactive analytics.
</p>

<p align="center">

![Python](https://img.shields.io/badge/Python-3.12+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Django](https://img.shields.io/badge/Django-REST-092E20?style=for-the-badge&logo=django&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Database-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)
![React](https://img.shields.io/badge/React-TypeScript-61DAFB?style=for-the-badge&logo=react&logoColor=black)

</p>

---

# 🚀 What is AI Database Assistant?

**AI Database Assistant** is a full-stack database analytics application that lets users interact with structured PostgreSQL data using natural language.

Instead of manually writing SQL queries, users can ask questions such as:

> **"What are our top 10 customers by total order value?"**

The system processes the request, generates SQL, validates the query, executes it against PostgreSQL, and presents the results in a readable format.

```text
User Question
      │
      ▼
┌──────────────────────┐
│   AI Query Service   │
└──────────┬───────────┘
           │
           ▼
     Generated SQL
           │
           ▼
┌──────────────────────┐
│   SQL Validator      │
└──────────┬───────────┘
           │
           ▼
      PostgreSQL
           │
           ▼
    Query Results
           │
           ▼
┌──────────────────────┐
│ Analytics Dashboard  │
└──────────────────────┘
```

---

# 🖥️ Application Preview

> Add your actual Antigravity-generated screenshots inside `docs/screenshots/`.

<p align="center">
  <img src="docs/screenshots/hero.png" width="100%">
</p>

<p align="center">
  <em>AI Database Assistant — main analytics interface</em>
</p>

---

# ✨ Core Features

<table>
<tr>

<td width="50%">

## 🤖 AI SQL Generation

<p align="center">
  <img src="docs/screenshots/ai-query.png" width="100%">
</p>

Ask database questions using natural language.

Examples:

```text
"Show monthly revenue"

"Who are our top customers?"

"Which products have the highest sales?"

"Compare revenue by category"
```

</td>

<td width="50%">

## 🗄️ PostgreSQL Analytics

<p align="center">
  <img src="docs/screenshots/query-results.png" width="100%">
</p>

Generated queries execute against a real PostgreSQL database and return structured results.

</td>

</tr>
</table>

---

# 🔄 How It Works

## The complete pipeline

```text
┌──────────────────────┐
│    Natural Language  │
│       Question       │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│     AI Provider      │
│   Query Generation   │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│    SQL Validator     │
│                      │
│ Security + Syntax    │
│ Validation + Limits  │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│      PostgreSQL      │
│                      │
│ Customers            │
│ Products             │
│ Orders               │
│ Payments             │
│ Events               │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│     Query Results    │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│ Analytics + AI       │
│ Explanation          │
└──────────────────────┘
```

---

# 🧠 Natural Language → SQL

Users don't need to know SQL to explore the database.

### Example

**User asks:**

```text
Which 10 customers generated the most revenue?
```

### AI generates a query similar to:

```sql
SELECT
    c.id,
    c.name,
    SUM(o.total_amount) AS total_revenue
FROM customers c
JOIN orders o
    ON o.customer_id = c.id
GROUP BY c.id, c.name
ORDER BY total_revenue DESC
LIMIT 10;
```

### Result

```text
Customer              Revenue
──────────────────────────────
Customer A            $42,500
Customer B            $38,210
Customer C            $34,890
...
```

The application can then explain the result in natural language.

---

# 🔐 SQL Security

AI-generated SQL should **never be trusted blindly**.

The application includes a validation layer between the AI and PostgreSQL.

```text
AI Generated SQL
       │
       ▼
┌──────────────────┐
│ SQL Validator    │
├──────────────────┤
│ Statement Check  │
│ Keyword Check    │
│ Query Limits     │
│ Read-only Rules  │
└────────┬─────────┘
         │
         ▼
     PostgreSQL
```

For normal analytics operations, destructive statements are rejected.

Examples include:

```text
DROP
DELETE
TRUNCATE
ALTER
CREATE
GRANT
REVOKE
INSERT
UPDATE
```

The objective is to keep the AI analytics layer **read-oriented and controlled**.

---

# 📊 Analytics Dashboard

<p align="center">
  <img src="docs/screenshots/dashboard.png" width="100%">
</p>

The dashboard provides a visual layer on top of database queries.

Potential visualizations include:

- Revenue trends
- Order volume
- Customer analysis
- Product performance
- Category performance
- Payment statistics
- Website events

---

# 🧮 SQL Engineering

This project is designed to demonstrate practical SQL and database engineering rather than simple CRUD operations.

### Query techniques

```text
JOIN
CTE
Subqueries
Window Functions
GROUP BY
Aggregations
ORDER BY
Filtering
Pagination
```

### Example analytical query

```sql
WITH customer_revenue AS (
    SELECT
        customer_id,
        SUM(total_amount) AS revenue
    FROM orders
    GROUP BY customer_id
)
SELECT
    customer_id,
    revenue,
    RANK() OVER (ORDER BY revenue DESC) AS revenue_rank
FROM customer_revenue;
```

---

# ⚡ Query Optimization

Database performance is treated as an engineering concern.

The project uses PostgreSQL query analysis tools such as:

```sql
EXPLAIN
```

and:

```sql
EXPLAIN ANALYZE
```

These can be used to inspect:

- Query execution plans
- Sequential scans
- Index usage
- Join strategies
- Estimated vs actual execution behavior

Indexes are added to frequently queried fields where appropriate.

---

# 🗄️ Database Architecture

The demonstration database contains business-oriented entities such as:

```text
┌──────────────┐
│  Customers   │
└──────┬───────┘
       │
       │
      
