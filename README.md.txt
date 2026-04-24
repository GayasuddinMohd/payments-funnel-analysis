# Product Funnel & Growth Analysis – Payments Use Case

## Problem Statement
Consumer fintech apps lose most users during onboarding before they ever transact.
This project simulates and analyzes a real payments funnel (Signup → KYC → First Transaction → Repeat)
to identify drop-off points, retention drivers, and high-value user segments.

---

## Tools & Tech
- **SQL (MySQL)** – Funnel queries, cohort analysis, segmentation
- **Python** – Data generation, analysis, visualization (pandas, matplotlib, seaborn)
- **Dataset** – 5,000 synthetic users | 10,164 events | 6,671 transactions

---

## Project Structure

payments-funnel-analysis/
├── data/
│   ├── users.csv
│   ├── events.csv
│   └── transactions.csv
├── generate_data.py
├── sql/
│   ├── 01_funnel_analysis.sql
│   ├── 02_cohort_retention.sql
│   └── 03_segmentation.sql
├── analysis.ipynb
└── README.md


---

## Key Findings

### 1. 35% Drop-off at KYC Completion
- 85.6% of users started KYC but only 64.8% completed it
- This single step is the biggest friction point in the entire funnel
- **Recommendation:** Simplify KYC steps, add progress indicators,
  send nudge notifications to users who started but didn't complete

### 2. Referral Channel Drives Highest Retention
- Referral users retained at **27.5%** vs Organic at **20.8%**
- That's a **32% lift** in retention over the weakest channel
- **Recommendation:** Prioritize referral incentive budget over paid ads
  which showed similar retention (22.4%) at higher CAC

### 3. Evening Hours (18–23) Are Peak Revenue Window
- Hours 18–23 contribute **~29% of total revenue**
- Clear behavioral pattern — users transact after work hours
- **Recommendation:** Schedule push notifications, offers, and
  re-engagement campaigns between 6PM–11PM

### 4. High Value Segment = 6x Revenue vs One-Time Users
- High Value users (544): avg ₹21,248 revenue, 6.2 txns
- One-Time users (728): avg ₹3,458 revenue, 1 txn
- **Recommendation:** Build loyalty program targeting Engaged users
  (399 users, 3.6 avg txns) to convert them to High Value

---

## How to Run

1. `python generate_data.py` — generates 3 CSV files in data/
2. Load CSVs into MySQL using the schema in `sql/01_funnel_analysis.sql`
3. Run SQL scripts in order (01 → 02 → 03)
4. Open `analysis.ipynb` and run all cells for visualizations