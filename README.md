# Smart-city-Data-Monitoring
##  Project Overview

A **Smart City Simulation System** that processes real-time IoT sensor data across three key urban domains:

- 🚦 **Traffic Monitoring**
- 🌫️ **Air Quality Monitoring**
- ⚡ **Energy Usage Monitoring**

The system collects, cleans, analyzes, and visualizes sensor data to help city planners and administrators make data-driven decisions.

---

## 🎯 Key Features

- ✅ Multi-source IoT sensor data simulation and ingestion
- ✅ Data cleaning — handles missing values and outliers using Pandas
- ✅ Time-series plots, heatmaps, and correlation matrices using Matplotlib & Seaborn
- ✅ SQL-based reporting on 500+ sensor records
- ✅ Anomaly detection (5+ anomaly types) using NumPy statistical methods
- ✅ Interactive Power BI dashboards for city-wide trend visualization

---

## 🛠️ Tech Stack

| Category | Tools |
|---|---|
| Language | Python 3.8+ |
| Data Processing | Pandas, NumPy |
| Visualization | Matplotlib, Seaborn |
| Database | SQL (SQLite / PostgreSQL) |
| Dashboard | Power BI |

---

## 📂 Project Structure

```
smart-city-iot/
│
├── data/
│   ├── raw/                  # Raw sensor data (CSV/JSON)
│   ├── processed/            # Cleaned and processed data
│   └── sql/                  # SQL scripts and queries
│
├── notebooks/
│   ├── 01_data_cleaning.ipynb
│   ├── 02_eda_visualization.ipynb
│   └── 03_anomaly_detection.ipynb
│
├── src/
│   ├── sensor_simulator.py   # IoT sensor data simulation
│   ├── data_cleaning.py      # Missing value & outlier handling
│   ├── visualization.py      # Plots and heatmaps
│   ├── anomaly_detection.py  # NumPy-based anomaly detection
│   └── sql_queries.py        # SQL query execution
│
├── powerbi/
│   └── smart_city_dashboard.pbix
│
├── requirements.txt
└── README.md
```

---

## 🌫️ Sensors & Data Domains

### Air Quality Sensors
| Parameter | Description |
|---|---|
| PM2.5 | Fine particulate matter |
| PM10 | Coarse particulate matter |
| NO2 | Nitrogen Dioxide |
| O3 | Ozone |
| CO | Carbon Monoxide |
| AQI | Air Quality Index |
| Index Category | Good / Moderate / Unhealthy / Very Unhealthy / Hazardous |

### Traffic Sensors
- Vehicle count, speed, congestion level, road occupancy

### Energy Sensors
- Power consumption (kWh), peak load, usage category

---

## 📊 Visualizations

- 📈 **Time-Series Plots** — Sensor readings over time
- 🌡️ **Heatmaps** — Spatial and temporal patterns across city zones
- 🔗 **Correlation Matrix** — Relationships between pollution, traffic, and energy metrics
- 📉 **Anomaly Highlights** — Visual flagging of detected anomalies

---

## 🗄️ SQL Highlights

```sql
-- Example: Top 10 sensors with highest AQI readings
SELECT sensor_id, AVG(aqi) AS avg_aqi, MAX(aqi) AS max_aqi
FROM air_quality
GROUP BY sensor_id
ORDER BY avg_aqi DESC
LIMIT 10;
```

- Designed queries to extract and report on **500+ sensor records**
- Aggregations, filtering, and trend extraction across all three domains

---

## 🔍 Anomaly Detection

Using **NumPy statistical analysis**, the system detects:

1. 🚨 AQI spikes beyond threshold (> 200)
2. ⚡ Sudden energy consumption surges
3. 🚦 Abnormal traffic congestion patterns
4. 🌡️ Sensor dropouts (null/zero readings)
5. 📉 Negative or out-of-range sensor values

```python
# Z-score based anomaly detection example
z_scores = np.abs((data - data.mean()) / data.std())
anomalies = data[z_scores > 3]
```

---

## 🚀 Getting Started

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/smart-city-iot.git
cd smart-city-iot
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Run the Sensor Simulator
```bash
python src/sensor_simulator.py
```

### 4. Run Analysis Notebooks
```bash
jupyter notebook notebooks/
```
---

form air_quality
{
	displayname = "Air Quality"
	success message = "Data Added Successfully!"
	Section
	(
		type = section
	 	row = 1
	 	column = 0   
		width = medium
	)
	sensor
	(
		type = list	
		displayname = "Sensor"
		values  = sensors.ID
    	displayformat = [sensor_id]
		allow new entries
		[
			displayname = "Add New"
		]
		sortorder = ascending
		height = 13px
	 	row = 1
	 	column = 1   
		width = medium
	)
	pm25
	(
		type = decimal
		displayname = "PM2.5"
		maxchar = 16
	 	row = 1
	 	column = 1   
		width = medium
	)
	pm10
	(
		type = decimal
		displayname = "PM10"
		maxchar = 16
	 	row = 1
	 	column = 1   
		width = medium
	)
	no2
	(
		type = decimal
		displayname = "NO2"
		maxchar = 16
	 	row = 1
	 	column = 1   
		width = medium
	)
	o3
	(
		type = decimal
		displayname = "O3"
		maxchar = 16
	 	row = 1
	 	column = 1   
		width = medium
	)
	co
	(
		type = decimal
		displayname = "CO"
		maxchar = 16
	 	row = 1
	 	column = 1   
		width = medium
	)
	aqi
	(
		type = number
		displayname = "AQI"
		maxchar = 19
	 	row = 1
	 	column = 1   
		width = medium
	)
	index_category
	(
		type = picklist
		displayname = "Index Category"
		values = {"Very Unhealthy","Unhealthy","Moderate","Good","Hazardous"}
		others option = true
	 	row = 1
	 	column = 1   
		width = medium
	)
	recorded_at
	(
    	type = datetime
		displayname = "Recorded At"
		timedisplayoptions = "hh:mm:ss"
		alloweddays = 0,1,2,3,4,5,6
	 	row = 1
	 	column = 1   
		width = medium
	)
	
	actions
	{
		on add
		{
			submit
			(
   				type = submit
   				displayname = "Submit"
			)
			reset
			(
   				type = reset
   				displayname = "Reset"
			)
		}
		on edit
		{
			update
			(
   				type = submit
   				displayname = "Update"
			)
			cancel
			(
   				type = cancel
   				displayname = "Cancel"
			)
		}
	}
}

## 📦 Requirements

```
pandas
numpy
matplotlib
seaborn
jupyter
sqlalchemy
faker
```

---

## 📈 Sample Output

```
✅ Loaded 500 sensor records
✅ Missing values handled: 12 records imputed
✅ Outliers detected: 8 records flagged
✅ Anomalies found: 23 events across 5 categories
✅ Visualizations saved to /output/plots/
```

---

##  Author:
VIDYA SHREE L
- 🔗 https://www.linkedin.com/in/vidya-shree-l-7b142327b?utm_source=share_via&utm_content=profile&utm_medium=member_android 
- 💻 https://github.com/Vidyashree-L
---
