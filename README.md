# fintech-dashboard
End-to-end FinTech transactions analysis · Python EDA · Power BI · Tableau · AI-assisted


# 🏦 Credit Card Fraud Detection Dashboard

> End-to-end data analysis and machine learning project on financial transaction fraud detection.  
> **Tools:** Python · Power BI · XGBoost · Random Forest · SMOTE · GitHub

---

## 📌 Project Overview

This project simulates the work of a junior Data Analyst at a bank. Starting from a raw dataset of 100,000 transactions, I performed a full EDA, built ML models to detect fraud, and designed an interactive BI dashboard to communicate findings to business stakeholders.

**Business question:**
> *"How can a bank identify fraudulent transactions and prioritize security investments?"*

---

## 📊 Dataset

| Property | Value |
|---|---|
| Source | Synthetic credit card transactions dataset |
| Rows | 100,000 transactions |
| Features | 7 columns (Amount, TransactionType, Location, IsFraud, TransactionDate...) |
| Class balance | 99% Normal · 1% Fraud (1,000 fraud cases) |

---

## 🔍 Key Insights

- **⏰ Time pattern:** Fraud peaks at **1AM, 8AM and 6PM** — hours with reduced bank staff monitoring, suggesting fraudsters exploit low-surveillance windows
- **🏙️ Geography:** **New York and San Diego** recorded the highest fraud counts, though the difference across cities was not statistically significant
- **💰 Amount:** No meaningful difference in transaction amounts between fraud and normal cases — fraudsters blend in with average spending behavior (~$2,497 average)
- **⚠️ Dataset limitation:** Features showed weak discriminative power, confirming that real-world fraud detection requires richer data (device ID, IP address, customer history)

---

## 🤖 ML Models

### Approach
The dataset had a severe class imbalance (99/1%). Two strategies were tested:

| Strategy | Model | Recall (Fraud) | F1 (Fraud) |
|---|---|---|---|
| SMOTE + Default threshold | Random Forest | 0.00 | 0.00 |
| SMOTE + Threshold 0.02 | Random Forest | 0.23 | 0.02 |
| scale_pos_weight=99 | **XGBoost** | **0.10** | **0.02** |

### Key learnings
- **Overfitting risk:** A model predicting always "Normal" achieves 99% accuracy but detects 0 frauds
- **Better metric:** F1-Score and Recall are more relevant than Accuracy for imbalanced datasets
- **Feature Engineering:** Created `Hour` and `Day` features from `TransactionDate` to capture temporal patterns

---

## 📈 Dashboard

**Power BI — Credit Card Fraud Detection Dashboard**

![Dashboard Preview](docs/dashboard_preview.png)

**KPIs:**
- 100K Total Transactions
- 250M Total Amount
- 1K Total Frauds
- 1.0% Fraud Rate

---

## 🛠️ Tools Used

| Category | Tools |
|---|---|
| Language | Python 3 |
| Data Analysis | Pandas, NumPy |
| Visualization | Matplotlib, Seaborn |
| Machine Learning | Scikit-learn, XGBoost, Imbalanced-learn |
| BI Dashboard | Power BI Desktop |
| AI Assistance | Claude AI, GitHub Copilot (data cleaning automation) |
| Version Control | Git, GitHub |

---

## 🚀 How to Run

```bash
# 1. Clone the repository
git clone https://github.com/FernandDevCode/sales-dashboard.git
cd sales-dashboard

# 2. Install dependencies
pip install -r requirements.txt

# 3. Run the notebook
jupyter notebook notebooks/01_exploration.ipynb
```
pip install pandas numpy matplotlib seaborn scikit-learn xgboost imbalanced-learn

# 3. Run the notebook
jupyter notebook notebooks/01_exploration.ipynb
```

---

# 📁 Project Structure

```
fintech-dashboard/
│
├── data/
│   └── fraud_clean.csv          # Cleaned dataset with engineered features
│
├── notebooks/
│   └── 01_exploration.ipynb     # Full EDA + ML models
│
├── dashboards/
│   └── fraud_dashboard.pbix     # Power BI dashboard file
│
├── docs/
│   └── dashboard_preview.png    # Dashboard screenshot
│
└── README.md


# 👤 Author

# Fernand Kissira SOHOU 

# Computer Science & Telecommunications Student  




*This project was built as part of a personal portfolio to demonstrate data analysis, machine learning, and BI skills*