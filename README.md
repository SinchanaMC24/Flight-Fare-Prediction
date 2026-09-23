##✈️ Flight Fare Prediction using Machine Learning
📌 Project Overview

Flight Fare Prediction is an end-to-end machine learning regression project focused on predicting flight ticket prices using historical flight data.

The project analyzes how factors such as airline, source, destination, journey date, departure and arrival time, flight duration, and number of stops influence ticket prices.

The complete workflow covers data understanding, data cleaning, exploratory data analysis, feature engineering, preprocessing, model development, model comparison, hyperparameter tuning, feature importance analysis, and final model validation.

Five regression algorithms were evaluated, followed by hyperparameter optimization of the Random Forest model to improve prediction performance.

🎯 Objectives
Analyze flight fare patterns and identify important pricing factors.
Perform comprehensive exploratory data analysis.
Clean and transform raw flight data for machine learning.
Engineer meaningful features from date, time, duration, and stop information.
Develop and evaluate multiple regression models.
Compare model performance using appropriate regression metrics.
Optimize the selected model using hyperparameter tuning.
Interpret important features influencing flight fare predictions.
Validate the final model using actual vs. predicted prices and prediction-error analysis.
📊 Dataset

The dataset contains historical flight information with features related to:

Airline
Date of Journey
Source
Destination
Route
Departure Time
Arrival Time
Duration
Total Stops
Additional Information
Price
Target Variable

Price

Since the target variable is continuous, the problem is formulated as a supervised regression problem.

The dataset contains flight prices ranging up to approximately ₹79,512, with a median price of approximately ₹8,372.

🔍 Exploratory Data Analysis

EDA was performed to understand the distribution and relationship between flight characteristics and ticket prices.

Key observations

Airline

Flight prices vary considerably across airlines.
Premium/business categories show substantially higher fares.
Jet Airways has a high number of flights in the dataset.

Source & Destination

Delhi is the most common source.
Cochin is the most common destination.
Fare distributions differ across different source and destination locations.

Number of Stops

Non-stop flights generally have lower median fares.
One-stop flights have a wider price range and several high-price observations.
The relationship between number of stops and fare is not strictly linear.

Price Distribution

Most fares are concentrated in the lower price range.
The target distribution is right-skewed.
High-value observations are present and were retained because they may represent genuine flight fares.

Flight Duration

Duration_Minutes shows a moderate positive correlation with Price of approximately 0.502.
This makes duration an important feature for the prediction task.
🛠️ Data Preprocessing & Feature Engineering

The raw dataset was transformed into a machine-learning-ready format through several preprocessing steps.

Data Cleaning
Checked for duplicate records.
Identified missing values.
Removed duplicate records.
Removed rows with missing Route and Total_Stops values.
Examined unique values and category distributions.
Feature Engineering

New features were extracted from existing columns:

Journey_Day
Journey_Month
Dep_Hour
Arrival_Hour
Duration_Minutes
Numerical representation of Total_Stops
Route_Count

Original date/time and duration representations were removed after extracting the required information.

Categorical Encoding

Categorical variables such as:

Airline
Source
Destination

were transformed using one-hot encoding.

Additional_Info was excluded because of its highly imbalanced distribution.

Feature Scaling

StandardScaler was applied to the features used by KNN, since KNN relies on distance calculations and is sensitive to differences in feature scales.

🤖 Machine Learning Models

Five regression algorithms were developed and evaluated:

Model	Description
Linear Regression	Baseline linear regression approach
Decision Tree	Captures non-linear relationships
Random Forest	Ensemble of multiple decision trees
Gradient Boosting	Sequential boosting-based regression
K-Nearest Neighbors	Distance-based regression

The models were evaluated using:

MAE – Mean Absolute Error
MSE – Mean Squared Error
RMSE – Root Mean Squared Error
R² Score – Coefficient of Determination
📈 Model Comparison

Among the five initial models, Random Forest produced the strongest performance in the notebook's model comparison.

Initial Random Forest Performance
Metric	Score
MAE	1213.79
RMSE	1989.51
R² Score	0.8102

Based on these results, Random Forest was taken forward for further optimization.

⚙️ Hyperparameter Optimization

To improve the Random Forest model, RandomizedSearchCV with 3-fold cross-validation was implemented.

The tuning process explored combinations of parameters including:

n_estimators
max_depth
min_samples_split
min_samples_leaf

The best-performing parameter combination was selected using R² Score as the evaluation criterion.

