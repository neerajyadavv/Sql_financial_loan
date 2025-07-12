# 🏦 Bank Loan Data Analysis with SQL

## 📌 Project Overview

This project presents a comprehensive analysis of **bank loan data** using **SQL Server**. It explores loan application patterns, funding distribution, repayment behavior, and borrower risk categories across different time frames and dimensions such as region, employment, term, and more.

The goal is to extract **actionable insights** for financial institutions to assess loan performance, identify good/bad loan trends, and support data-driven decision-making.

---

## 🗃️ Dataset

- **Table Name:** `bank_loan_data`
- **Total Records:** 38,576 loan applications
- **Fields Include:**  
  `id`, `loan_amount`, `total_payment`, `issue_date`, `loan_status`, `term`,  
  `int_rate`, `dti`, `address_state`, `emp_length`, `purpose`, `home_ownership`

---

## 🧠 Key Metrics & Insights

### 📊 Overall Loan Statistics
- Total Loan Applications
- Total Funded Amount
- Total Amount Received
- Average Interest Rate
- Average DTI (Debt-to-Income Ratio)

### 📆 Monthly Trend Analysis
- MTD (Month-to-Date) vs PMTD (Previous Month-to-Date) Loan Performance
- Monthly breakdown of:
  - Loan applications
  - Funded amounts
  - Amounts received

### ✅ Good Loan vs ❌ Bad Loan Analysis
- Good Loans: `Fully Paid`, `Current`
- Bad Loans: `Charged Off`

Metrics include:
- Loan count
- Total funded amount
- Total amount received
- Percentage contribution

### 📍 Dimensional Analysis
- By **Loan Status**
- By **State**
- By **Term**
- By **Employee Length**
- By **Purpose**
- By **Home Ownership**

---

## 📄 Sample SQL Queries

```sql
-- Total Applications
SELECT COUNT(id) AS Total_Applications FROM bank_loan_data;

-- MTD Applications
SELECT COUNT(id) FROM bank_loan_data WHERE MONTH(issue_date) = 12;

-- Bad Loan Percentage
SELECT
    (COUNT(CASE WHEN loan_status = 'Charged Off' THEN id END) * 100.0) / COUNT(id) AS Bad_Loan_Percentage
FROM bank_loan_data;

-- Purpose-wise Loan Analysis
SELECT 
    purpose, COUNT(id), SUM(loan_amount), SUM(total_payment)
FROM bank_loan_data
GROUP BY purpose;
