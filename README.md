# Fashion Demand Forecasting: Seasonal Retail Model Benchmarking

## Table of Contents
- Executive Summary  
- Business Context  
- Modeling Framework  
- Data Description  
- Model Comparison  
- Visual Diagnostics  
- Deployment Recommendation  
- Limitations  
- Tech Stack  
- Skills Demonstrated  
- Why This Project Matters  
- How to Run  

---

# Executive Summary

This project evaluates forecasting approaches for monthly seasonal retail demand across three product categories: Swimwear, Knitwear, and Jersey Fancy.

Key findings:

- Retail demand is strongly driven by repeat annual seasonality.
- Simple seasonal baselines are highly competitive.
- Model complexity does not guarantee improved accuracy.
- Forecast error ranges from ~9% in stable categories to ~32% in highly volatile categories.
- Model performance is category-dependent.

For short seasonal retail time series, stability and interpretability often outperform algorithmic complexity.

---

# Business Context

Retail inventory allocation depends heavily on reliable short-term forecasts.  

Poor forecasting can result in:

- Overstock and increased holding costs  
- Stockouts and lost sales  
- Margin erosion due to markdowns  

The objective of this project was to determine whether increasingly sophisticated models provide meaningful performance improvement over simple seasonal benchmarks for monthly demand forecasting.

---

# Modeling Framework

The project follows a structured benchmarking approach:

1. Data cleaning and monthly aggregation  
2. Baseline forecasting models  
3. Linear regression with lag features (Ridge)  
4. Nonlinear machine learning (Random Forest)  
5. Classical time-series modeling (SARIMA)  
6. Evaluation using MAE and RMSE  
7. Joint ranking and scale-adjusted error analysis  

Models were compared within each category using both absolute error metrics and error as a percentage of average demand.

---

# Data Description

Dataset: H&M Personalized Fashion Recommendations (Kaggle)

Transaction-level data was aggregated to monthly unit demand at the product category level.

Categories analyzed:

- Swimwear (high volatility)
- Knitwear (moderate seasonality)
- Jersey Fancy (stable seasonal structure)

Time horizon: ~24 months of historical data.

---

# Model Comparison

Models evaluated:

| Model | Type |
|-------|------|
| Naive | Last observed value |
| Seasonal Naive | Same month previous year |
| Moving Average | Windowed smoothing |
| Ridge Regression | Linear model with lag features |
| Random Forest | Nonlinear tree-based model |
| SARIMA | Classical seasonal time-series |

Evaluation metrics:

- Mean Absolute Error (MAE)  
- Root Mean Squared Error (RMSE)  
- Error as % of average monthly demand  
- Joint ranking across MAE and RMSE  

---

# Visual Diagnostics

The following visual analyses were used to evaluate performance:

- Seasonal demand patterns by category  
- Actual vs forecast overlays  
- Model error comparison  
- Ranking summary across models  

(Visuals embedded below.)

---

# Final Model Selection

Based on joint MAE and RMSE ranking:

| Category | Recommended Model |
|----------|------------------|
| Swimwear | Seasonal Naive |
| Knitwear | SARIMA |
| Jersey Fancy | SARIMA |

Findings:

- Seasonal Naive performs best in volatile demand environments.
- SARIMA performs strongest in smoother seasonal categories.
- Random Forest does not deliver consistent improvements.
- Ridge remains competitive but does not dominate in joint ranking.

---

# Deployment Recommendation

For production implementation:

1. Use Seasonal Naive as a benchmark baseline.
2. Deploy SARIMA for smoother seasonal series.
3. Avoid high-variance nonlinear models unless historical depth increases.
4. Incorporate external drivers (price, promotions, weather) before increasing model complexity.

---

# Limitations

- Limited historical depth (~24 months) constrains seasonal parameter estimation.
- Models trained independently by category.
- No external explanatory variables included.
- Single validation split (not rolling cross-validation).

---

# Tech Stack

- Python  
- pandas  
- numpy  
- scikit-learn  
- statsmodels  
- matplotlib  

---

# Skills Demonstrated

- Time-series forecasting  
- Model benchmarking  
- Feature engineering  
- Error metric evaluation  
- Comparative model ranking  
- Business-oriented interpretation  
- Operational recommendation design  

---

# Why This Project Matters

This project demonstrates structured model comparison in a real-world retail forecasting context.

Rather than assuming complex models outperform simple baselines, the analysis evaluates trade-offs between accuracy, stability, and operational practicality.

It highlights the importance of aligning model sophistication with data structure and business needs.

---

# How to Run

1. Clone the repository  
2. Install dependencies
3. Download the H&M dataset from Kaggle  
4. Place files in the `data/` directory  
5. Open and run `FashionDemandForecast.ipynb` from top to bottom  
