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
       ▼
┌──────────────┐
│    Orders    │
└──────┬───────┘
       │
       ▼
┌──────────────┐
│ Order Items  │
└──────┬───────┘
       │
       ▼
┌──────────────┐
│   Products   │
└──────────────┘


┌──────────────┐
│   Payments   │
└──────────────┘


┌──────────────┐
│Website Events│
└──────────────┘
```

The schema is designed around normalized relational data with appropriate:

- Primary keys
- Foreign keys
- Constraints
- Indexes
- Relationships

---

# 🔎 Schema Explorer

<p align="center">
  <img src="docs/screenshots/schema-explorer.png" width="100%">
</p>

The schema explorer allows users to understand the available database structure before asking analytical questions.

Users can inspect:

- Tables
- Columns
- Data types
- Relationships
- Available fields

This helps the AI query-generation layer work with the actual database schema.

---

# 📝 Query History

<p align="center">
  <img src="docs/screenshots/query-history.png" width="100%">
</p>

The application keeps track of previous database questions and their generated queries.

A query history record can contain:

```text
User Question
      +
Generated SQL
      +
Execution Result
      +
Execution Metadata
      +
Timestamp
```

This makes the system useful not only as an AI interface but also as a practical analytics workspace.

---

# 🏗️ System Architecture

```text
                         ┌───────────────┐
                         │     User      │
                         └───────┬───────┘
                                 │
                                 ▼
                     ┌─────────────────────┐
                     │   React Frontend    │
                     │ TypeScript + Vite   │
                     └──────────┬──────────┘
                                │
                                │ REST API
                                ▼
                     ┌─────────────────────┐
                     │   Django REST API   │
                     └──────────┬──────────┘
                                │
                 ┌──────────────┼──────────────┐
                 │              │              │
                 ▼              ▼              ▼
          ┌────────────┐ ┌────────────┐ ┌─────────────┐
          │ AI Service │ │ Query      │ │ Schema      │
          │            │ │ Validator  │ │ Explorer    │
          └─────┬──────┘ └─────┬──────┘ └─────────────┘
                │              │
                └───────┬──────┘
                        ▼
               ┌──────────────────┐
               │    PostgreSQL    │
               │                  │
               │ Customers        │
               │ Orders           │
               │ Products         │
               │ Payments         │
               │ Events           │
               └──────────────────┘
```

---

# 🧰 Technology Stack

| Layer | Technology |
|---|---|
| Backend | Python |
| Framework | Django |
| API | Django REST Framework |
| Database | PostgreSQL |
| Database Driver | psycopg |
| Validation | Pydantic |
| Frontend | React |
| Language | TypeScript |
| Build Tool | Vite |
| Styling | Tailwind CSS |
| AI | OpenAI-compatible provider abstraction |
| Containers | Docker |
| Testing | Pytest / Django testing |
| CI/CD | GitHub Actions |

---

# 🔌 AI Provider Architecture

The AI layer is designed around a provider abstraction rather than tightly coupling the application to a single model provider.

```text
                 AI Service
                     │
                     ▼
            ┌─────────────────┐
            │ Provider Layer  │
            └────────┬────────┘
                     │
          ┌──────────┴──────────┐
          │                     │
          ▼                     ▼
 OpenAI-Compatible        Mock / Demo
    Provider                Provider
```

This makes it possible to change or extend AI providers without redesigning the application.

---

# 🛡️ Safe Database Access

The analytics workflow follows a controlled pattern:

```text
Natural Language
      ↓
AI
      ↓
SQL
      ↓
Validation
      ↓
Read-only Analytics Rules
      ↓
Query Limits
      ↓
PostgreSQL
      ↓
Results
```

The application does **not** simply send unrestricted AI-generated SQL directly to the database.

---

# 🔑 Environment Configuration

Sensitive credentials should be supplied through environment variables.

Example:

```env
DATABASE_URL=postgresql://user:password@localhost:5432/database
AI_API_KEY=your_api_key
AI_MODEL=your_model
DJANGO_SECRET_KEY=your_secret_key
```

Never commit real credentials or API keys to GitHub.

A demo/mock mode can be used without requiring a production AI API key.

---

# 🐳 Docker

The project can be run through Docker for a reproducible development environment.

Typical services:

```text
┌────────────────────┐
│ Frontend Container │
└─────────┬──────────┘
          │
┌─────────▼──────────┐
│ Django API         │
└─────────┬──────────┘
          │
┌─────────▼──────────┐
│ PostgreSQL         │
└────────────────────┘
```

---

# 🧪 Testing

The project includes testing around important application components.

Areas include:

```text
API Endpoints
Authentication
Database Operations
SQL Validation
AI Service
Query Execution
Schema Access
Error Handling
```

Example workflow:

```text
User Question
      ↓
AI Service
      ↓
Generated SQL
      ↓
Validator
      ↓
Database
      ↓
Expected Result
```

---

# 📈 Example Analytics Questions

The application can be designed to answer questions such as:

```text
"What were our monthly sales?"

"Which products generate the most revenue?"

"Who are our top customers?"

"What is the average order value?"

"Which category has the highest revenue?"

"How many orders were placed this month?"

"Show revenue growth over time."

