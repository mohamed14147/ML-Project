# ML Project 

## About Dataset
**Dataset Description:**  
This dataset serves as a comprehensive repository of global development metrics, consolidating data from multiple international organizations into a single, unified structure. It provides a granular view of the state of health, economy, and nutrition across 193 countries over a 30-year period (1990–2019).

The data is organized by **Country**, **Year**, and **Gender** (Male, Female, and Both Sexes), making it a valuable resource for longitudinal studies, demographic analysis, and socio-economic research. It combines high-level economic indicators (like GDP) with granular health metrics (specific mortality rates) and detailed nutritional breakdowns (diet composition by food group).

**Content Overview:**  
- **Demographics & Economy:** Population stats, GNI, GDP, and poverty rates  
- **Mortality & Life Expectancy:** Survival rates at various ages, maternal mortality, and life expectancy  
- **Public Health:** Incidence of infectious diseases (Malaria, Tuberculosis, Hepatitis B) and prevalence of health risks (Tobacco, road traffic accidents)  
- **Environmental Health:** Mortality attributed to air pollution, sanitation access, and clean fuel availability  
- **Nutrition:** Detailed caloric and quantity breakdown of food consumption (fruits, vegetables, cereals, meats, etc.)  
- **Healthcare Infrastructure:** Coverage of essential health services and density of medical professionals  

**Dataset Source:** [Kaggle Link](https://www.kaggle.com/datasets/miguelroca/global-health-nutrition-mortality-economic-data/code)

---

## 1️⃣ Data Loading
- Read CSV using pandas  
- Checked first 5 rows, dataset info, and summary statistics

## 2️⃣ Handling Categorical Data
- Columns **Country** and **Gender** were categorical  
- Used **OneHotEncoder** to convert them into numeric columns

## 3️⃣ Handling Missing Values
- Checked for null values using `isnull()`  
- Instead of dropping rows with nulls (which would remove too much data), we used `fillna()` with mean to keep all rows

## 4️⃣ Removing Duplicates
- Checked for duplicates and removed them if any

## 5️⃣ Detecting Outliers
- Used **Z-score** on Life Expectancy to identify outliers (`|Z| > 3`)

## 6️⃣ Feature Analysis
- Calculated correlations with **Life Expectancy**  
- Plotted top and bottom correlated features to understand which features impact life expectancy the most

## 7️⃣ Normalization / Scaling
- Used **MinMaxScaler** to scale all features between 0 and 1 for better model performance

## 8️⃣ Preparing Data for Modeling
- Features (`X`) = all columns except **Life Expectancy**  
- Target (`y`) = **Life Expectancy**  
- Split data into train and test sets (80/20)

## 9️⃣ Model Selection
Tested three models:  
- **Random Forest Regressor** → Chosen for its high accuracy and ability to handle many features with low overfitting  
- **Bagging Decision Trees** → Reduces variance, good for noisy data  
- **Gradient Boosting Regressor** → High accuracy, reduces bias  
- Evaluated each model using **R²**, **MAE**, and **MSE**, and plotted Actual vs Predicted

## 🔟 Why We Chose Random Forest
- Handles large number of features well  
- Resistant to overfitting  
- Gives good predictions even if some features are correlated

## 💡 Key Points
- Using `fillna()` was important to keep all rows; dropping nulls would have removed too much data  
- Preprocessing included: Encoding categorical data, scaling, handling nulls, detecting outliers, and removing duplicates  
- Feature analysis helped us understand which factors affect life expectancy the most

## 📊 Model Performance

| Model                       | R²     | MAE    | MSE      |
| --------------------------- | ------ | ------ | -------- |
| Random Forest Regressor     | 0.9948 | 0.0067 | 0.000127 |
| Bagging Decision Tree       | 0.9944 | 0.0069 | 0.000137 |
| Gradient Boosting Regressor | 0.9349 | 0.0292 | 0.001576 |
