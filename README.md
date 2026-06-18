# DecodeLabs-Task1
# 🛡️ Data Integrity & Quality Audit Documentation

### 📊 Project: Phase 1 – Data Cleaning & Preparation
* **Organization:** Decode Labs | Industrial Training Kit
* **Batch:** 2026
* **Analyst:** Youmna Moussa
* **Role:** Junior Data Analyst

---

## 1. 🎯 Project Scope & Objective
* **Objective:** Transform raw data into a **"Gold Standard"** dataset for reliable BI modeling.
* **Standard:** Followed DecodeLabs data quality guidelines via EDA and structural cleaning.
* **Target:** Achieve a strict **0% error rate** on unique identifiers and date formats.

---

## 2. 🔍 Exploratory Data Analysis (EDA) for Missing Values
An initial audit revealed a total of **309 missing values (Blanks)** concentrated in the *Coupon Code* column. To prevent loss of statistical power resulting from listwise deletion (arbitrary row removal), a cross-tabulation analysis was conducted against key operational metrics:

### A. Items in Cart vs. Coupon Blanks
* **Cart Size Audit:** 175 blank cases were scattered across orders ranging from 2 to 10 items (including 19 cases at max capacity).
* **Conclusion:** This uniform distribution proves missing coupons are purely random and completely unrelated to order quantity.

### B. Order Status vs. Coupon Blanks
| Order Status | Missing Coupon Cases |
| :--- | :---: |
| ❌ Cancelled | 58 |
| ⏳ Pending | 59 |
| 🔄 Returned | 76 |
| 🚚 Shipped | 64 |

> 💡 **Analytical Insight:** The close statistical proximity across successful and unsuccessful orders proves that the final order status is completely independent of coupon usage.

### C. Payment Method vs. Coupon Blanks
The *Payment Method* column was audited and found to be 100% clean with zero missing values. Cross-referencing yielded:
* **Online Transactions:** 80 cases
* **Debit Card Payments:** 64 cases
* **Cash Payments:** 64 cases
* **Credit Card Payments:** 55 cases
* **Gift Card Payments:** 48 cases

### D. Marketing Referral Source vs. Coupon Blanks
| Acquisition Channel | Blank Coupon Cases |
| :--- | :---: |
| 📘 Facebook | 67 |
| 🔍 Google Search | 63 |
| 📸 Instagram | 61 |
| 🔗 Direct Referral | 60 |
| 📧 Email Marketing | 55 |

### 🛑 EDA Conclusion:
The statistical balance of blanks across all parameters confirms that the missing data falls under **MCAR (Missing Completely at Random)**. It represents organic customer behavior (purchasing without a discount code) rather than a system logging failure. Therefore, **strategic imputation** is the correct path over row deletion.

---

## 🛠️ 3. Power Query Workflow
The raw dataset was processed sequentially through three main phases to achieve full data integrity:

* **Phase 1: Structural Integrity** – Handled data ingestion, removed duplicated transactions (*Removed Duplicates*), and standardized formatting (*Changed Date ColumnType*).
* **Phase 2: Text Standardization** – Cleaned and unified text columns (*Customer_IDs, Product Name, Payment Method, and Order Status*) using successive *Trim* and *Capitalize* transformations to eliminate trailing spaces.
* **Phase 3: Strategic Imputation** – Targeted missing fields by executing *Replaced null Values* in the Coupon Code column, substituting blanks with **"None"** to safely preserve all data rows without deletion.

---
## 📂 Files in this Repository
* `DecodeLabs-Task1.xlsx` - Cleaned dataset with full Power Query applied steps.
