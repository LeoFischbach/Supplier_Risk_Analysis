# Supplier Risk Scoring – Procurement Analytics Project

This project implements a structured **Supplier Risk Scoring Model (0–100)** based on procurement and supplier master data.

The objective is to transform raw ERP-style data into a transparent, scalable, and automation-ready risk assessment framework that supports strategic sourcing decisions.

---

## 🎯 Objective

Design and implement a composite **Supplier Risk Score** that:

- Creates transparency across the supplier base  
- Quantifies structural sourcing risks  
- Supports data-driven procurement decisions  
- Demonstrates automation potential in procurement analytics  

---

## 📊 Data

The analysis is based on structured procurement-related datasets:

- `suppliers.csv`
- `orders.csv`
- `articles.csv`
- `addresses.csv`
- `indices.csv`

### Data Preparation

Key preprocessing steps:

- ID harmonization and cleaning  
- Duplicate detection (1 supplier = 1 row principle)  
- Aggregation of order values  
- Calculation of supplier share per article  
- Validation checks (e.g. ∑ supplier share per article = 1)  
- Plausibility checks of financial metrics (sum of order volumes match across dataframes)

The final result is a structured **Supplier Master Table** used for risk modeling.

---

## 🧠 Risk Model

The Supplier Risk Score (0–100) is composed of four dimensions:

| Dimension           | Methodology |
|--------------------|------------|
| **Geopolitical Risk** | (HMI + Environmental Index) / 2 |  
| **Dependency Risk** | Based on share of total order volume and number of supplied articles |
| **Supplier Size Risk** | Log-scaled revenue (large suppliers = lower risk) |
| **Compliance Risk** | Certificate availability (binary scoring) |

Each dimension is normalized to a 0–100 scale and aggregated into a composite risk score.

### Score Characteristics

- **Minimum Score:** 23  
- **Maximum Score:** 65  
- **Average Score:** 41  

Main risk drivers:
- Supplier size dispersion  
- Compliance availability  

No single-source dependency risk detected (≥11 suppliers per article).

---

## 📈 Key Insights

- Risk exposure is structurally diversified across suppliers.
- Compliance differences significantly impact overall risk dispersion.
- Supplier size introduces measurable structural variance.
- The framework enables prioritization of suppliers for further review.

---

## 🛠 Tech Stack

- Python  
- Pandas  
- NumPy  
- Structured data validation logic  
- Log-scaling & normalization techniques  

---

## ⚙️ Scalability & Future Improvements

Current limitations:

- Static snapshot (no time-series component)
- No integration of price developments
- Binary compliance dimension
- No operational performance KPIs included

Potential extensions:

- Time-series risk tracking  
- Automated data ingestion pipeline  
- Configurable weighting & thresholds  
- Integration of external risk data sources  
- Advanced compliance scoring  
- Simulation of risk scenarios  

---

## 🏗 Conceptual Architecture
1. Raw ERP data
2. Data Cleaning & Validation
3. Supplier Master Table
4. Risk Dimension Engineering
5. Composite Risk Score (0-100)
6. Decision Support
