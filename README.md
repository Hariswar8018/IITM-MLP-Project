# Cinema Audience Forecasting Challenge 🎬📊

## Project Overview

This project tackles the **Cinema Audience Forecasting Challenge**, a time series prediction competition aimed at forecasting daily theatre audience counts across multiple locations. The goal is to predict the `target` variable (daily audience count) for different `book_theater_id` entities using historical data.

### Competition Details
- **Host**: IITM BS CS 2008P
- **Metric**: RMSE (Root Mean Square Error)
- **Duration**: Sep 15, 2025 - Nov 30, 2025
- **Participants**: 2,982 entrants, 2,632 teams

---

## Abstract

Cinema audience prediction presents a complex time series forecasting challenge due to multiple factors including location-specific patterns, temporal trends, and external influences. This project explores various machine learning approaches—from simple baseline models to advanced ensemble methods—to accurately predict daily theatre attendance.

Our methodology evolved through several stages:

1. **Initial Exploration with Simple Models**: We began with baseline models and traditional machine learning algorithms to establish performance benchmarks. Initial experiments yielded baseline RMSE scores that highlighted the complexity of the problem.

2. **Feature Engineering Attempts**: We experimented with time series features including:
   - Rolling statistics (moving averages, standard deviations)
   - Exponential Moving Averages (EMA)
   - Lag features
   
   However, these traditional time series features showed limited improvement in initial trials.

3. **Classical Time Series Models - Limitations**: We evaluated ARIMA and SARIMA models but encountered significant challenges:
   - The dataset contains multiple independent time series (one per `book_theater_id`)
   - Each theatre location exhibits unique patterns and seasonality
   - ARIMA/SARIMA require fitting separate models for each entity, leading to computational complexity and scalability issues
   - Individual model tuning for hundreds of theatre IDs proved impractical

4. **Ensemble Methods Breakthrough**: Transitioning to ensemble approaches, particularly:
   - **Bagging Models**: Random Forest and other bagging-based regressors
   - **Boosting Models**: Gradient Boosting variants, with emphasis on XGBoost
   
5. **Final Solution - XGBoost Regressor**: Our breakthrough came with **XGBoost Regressor**, which successfully:
   - Captured non-linear relationships in the data
   - Handled multiple theatre IDs simultaneously
   - Incorporated temporal patterns without explicit feature engineering
   - Achieved performance metrics that exceeded the competition cutoff
   - Delivered competitive public leaderboard scores

---

## Technical Approach

### Data Characteristics
- **Type**: Time series data with multiple entities
- **Target**: Daily audience count
- **Key Challenge**: Multiple independent time series (`book_theater_id`)

### Model Progression

#### Phase 1: Baseline Models
- Simple statistical models
- Basic regression techniques
- Established initial RMSE benchmarks

#### Phase 2: Feature Engineering
- Rolling window statistics
- Exponential Moving Averages (EMA)
- Lag features for temporal dependencies

#### Phase 3: Classical Time Series (Attempted)
- **ARIMA/SARIMA**: Ruled out due to:
  - Multiple independent time series per theatre
  - Computational complexity for individual model fitting
  - Difficulty in hyperparameter tuning across entities

#### Phase 4: Ensemble Methods
- **Bagging**: Random Forest and ensemble variants
- **Boosting**: Focus on gradient boosting algorithms

#### Phase 5: Final Solution
- **XGBoost Regressor**: Primary model
- Successfully passed competition cutoff
- Balanced performance with computational efficiency

---

## Key Results

- ✅ **Improved RMSE** through iterative model refinement
- ✅ **Competitive Public Score** on leaderboard
- ✅ **Passed Cutoff** using XGBoost Regressor
- ✅ **Scalable Solution** handling multiple theatre locations

---

## Technologies Used

- **Python** 🐍
- **Pandas & NumPy**: Data manipulation
- **Scikit-learn**: Model development and evaluation
- **XGBoost**: Primary modeling framework
- **Matplotlib/Seaborn**: Visualization

---

## Methodology Summary

```
Simple Models → Feature Engineering (Rolling/EMA/Lags) → 
Classical TS (ARIMA/SARIMA - Not Viable) → 
Bagging Models → Boosting Models → XGBoost ✓
```

---

## Key Learnings

1. **Entity-specific time series** require scalable solutions that can handle multiple independent sequences
2. **Classical time series models** (ARIMA/SARIMA) face practical limitations with multi-entity datasets
3. **Gradient boosting methods** (XGBoost) excel at capturing complex patterns without extensive manual feature engineering
4. **Iterative experimentation** is crucial—moving from simple to complex models helps identify optimal approaches

---

## Repository Structure

```
├── notebook/
│   ├── [RollNo]-notebook-t32025.ipynb    # Main analysis notebook
├── data/
│   ├── train.csv                          # Training dataset
│   ├── test.csv                           # Test dataset
│   └── sample_submission.csv              # Submission format
├── submissions/
│   └── final_submission.csv               # Final predictions
├── models/
│   └── xgboost_model.pkl                  # Saved model
└── README.md                              # This file
```

---

## How to Run

1. **Clone the repository**
2. **Install dependencies**:
   ```bash
   pip install pandas numpy scikit-learn xgboost matplotlib seaborn
   ```
3. **Run the notebook**: Open `[RollNo]-notebook-t32025.ipynb` and execute cells
4. **Generate predictions**: Model will output `final_submission.csv` in required format

---

## Submission Format

```python
# Predictions saved as:
submission = pd.DataFrame({
    'id': test_ids,
    'target': predictions
})
submission.to_csv('submission.csv', index=False)
```

---

## Competition Links

- **Competition Page**: [Cinema Audience Forecasting Challenge](https://www.kaggle.com/competitions/...)
- **Notebook**: Shared with `iitmbscs2008p` collaborator (Private)

---

## Author

**Team**: [Your Kaggle Username]  
**Roll No**: [Your Roll Number]  
**Affiliation**: IITM BS CS

---

## Acknowledgments

- Competition organizers: IITM BS CS 2008P
- Kaggle community for insights and discussions
- XGBoost development team

---

**Note**: This project was completed as part of the MLP Project T32025 competition series.