🏆 Final Model Performance

The optimized Random Forest model achieved:

Metric	Tuned Random Forest
MAE	1177.72
RMSE	1893.62
R² Score	0.8280

The R² Score improved from 0.8102 to 0.8280 after hyperparameter tuning, while the prediction error metrics decreased.

Performance Improvement
Original Random Forest
R² = 0.8102
        ↓
Hyperparameter Tuning
        ↓
Tuned Random Forest
R² = 0.8280

The tuned Random Forest model was therefore used as the final model in the project.

🔎 Feature Importance Analysis

Feature importance was analyzed using the final tuned Random Forest model to understand which variables contributed most to fare prediction.

The analysis identified:

Duration_Minutes – approximately 0.49 importance
Journey_Day
Jet Airways Business
Jet Airways
Journey Month
Arrival Time-related features
Departure Time-related features

The results indicate that flight duration, journey date, airline, and timing-related features play an important role in the model's fare predictions.

📉 Model Validation

The final model was further validated using:

Actual vs. predicted price visualization
Prediction error analysis
Average prediction error
Minimum and maximum prediction errors

The actual-vs-predicted analysis shows that the model captures the overall pattern of flight fares, while some individual predictions differ considerably from their actual prices.

💡 Business Insights

The analysis provides several useful insights into flight pricing:

Flight fares differ significantly across airlines.
Journey duration has a noticeable relationship with ticket price.
Source and destination influence fare patterns.
Number of stops contributes to differences in fare distribution.
Journey dates and flight timing can influence pricing patterns.
Premium/business flight categories can have substantially higher fares.
Flight pricing is influenced by multiple interacting factors rather than a single variable.

These insights can support fare estimation, pricing analysis, and travel decision-support applications.

🧩 Challenges Addressed
1. High-Cardinality Time Information

Exact departure and arrival times contained many unique values. Hour-based features were therefore extracted to make them more suitable for modelling.

2. Categorical Variables

Airline, source, and destination were categorical variables and required encoding before model training.

3. Skewed Price Distribution

The target variable contained a right-skewed distribution and high-value observations. Potential outliers were investigated rather than automatically removed.

4. Different Feature Scales

KNN requires appropriately scaled features because it relies on distance calculations.

5. Model Optimization

After comparing multiple algorithms, Random Forest was further optimized using cross-validation and randomized hyperparameter search.

🧰 Technologies & Libraries

Programming Language

Python

Data Analysis

Pandas
NumPy

Data Visualization

Matplotlib
Seaborn

Machine Learning

Scikit-learn

Development Environment

Jupyter Notebook

Dataset Format

Excel
📁 Project Structure
Flight-Fare-Prediction/
│
├── Dataset/
│   └── Flight_Fare.xlsx
│
├── Models/
│   ├── <trained-model-1>.pkl
│   └── <trained-model-2>.pkl
│
├── Flight_Fare_Prediction.ipynb
│
└── README.md
🚀 Project Workflow
Raw Flight Data
      │
      ▼
Data Understanding
      │
      ▼
Data Cleaning
      │
      ▼
Exploratory Data Analysis
      │
      ▼
Feature Engineering
      │
      ▼
Data Preprocessing
      │
      ▼
Train-Test Split
      │
      ▼
Multiple Regression Models
      │
      ▼
Model Comparison
      │
      ▼
Random Forest Selection
      │
      ▼
Hyperparameter Tuning
      │
      ▼
Feature Importance Analysis
      │
      ▼
Final Model Validation
      │
      ▼
Saved Trained Model
👥 Team Contribution

This project was developed collaboratively.

Team Member 1

Worked on the project through the initial data preparation and model-building stages.

My Contribution

Continued the project after the initial model-building stage.
Performed model comparison and evaluation.
Implemented Random Forest hyperparameter tuning.
Evaluated the tuned model.
Performed feature importance analysis.
Conducted actual-vs-predicted analysis and prediction-error analysis.
Completed final model validation and selection.
Saved the trained model for future use.
📌 Final Outcome

The project demonstrates a complete machine learning regression pipeline for flight fare prediction, from raw data exploration to final model validation.

The tuned Random Forest model achieved an R² Score of 0.8280, with an MAE of ₹1,177.72 and RMSE of ₹1,893.62 on the evaluated test data.

The project also demonstrates practical skills in Python, data preprocessing, EDA, feature engineering, regression modelling, model evaluation, hyperparameter tuning, and machine learning model interpretation.
