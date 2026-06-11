<div align="center">

<!-- Animated Header Banner -->
<img src="https://capsule-render.vercel.app/api?type=waving&color=0,003366,005baa&height=200&section=header&text=HDFC%20Bank%20Financial%20Dashboard&fontSize=36&fontColor=ffffff&fontAlignY=38&desc=Power%20BI%20Analytics%20Project&descAlignY=58&descSize=18&animation=fadeIn" width="100%"/>

<!-- Badges -->
![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)
![Star Schema](https://img.shields.io/badge/Star%20Schema-003366?style=for-the-badge&logo=databricks&logoColor=white)
![CSV](https://img.shields.io/badge/Dataset-CSV-217346?style=for-the-badge&logo=files&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-28a745?style=for-the-badge)

</div>

---

## 🏦 Project Overview

> **A multi-page Power BI Financial Dashboard** built on real-world structured banking data from HDFC Bank, covering deposit analytics, loan repayments, and branch-level performance tracking — all powered by a clean **Star Schema** data model and custom **DAX measures**.

This dashboard provides end-to-end visibility into:
- 📊 **Deposit vs. Target performance** across branches, regions, and product types
- 🗺️ **Geographic distribution** of deposits across India
- 📈 **Trend analysis** across financial years, quarters, and months
- 🏷️ **Loan repayment** tracking and outstanding balance monitoring

---

## 📁 Folder Structure

```
📦 HDFC Bank/
├── 📂 Assets/                        # Icons, logos, and design assets
├── 📂 HDFC_Bank_Dataset/             # Raw source data (CSV files)
│   ├── 📄 DimAccount.csv             # 100,000 customer accounts
│   ├── 📄 DimBranch.csv              # 500 branches with city/region/zone
│   ├── 📄 DimDate.csv                # Date dimension (2023–2025)
│   ├── 📄 DimProduct.csv             # 10 product types (loans, savings)
│   ├── 📄 BranchDepositTargets.csv   # 18,000 branch deposit targets
│   ├── 📄 FactTransactions.csv       # 500,000 transaction records
│   └── 📄 FactLoanRepayments.csv     # 150,000 loan repayment records
├── 📂 Screenshots/                   # Dashboard page previews
│   ├── 🖼️ Model_View.png             # Star schema model view
│   ├── 🖼️ Page1_Dashboard.png        # Deposit vs Target page
│   ├── 🖼️ Page2_Dashboard.png        # Page 2 overview
│   └── 🖼️ Page3_Dashboard.png        # Page 3 overview
└── 📊 HDFC Financial Dashboard.pbix  # Main Power BI file
```

---

## 📐 Data Model — Star Schema

<div align="center">

> Clean **Star Schema** connecting two fact tables to four dimension tables for flexible, performant analytics.

![Model View](Screenshots/Model_View.png)

</div>

| Table | Type | Rows | Key Fields |
|---|---|---|---|
| `FactTransactions` | Fact | 500,000 | TransactionID, AccountID, BranchID, DateKey, Amount |
| `FactLoanRepayments` | Fact | 150,000 | RepaymentID, AccountID, BranchID, EMIAmount, OutstandingBalance |
| `BranchDepositTargets` | Fact | 18,000 | BranchID, Year, Month, DepositTarget |
| `DimAccount` | Dimension | 100,000 | AccountID, CustomerName, BranchID, ProductCode |
| `DimBranch` | Dimension | 500 | BranchID, BranchName, City, Zone, Region |
| `DimDate` | Dimension | 1,096 | DateKey, Year, Quarter, Month, MonthName |
| `DimProduct` | Dimension | 10 | ProductCode, ProductName |

---

## 📊 Dashboard Pages

### 📌 Page 1 — Deposit vs Target Dashboard

<div align="center">

![Page 1 Dashboard](Screenshots/Page1_Dashboard.png)

</div>

**Key Visuals:**
- 💰 **KPI Cards** — Total Deposit (₹17.77bn), Target (₹20bn), Achievement % (88.87%), Total Deposits Count
- 🍩 **Donut Chart** — Deposit by Product Type (Personal Loan, Vehicle Loan, Business Loan, Education Loan, Home Loan)
- 📉 **Line Chart** — Deposit Trend from 2023 → 2025
- 🗺️ **Map Visual** — Geographic Deposit Distribution across India
- 💡 **Key Insights Card** — Auto-generated business insights
- 🔽 **Slicers** — Financial Year, Quarter, Month, Region, Zone, City, Products

---

### 📌 Page 2 — *(Branch & Loan Analytics)*

> Drill-down into branch-level performance, loan repayment tracking, and outstanding balances segmented by product and geography.

---

### 📌 Page 3 — *(Executive Summary)*

> High-level executive view summarising overall bank health, deposit growth YoY, and target gap analysis.

---

## ⚙️ DAX Measures Highlights

```dax
-- Total Deposit Amount
Total Deposit = SUM(FactTransactions[Amount])

-- Deposit Target
Deposit Target = SUM(BranchDepositTargets[DepositTarget])

-- Achievement %
Achievement % = DIVIDE([Total Deposit], [Deposit Target], 0)

-- Gap to Target
Gap to Target = [Deposit Target] - [Total Deposit]
```

---

## 🛠️ Tools & Technologies

<div align="center">

| Tool | Usage |
|---|---|
| **Microsoft Power BI Desktop** | Dashboard design, DAX, visuals |
| **Power Query (M Language)** | Data transformation & cleaning |
| **DAX** | Calculated columns & measures |
| **Star Schema Modeling** | Relational data architecture |
| **Bing Maps (Power BI)** | Geographic distribution visual |
| **CSV / Excel** | Raw data source format |

</div>

---

## 🚀 How to Use

```bash
# 1. Clone or download this repository
git clone https://github.com/renseegajipara/hdfc-financial-dashboard.git

# 2. Open the dataset folder
cd "HDFC_Bank_Dataset"

# 3. Open the Power BI file
# Double-click: HDFC Financial Dashboard.pbix
# Or open via Power BI Desktop → File → Open
```

> ⚠️ **Note:** If prompted, refresh the data source paths to point to your local `HDFC_Bank_Dataset/` folder.

---

## 📂 Dataset Summary

| File | Records | Description |
|---|---|---|
| `FactTransactions.csv` | 500,000 | All banking transactions (deposits, withdrawals) |
| `FactLoanRepayments.csv` | 150,000 | EMI payments and outstanding loan balances |
| `BranchDepositTargets.csv` | 18,000 | Monthly deposit targets per branch |
| `DimAccount.csv` | 100,000 | Customer account master data |
| `DimBranch.csv` | 500 | Branch details (city, region, zone) |
| `DimDate.csv` | 1,096 | Full date dimension (2023–2025) |
| `DimProduct.csv` | 10 | Product catalogue (loan types, savings) |

---

## 👨‍💻 Author

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=rect&color=gradient&customColorList=2&height=3&width=60%25" width="60%"/>

### ✨ Rensee Gajipara

[![GitHub](https://img.shields.io/badge/GitHub-renseegajipara-181717?style=for-the-badge&logo=github)](https://github.com/renseegajipara)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin)](https://linkedin.com/in/renseegajipara)
[![Power BI](https://img.shields.io/badge/Power%20BI-Portfolio-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)](https://github.com/renseegajipara)

> 💼 *Data Analytics Enthusiast | Power BI Developer | Star Schema Designer*
> 
> 🌍 *Surat, Gujarat, India*

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=500&size=16&pause=1000&color=005BAA&center=true&vCenter=true&width=500&lines=Turning+raw+data+into+actionable+insights;Building+dashboards+that+tell+stories;Power+BI+%7C+DAX+%7C+Data+Modeling" alt="Typing SVG" />

</div>

---

<div align="center">

<!-- Stickers / Emojis Section -->
> 🏆 Built with passion for data &nbsp;|&nbsp; 📊 Powered by Power BI &nbsp;|&nbsp; 🇮🇳 Made in India

<img src="https://capsule-render.vercel.app/api?type=waving&color=0,005baa,003366&height=120&section=footer&animation=fadeIn" width="100%"/>

*⭐ If you found this project useful, please consider starring the repository!*

</div>
