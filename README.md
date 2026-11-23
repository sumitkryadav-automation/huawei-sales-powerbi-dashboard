# 📱 Huawei Smartphone Sales Dashboard (India) · Power BI

An interactive Power BI dashboard that analyses Huawei smartphone sales across **19 Indian cities** and **15 models** from **Oct 2021 to Oct 2024**. It shows sales value, units sold and transactions by city, model, month, year, payment method and customer rating.

> **About the data:** I generated this sample dataset with AI tools for practice. It is **not** Huawei data, employer data or data from any real company. All figures are illustrative.

![Huawei Sales Dashboard](images/dashboard-overview.png)

---

## 🎯 Business question

**Which cities, models and time periods drive Huawei smartphone sales in India, and how do customers pay and rate their purchases?**

---

## 📂 Dataset

| Item | Detail |
|---|---|
| File | `data/Huawei_Mobile_Sales_Data.xlsx` |
| Rows | 3,835 transactions |
| Period | Oct 2021 – Oct 2024 |
| Coverage | 19 Indian cities · 15 Huawei models |
| Fields | Date parts (Day, Month, Year), city, mobile model, units, sales value, payment method, customer rating |
| Model | One table (`Sales_Data`), no relationships |

---

## 🛠️ Tools used

![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=flat-square&logoColor=black)
![Power Query](https://img.shields.io/badge/Power_Query-217346?style=flat-square)
![DAX](https://img.shields.io/badge/DAX-0F6CBD?style=flat-square)
![Excel](https://img.shields.io/badge/Excel-217346?style=flat-square)

---

## 🔍 Approach

### 1. Data cleaning (Power Query)
- Built a proper **Date** column from the separate Day, Month and Year columns using:
  ```powerquery
  #date([Year], [Month], [Day])
  ```
- Checked that all **3,835 rows** loaded with no errors (see *Challenges* below).

### 2. DAX measures
| Measure | Shown as |
|---|---|
| `Total_Sales` | Total Sales |
| `Total_QTY` | Total QTY |
| `Total_Transactions` | Total Transactions |
| `Average` | Avg Price/Unit |

### 3. Dashboard design
- **KPI cards:** Total Sales · Total QTY · Total Transactions · Avg Price/Unit
- **Visuals:** city-wise sales map · month-wise QTY line chart · year-wise sales area chart · Top-3 models · Top-4 cities · customer ratings funnel · payment method pie chart
- **Interactivity:** City, Year, Payment Method and Mobile Model dropdown slicers, plus January–December month buttons

---

## 📊 Key findings

| Metric | Value |
|---|---|
| 💰 Total sales | **₹769.2M** |
| 📦 Units sold | **19.2K** |
| 🧾 Transactions | **3,835** |
| 🏷️ Avg price per unit | **₹40.1K** |

- 🏙️ **Two cities dominate:** Delhi (₹204M) and Mumbai (₹127M) bring in about **43%** of all sales.
- 📱 **Top models:** Huawei P40 Lite (₹60M), Nova 8 (₹58M) and Mate 20 Pro (₹56M).
- 📅 **Best year:** 2022 was the strongest full year at **₹262M**, followed by 2023 at **₹253M**. 2021 covers only Oct–Dec and 2024 only Jan–Oct, so those years aren't directly comparable.
- 📈 **Seasonality:** July sold the most units (**1,700**) and February the fewest (**1,451**).
- ⭐ **Customer satisfaction:** 5 stars is the most common rating (**1,488** transactions), and about **61%** of ratings are 4 or 5 stars.
- 💳 **Payments are evenly split:** UPI 26.4% · Debit card 24.7% · Credit card 24.7% · Cash 24.2%.

---

## 💡 Recommendations

*Based on this sample data. With real data, these would be the starting points for discussion with a sales team.*

1. **Protect the top two cities.** Delhi and Mumbai bring in 43% of revenue, so prioritise stock availability and retail partnerships there, while testing growth campaigns in mid-performing cities to reduce dependence on two markets.
2. **Stock for the bestsellers.** Keep the P40 Lite, Nova 8 and Mate 20 Pro well stocked, and review slow-moving models.
3. **Plan ahead of the July peak.** Build inventory and run promotions before July, and use February's slow period for clearance offers.
4. **Keep every payment option.** No single method dominates, so all four (UPI, cards and cash) need to stay available. Payment-specific offers are unlikely to shift behaviour much.
5. **Follow up on low ratings.** About 39% of ratings are 3 stars or below, so a post-purchase feedback process could find out what's driving them.

---

## 🧩 Challenges & what I learned

**Problem:** My first attempt at building the date merged Day, Month and Year as text and then changed the type to Date. Power BI read the dates as **Month/Day/Year**, so every date with a day above 12 became an error. Removing those errors silently **dropped about 60% of the data**, and total sales showed **₹307.8M instead of ₹769.2M**.

**Fix:** I rebuilt the column with `#date([Year], [Month], [Day])`, which sets each part explicitly and doesn't depend on locale. All rows were restored.

**Second fix:** The Customer Ratings visual was **summing** the rating values (1–5) instead of **counting** transactions. I changed the aggregation to **Count**.

**Lesson:** Always check row counts and totals after each cleaning step. "Remove errors" can hide a much bigger problem.

---

## 📁 Repository structure

```
huawei-sales-powerbi-dashboard/
├── Huawei_Dashboard.pbix          # Power BI report
├── data/
│   └── Huawei_Mobile_Sales_Data.xlsx
├── images/
│   └── dashboard-overview.png
└── README.md
```

## ▶️ How to use

1. Download or clone this repository.
2. Open `Huawei_Dashboard.pbix` in **Power BI Desktop** (free for Windows).
3. If prompted, point the data source to `data/Huawei_Mobile_Sales_Data.xlsx`.
4. Use the slicers and month buttons to explore.

---

## 👤 Author

**Sumit Kumar Yadav**, MIS & Data Analyst
[LinkedIn](https://www.linkedin.com/in/sumitkryadav-automation) · [GitHub](https://github.com/sumitkryadav-automation)

*Built independently as a practice project to strengthen my Power BI, Power Query and DAX skills.*
