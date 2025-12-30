# Fraud Detection on Transaction Data

## Overview

This project explores, analyzes, and models fraudulent financial transactions using the Kaggle Fraudulent Transactions dataset. The goal is to build a realistic, leakage-free fraud detection pipeline that mirrors how fraud systems operate in production.

Key features:

- [x] No target leakage (fraud labels are never used to create predictive features)
- [x] Time-aware feature engineering
- [ ] Retroactive analysis of fraud-linked customers after detection

---

## Dataset

**Source:** [Kaggle – Fraudulent Transactions Data](https://www.kaggle.com/datasets/chitwanmanchanda/fraudulent-transactions-data/data)

Each row represents a single transaction between two entities:

### Data Dictionary (Source: Kaggle):

* `step` - 1 hour unit. Total steps 744 (30 days simulation).

* `type` - Type of transaction (CASH-IN, CASH-OUT, DEBIT, PAYMENT and TRANSFER)

* `amount` - Amount of the transaction in local currency.

* `nameOrig` - Customer who started the transaction

* `oldbalanceOrg` - Initial balance before the transaction

* `newbalanceOrig` - New balance after the transaction

* `nameDest` - Recipient of the transaction

* `oldbalanceDest` - Initial balance recipient before the transaction

* `newbalanceDest` - New balance recipient after the transaction

* `isFraud` - This is the transactions made by the fraudulent agents inside the simulation. In this specific dataset the fraudulent behavior of the agents aims to profit by taking control or customers accounts and try to empty the funds by transferring to another account and then cashing out of the system.

* `isFlaggedFraud` - The business model aims to control massive transfers from one account to another and flags illegal attempts. An illegal attempt in this dataset is an attempt to transfer more than 200.000 in a single transaction.

### Data Dictionary Continued (Engineered Categories)


Entity naming convention:

* IDs starting with `C` → Customer
* IDs starting with `M` → Merchant

Constraints:

* Merchants do not have balance information
* Fraud labels (`isFraud`, `isFlaggedFraud`) represent post-event truth and must not be used for feature creation

## Performance

| Class            | Precision | Recall | F1-Score | Support   |
| ---------------- | --------- | ------ | -------- | --------- |
| Non-Fraud (0)    | 1.00      | 1.00   | 1.00     | 1,268,270 |
| Fraud (1)        | 0.51      | 0.89   | 0.65     | 4,254     |
| Macro Avg        | 0.76      | 0.94   | 0.82     | 1,272,524 |
| Weighted Avg     | 1.00      | 1.00   | 1.00     | 1,272,524 |

| Actual \ Predicted | Non-Fraud (0) | Fraud (1) |
| ------------------ | ------------- | --------- |
| Non-Fraud (0)      | 1,264,697     | 3,573     |
| Fraud (1)          | 485           | 3,769     |

Source: Commit `73c3d00`
---
