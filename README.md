# BigData-Taxi-Analytics

## Overview
This project analyzes New York City taxi trip data with **Apache Spark** to derive business insights and predict high-tip trips. It integrates trip records with geographic zone metadata and leverages **Spark SQL**, **DataFrame APIs**, and **Spark MLlib** pipelines for large-scale preprocessing, analytics, and classification.

## Objectives
- Clean and transform raw taxi trip and zone datasets
- Execute Spark-based analytical queries for business insights
- Engineer features relevant to tipping behavior
- Build and evaluate machine learning models to classify high-tip trips

## Dataset
- `taxi_trip_data.csv`: ride details such as fare, tip, timestamps, location IDs, and passenger info
- `taxi_zone_geo.csv`: maps location IDs to NYC zone names and boroughs

## Dataset Access
Due to file size limitations, the datasets are hosted externally on Google Drive.

🔗 [Download CSV Files](https://drive.google.com/drive/folders/1GkYSp48BCZ26heLnc2XIxq5BlboRf1zG?usp=sharing)

> This folder contains both `taxi_trip_data.csv` and `taxi_zone_geo.csv`.

## Key Components

### Data Preprocessing
- Converted pickup and dropoff timestamps to datetime format
- Calculated **`trip_duration_minutes`** from timestamps
- Computed **`total_trip_cost`** (fare + taxes + tips + tolls + extras)
- Joined trip data with **pickup** and **dropoff** geographic zone/borough information
- Derived features used for analytics & ML (e.g., **hour**, **time_of_day**, encoded boroughs/locations)
- **Applied data quality filters** (e.g., removing implausible records: very long trips, non-positive fares, etc.)

### Analytical Queries (Spark SQL & DataFrame API)
- Boroughs with **highest revenue vs. trip volume** (pickup-based)
- **Average tip amount** by passenger count
- **Top 5 pickup zones** by trip frequency
- **Longest trips** by duration, and checks for **cost vs. time anomalies**
- **Inter-borough travel patterns** (pickup to dropoff flows)
- **Purchase-time patterns** (hour/time-of-day analyses)

### Machine Learning with Spark MLlib
- **Label:** `high_tip = 1` if tip > **15% of fare**, else `0`
- **Features:** trip duration, passenger count, pickup/dropoff borough/location encodings, total cost, hour/time-of-day, and other derived fields
- **Models:**
  - Logistic Regression
  - Decision Tree Classifier
  - Random Forest Classifier
  - **Gradient-Boosted Trees (GBT)**
- **Training details:**
  - **Class weighting** applied to address label imbalance
- **Evaluation metrics:**
  - **AUC**, **Accuracy**, **Precision**, **Recall**, **F1**
  - **Feature importance** (tree-based models)

## Technologies Used
- **Apache Spark (PySpark)**
- **Spark SQL** and **DataFrame API**
- **Spark MLlib** (classification pipelines)
- Google Colab / Jupyter Notebook
- Python
