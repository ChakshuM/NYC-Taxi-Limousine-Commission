# Data Driven Rides: Operational Insights from New York City Taxi Trips using Power BI

## Overview
This project analyzes **New York City Yellow Taxi Trip Data** to uncover insights into passenger demand, operational efficiency, fare structures, and payment behavior.  
Through **Power BI dashboards**, it delivers actionable intelligence to support the **New York City Taxi & Limousine Commission (TLC)** in improving service allocation, revenue optimization, and decision-making.

---

## Table of Contents
1. [Executive Summary](#executive-summary)
2. [Business Problem](#business-problem)
3. [Objectives & Analytical Questions](#objectives--analytical-questions)
4. [Project Scope](#project-scope)
5. [Data Source](#data-source)
6. [Data Model & Entities](#data-model--entities)
7. [Data Processing Pipeline](#data-processing-pipeline)
8. [Dashboard Design](#dashboard-design)
9. [Key Reports & Insights](#key-reports--insights)
10. [Testing & Validation](#testing--validation)
11. [Optimization & Future Enhancements](#optimization--future-enhancements)
12. [References](#references)

---

## Executive Summary
The project developed an interactive **Power BI dashboard** to analyze NYC Yellow Taxi trip data (Jan–Mar 2025). It uncovered temporal, geographic, and behavioral patterns across millions of records, highlighting:

- **Peak ridership** between **4 PM – 11 PM**, especially on **Thursdays and Saturdays**.  
- **Vendor 2** held a slight market lead (51% of total trips).  
- **Average fare:** $18, **total distance:** 26.63 million miles.  
- **Credit cards** dominated payments (85%), showing strong digital adoption.  
- **Central Manhattan** emerged as the busiest pickup and drop-off region.  

These insights support TLC in **driver deployment**, **fare strategy refinement**, and **service coverage optimization**.

---

## Business Problem
NYC Taxi operations face inefficiencies due to:
- Uneven fleet distribution across boroughs.  
- Limited analytical insight into demand patterns and pricing.  
- Under-optimized fare strategies for airport and long-distance trips.  
- Fragmented understanding of payment preferences.  

The project addresses these through a **data-driven analytical framework** for smarter resource planning and revenue management.

---

## Objectives & Analytical Questions
The analysis focused on **six descriptive questions** to improve TLC operations:
1. **When** are the busiest hours and days for taxi demand?  
2. **Where** are the most active pickup and drop-off zones?  
3. What is the **average passenger count per trip**, and how does it vary?  
4. How do **trip distances and fares** differ across zones and time?  
5. How do **payment preferences** (cash vs. card) vary by region and time?  
6. What proportion of trips use **standard, flat, or negotiated rates**?

Each question is supported by targeted Power BI visuals and interactive filters.

---

## Project Scope
**In Scope:**
- Analysis of NYC Yellow Taxi data (Jan–Mar 2025).  
- Data cleaning, modeling, and visualization in Power BI.  
- Development of six interactive dashboards.  
- Generation of operational and financial insights.

**Out of Scope:**
- Real-time analytics or live API integration.  
- Predictive or prescriptive modeling.  
- Integration with non-TLC data sources (Uber, Lyft, etc.).

**Timeline:** May 15 – August 15, 2025.  
**Deliverable:** Power BI dashboard with comprehensive insights for TLC.

---

## Data Source
Dataset: **NYC Yellow Taxi Trip Records** from the [NYC Open Data Portal](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page).

**Contents include:**
- Pickup/drop-off datetime and location.  
- Passenger count and trip distance.  
- Fare components and payment types.  
- Rate code and vendor details.

**Format:** Apache Parquet.  
**Period Analyzed:** January–March 2025.  
**Supplementary data:** TLC taxi zone shapefiles for spatial visualization.

---

## Data Model & Entities
The data follows a **star schema** with one central fact table and four dimension tables.

**Fact Table:** `Fact_Trips`  
Includes:
- Pickup & drop-off datetime  
- Passenger count  
- Trip distance  
- Fare, other charges, total amount  
- Payment type, rate code, vendor ID  

**Dimension Tables:**
- `Dim_RateCode` – Standard, JFK Flat, Negotiated fares  
- `Dim_Vendor` – Vendor identification  
- `Dim_PaymentType` – Cash, Credit Card, Dispute  
- `Dim_Calendar` – Date, month, week, holiday flags  

This model ensures efficient aggregation, scalability, and dashboard performance.

---

## Data Processing Pipeline
The ETL process was built using **Power BI Power Query**:

### Level 1: Data Cleaning
- Mean/Mode imputation for missing values.  
- Removal of invalid and placeholder records.  
- Consolidation of fare-related columns.  
- Filtering of outliers in trip distance and fare.

### Level 2: Data Transformation
- Extracted time-based attributes (hour, day, month).  
- Created **IsWeekend** and **holiday flags**.  
- Derived trip duration and generated a date dimension table.  
- Mapped pickup/drop-off zones for spatial analysis.

### Level 3: Loading
- Cleaned dataset stored on **OneDrive**.  
- Connected directly to **Power BI** for auto-refresh.  
- Enabled shared access and real-time data synchronization.

---

## Dashboard Design
The Power BI solution was designed for:
- **Operational Efficiency:** Identify peak zones, high-demand hours, and occupancy patterns.  
- **Revenue Management:** Track fares, payment types, and zone-based profitability.

**Architecture:**
- Direct cloud connection (OneDrive → Power BI).  
- Star schema for fast querying.  
- Automated refresh and role-based access control.

The interface features interactive filters, maps, and KPIs for intuitive analysis.

---

## Key Reports & Insights
### 1. Executive Summary
- **9 million trips**, generating **$154.91 million** in base fares.  
- **Peak hour:** 6 PM; **busiest day:** Thursday.  
- **Top payment method:** Credit Card (85%).  
- **Highest pickup:** Midtown Center; **Top drop-off:** Upper East Side North.

### 2. Peak Demand
- Ridership peaks **4–6 PM**; strongest demand Thursday–Saturday.  
- Manhattan and parts of Brooklyn are dominant demand clusters.

### 3. Demand Zones
- **Midtown Center** and **Upper East Side North** lead trip volume.  
- January and March saw over 70% of total rides.  
- Short trips (1.2–1.5 miles) generate significant revenue in dense areas.

### 4. Passenger Load
- 11 million passengers served.  
- Higher weekday ridership; late-week and weekends driven by tourism and nightlife.

### 5. Fare & Distance Trends
- Average fare: **$18**; average distance: **3 miles**.  
- Long-distance trips from JFK and Newark yield highest revenue.

### 6. Rate Type Analysis
- **Standard rate:** 8.15 million rides.  
- **Premium fares:** Nassau/Westchester ($134 avg), Newark ($109), JFK ($94).  
- Central Manhattan dominates standard rate trips.

### 7. Payment Method Distribution
- Credit cards (85%), cash (12.6%), disputes (2%).  
- Cash usage higher in Bronx and Queens; disputes linked to longer trips.

---

## Testing & Validation
**Testing Objectives:**
- Validate accuracy, usability, and performance of dashboards.

**Testing Methods:**
1. **Data Validation:** Checked for missing, null, and duplicate values.  
2. **Performance Testing:** Measured visual load times; optimized slow DAX queries.  
3. **Functional Testing:** Verified business alignment with analytical goals.

**Results:**
- 99% data consistency vs. raw source.  
- Load time < 3 seconds per visual.  
- Clear alignment with business objectives.

**Limitations:**
- No integration with real-time or external (weather/event) data.  
- Descriptive analytics only (no predictive modeling).

---

## Optimization & Future Enhancements
To improve performance and analytical depth:
- Integrate **weather, traffic, and event data** for contextual insights.  
- Implement **incremental refresh** and **summary tables** to boost speed.  
- Add **predictive modeling** for demand forecasting.  
- Develop **mobile-responsive dashboards** for on-the-go access.  
- Enable **real-time data streaming** from TLC APIs.

These enhancements will improve decision accuracy, reduce idle driver time, and increase customer satisfaction.

---

## References
- NYC Taxi & Limousine Commission. (n.d.). *TLC Trip Record Data*. [nyc.gov](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page)  
