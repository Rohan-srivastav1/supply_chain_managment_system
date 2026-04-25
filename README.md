<div align="center">

<!-- Banner -->
<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0f2027,50:203a43,100:2c5364&height=200&section=header&text=Supply%20Chain%20Management%20System&fontSize=36&fontColor=ffffff&fontAlignY=38&desc=SQL%20%26%20Python%20End-to-End%20Analysis&descAlignY=58&descColor=7ecbff&animation=fadeIn" width="100%"/>

<br/>

![SQL](https://img.shields.io/badge/SQL-MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-11557C?style=for-the-badge&logo=python&logoColor=white)

<br/>

> **A production-grade relational database system tracking the full product lifecycle —**  
> *from suppliers and inventory to customer orders and revenue insights.*

<br/>

</div>

---

## 📖 Overview

This repository presents a **comprehensive, end-to-end data analysis project** built around a Supply Chain Management System. It covers every phase of a real-world data engineering workflow — from schema design and relational database implementation to advanced SQL querying and rich Python visualizations.

The core objective was to design a **robust, normalized relational database** capable of tracking product lifecycles across suppliers, inventory, customer orders, and sales — and then extract meaningful business intelligence from it.

---

## 🗂️ Project Structure

```
Supply-Chain-Management/
│
├── 📄 supplychainsolution.sql       # Full DB schema + data population script
├── 📓 sql-pythonproject.ipynb       # Python analysis & visualization notebook
├── 📋 Practice_Questions.md         # 25+ business-driven SQL challenges
└── 📘 README.md                     # You are here
```

The workflow is broken into logical, production-aligned phases:

| Phase | Description |
|-------|-------------|
| **1. Database Design** | ER logic, schema documentation, entity relationships |
| **2. SQL Implementation** | Table creation, primary/foreign keys, indexing |
| **3. Practice Challenges** | 25+ SQL questions from beginner to expert level |
| **4. Python Integration** | MySQL connection, Pandas extraction, Matplotlib/Seaborn charts |

---

## 🏗️ Database Schema

The system is built on **5 core relational tables**, carefully normalized:

```
┌──────────────┐       ┌──────────────┐       ┌──────────────────┐
│   Customer   │──────>│    Orders    │──────>│    OrderItem     │
│──────────────│  1:N  │──────────────│  1:N  │──────────────────│
│ CustomerID   │       │ OrderID      │       │ OrderItemID      │
│ CustomerName │       │ CustomerID   │       │ OrderID          │
│ Email        │       │ OrderDate    │       │ ProductID        │
│ City         │       │ Status       │       │ Quantity         │
│ Segment      │       │ TotalAmount  │       │ UnitPrice        │
└──────────────┘       └──────────────┘       └──────────────────┘
                                                       │
                              ┌──────────────┐         │
                              │   Supplier   │         │
                              │──────────────│         ▼
                              │ SupplierID   │  ┌──────────────┐
                              │ SupplierName │  │   Product    │
                              │ Country      │  │──────────────│
                              │ ContactEmail │  │ ProductID    │
                              └──────┬───────┘  │ ProductName  │
                                     └─────────>│ SupplierID   │
                                                │ Category     │
                                                │ StockQty     │
                                                └──────────────┘
```

---

## ✨ Key Features

### 🔗 Relational Mapping
Structured data across 5 interconnected core tables with enforced foreign key constraints and referential integrity.

### 🧠 Advanced SQL Techniques
- **Complex Joins** — multi-table joins for cross-domain analysis  
- **Window Functions** — `RANK()`, `ROW_NUMBER()`, `LAG()`, `LEAD()` for trend analysis  
- **CTEs** — Common Table Expressions for readable, modular query design  
- **Subqueries** — correlated and non-correlated for filtering and aggregation  

### 📊 Data Visualizations
| Visual | Description |
|--------|-------------|
| 📈 Revenue Trends | Year-over-year financial performance tracking |
| 👥 Customer Insights | Demographic analysis and loyalty segmentation |
| 🏷️ Market Research | High-demand products and category landscapes |
| 📦 Inventory Health | Active vs. discontinued product breakdowns |

### ⚡ Performance Optimization
Strategic indexing on high-frequency query columns:
```sql
CREATE INDEX idx_customer_name ON Customer(CustomerName);
CREATE INDEX idx_order_date    ON Orders(OrderDate);
```

---

## 🛠️ Technologies Used

| Technology | Purpose |
|------------|---------|
| **MySQL** | Database engine, schema design, complex queries |
| **Python 3.x** | Data pipeline and analysis scripting |
| **Pandas** | DataFrame manipulation and data wrangling |
| **NumPy** | Numerical computations |
| **Matplotlib** | Core plotting and chart generation |
| **Seaborn** | Statistical visualizations with aesthetic polish |
| **Jupyter Notebook** | Interactive, documented analysis environment |

---

## 🚀 Getting Started

### Prerequisites

```bash
pip install mysql-connector-python pandas numpy matplotlib seaborn jupyter
```

### Step 1 — Database Setup

1. Open **MySQL Workbench** (or any MySQL client)
2. Run the full script to initialize the database:

```sql
SOURCE supplychainsolution.sql;
```

This will create the `Supply_chain` database, define all tables, insert sample data, and build indexes.

### Step 2 — Explore the SQL Challenges

Open `Practice_Questions.md` to browse **25+ business-scenario queries** across four difficulty levels:

- 🟢 **Basic** — SELECT, WHERE, ORDER BY, GROUP BY  
- 🟡 **Intermediate** — JOINs, aggregations, HAVING  
- 🟠 **Advanced** — Subqueries, CTEs, date functions  
- 🔴 **Expert** — Window functions, ranking, analytical queries  

### Step 3 — Python Visualizations

1. Update database credentials in the notebook:

```python
conn = mysql.connector.connect(
    host="localhost",
    user="your_username",      # 👈 update this
    password="your_password",  # 👈 update this
    database="Supply_chain"
)
```

2. Launch Jupyter and run all cells:

```bash
jupyter notebook sql-pythonproject.ipynb
```

---

## 💡 Key Business Insights

> The analysis surfaced several actionable findings from the supply chain data:

- **📈 Revenue Growth** — Identified peak performance periods and seasonal revenue patterns through year-over-year trend analysis
- **📦 Inventory Health** — Flagged active vs. discontinued products to streamline supply chain decisions
- **🥇 Customer Loyalty** — Ranked customers by order frequency and total spend to isolate high-value segments
- **💰 Savings Analysis** — Measured the gap between unit cost and selling price to quantify discount impacts on profitability

---

## 📬 Contributing

Contributions are welcome! If you'd like to add more SQL challenges, improve visualizations, or extend the schema:

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature`
3. Commit your changes: `git commit -m 'Add: your feature description'`
4. Push and open a Pull Request

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:2c5364,50:203a43,100:0f2027&height=100&section=footer" width="100%"/>

**Built with 🔍 curiosity, 🛠️ SQL, and 🐍 Python**

*If this project helped you, consider leaving a ⭐ on the repository!*
