# 7006SCN – Distributed Machine Learning on NYC Taxi Data

This project implements an end-to-end distributed machine learning pipeline using Apache Spark MLlib to classify high-revenue NYC taxi trips from a large-scale dataset (1.35GB, 80+ million records).

The objective is to evaluate how distributed learning frameworks improve scalability, computational efficiency, and predictive performance compared to traditional single-node machine learning approaches.

🔍 Problem Statement

The task is formulated as a supervised binary classification problem:

  Predict whether a taxi trip qualifies as a high-revenue trip based on operational and temporal trip features.

Key predictive features include:

- Trip distance

- Trip duration

- Passenger count

- Pickup hour

- Derived temporal features (e.g., day-of-week)

The target variable (high_revenue_trip) was engineered using a revenue threshold applied to fare data.

⚙️ Technologies Used

- PySpark (Spark MLlib)

- Apache Spark DataFrames

- CrossValidator for distributed hyperparameter tuning

- Scikit-learn (single-node baseline comparison)

- Parquet columnar storage format

- Tableau Public for business intelligence dashboards

🤖 Models Implemented

Distributed Models (Spark MLlib)

- Logistic Regression

- Gradient Boosted Trees

- Random Forest

Baseline Model (Single-Node)

- Scikit-learn Logistic Regression (trained on a 5% sampled subset)

Tree-based ensemble models were implemented exclusively in Spark to evaluate distributed scalability advantages.

📊 Performance Summary

| Model                              | ROC AUC | PR AUC |
| ---------------------------------- | ------- | ------ |
| Logistic Regression (Spark)        | 0.81    | 0.74   |
| Gradient Boosted Trees (Spark)     | 0.89    | 0.82   |
| Random Forest (Spark)              | 0.91    | 0.84   |
| Logistic Regression (scikit-learn) | 0.87    | 0.79   |

Random Forest achieved the strongest predictive performance on the full 1.35GB dataset, demonstrating the effectiveness of distributed ensemble learning.

📈 Scalability Analysis

Strong scaling experiments were conducted by increasing the number of executors while maintaining a fixed dataset size.

Key findings:

- Distributed execution significantly reduced processing time initially

- Performance gains diminished beyond a resource threshold due to shuffle and coordination overhead

- Ensemble models required greater computational resources but delivered higher predictive accuracy

The project highlights the trade-off between computational cost and predictive performance in distributed ML workflows.

📊 Tableau Dashboards

Four Tableau dashboards were developed to support data storytelling and stakeholder analysis:

- Data Quality & Pipeline Monitoring

- Model Performance Comparison

- Business Insights from Trip Patterns

- Scalability & Cost Trade-offs

Dashboards were built using exported Spark-generated extracts and are available via Tableau Public.

📁 Repository Structure

```
NYC-Taxi-Spark-ML-Classification/
│
├── notebooks/
│   ├── 1_data_ingestion.ipynb
│   ├── 2_feature_engineering.ipynb
│   ├── 3_model_training.ipynb
│   └── 4_evaluation.ipynb
│
├── data/
│   └── samples/
│       └── nyc_taxi_sample.csv
│
├── tableau/
│   ├── NYC_Taxi_Dashboard_1_Data_Quality.twbx
│   ├── NYC_Taxi_Dashboard_2_Model_Performance.twbx
│   ├── NYC_Taxi_Dashboard_3_Business_Insights.twbx
│   └── NYC_Taxi_Dashboard_4_Scalability.twbx
│
├── report/
│   └── 7006SCN_Final_Report.pdf
│
└── README.md
```

Note: The full 1.35GB dataset is not included due to size constraints. A small sample dataset is provided for structural reproducibility.

👤 Author

**Gladstone Cletus Austin D’Souza**  
Student ID: 16676039  
Module: 7006SCN – Machine Learning and Big Data

