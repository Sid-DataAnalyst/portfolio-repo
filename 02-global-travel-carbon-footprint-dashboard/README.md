# Global Travel Carbon Footprint Dashboard
### Business Travel GHG (Scope 3) Analytics in Power BI

**Tool:** Microsoft Power BI Desktop

## 1. Project Overview
This project simulates a multinational organization's business-travel carbon footprint program and presents an interactive Power BI dashboard that tracks flight-related greenhouse gas (GHG) emissions across offices, regions, and travel purpose. It demonstrates relational data modeling across 11 tables, DAX time-intelligence and emissions calculations, interactive filtering, and drill-down navigation for sustainability (ESG) reporting.

## 2. Business Objective
- Monitor total absolute emissions (kg CO2e) and emissions per employee (FTE).
- Compare emissions across regions and drill into individual offices.
- Break down emissions by haul type (Short, Medium, Long).
- Segment emissions by case/engagement type (Billable, Administrative, Client Development, Pro Bono).
- Track month-over-month and year-over-year emissions trends.
- Support inter-office and own-office emissions comparisons.

## 3. Dataset Description
Source: `data/GHG_Emissions_Dashboard_Dataset.xlsx` — 11 related tables, 1,500 travel/emission records, 2020–2023, across 20 countries, 20 offices, 120 employees.

| Table | Description |
|---|---|
| Travel | One row per flight leg: carrier, haul class, mileage, cost, dates |
| Travel Emission | One row per flight leg's calculated emissions (kg CO2e), case type |
| Employee | Employee master: department, status, home country |
| Office | Office/legal-entity master: billing office, GL region/country |
| Region | 4 global regions with ESG coordinator and preferred currency |
| Countries | 20 countries with ESG coordinator and office contact |
| Locations | City-level office locations with coordinates |
| Service | Travel service type: Air, Rail, Car Rental, Hotel |
| Factor | Emission factors (kg CO2e/passenger-km) by haul class and year |
| Date | Standalone calendar table (2020–2023) |
| Metric Selection | Disconnected what-if table for Absolute Emission / Emission-per-FTE toggle |

## 4. Tools & Skills Demonstrated

| Area | Details |
|---|---|
| BI Tool | Microsoft Power BI Desktop |
| Data Modeling | 11-table relational model (star/snowflake hybrid) with a dedicated Date table |
| DAX | Absolute emissions, emissions/FTE, YoY comparisons, rolling 3-year windows, metric toggle |
| Visuals Used | KPI cards, area chart, stacked column chart, clustered bar, donut, line/column combo |
| Interactivity | Multi-select slicers (Haul, Comparison Year, Travel Start Date, Case Type, Office, Year, Region) |
| Navigation | Multi-page report: Inter-Office Emissions and Own-Office Emissions |
| Design | Dark theme with gold/teal/blue accents, card-based KPI layout |

## 5. Data Model
- **Fact table:** Travel Emission — Emission Factor, Absolute Emission, Case Type, Date ID.
- **Bridge/fact table:** Travel — carrier, haul class, mileage, cost, links to Employee/Office/Service.
- **Dimensions:** Date, Countries, Region, Office, Locations, Employee, Service, Factor, Metric Selection.
- **Key relationships:** Travel Emission[Travel Code] ↔ Travel[Travel Code] (1:1); Travel[Office Code] → Office[Office Code]; Office[Country Code] → Countries[Country Code]; Countries[Region Code] → Region[Region Code]; Travel Emission[Date ID] → Date[Date ID]; Travel Emission[Factor Code] → Factor[Factor Code].

## 6. Key DAX Measures

| Measure | Purpose |
|---|---|
| Total Global Flights | COUNTROWS of Travel |
| Global Absolute Emissions | SUM of Travel Emission[Absolute Emission] |
| Global Emissions/FTE | Global Absolute Emissions ÷ DISTINCTCOUNT of active employees |
| Total Global Flight Mileage | SUM of Travel[Flight Mileage] |
| _SumEmissionFactor | SUM of Travel Emission[Emission Factor] |
| _This Year / _Previous Year | Year-over-year comparison via CALCULATE |
| _Last 3 Years / _Next 3 Years | Rolling window via DATESINPERIOD |
| _Year to date | `CALCULATE([Absolute Emission], DATEADD(Travel[Travel Start Date], -12, DAY))` |
| Travel Emission/FTE | Normalized emissions, toggled via Metric Selection |

## 7. Dashboard Pages

**Page 1 — Inter-Office Emissions (Landing Page):** KPI strip, Absolute Emissions by Office (bar), Average Absolute Emissions by Region (area), Monthly Absolute Emissions for Selected Offices (donut), Global Monthly Absolute Emissions (column), slicer panel (Office, Case Type, Year).

**Page 2 — Own-Office Emissions:** Monthly trend (column), Case Type breakdown (bar), Haul-class stacked column with Comparison Year slicer.

## 8. Key Insights
- **Overall footprint:** 630,365 kg CO2e (~630 tonnes) across 4.49M km flown; ~5,253 kg CO2e/FTE.
- **Regional split:** Europe (196,399 kg) and Asia & Pacific (185,270 kg) lead, ahead of South/Latin America (146,366 kg) and North America (102,330 kg).
- **Haul-class impact:** Long-haul flights account for 288,897 kg from only 304 legs — the highest-leverage reduction target.
- **Case-type mix:** Billable client travel drives the majority (346,921 kg, 821 legs).
- **Office concentration:** Mexico, Peru, Germany, United States, and Italy offices are the top 5 emitters (34K–37K kg each).
- **Year-over-year trend:** Relatively flat, ~150K–167K kg/year, peaking in 2022.

## 9. How to Use
Use the slicers to filter every visual; hover for tooltip detail; use the Metric Selection toggle to switch between Absolute Emission and Absolute Emission/FTE; switch pages for global vs. single-office views.

## 10. Potential Enhancements
- Reduction Target overlay vs. actuals
- Top N Highest-Emitting Routes table
- Ground-transport and hotel-stay emissions
- Power BI Service publish with scheduled refresh (Concur/Egencia)
- Row-level security (RLS) per regional ESG coordinator

## 11. Project Files

| File | Description |
|---|---|
| `data/GHG_Emissions_Dashboard_Dataset.xlsx` | Source data (11 tables, 1,500 records) |
| `Global_Travel_Emissions_Dashboard.pbix` | Power BI report file |
| `README.md` | This documentation |
