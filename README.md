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

👉 **[Click here to view the Live Interactive Dashboard on Tableau Public](https://public.tableau.com/authoring/DeloitteVirtualInternship-TelemetryAnalysis/Mydashboard#2)**

### Key Visuals Included:
* **Down Time per Factory:** Столбчатая диаграмма, показывающая, что завод `daikibo-factory-seiko` страдает от самых серьезных операционных простоев.
* **Failure Rate by Device Type:** График (например, древовидная карта или bar chart), который четко подсвечивает наиболее склонные к поломкам типы устройств.
* **Downtime Trends Over Time:** Линейный график для отслеживания динамики сбоев во времени и выявления пиковых периодов нагрузки.

## 💡 Key Insights & Business Impact
* **Главный источник проблем:** Завод `daikibo-factory-seiko` лидирует по количеству статусов «Unhealthy», что напрямую генерирует самые высокие операционные убытки из-за простоев оборудования.
* **Критически уязвимые узлы:** Определенные типы устройств показывают аномально высокую частоту отказов по сравнению с остальным парком оборудования.
* **Переход к Data-Driven решениям:** Трансформация сырых JSON-логов в интерактивную модель Tableau позволила руководству сократить время поиска первопричины сбоя (Root-Cause Analysis) с нескольких часов до пары кликов.

## 🚀 Strategic Recommendations
1. **Превентивное обслуживание:** Внедрить регламент прогнозного ТО для типов устройств с высокой частотой отказов, чтобы предотвращать сбои до накопления критических 10-минутных простоев.
2. **Аудит на заводе Seiko:** Инициировать детальную проверку условий эксплуатации оборудования на объекте `daikibo-factory-seiko` для выявления локальных причин повышенного износа.
3. **Автоматизация дата-конвейера:** Перенести текущий ETL-процесс из Excel/Power Query в облачную базу данных (например, AWS или Azure) для настройки автоматического обновления Tableau-дашборда в режиме реального времени.
