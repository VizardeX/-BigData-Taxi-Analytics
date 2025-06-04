# BigData-Taxi-Analytics

## Overview
This project explores and analyzes New York City taxi trip data using big data tools and machine learning techniques. It focuses on deriving insights from trip-level data and predicting the likelihood of high tips using Spark and NoSQL-based processing. The project integrates trip records with geographic metadata and leverages Spark SQL, DataFrame APIs, and SparkML pipelines.

## Objectives
- Clean and transform raw taxi trip and zone datasets
- Execute Spark-based analytical queries for business insights
- Engineer features relevant to tipping behavior
- Build and evaluate machine learning models to classify high-tip trips

## Dataset
- `taxi_trip_data.csv`: Contains ride details such as fare, tip, timestamps, location IDs, and passenger info
- `taxi_zone_geo.csv`: Maps location IDs to NYC zone names and boroughs

## Dataset Access

Due to file size limitations, the datasets are hosted externally on Google Drive.

🔗 [Download CSV Files](https://drive.google.com/drive/folders/1GkYSp48BCZ26heLnc2XIxq5BlboRf1zG?usp=sharing)

> This folder contains both `taxi_trip_data.csv` and `taxi_zone_geo.csv`.  

## Key Components

### Data Preprocessing
- Converted pickup and dropoff timestamps to datetime format
- Calculated `trip_duration_minutes` from timestamps
- Computed `total_trip_cost` by summing fare, tax, tips, tolls, and extras
- Merged trip data with geographic zone information

### Analytical Queries (Spark SQL & DataFrame API)
- Most common payment types segmented by time of day (morning, afternoon, evening)
- Boroughs with highest revenue vs. trip volume (pickup-based)
- Average tip amount by passenger count
- Top 5 pickup zones by frequency and efficiency
- Longest trips by duration, including anomalies in cost vs. time
- Most frequent inter-borough travel patterns

### Machine Learning with SparkML
- Created a binary label `high_tip` (1 if tip > 15% of fare)
- Feature engineering: trip duration, passenger count, pickup/dropoff location, total cost, hour of day
- Models used:
  - Logistic Regression
  - Decision Tree Classifier
  - Random Forest Classifier
- Evaluation: Accuracy, confusion matrix, classification report, feature importance

## Technologies Used
- Apache Spark (PySpark)
- Spark SQL and DataFrame API
- Spark MLlib (classification pipelines)
- Google Colab / Jupyter Notebook
- Python libraries: pandas, matplotlib, seaborn

