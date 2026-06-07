# AtliQ Grands — Hospitality Revenue Optimization and Market Share Analysis

---

## Business Problem

AtliQ Grands is a luxury hotel chain operating across 4 cities in India — Mumbai, Delhi, Hyderabad, and Bangalore. The company is losing market share and revenue due to increasing competition and poor management decisions.

**Management has no visibility into:**
- Why revenue is not growing despite stable bookings
- Which cities and properties are underperforming
- What is driving revenue leakage

They hired a Data Analyst to analyze 3 months of historical booking data and identify root causes with actionable recommendations.

---

## Dashboard Preview

### 📊 Page 1 — Business Overview
![Dashboard Page 1](./Dashboard%20Page1.jpeg)

### 📊 Page 2 — Issues & Root Cause
![Dashboard Page 2](./Dashboard%20Page2.jpeg)


## Dataset Overview

| Table | Description | Rows |
|---|---|---|
| `dim_hotels` | Property master data — name, city, category | 25 |
| `dim_rooms` | Room classification (Standard, Elite, Premium, Presidential) | 4 |
| `dim_date` | Calendar table — date, week, day type | 92 |
| `fact_booking` | Transaction-level booking records | 1,34,590 |
| `fact_aggregated_bookings` | Daily room-level capacity & bookings | 9,200 |

**Period:** May 2022 – July 2022 (92 days)

---

## Approach

```
Raw Data → Data Understanding → Data Cleaning → SQL Analysis → Python Visualisation → Business Recommendations → Power BI Dashboard (In Progress)
```

**5 data quality issues identified and resolved during cleaning:**
- `property_id` converted from int64 to object (identifier, not numeric)
- Date columns converted to datetime64 across 3 tables
- `day_type` corrected to hospitality standard (Fri + Sat = Weekend)
- `ratings_given` nulls retained as-is — 57.88% missing, imputation would corrupt analysis

---

## Key Performance Indicators

| Metric | Value |
|---|---|
| Revenue Generated (Expected) | ₹200.75 Cr |
| Revenue Realized (Actual) | ₹170.87 Cr |
| Realization Rate | 85.1% |
| Overall Occupancy | 57.9% |
| RevPAR | ₹7,347 |
| Average Daily Rate (ADR) | ₹14,925 |
| Total Bookings | 1,34,590 |

---

## Analysis Performed (Python + SQL)

1. City-wise revenue performance and per-property efficiency
2. RevPAR by property — identifying strongest and weakest performers
3. Room class analysis — booking share vs ADR
4. Occupancy by hotel category (Luxury vs Business)
5. Booking platform contribution and realisation rate
6. Revenue leakage analysis — identifying source and size
7. Cancellation rate breakdown — by city, platform, property, category
8. Weekday vs Weekend ADR and booking behaviour
9. Monthly and weekly revenue trend analysis

---

## Key Findings

### 1. Revenue Leakage — ₹2,988 Lakhs Lost to Cancellations
- Overall revenue leakage is **14.9%** of expected revenue
- **100% of leakage is caused by cancellations** — Checked Out and No Show bookings show zero leakage
- Cancelled bookings recover only **40% of expected revenue** through penalties
- Cancellation rate is **~24–25% across every city and every platform** — this is a system-wide policy problem, not location-specific

### 2. No Dynamic Pricing Strategy
- Weekday ADR: ₹12,683 | Weekend ADR: ₹12,725 — **nearly identical**
- AtliQ is charging the same rate on Saturday as Tuesday
- Weekend demand already exists — not being monetised

### 3. Delhi and Hyderabad Are Structurally Underperforming
- Mumbai: ₹835.75 Lakhs per property
- Delhi: ₹589L (-29.5% vs Mumbai)
- Hyderabad: ₹542L (-35.1% vs Mumbai)
- Gap is too large for random variation — these cities need separate revenue strategies

### 4. Presidential Room Pricing/Demand Mismatch
- Presidential ADR: ₹27,465 — highest among all room classes
- Presidential booking share: **12% — lowest among all room classes**
- Elite rooms (ADR ₹13,316) dominate at 36.7% share — customers are choosing mid-range over premium

### 5. Occupancy at 57.9% — 42% of Rooms Empty Every Night
- Both Luxury and Business categories show similar occupancy (~58%)
- Not a category-specific issue — company-wide structural problem

---

## Business Recommendations

| Priority | Recommendation |
|---|---|
| 🔴 High | Introduce tiered cancellation policy — full refund 7+ days, 50% at 3–7 days, no refund within 3 days |
| 🔴 High | Implement dynamic pricing — 10–15% premium on Fri/Sat, corporate discounts on weekdays |
| 🟡 Medium | City-specific strategies — corporate packages for Delhi, extended-stay packages for Hyderabad |
| 🟡 Medium | Review Presidential room value proposition — reduce price or add service to justify premium |

---

## Project Structure

```
├── Hospitality Project.ipynb     # Main analysis notebook (Python + SQL)
├── AtliQ Grands — Revenue Performance & Market Share Analysis.pdf  # Report
├── DATA/
│   ├── dim_hotels.csv
│   ├── dim_rooms.csv
│   ├── dim_date.csv
│   ├── fact_bookings.csv
│   └── fact_aggregated_bookings.csv
└── README.md
```

---

## Tools & Skills

- **Python** — Pandas, NumPy, Matplotlib, Seaborn
- **SQL** — SQLite via sqlite3, CTEs, JOINs, Window Functions, Aggregations, CASE statements
- **Analysis** — EDA, Revenue Analysis, Cancellation Analysis, Trend Analysis, RevPAR / ADR / Occupancy metrics
- **Power BI** — Dashboard in progress (Executive Overview, Revenue Leakage, Weekly/Monthly Trends)

---

## Author

**Sarvesh Gaikwad**
[LinkedIn](https://linkedin.com/in/sarveshgaikwad082) | [GitHub](https://github.com/SarveshGaikwad082)