"Which customers have never placed an order?"
```

The goal is to make database analytics accessible through natural language while keeping SQL visible and inspectable.

---

# 📂 Project Structure

```text
ai-database-assistant/
│
├── backend/
│   ├── config/
│   ├── apps/
│   │   ├── accounts/
│   │   ├── database/
│   │   ├── queries/
│   │   ├── analytics/
│   │   └── ai/
│   │
│   ├── manage.py
│   └── requirements.txt
│
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── services/
│   │   └── types/
│   │
│   ├── package.json
│   └── vite.config.ts
│
├── database/
│   ├── schema.sql
│   └── seed/
│
├── docs/
│   └── screenshots/
│
├── tests/
│
├── docker-compose.yml
├── .env.example
├── README.md
└── .github/
    └── workflows/
```

> Adjust the structure to match the actual Antigravity-generated repository if your implementation differs.

---

# 🚀 Getting Started

## Requirements

```text
Python 3.12+
Node.js
PostgreSQL
Git
Docker (optional)
```

---

## 1. Clone

```bash
git clone <your-repository-url>
cd ai-database-assistant
```

---

## 2. Configure Environment

Copy the example environment file:

```bash
cp .env.example .env
```

Configure the required database and AI settings.

---

## 3. Start PostgreSQL

If using Docker:

```bash
docker compose up -d
```

---

## 4. Start Backend

```bash
cd backend

python -m venv .venv
```

Activate the environment:

### Windows

```bash
.venv\Scripts\activate
```

### Linux / macOS

```bash
source .venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Run migrations:

```bash
python manage.py migrate
```

Start Django:

```bash
python manage.py runserver
```

---

## 5. Start Frontend

```bash
cd frontend
npm install
npm run dev
```

---

# 📸 Screenshots

Store project screenshots in:

```text
docs/screenshots/
```

Recommended screenshots:

```text
docs/screenshots/
├── hero.png
├── ai-query.png
├── query-results.png
├── dashboard.png
├── schema-explorer.png
├── query-history.png
├── sql-viewer.png
├── login.png
└── responsive.png
```

The README should prioritize screenshots of the **actual running application** rather than placeholder graphics.

---

# 📊 Engineering Highlights

## AI Engineering

- Natural language database interaction
- AI-generated SQL
- Provider abstraction
- Prompt-based schema-aware query generation
- AI result explanation
- Mock/demo AI mode

## Database Engineering

- PostgreSQL
- Relational schema design
- Normalization
- Foreign keys
- Constraints
- Indexing
- CTEs
- Window functions
- Query optimization
- `EXPLAIN ANALYZE`

## Backend Engineering

- Django
- Django REST Framework
- API design
- Authentication
- Query execution
- Validation
- Error handling
- Query history

## Frontend Engineering

- React
- TypeScript
- Vite
- Tailwind CSS
- Interactive analytics
- Tables
- Charts
- Schema explorer

## DevOps

- Docker
- Environment configuration
- GitHub Actions
- Automated testing
- Reproducible development environment

---

# 🔮 Future Roadmap

### Phase 1 — Core Platform

- [x] PostgreSQL integration
- [x] Natural language query workflow
- [x] SQL validation
- [x] Query execution
- [x] Query history
- [x] Schema exploration

### Phase 2 — Analytics

- [ ] Advanced dashboard widgets
- [ ] Saved reports
- [ ] Export to CSV
- [ ] Scheduled reports
- [ ] Custom chart builder

### Phase 3 — AI

- [ ] Multi-model support
- [ ] Improved SQL generation
- [ ] Query correction
- [ ] Follow-up questions
- [ ] Conversational analytics
- [ ] Automatic insight detection

### Phase 4 — Production

- [ ] Role-based access control
- [ ] Audit logging
- [ ] Advanced observability
- [ ] Query cost monitoring
- [ ] Rate limiting
- [ ] Production deployment

---

# 🎯 Why This Project?

AI can generate SQL, but a useful production-oriented system requires much more than sending a prompt to an LLM.

This project explores the engineering layers required to build a safer and more practical AI database interface:

```text
       AI
       │
       ▼
   SQL Generation
       │
       ▼
    Validation
       │
       ▼
  Database Access
       │
       ▼
 Query Optimization
       │
       ▼
 Analytics
       │
       ▼
 User-Friendly Insights
```

It combines:

**AI Engineering + Backend Engineering + Database Engineering + Full-Stack Development**

---

# 📚 Skills Demonstrated

```text
Python
Django
Django REST Framework
PostgreSQL
SQL
Database Design
Query Optimization
AI / LLM Integration
Natural Language → SQL
React
TypeScript
REST APIs
Authentication
Docker
Testing
GitHub Actions
```

---

# 🤝 Contributing

Contributions, ideas, and improvements are welcome.

Typical workflow:

```bash
git clone <repository-url>
git checkout -b feature/your-feature
```

Make your changes, test them, and submit a pull request.

---

# 📄 License

Add the license appropriate for your project.

If this is a portfolio or proprietary project, choose the license according to how you intend others to use the code.

---

# 👩‍💻 Author

**Maryam Abdul Karim**

AI Engineer | Machine Learning | AI Agents | RAG | Python | Django

Building intelligent systems that combine:

**AI + Data + Software Engineering + Real-World Applications**

---

<p align="center">
  <strong>⭐ If you find this project interesting, consider giving the repository a star.</strong>
</p>

<p align="center">
  Built with Python, Django, PostgreSQL, React & AI
</p>
