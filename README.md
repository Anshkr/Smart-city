# 🌆 Smart City Pollution Intelligence

### An End-to-End Data Engineering and Business Intelligence Project

**Transforming environmental data into actionable insights for smarter, healthier cities.**

---

## 📌 Project Overview

Smart City Pollution Intelligence is an end-to-end data engineering and business intelligence project designed to collect, process, analyze, and visualize air pollution and weather-related data across six major Indian metropolitan cities.

The project integrates environmental data from multiple APIs, processes it using **Azure Databricks**, organizes it through a **Medallion Architecture (Bronze, Silver, and Gold)**, and presents meaningful insights through an interactive **Power BI dashboard**.

The solution helps users explore pollution patterns, compare air quality across cities, identify pollution hotspots, and understand pollutant trends.

### 🌍 Cities Covered

- Delhi
- Mumbai
- Bengaluru
- Chennai
- Kolkata
- Hyderabad

---

## 🎯 Project Objectives

- Collect real-world air quality and weather data from external APIs.
- Build an automated and structured data ingestion workflow.
- Store raw data using Databricks Unity Catalog Volumes.
- Implement Bronze, Silver, and Gold data layers.
- Clean, transform, and organize environmental datasets.
- Develop analytical tables for city-level pollution analysis.
- Build a Databricks Declarative ETL Pipeline.
- Connect processed data to Power BI.
- Create interactive dashboards for pollution monitoring and comparison.

---

## 🏗️ System Architecture

The project follows an end-to-end data pipeline, from external data collection to business intelligence reporting.

```mermaid
flowchart TD
    A["Open-Meteo Air Quality API"]
    B["Open-Meteo Weather API"]
    C["NASA POWER API"]

    A --> D["API Data Extraction"]
    B --> D
    C --> D

    D --> E["Databricks"]
    E --> F["Unity Catalog Volume"]
    F --> G["Bronze Layer"]

    G --> H["Silver Layer"]
    H --> I["Gold Layer"]

    I --> J["Databricks SQL Warehouse"]
    J --> K["Power BI Dashboard"]

    K --> L["City Overview"]
    K --> M["Pollution Hotspots"]
    K --> N["Pollutant Trends"]
```

### 🔄 Data Flow

1. **Data Collection:** Environmental data is retrieved from Open-Meteo and NASA POWER APIs.
2. **Data Ingestion:** Python-based workflows collect and organize the API responses.
3. **Data Storage:** Raw data is stored in Databricks Unity Catalog Volumes.
4. **Bronze Layer:** Raw ingested datasets are maintained in Bronze tables.
5. **Silver Layer:** Data is cleaned, structured, and prepared for analysis.
6. **Gold Layer:** Analytical datasets are created for reporting and visualization.
7. **ETL Pipeline:** A Databricks Declarative ETL Pipeline manages the configured data transformation workflow.
8. **Visualization:** Power BI connects to Databricks SQL Warehouse to display interactive reports.

---

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| Python | API integration and data processing |
| Azure Databricks | Data engineering and processing |
| Databricks Unity Catalog | Data governance and organization |
| Databricks Volumes | Raw data storage |
| Google Drive | Data storage for ingestion |
| Delta Tables | Structured data storage |
| Declarative ETL Pipeline | Data transformation workflow |
| Databricks SQL Warehouse | Analytical data access |
| Power BI Desktop | Dashboard development |
| DAX | Measures and calculations |
| GitHub | Version control and project documentation |

---

## 🌐 Data Sources

The project uses three external environmental data sources.

### 1. Open-Meteo Air Quality API

Provides air pollution measurements for the selected cities.

**Parameters include:**
- PM2.5
- PM10
- Nitrogen Dioxide (NO₂)
- Sulphur Dioxide (SO₂)
- Carbon Monoxide (CO)
- Ozone (O₃)

Documentation: https://open-meteo.com/en/docs/air-quality-api

### 2. Open-Meteo Weather API

Provides weather information to support environmental analysis.

**Parameters include:**
- Temperature
- Relative humidity
- Wind speed
- Precipitation

Documentation: https://open-meteo.com/en/docs

### 3. NASA POWER API

Provides daily environmental and meteorological data for additional analysis.

Documentation: https://power.larc.nasa.gov/

