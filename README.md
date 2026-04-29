# 🏦 Banking Transactions & Fraud Detection Database

## 📌 Objective
The objective of this project is to design a normalized, production-ready relational database for a fictional bank. It simulates real-world banking operations, tracks customer accounts, logs transactions, and utilizes advanced SQL logic to automatically detect and flag fraudulent activity.

## 🛠️ Tools Used
* **Database Management System:** MySQL 8.0
* **Concepts Applied:** 3NF Normalization, Foreign Key Constraints, Window Functions, Views, Stored Triggers, Data Profiling.

## 🗄️ Database Schema
The database is built using a 3rd Normal Form (3NF) architecture to ensure data integrity and eliminate redundancy. 
* **`customers`**: Stores KYC-verified client details.
* **`accounts`**: Tracks savings, current, and salary accounts linked to branches.
* **`branches`**: Bank location and routing data.
* **`merchants`**: Categorized business entities where money is spent.
* **`transactions`**: The central fact table recording all financial movements (pos, upi, net banking, atm).
* **`risk_events`**: A security log that stores automatically flagged suspicious transactions.
  
## 🕵️‍♂️ Fraud Detection Logic (Key Features)
This project goes beyond simple data storage by implementing business-logic rules used by real Fraud Analysts:
1. **Velocity Rule (`VEL_10M`):** Identifies rapid-fire transactions (e.g., 5+ transactions within a 10-minute window) to catch stolen credit card testing.
2. **Device Change / Impossible Travel (`DEV_CHANGE`):** Flags transactions occurring on different devices or vastly different locations within an impossibly short timeframe (30 minutes).
3. **High-Value Spikes (`AMT_THRESH`):** An automated MySQL Trigger that actively listens for incoming transactions and instantly flags any transfer exceeding 200,000 INR into the risk ledger.

## 📊 Analyst Views
To support Risk Operations, the database includes pre-built views:
* **`v_running_balance`**: Uses SQL Window Functions to calculate line-by-line account balances.
* **`v_risky_accounts`**: Aggregates fraud flags to highlight the most dangerous accounts.
* **`v_hourly_volume_heatmap`**: Tracks total transaction volume by hour of day to identify abnormal nocturnal bot activity.

## 💡 Conclusion
This project demonstrates a deep understanding of not just SQL syntax, but how databases solve real business problems in the FinTech sector. By combining strict data constraints with automated monitoring, this system effectively reduces financial risk while providing clean, accessible data for financial analysts.
![Fraud Detection Results](<Screenshot 2026-04-29 103755.png>)
