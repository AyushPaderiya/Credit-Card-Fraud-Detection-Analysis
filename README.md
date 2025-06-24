
## 📌 Overview  
This project analyzes **1.3 million credit card transactions** to detect potential fraud using behavioral patterns and rule-based flagging. It combines **data cleaning, feature engineering, and interactive dashboards** to identify high-risk transactions based on:  
- **Unusual spending amounts** (vs. user history)  
- **Odd-hour transactions** (midnight–5 AM)  
- **Rapid sequential purchases** (<60 seconds apart)  

**Output**: A Power BI dashboard highlighting flagged transactions for further investigation.  

---

## 🛠️ Features  
### **1. Data Processing**  
- Cleaned raw transaction data (removed duplicates, irrelevant columns).  
- Engineered features:  
  - Time-based (`hour`, `weekday`, `time_since_last_transaction`).  
  - User-level spending metrics (`mean`, `std_dev`).  
- Generated 3 risk flags:  
  ```python
  df["high_value_flag"] = (df["amt"] > (df["user_mean"] + 2 * df["user_std"]))  
  df["odd_hour_flag"] = (df["hour"].between(0, 5))  
  df["rapid_txn_flag"] = (df["time_diff"] < 60)  
  ```

### **2. Dashboard Insights**  
- **Temporal Trends**: Fraud spikes in Q1 2020.  
- **High-Risk Categories**: `entertainment` and `food_dining`.  
- **Geographic Hotspots**: States like AK and AL.  
- **User Behavior**: 21.7% of transactions flagged as suspicious.  

### **3. Outputs**  
- `Credit Card Transactions Fraud Detection Dataset(Cleaned).csv`: Processed dataset with risk flags.  
- `Flagged_Transactions.xlsx`: High-risk subset for audit.  
- **Power BI Dashboard**: Interactive visualizations.  

---

## 📂 Files  
| File | Description |  
|------|-------------|  
| `fraudTrain.csv` | Raw transaction data |  
| `Credit Card Transactions Fraud Detection Dataset.ipynb` | Python notebook for analysis |  
| `Credit Card Transactions Fraud Detection Dataset(Cleaned).csv` | Processed data with risk flags |  
| `Flagged_Transactions.xlsx` | High-risk transactions |  
| `Transaction Fraud Dashboard.pbix` | Power BI dashboard file |  

---

## 🔍 Key Findings  
1. **281K flagged transactions** (21.7% of total).  
2. **27K high-value outliers** (>2σ from user mean).  
3. **4K rapid transactions** (potential card testing).  
4. Odd-hour fraud peaks at **3 AM**.  

---

## 🚀 How to Use  
1. **Run the Jupyter Notebook**:  
   ```bash
   jupyter notebook "Credit Card Transactions Fraud Detection Dataset.ipynb"
   ```  
2. **Explore the Dashboard**:  
   - Open `Transaction Fraud Dashboard.pbix` in Power BI.  
   - Filter by date, category, or state.  

---

## 🤝 Contribution  
Suggestions welcome! Open an issue or PR for:  
- Adding ML models (e.g., isolation forests).  
- Enhancing real-time monitoring.  

---
**🔗 Tags**: #FraudDetection #DataAnalysis #PowerBI #Python