---

## 🧱 Data Engineering: Medallion Architecture

The project uses a three-layer Medallion Architecture to organize data processing.

### 🥉 Bronze Layer — Raw Data

The Bronze layer stores the ingested environmental datasets.

**Tables:**

- `smart_city.pollution.bronze_air_quality`
- `smart_city.pollution.bronze_weather`
- `smart_city.pollution.bronze_nasa_power`

**Purpose:**
- Preserve ingested source data.
- Maintain structured raw datasets.
- Provide a foundation for downstream transformations.

### 🥈 Silver Layer — Cleaned Data

The Silver layer contains processed and structured datasets.

**Pipeline output tables:**

- `smart_city.pollution_etl.silver_air_quality`
- `smart_city.pollution_etl.silver_weather`
- `smart_city.pollution_etl.silver_nasa_power`

**Purpose:**
- Prepare data for analysis.
- Organize environmental measurements.
- Provide structured datasets for analytical processing.

### 🥇 Gold Layer — Analytical Data

The Gold layer contains datasets designed for reporting and business intelligence.

**Pipeline output tables:**

- `smart_city.pollution_etl.gold_city_daily`
- `smart_city.pollution_etl.gold_pollution_hotspots`
- `smart_city.pollution_etl.gold_pollutant_trends`

**Purpose:**
- Support city-level pollution analysis.
- Enable hotspot identification.
- Support pollutant trend visualization.
- Provide analytical data for Power BI.

> **Note:** The project also contains notebook-generated Silver and Gold tables under `smart_city.pollution`. These are separate from the Declarative ETL Pipeline outputs under `smart_city.pollution_etl`.

---

## ⚙️ Databricks Implementation

### Unity Catalog Configuration

The project uses the following Unity Catalog structure:

| Component | Name |
|---|---|
| Catalog | `smart_city` |
| Schema | `pollution` |
| Raw Data Volume | `/Volumes/smart_city/pollution/raw_data` |
| ETL Output Schema | `smart_city.pollution_etl` |

### Declarative ETL Pipeline

**Pipeline Name:** `Smart_city_capstone`

**Pipeline Type:** Ingestion Pipeline

**Output Schema:** `smart_city.pollution_etl`

The pipeline is configured to process environmental datasets and generate Silver and Gold output tables.

The pipeline execution was successfully completed during project implementation.

---

## 📊 Power BI Dashboard

The processed data is connected to Power BI through a Databricks SQL Warehouse.

The dashboard is organized into three interactive pages.

### 1. City Overview

Provides a high-level view of air quality and environmental conditions across the six cities.

**Dashboard elements:**
- Average PM2.5
- Average PM10
- Average temperature
- Average humidity
- Daily PM2.5 trend
- City-wise PM2.5 comparison
- Pollutant comparison
- City and date slicers

### 2. Pollution Hotspots

Focuses on identifying and comparing areas with elevated pollution measurements.

**Dashboard elements:**
- Hotspot average PM2.5
- Hotspot maximum PM2.5
- City-wise pollution comparison
- Hotspot summary table

### 3. Pollutant Trends

Provides a view of pollutant behavior over time.

**Dashboard elements:**
- Pollutant trend line chart
- Pollutant selection slicer
- Average pollutant value
- Time-based trend analysis

### 📷 Dashboard Preview

Add your actual Power BI screenshots below after uploading them to the repository.

| City Overview | Pollution Hotspots |
|---|---|
| Add screenshot here | Add screenshot here |

| Pollutant Trends |
|---|
| Add screenshot here |

---

## 📐 DAX Measures

The Power BI report includes the following DAX measures:

1. Average PM2.5
2. Average PM10
3. Average Temperature
4. Average Humidity
5. Maximum PM2.5
6. Cities Monitored
7. Total Air Quality Readings
8. Average Pollutant Value
9. Hotspot Average PM2.5
10. Hotspot Maximum PM2.5

These measures support KPI cards, comparisons, and analytical visualizations.

---

## 📁 Repository Structure

