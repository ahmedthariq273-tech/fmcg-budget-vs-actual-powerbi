# FMCG Budget vs Actual Dashboard (Power BI)

An FP&A-style Budget vs Actual reporting pack for a fictional FMCG company, covering revenue, margin, variance, time intelligence, mix and unit economics across 4 regions and 5 product lines.

## Business Question
Where are we against plan, what is driving the gap, and which region/product should management look at first?

## Dataset (synthetic)
Built by me in Excel 2016. No real company data is used.
- 24 months (Jan 2024 – Dec 2025) x 4 regions x 5 product lines = 480 rows per fact table
- Actuals: units with trend and quarterly seasonality; revenue, COGS and Opex derived from units and ratios
- Budget: generated as a randomised band around actuals
- A deliberate West-region underperformance (Jul–Sep 2025) was injected to create a traceable variance story

## Data Model (star schema)
| Table | Type | Notes |
|---|---|---|
| Fct_Actuals | Fact | Date, Region, Product, Units, Revenue, COGS, Opex |
| Fct_Budget | Fact | Date, Region, Product, Budget Revenue, COGS, Opex |
| Dim_Date | Dimension | Built in DAX, marked as date table |
| Dim_Region | Dimension | North, South, East, West |
| Dim_Product | Dimension | 5 product lines |
| _Measures | Measure table | All DAX measures in 8 folders |

Single-direction relationships; facts connect only through shared dimensions.

## DAX Measure Folders
01 Base · 02 Budget · 03 Profitability · 04 Variance Analysis · 05 Time Intelligence (YTD, prior year, YoY) · 06 Mix Analysis · 07 Unit Economics · 08 Dynamic Measures (titles)

## Report Pages
| # | Page | Purpose |
|---|---|---|
| 1 | Executive Overview | KPIs, actual vs budget trend, region variance, product contribution |
| 2 | Revenue & Margin Analysis | Revenue, gross profit, margin by product |
| 3 | Budget & Variance Analysis | Variance trend and variance by financial metric |
| 4 | Regional Performance | Revenue, margin and variance by region |
| 5 | Time Intelligence | YTD, YoY growth, monthly trends |
| 6 | Mix Analysis | Product and region contribution |
| 7 | Unit Economics | Revenue, COGS and gross profit per unit |
| 8 | FP&A Executive Control Room | Single-screen summary with dynamic title and slicers |
| 9 | Product Performance Detail | Drill-through by product |
| 10 | Region Performance Detail | Drill-through by region |

## Key Findings (all regions, all years)
- Revenue closed 0.98% (about ₹1.6M) below budget; budget achievement 99.0%
- West accounts for roughly two-thirds of the shortfall, concentrated in Jul–Sep 2025
- Gross profit variance (about −₹2.6M) is larger than the revenue miss because COGS also ran over budget, so it is a margin story as well as a sales story#

 ## Variance Convention

Positive = favourable. Revenue and profit variances are Actual − Budget; cost variances (COGS, Opex) are Budget − Actual.

## Design
Teal primary palette, grey for budget, red/green reserved for variance, left-aligned titles, consistent KPI card row on every page.

## How to Open
Download `pbix/FMCG_BvA_Dashboard.pbix` and open in Power BI Desktop (free).

## Tools
Excel 2016 · Power BI Desktop · DAX · Power Query

## Author
Ahmed | MBA (Finance) | FP&A aspirant
LinkedIn: linkedin.com/in/ahmed-thariq16
