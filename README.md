# 🚚 Supply Chain Delivery Performance Analysis & Predictive Modeling

An end-to-end Python-based supply chain analytics project covering EDA, bottleneck detection, root cause analysis, time-based delay pattern analysis, and a machine learning model to predict late deliveries — built on 172,765 orders from a global e-commerce operation.

---

## 📌 Short Description

This project analyzes the delivery operations of a global e-commerce company managing order fulfillment across multiple regions and product categories. The analysis identifies root causes of chronic late deliveries, quantifies their financial impact at $2.1M in profit at risk, and deploys a Random Forest classifier achieving 74% accuracy to flag high-risk orders before shipment. Intended for supply chain analysts, operations managers, and data scientists seeking a data-driven framework for fulfillment improvement.

---

## 🛠️ Tech Stack

The project was built using the following tools and technologies:

- 🐍 **Python** – Core programming language for all analysis and modeling
- 📊 **Pandas** – Data loading, cleaning, feature engineering, and aggregation
- 📈 **Matplotlib & Seaborn** – Data visualization across EDA, bottleneck detection, and time-based analysis
- 🔢 **NumPy** – Numerical computation and array operations
- 🤖 **Scikit-learn** – Machine learning pipeline: train/test split, Random Forest classifier, classification metrics
- ⚖️ **imbalanced-learn (SMOTE)** – Oversampling to handle class imbalance in the target variable
- 📓 **Jupyter Notebook** – Interactive development and report-style narrative presentation
- 📁 **File Format** – `.ipynb` for the analysis notebook and `.csv` for the dataset

---

## 📂 Data Source

**Source:** DataCo Global Supply Chain Dataset

The dataset covers **172,765 orders** spanning January 2015 through January 2018 across a global e-commerce platform selling sporting goods, fitness equipment, outdoor gear, footwear, and apparel. Key fields include order dates, shipping dates, scheduled delivery windows, customer segments, shipping modes, order regions, department names, payment types, and order-level profit figures.

---

## ✨ Features / Highlights

### 🔴 Business Problem
A global e-commerce company faces chronic late deliveries where actual shipping times consistently deviate from scheduled windows. Key questions driving the analysis:
- What percentage of orders are being delivered late and what is the financial cost?
- Which shipping modes, regions, and departments are the primary bottlenecks?
- Are delays systemic or localized to specific geographies or customer segments?
- Can a predictive model flag high-risk orders before they ship to enable proactive intervention?

### 🎯 Goal of the Project
To deliver a comprehensive analytical and predictive framework that:
- Establishes a performance baseline through KPI computation
- Identifies operational bottlenecks across six dimensions using delay rate analysis
- Pinpoints root causes in the highest-delay region through driver decomposition
- Reveals temporal patterns to support seasonal capacity planning
- Deploys a machine learning model to predict late delivery risk at order level

### 🖥️ Walkthrough of Key Analysis Sections

**Business KPIs (Baseline)**
- Total Orders: **172,765**
- Late Deliveries: **94,523 (54.71%)**
- On-Time Delivery Rate: **45.29%**
- Total Profit (profitable orders): **$7.5M**
- Profit at Risk (delayed orders): **$2.1M**
- 90th Percentile Delay: **3 days**
- Average Order Profit: **$22.03**

**Profitability Analysis**
Order-level profitability classified into Profit (80.7%), Loss (18.7%), and Break-even (0.6%). Mean profit per order remains stable at $20–$23 regardless of delay length — confirming that the $2.1M profit at risk is driven by volume of delayed orders, not individual order economics.

**Bottleneck Detection**
Delay percentage computed across six operational dimensions — Region, Customer Segment, Shipping Mode, Order Status, Payment Type, and Department. Key finding: Shipping Mode is the dominant lever, with First Class at 100% delay rate and Second Class at 79.8%, while Same Day achieves 0%.

**Root Cause Analysis**
Deep-dive into Central Africa (highest-delay region at 58.7%) — top 10 driver factors ranked by delay percentage, with Shipping Mode: First Class (100%) and Shipping Mode: Second Class (82.8%) as the top two drivers, followed by Order Status: PAYMENT_REVIEW (80%).

**Time-Based Delay Patterns**
Delay rates analyzed across month, day of week, and hour of day. Peak delay months: August & September (55.4%) and December (55.2%). Late-evening orders (Hour 21) show the highest intra-day delay rate at 57.1%, likely reflecting processing cutoff windows.

**Machine Learning — Random Forest Classifier**
- Features: Shipping Mode, Scheduled Days, Category, Segment, Department, Region, Payment Type, Order Month, Order Hour (frequency encoded)
- Class imbalance handled via SMOTE oversampling
- **74% overall accuracy** | Precision on late orders: **0.78** | Recall on late orders: **0.75**
- Model is deployable as an order-level late-delivery alert system at point of confirmation

### 💡 Business Impact & Insights
- **Shipping Mode is the #1 fix:** First Class at 100% delay is operating in complete contradiction to its brand promise — an immediate carrier SLA audit is warranted
- **The problem is systemic, not regional:** All regions cluster between 55–59% delay rate, ruling out a localized logistics failure
- **No customer segment receives preferential delivery:** Consumer, Corporate, and Home Office all experience the same broken delivery promise
- **Seasonal surges are plannable:** July is a consistent low-point (~53.75%) while August–September and December spike — capacity can be pre-positioned
- **Predictive model is production-ready:** 78% precision on late orders means the alert system can trigger interventions without excessive false alarms

---

## 🚀 How to Use

1. Clone or download this repository
2. Install dependencies: `pip install pandas numpy matplotlib seaborn scikit-learn imbalanced-learn`
3. Place `DataCoSupplyChainDataset.csv` in the same directory as the notebook
4. Open `Supply_Chain_Analysis.ipynb` in Jupyter Notebook or JupyterLab
5. Run all cells sequentially — the notebook is structured in order: EDA → KPIs → Profitability → Bottlenecks → Root Cause → Time Analysis → ML Model
