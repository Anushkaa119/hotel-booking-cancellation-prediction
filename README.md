# 🏨 Hotel Booking Cancellation Prediction

An end-to-end Machine Learning project that predicts whether a hotel booking is likely to be cancelled based on booking, guest, stay, customer, and reservation-related information.

## 📌 Project Overview

Hotel booking cancellations can affect room availability, revenue forecasting, and operational planning.

This project uses historical hotel booking data to build and evaluate classification models for predicting booking cancellations.

The project follows a complete Machine Learning workflow:

**Data Understanding → Exploratory Data Analysis → Data Cleaning → Feature Engineering → Preprocessing → Model Training → Model Evaluation → Prediction**

---

## 🎯 Objective

The objective of this project is to predict the cancellation status of a hotel booking.

The target variable is:

- `0` → Booking Not Cancelled
- `1` → Booking Cancelled

The final prediction pipeline also provides the estimated probability of cancellation for a new booking.

---

## 📊 Dataset

The project uses the **Hotel Booking Demand Dataset**, which contains booking information for:

- Resort Hotel
- City Hotel

The original dataset contains **119,390 booking records and 32 features**.

The dataset includes information about:

- Booking lead time
- Arrival date
- Length of stay
- Number of guests
- Market segment
- Distribution channel
- Deposit type
- Previous cancellations
- Previous bookings
- Room types
- Customer type
- Special requests
- Average Daily Rate (ADR)

> **Note:** The raw CSV dataset is not included in this GitHub repository because of its size. It can be downloaded separately and placed inside the `data/` folder.

---

# 🔍 Exploratory Data Analysis

The EDA process included:

- Understanding dataset structure
- Checking data types
- Analyzing missing values
- Identifying duplicate records
- Studying categorical and numerical variables
- Analyzing cancellation distribution
- Detecting unusual and inconsistent observations
- Examining relationships between booking features and cancellation status
- Identifying potential outliers

---

# 🧹 Data Cleaning

Several data quality issues were addressed before model development.

### Key cleaning steps

- Duplicate records were identified and removed.
- Missing values were analyzed based on the meaning of each feature.
- Numerical and categorical missing values were handled appropriately.
- Invalid and inconsistent booking records were identified.
- Logically impossible guest combinations were investigated.
- Extreme values and outliers were examined before modeling.

The cleaned dataset was then used for feature engineering and model development.

---

# ⚙️ Feature Engineering

Additional features were created to capture meaningful booking patterns.

| Feature | Description |
|---|---|
| `total_guests` | Total adults + children + babies |
| `total_stay_nights` | Weekend nights + weekday nights |
| `total_previous_bookings` | Previous cancelled + previous non-cancelled bookings |
| `arrival_date` | Combined arrival year, month and day |
| `arrival_day_of_week` | Day of the week of arrival |
| `is_family` | Indicates whether children or babies are present |
| `has_previous_booking` | Indicates whether the customer has previous booking history |

These engineered features were included in the model development pipeline.

---

# 🛠️ Data Preprocessing

Scikit-learn preprocessing techniques were used to prepare the data for machine learning.

The preprocessing pipeline included:

- Numerical feature processing
- Categorical feature encoding using One-Hot Encoding
- Train-test splitting
- Consistent feature transformation
- Prevention of data leakage by fitting transformations only on training data

The preprocessing pipeline transformed the data into **574 model-ready features**.

The fitted preprocessing pipeline was saved using **Joblib** and reused during prediction.

---

# 🤖 Machine Learning Models

Four classification algorithms were trained and evaluated:

1. Logistic Regression
2. Decision Tree
3. Random Forest
4. Gradient Boosting

The models were evaluated using:

- Accuracy
- Precision
- Recall
- F1 Score
- ROC-AUC

---

# 📈 Model Performance

| Model | Accuracy | Precision | Recall | F1 Score | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| Logistic Regression | 80.35% | 68.44% | 52.94% | 59.70% | 85.78% |
| Decision Tree | 82.02% | 69.74% | 61.14% | 65.16% | 87.42% |
| Random Forest | 79.54% | 84.43% | 31.36% | 45.74% | 87.75% |
| **Gradient Boosting** | **83.09%** | **74.35%** | **58.77%** | **65.65%** | **89.13%** |

## 🏆 Best Model

Based on the evaluation results, **Gradient Boosting** was selected as the final model.

It achieved:

- **Accuracy:** 83.09%
- **Precision:** 74.35%
- **Recall:** 58.77%
- **F1 Score:** 65.65%
- **ROC-AUC:** 89.13%

The model achieved the highest overall ROC-AUC and accuracy among the evaluated models.

---

# 🔎 Feature Importance

The Gradient Boosting model identified several features that contributed strongly to its predictions.

Some of the important features included:

- `lead_time`
- `country`
- `agent`
- `total_of_special_requests`
- `required_car_parking_spaces`
- `market_segment`
- `deposit_type`
- `customer_type`
- `previous_cancellations`
- `booking_changes`

This suggests that factors such as booking timing, booking source, customer history, and reservation characteristics contain useful information for predicting cancellation behavior.

---

# 🔮 Prediction

The trained model and preprocessing pipeline were saved using Joblib and used to make predictions on new booking data.

Example prediction:

```text
Prediction: Not Cancelled
Cancellation Probability: 48.20%