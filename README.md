# Industrial Telemetry & Machine Downtime Analysis (Deloitte Virtual Case Study)

## 📌 Project Overview
This repository contains my solution for the Deloitte Australia Data Analytics virtual experience on The Forage. The goal of this project was to analyze raw industrial machine telemetry data, identify operational bottlenecks, and translate technical engineering logs into actionable Business Intelligence (BI) metrics for management.

## 🛠️ Tech Stack & Tools Used
* **Data Processing & ETL:** Microsoft Excel (Power Query)
* **Data Visualization & BI:** Tableau Public
* **File Format Transformation:** JSON to CSV/XLSX structural flattening

## 📉 Business Problem & Objectives
The production facility generates massive streams of nested telemetry data. Management needed a way to:
1. Monitor machine health and track potential downtime across different factories.
2. Identify which specific device types are the most failure-prone.
3. Enable root-cause analysis through interactive data filtering.

*Note: For every "Unhealthy" status recorded, 10 minutes of potential downtime was calculated.*

## ⚙️ Data Pipeline & Methodology
1. **ETL Process:** Imported raw `daikibo-telemetry-data.json` into Excel via Power Query. Used the `To Table` feature and expanded deeply nested columns (`location` and `data` fields) to uncover raw device logs and machine statuses.
2. **Calculated Measures:** Created a custom field `[Unhealthy]` using the following logic:
   `IF [Status] = 'Unhealthy' THEN 10 ELSE 0 END`
3. **Data Modeling:** Loaded the flattened dataset into Tableau Public for dashboard engineering.

## 📊 Live Interactive Dashboard
I have built and published a fully interactive BI Dashboard. 

👉 **[Click here to view the Live Interactive Dashboard on Tableau Public](https://public.tableau.com/authoring/DeloitteVirtualInternship-TelemetryAnalysis/Mydashboard#1)**

### Key Visuals Included:
* **Down Time per Factory:** A bar chart identifying that `daikibo-factory-seiko` suffers the most significant operational losses (480 minutes of potential downtime).
* **Down Time per Device Type:** A sorted bar chart highlighting failure-prone assets (e.g., LaserCutter and LaserWelder).
* **Interactive Filtering:** Implemented a global action filter—clicking on any factory automatically filters the machine performance layout below.

---
*Disclaimer: This project was completed as part of a simulated virtual experience with Deloitte AU and uses mock industrial telemetry data.*