```text
Smart-City-Pollution-Intelligence/
│
├── README.md
│
├── Databricks/
│   ├── API_Data_Extraction.py
│   ├── Bronze_Layer.py
│   ├── Silver_Layer.py
│   ├── Gold_Layer.py
│   └── Pipeline_Documentation.md
│
├── PowerBI/
│   ├── Smart_City_Dashboard.pbix
│   └── Dashboard_Screenshots/
│       ├── City_Overview.png
│       ├── Pollution_Hotspots.png
│       └── Pollutant_Trends.png
│
├── Presentation/
│   └── Smart_City_Pollution_Intelligence_Presentation.pptx
│
├── Documentation/
│   ├── Project_Report.pdf
│   ├── Architecture.png
│   └── Data_Sources.md
│
└── Screenshots/
    ├── Databricks_Pipeline.png
    ├── Bronze_Tables.png
    ├── Silver_Tables.png
    └── Gold_Tables.png
```

*The filenames above represent the recommended repository organization. Update them to match the actual files uploaded.*

---

## 🚀 How to Explore the Project

### Prerequisites

- Python
- An Azure Databricks workspace
- Access to Databricks Unity Catalog
- Databricks SQL Warehouse access
- Power BI Desktop
- Git and GitHub

### Step 1: Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/Smart-City-Pollution-Intelligence.git
```

### Step 2: Open the Databricks Notebooks

Import the notebooks from the `Databricks/` directory into your Databricks workspace.

Configure the required API parameters and storage locations according to your workspace.

### Step 3: Configure Data Storage

Ensure the Unity Catalog catalog, schema, and volume are available:

```text
Catalog: smart_city
Schema: pollution
Volume: raw_data
```

### Step 4: Execute the Data Workflow

Run the data ingestion and transformation notebooks in the appropriate order.

Review the Bronze, Silver, and Gold datasets after execution.

### Step 5: Review the ETL Pipeline

Open the Databricks Declarative ETL Pipeline named:

```text
Smart_city_capstone
```

Review its execution status, data flow graph, and output tables.

### Step 6: Open the Power BI Dashboard

Open the `.pbix` file from the `PowerBI/` directory.

Configure the Databricks connection and required credentials to access the analytical datasets.

---

## 📈 Project Outcomes

The project demonstrates an end-to-end implementation of an environmental data analytics workflow.

Key deliverables include:

- Integration of three environmental data sources.
- Coverage of six major Indian cities.
- Databricks-based data ingestion and processing.
- Unity Catalog-based data organization.
- Bronze, Silver, and Gold data layers.
- A Databricks Declarative ETL Pipeline.
- Analytical Gold datasets for pollution reporting.
- Ten Power BI DAX measures.
- Three interactive Power BI dashboard pages.

---

## ⚠️ Limitations

- The analysis depends on the availability and quality of external API data.
- Data coverage may vary depending on API availability and selected locations.
- Environmental measurements should be interpreted with their source, units, timestamps, and measurement context.
- The dashboard provides analytical insights and is not a substitute for official regulatory air-quality monitoring.
- Actual pollution rankings and conclusions should be based on validated data from the executed datasets.

---

## 🔮 Future Enhancements

Potential improvements include:

- Adding real-time or scheduled data ingestion.
- Expanding coverage to additional Indian cities.
- Implementing automated data quality checks.
- Adding historical pollution comparisons.
- Integrating official monitoring station datasets.
- Developing pollution forecasting models.
- Adding geographical pollution maps.
- Implementing automated alerts for elevated pollution levels.
- Improving pipeline monitoring and error handling.

---

## 👥 Team

**Project:** Smart City Pollution Intelligence

**Team Size:** 3 Members

This project combines data engineering, environmental data analysis, and business intelligence to demonstrate how cloud-based data platforms can support smarter environmental monitoring.

**Lead:** Ansh Kumar

---

## 📚 References

- Open-Meteo Air Quality API: https://open-meteo.com/en/docs/air-quality-api
- Open-Meteo Weather API: https://open-meteo.com/en/docs
- NASA POWER: https://power.larc.nasa.gov/
- Databricks Documentation: https://docs.databricks.com/
- Microsoft Power BI Documentation: https://learn.microsoft.com/en-us/power-bi/

---

## ⭐ Acknowledgement

This project was developed as an academic capstone project to demonstrate practical applications of data engineering, cloud data processing, and business intelligence in environmental monitoring.

**Smart City Pollution Intelligence — Turning Environmental Data into Meaningful Insights.**
