# Fleet Performance and Efficiency Dashboard — Power BI

A single-page Power BI dashboard built to track vehicle trips, delivery performance, fuel efficiency, and maintenance cost across a vehicle fleet. Built as a module-end assignment.

## 📊 Overview

The report answers three core questions for a fleet operations audience:

- **How efficiently is the fleet running?** — cost per km, distance travelled, fuel efficiency trends
- **How reliable are deliveries?** — on-time delivery %, delivery status influencers, on-time delivery by destination
- **Where is cost coming from?** — maintenance cost by vehicle type, cost-per-km breakdown

## 🎯 Objectives

This dashboard was built to give a fleet manager a single view to:

1. **Monitor overall fleet health** — track total trips, average distance per trip, and average cost per km at a glance via top-line KPI cards.
2. **Measure delivery reliability** — surface on-time delivery % overall and broken down by destination, to spot problem routes.
3. **Diagnose the drivers of poor delivery performance** — use the Key Drivers visual to identify which factors (vehicle type, driver, distance) most affect delivery status, enabling root-cause investigation rather than just reporting the symptom.
4. **Track efficiency over time** — visualize fuel efficiency trends by date to catch gradual degradation or improvement.
5. **Control maintenance and running cost** — compare maintenance cost across vehicle types and drill into cost-per-km through an interactive decomposition tree, down to the vehicle-type / distance level.
6. **Support ad-hoc filtering** — let the user slice the whole page by vehicle type without switching reports.

In short: move from "what happened" (KPIs) to "why it happened" (Key Drivers, decomposition tree) on a single page.

## 💡 Key Insights This Dashboard Is Designed to Surface

> These are the questions the report structure is built to answer once populated with live data — refresh the model in Power BI Desktop to see the actual current figures.

- **Cost efficiency**: whether cost-per-km is being driven more by fuel/distance or by maintenance, and which vehicle type is the most expensive to run.
- **Delivery reliability**: which destinations have the worst on-time delivery %, and whether that's tied to a specific vehicle type or driver rather than distance alone.
- **Root cause of delays**: the Key Drivers visual ranks the factors most associated with a poor delivery status, so you can act on the biggest lever instead of guessing.
- **Fleet aging / efficiency drift**: the fuel-efficiency-by-date trend line makes it easy to spot whether efficiency is declining over time (a signal for maintenance or fleet renewal).
- **Cost concentration**: the decomposition tree lets you drill from total cost-per-km down into the vehicle types and distance bands that contribute most, rather than only seeing an average.

## 🗂️ Data Model

| Table | Role | Key Fields |
|---|---|---|
| `Trip_Data` | Fact table — one row per trip | Trip_ID, Delivery_Date, Delivery_Status, Destination, Driver_ID, Distance_km, fuel efficiency new |
| `Vehicle_Master` | Dimension — vehicle attributes | Vehicle_ID, Vehicle_Type, Maintenance_Cost |
| `Table` | Measures table | On-Time Delivery %, costperkm, Total Trips |

**Relationship:** `Trip_Data` → `Vehicle_Master` via `Vehicle_ID`

## 📈 Dashboard Visuals

| Visual | Title | Fields / Measures |
|---|---|---|
| Card | Average cost per Km | `costperkm` |
| Card | Average distance km | `Sum(Distance_km)` |
| Card | Total trips | `Total Trips` |
| KPI | On-Time Delivery % | `On-Time Delivery %`, `Delivery_Date` |
| Clustered Bar Chart | On-Time Delivery % by Destination | `Destination`, `On-Time Delivery %` |
| Pie Chart | Average Maintenance Cost by Vehicle Type | `Vehicle_Type`, `Maintenance_Cost` |
| Line Chart | Fuel efficiency by Date | `fuel efficiency new`, `Delivery_Date` |
| Decomposition Tree | Cost per KM Analysis | `costperkm`, `Distance_km`, `Maintenance_Cost`, `Vehicle_Type` |
| Key Drivers | Delivery Status Influencers | `Delivery_Status`, `Vehicle_Type`, `Driver_ID`, `Distance_km` |
| Slicer | Vehicle Type filter | `Vehicle_Type` |
| Button | Reset / navigation action | — |

## 🖼️ Layout

A to-scale schematic of the report page (reconstructed from the file's layout definition):

<img width="876" height="497" alt="image" src="https://github.com/user-attachments/assets/ea36417e-b67b-4466-9de8-f3ad18697f6e" />

## 📁 Repository Contents

```
├── powerBI_module_end_assignment.pbix   # Power BI report file
├── Fleet_Dashboard_Documentation.pdf     # Full write-up: data model, visuals, narrative
├── Fleet_Dashboard_Documentation.docx    # Editable version of the above
├── dashboard_layout_schematic.png        # Layout diagram
└── README.md
```

## 🛠️ How to Open

1. Install [Power BI Desktop](https://www.microsoft.com/en-us/power-platform/products/power-bi/desktop) (Windows only).
2. Open `powerBI_module_end_assignment.pbix`.
3. Refresh the data model if prompted.

## 📄 Documentation

See [`Fleet_Dashboard_Documentation (1).pdf`](Fleet_Dashboard_Documentation (1).pdf for a full breakdown of the data model, every visual and the fields it uses, and a narrative walkthrough of the dashboard.

## ✍️ Author

*Vasumitha T*


