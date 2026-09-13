# SLA Compliance & Ticket Resolution Dashboard
### IT Helpdesk Analytics in Power BI

**Tool:** Microsoft Power BI Desktop

## 1. Project Overview
This project simulates a real-world IT Helpdesk / Support Ticketing environment and presents an interactive Power BI dashboard that tracks ticket volume, resolution performance, SLA (Service Level Agreement) compliance, and team workload. It demonstrates end-to-end BI development skills: data modeling, DAX calculations, interactive visuals, and drill-through navigation for root-cause analysis.

The dashboard answers questions a support operations manager would actually ask: How many tickets are open vs. closed? Which categories generate the most tickets? Who is carrying the heaviest workload? Are we meeting our SLA targets, and where are we breaching them?

## 2. Business Objective
- Monitor overall ticket health (open, closed, and total volume) in real time.
- Identify which issue categories (Hardware, Software, Network, Security) drive the most support load.
- Evaluate individual and team workload distribution across support agents.
- Track SLA compliance and flag the proportion of tickets breaching resolution deadlines.
- Spot trends in ticket volume over time to support staffing and capacity planning.
- Drill through from summary KPIs into ticket-level detail for audit and root-cause investigation.

## 3. Dataset Description
Source: `data/ticketing_Dataset.csv` — 1,557 ticket records spanning a full annual cycle (Jan–Dec).

| Column | Description |
|---|---|
| Ticket_ID | Unique identifier for each support ticket (e.g., T001) |
| Date_Opened | Date the ticket was logged |
| Date_Closed | Date the ticket was resolved (blank if still open) |
| Resolution_Due_Date | SLA deadline by which the ticket should be resolved |
| Category | Issue type: Hardware, Software, Network, or Security |
| Assigned_To | Support agent responsible for the ticket |
| Status | Current ticket state: Open or Closed |

## 4. Tools & Skills Demonstrated

| Area | Details |
|---|---|
| BI Tool | Microsoft Power BI Desktop |
| Data Modeling | Star-schema style model with a dedicated Calendar (date) table for time intelligence |
| DAX | Custom measures for KPIs, percentages, SLA status, and ticket aging |
| Visuals Used | KPI cards, donut chart, pie chart, clustered bar chart, line chart, slicers |
| Interactivity | Cross-filtering slicers (Status, Category, Assigned_To) and button-based drill-through |
| Navigation | Custom drill-through page with a back button for ticket-level detail views |
| Design | Consistent purple/navy brand theme, card-based KPI layout, clear visual hierarchy |

## 5. Data Model
- **Fact table:** TicketingDB — one row per ticket (Ticket_ID, dates, Category, Assigned_To, Status).
- **Dimension table:** Calendar Table — standalone date table for MTD/YTD/month-over-month time intelligence.
- **Relationship:** Calendar Table[Date] → TicketingDB[Date_Opened] (one-to-many).

## 6. Key DAX Measures

| Measure | Purpose |
|---|---|
| Total Tickets | COUNTROWS of the ticket fact table |
| Closed Tickets | Count of tickets where Status = "Closed" |
| Open Tickets | Count of tickets where Status = "Open" |
| Closed Tickets% | Closed Tickets ÷ Total Tickets |
| Open Tickets% | Open Tickets ÷ Total Tickets |
| SLA Days | Resolution_Due_Date − Date_Opened |
| SLA Status | "Within SLA" or "SLA Breach" |
| Age Closed | Date_Closed − Date_Opened |
| Open Tickets Age | TODAY() − Date_Opened |

## 7. Dashboard Pages

**Page 1 — Tickets Analysis (Landing Page):** KPI strip, Tickets by SLA Status (pie), Tickets by Category (bar), Tickets by Assigned_To (clustered bar), Tickets by Status (donut), Tickets Over Time (line), slicer panel.

**Page 2 — Drill-Through: Tickets Details:** Ticket-level detail by Assigned_To and by Category, with a back button.

## 8. Key Insights
- **Overall health:** 1,380 tickets closed (88.6%) vs. 177 open (11.4%).
- **SLA risk:** A large share of tickets breach their resolution deadline — the biggest opportunity area.
- **Category load:** Network (636 tickets) is the top driver, followed by Security (419), Hardware (252), Software (250).
- **Workload:** Sarah Brown and Mike Johnson carry the largest loads (331, 330); David Wilson has a high open-ticket backlog (40).
- **Volume trend:** Peak around March (~159 tickets), dip in June (~101 tickets).

## 9. How to Use
Use the slicers to filter every visual; hover for tooltip detail; drill through from Category/Assigned_To bars into ticket-level detail; use the back arrow to return.

## 10. Potential Enhancements
- Resolution Time trend by month/agent
- Top N Breached Tickets table
- Priority field (High/Medium/Low) weighting
- Power BI Service publish with scheduled refresh (Zendesk/ServiceNow/Jira)
- Row-level security (RLS) per agent

## 11. Project Files

| File | Description |
|---|---|
| `data/ticketing_Dataset.csv` | Source data (1,557 rows) |
| `Support_Tickets_Dashboard.pbix` | Power BI report file |
| `README.md` | This documentation |
