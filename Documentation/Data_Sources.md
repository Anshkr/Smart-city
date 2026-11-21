# Data Sources – Smart City Pollution Intelligence

## 1. Overview

The Smart City Pollution Intelligence project uses three external data sources to collect air-quality and weather-related information for six major Indian cities.

The collected data is ingested and processed using Databricks and is later used for analysis and visualization in Power BI.

## 2. Data Sources Used

### 2.1 Open-Meteo Air Quality API

**Source:** [Open-Meteo Air Quality API](https://open-meteo.com/en/docs/air-quality-api)

**Purpose:** To collect air-quality and pollutant information for the selected cities.

**Data fields used:**
- PM2.5 – Fine particulate matter
- PM10 – Particulate matter
- NO2 – Nitrogen dioxide
- SO2 – Sulphur dioxide
- CO – Carbon monoxide
- Ozone – Ozone concentration

**Usage in the project:**

The API provides air-quality information that is ingested into Databricks and stored in the Bronze layer for further processing and analysis.

### 2.2 Open-Meteo Weather API

**Source:** [Open-Meteo Weather API](https://open-meteo.com/en/docs)

**Purpose:** To collect weather information for the selected cities.

**Data fields used:**
- Temperature
- Relative humidity
- Wind speed
- Precipitation

**Usage in the project:**

Weather data is collected and stored in Databricks. It is processed alongside air-quality data to support combined environmental analysis.

### 2.3 NASA POWER API

**Source:** [NASA POWER](https://power.larc.nasa.gov/)

**Purpose:** To obtain daily weather-related environmental data.

**Usage in the project:**

NASA POWER data is ingested into Databricks and stored in the Bronze layer. It is used as an additional source for weather-related analysis.

## 3. Cities Covered

The project covers the following six Indian cities:

| No. | City | State |
|---|---|---|
| 1 | Delhi | Delhi |
| 2 | Mumbai | Maharashtra |
| 3 | Bengaluru | Karnataka |
| 4 | Chennai | Tamil Nadu |
| 5 | Kolkata | West Bengal |
| 6 | Hyderabad | Telangana |

## 4. Data Collection and Processing

The project follows this data workflow:

1. Collect data from the external APIs.
2. Ingest the collected data into the Databricks environment.
3. Store the original ingested data in the Bronze layer.
4. Clean and organize the data in the Silver layer.
5. Prepare analytical datasets in the Gold layer.
6. Connect the processed data to Power BI for visualization.

## 5. Data Storage

The project uses Databricks Unity Catalog.

**Catalog:** `smart_city`

**Schema:** `pollution`

**Raw Data Volume:**

`/Volumes/smart_city/pollution/raw_data`

### Bronze Tables

- `bronze_air_quality`
- `bronze_weather`
- `bronze_nasa_power`

## 6. Data Usage in Power BI

The processed data is used to develop three dashboard pages:

1. **City Overview** – Displays city-level pollution and weather indicators.
2. **Pollution Hotspots** – Supports comparison of pollution levels across cities.
3. **Pollutant Trends** – Displays pollutant trends over time.

## 7. Data Source References

- Open-Meteo Air Quality API: https://open-meteo.com/en/docs/air-quality-api
- Open-Meteo Weather API: https://open-meteo.com/en/docs
- NASA POWER: https://power.larc.nasa.gov/

## 8. Notes

- The project uses six selected Indian cities.
- Data availability and time coverage depend on the API requests and extraction configuration.
- API credentials or private access tokens must never be committed to the GitHub repository.
- The actual date range, refresh frequency, and record counts should be added after checking the ingested Databricks tables.