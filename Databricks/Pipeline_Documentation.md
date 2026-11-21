# Databricks Pipeline Documentation

## 1. Project Overview

The **Smart City Pollution Intelligence** project collects air quality and weather data for six major Indian cities and processes it using Databricks. The objective is to organize pollution data, identify pollution hotspots, and analyze pollutant trends.

The project uses the Medallion Architecture, consisting of Bronze, Silver, and Gold layers.

## 2. Technologies Used

- Databricks
- Python
- Apache Spark
- PySpark
- Unity Catalog
- Open-Meteo Air Quality API
- Open-Meteo Weather API
- NASA POWER API
- Power BI

## 3. Data Sources

The project uses three external data sources:

| Data Source | Data Collected |
|---|---|
| Open-Meteo Air Quality API | PM2.5, PM10, NO2, SO2, CO, Ozone |
| Open-Meteo Weather API | Temperature, humidity, wind speed, precipitation |
| NASA POWER API | Daily weather-related data |

### Cities Covered

1. Delhi
2. Mumbai
3. Bengaluru
4. Chennai
5. Kolkata
6. Hyderabad

## 4. Unity Catalog Structure

The project uses Unity Catalog to organize and manage data.

**Catalog:** `smart_city`

**Schema:** `pollution`

**Raw Data Volume:**

`/Volumes/smart_city/pollution/raw_data`

The raw data is stored and processed through Databricks notebooks and pipelines.

## 5. Medallion Architecture

### Bronze Layer – Raw Data

The Bronze layer stores the ingested source data.

Tables:

- `smart_city.pollution.bronze_air_quality`
- `smart_city.pollution.bronze_weather`
- `smart_city.pollution.bronze_nasa_power`

Purpose:
- Store source data.
- Maintain the initial ingested records.
- Provide input for further processing.

### Silver Layer – Cleaned Data

The Silver layer contains processed and structured data.

Purpose:
- Clean and organize the source data.
- Prepare data for analysis.
- Maintain structured datasets for downstream processing.

### Gold Layer – Analytical Data

The Gold layer contains data prepared for reporting and analysis.

The project creates the following analytical tables:

- `gold_city_daily` – Daily city-level pollution data.
- `gold_pollution_hotspots` – Data used to analyze pollution hotspots.
- `gold_pollutant_trends` – Data used to analyze pollutant trends.

## 6. Declarative ETL Pipeline

The project also uses a Databricks Declarative ETL pipeline.

**Pipeline Name:** `Smart_city_capstone`

**Pipeline Type:** Ingestion Pipeline

**Pipeline Output Schema:** `smart_city.pollution_etl`

The pipeline contains the following output tables:

### Silver Tables

- `silver_air_quality`
- `silver_weather`
- `silver_nasa_power`

### Gold Tables

- `gold_city_daily`
- `gold_pollution_hotspots`
- `gold_pollutant_trends`

The pipeline organizes the processing workflow and produces structured tables for analytical use.

## 7. Pipeline Execution

The Databricks pipeline was executed successfully.

The pipeline interface was used to monitor its execution status and view the processing workflow.

**Execution Status:** Completed

A screenshot of the successful pipeline execution is included in the project repository.

## 8. Power BI Integration

The processed Gold-layer data is used in Power BI to create interactive dashboards.

The dashboard contains three main pages:

1. **City Overview** – Displays pollution and weather indicators across the selected cities.
2. **Pollution Hotspots** – Supports analysis of cities with higher pollution levels.
3. **Pollutant Trends** – Displays pollutant trends for analytical comparison.

Power BI connects to the Databricks SQL Warehouse to access the processed data.

## 9. Project Outcome

The project demonstrates an end-to-end data engineering and analytics workflow using external APIs, Databricks, Unity Catalog, Medallion Architecture, Declarative ETL, and Power BI.

It provides a structured approach to collecting, processing, and analyzing urban air quality and weather data.

## 10. Repository Notes

- Do not upload API keys, passwords, or access tokens.
- Do not include private connection strings.
- Add screenshots of the actual pipeline execution and table previews.
- Keep notebook names and table names consistent with the implementation.