# 🚲 Predicting Bike Sharing Demand with AutoGluon

This project uses AutoGluon, an open-source AutoML library, to predict bike-sharing demand for the Kaggle Bike Sharing Demand competition. The goal is to train and optimize multiple models for accurate demand forecasting using tabular data from CSV files.

Bike-sharing demand prediction has real-world applications in optimizing transportation services like Uber, Lyft, and DoorDash, helping improve service availability and reduce delays.

## 📘 Project Overview

In this project, I applied AutoGluon’s Tabular Prediction module to build and optimize machine learning models that predict hourly bike rental counts.

The workflow involved:

- Conducting exploratory data analysis (EDA) to uncover demand patterns.
- Feature engineering to extract meaningful predictors (e.g., hour, month, weather).
- Model training and hyperparameter tuning using AutoGluon.
- Submitting results to Kaggle and tracking score improvements across multiple iterations.

## 🧠 Key Steps
🔹 Initial Training

When I first submitted predictions, I realized that Kaggle rejected files with negative prediction values and required submissions to follow a strict format with only two columns:
datetime and count.

The top-performing model was a WeightedEnsemble_L3, which combined several base learners (LightGBM, CatBoost, and Neural Networks) for improved accuracy.

🔹 Exploratory Data Analysis (EDA) & Feature Creation

- Through EDA, I discovered that:
- Seasonality did not drastically affect demand.
- Working days and holidays showed clear patterns — lower usage on holidays and higher on workdays.
- Weather conditions strongly influenced demand — clear skies led to higher usage, while rain reduced it.
- Temperature extremes (0°C or 40°C) led to minimal usage, while moderate temperatures encouraged it.

Feature Engineering:

- Extracted day, month, and hour from the datetime column using .dt.
- Converted categorical columns like season and weather to the category data type.

✅ Result: After adding new features, model performance improved by ≈66% (lower RMSE).

🔹 Hyperparameter Tuning

Fine-tuning hyperparameters (e.g., learning_rate, num_boost_round, num_epochs) improved model accuracy by an additional ≈17%.

If given more time, I would explore feature interactions, such as:

- weather × hour (e.g., effect of rain during commute hours).
- holiday × weekday (e.g., reduced weekday demand during public holidays).

## 📊 Model Performance
|Model |	HPO 1 |	HPO 2|	HPO 3|	Kaggle Score (RMSE)|
|--|--|--|--|--|
|Initial|	default	|default	|default|	1.79907|
|Add Features	|default	|default	|default|	0.60243|
|Tuned (HPO)	|learning_rate: 0.05	|num_boost_round: 100	|num_epochs: 10	|0.50390|

## 📈 Visualizations
Model Training Scores
![model_train_score.png](model_train_score.png)

Kaggle Submission Scores
![model_test_score.png](model_test_score.png)

## 🧩 Technologies Used
- Python 3
- AutoGluon
- Pandas, NumPy
- Matplotlib, Seaborn
- Jupyter Notebook
- Kaggle API

## 🏁 Summary

In this project, I used AutoGluon to predict bike-sharing demand.
The initial ensemble provided strong baseline results, which were significantly improved through feature engineering and hyperparameter optimization.
This project demonstrates how AutoML can efficiently produce competitive models for real-world forecasting problems while maintaining interpretability and reproducibility.