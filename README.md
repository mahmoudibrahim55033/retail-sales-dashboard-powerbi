# 🛒 Midway Retail Sales Dashboard (Power BI)

An interactive Power BI dashboard analysing retail sales performance across US store locations from 2020 to 2022. The report covers total sales, year-to-date trends, department breakdowns, fixed cost tracking, and KPI comparison against sales targets — across three store types (CORE, DIGITAL, LOCAL).

---

## 📊 Report Pages

### 1. Sales
The main overview page providing a high-level picture of retail performance across all locations and departments.

**Visuals:**
- **Department Slicer** — filter all visuals by department: Clothing, Electronics, Garage, Kitchen, Other
- **Key Metrics cards** — Total Sales, Total Transactions, and one additional KPI
- **Map — Total Sales by Store Location and StoreType** — bubble map of the US showing store-level sales volume, coloured by store type (CORE / DIGITAL / LOCAL)
- **Stacked bar chart — Total Sales by Store Location and Department** — ranked by state, broken down by department colour
- **Bar chart — Total Sales by StoreType** — CORE leads at $3.01bn, DIGITAL at $0.78bn, LOCAL at $0.27bn

---

### 2. Development
A time-series page focused on sales trend and year-to-date accumulation.

**Visuals:**
- **Line chart — Total Sales and Total Sales YTD by Date** — dual-line chart showing daily sales alongside the cumulative YTD total, spanning Jan 2020 to Dec 2022. The YTD line resets each January, clearly showing annual growth patterns across three full years.

---

### 3. Cost & Target
A KPI tracking and cost analysis page enabling store-level performance comparison against targets.

**Visuals:**
- **Date Slicer** — range slider from 1/1/2020 to 12/31/2022
- **Sales KPI Tracking gauge** — actual sales of $18.03M vs. goal of $27.30M (−33.93%), with a sparkline showing daily trend
- **Table — Store Location breakdown** — shows Total Wages, Total Sales, and Difference from Target per state, with conditional formatting icons (green circle = above target, orange triangle = near target, red diamond = below target)
- **Scatter chart — Total Rent and Store Size by Store** — plots rent ($) against store size (sqft) by store, coloured by StoreType, revealing cost efficiency across store formats

---

## 📁 Data Sources

| File | Description |
|---|---|
| `Sales_Retail_2020.csv` | Weekly sales data for 2020 |
| `Sales_Retail_2021.csv` | Weekly sales data for 2021 |
| `Sales_Retail_2022.csv` | Weekly sales data for 2022 |
| `Sales_Retail_2020_-_2022.csv` | Combined weekly sales across all three years |
| `Overview_-_Source.xlsx` | Aggregated sales and gross margin by date, store type, location, department, and group |
| `Store_Details.csv` | Store metadata: StoreID, StoreType (CORE/DIGITAL/LOCAL), StoreLocation (US state) |
| `Store_Size.csv` | Store footprint in square feet per StoreID |
| `Retail_Fixed_Costs.xlsx` | Weekly wages, rent, and target sales per store (6,240 records) |
| `Department_List.xlsx` | Department categories, definitions, and regulatory reference data |
| `Date.txt` | Continuous date dimension from 2020-01-01 to 2022-12-31 used as a date table |

---

## 🗂️ Data Model

The report uses a star schema with the following key relationships:

- `Store_Details` → linked to sales and cost tables via `StoreID`
- `Store_Size` → joined to `Store_Details` via `StoreID`
- `Retail_Fixed_Costs` → contains `Wages`, `Rent`, and `TargetSales` per store per week
- `Date.txt` → date dimension table used to drive time intelligence (YTD, date slicers)
- `Overview_-_Source` → pre-aggregated fact table with `Sales` and `Gross Margin`

**Store Types:** CORE · DIGITAL · LOCAL
**Departments:** Clothing · Electronics · Garage · Kitchen · Other
**Geography:** US states (approx. 40 store locations)
**Date Range:** January 2020 – December 2022

---

## 📐 Key DAX Measures

| Measure | Description |
|---|---|
| `Total Sales` | Sum of weekly sales across all stores |
| `Total Sales YTD` | Year-to-date cumulative sales using `DATESYTD` |
| `Total Wages` | Sum of weekly wage costs per store |
| `Total Rent` | Sum of weekly rent costs per store |
| `Target Sales` | Sum of weekly sales targets per store |
| `Difference from Target` | Variance between actual sales and target |

---

## 🛠️ Tools & Technologies

- **Power BI Desktop** — report development and DAX modelling
- **Power Query (M)** — data loading, transformation, and combining yearly CSV files
- **DAX** — time intelligence (YTD), KPI measures, and conditional formatting logic
- **Bing Maps** — geographic bubble map visual

---

## 🚀 How to Open

1. Install [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free)
2. Clone or download this repository
3. Place all data source files in the same folder as `midway.pbix`
4. Open `midway.pbix` — Power BI will load and refresh data automatically

> If prompted about data source paths, update them via **Home → Transform Data → Data Source Settings** to point to your local folder.

---

## 👤 Author

**mahmoudibrahim55033** — [GitHub Profile](https://github.com/mahmoudibrahim55033)
