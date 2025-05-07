# Will the Customer Accept the Coupon?

## 📌 Project Overview
This project aims to analyze whether a customer will accept a driving-related coupon based on various contextual features such as time, location, weather, companion, and destination. The dataset was collected via a survey on Amazon Mechanical Turk and is part of the UCI Machine Learning Repository.

The goal is to identify the differences between customers who accepted the coupon and those who did not, and to make data-driven recommendations on when and where coupons are most effective.

---

## 🧪 Problem Statement
Can we predict if a customer will accept a coupon offer while driving? What factors influence this decision the most — is it the time of day, the presence of passengers, the type of coupon, or something else?

---

## 🔍 Methodology
- 

---

## 📊 Key Findings
### Analyze problematic data
- Missing counts: 
	- car ≈ 99 % missing (only 108 non‑null). Car is effectively unusable; the five “frequency” columns have small, but non‑negligible, gaps.
	- Bar, CoffeeHouse, CarryAway, RestaurantLessThan20, Restaurant20To50 each missing 0.8 – 1.7 %
- Data types: 
	- All “frequency” columns are object rather than ordered‑categorical; numeric distance flags are int; temperature is int
	- Frequency columns will need cleaning/encoding if we model later.
- Duplicates
	- 73 exact duplicate rows detected (all False in isnull matrix)
	- Retaining duplicates could bias counts; safest to drop them.
- Anomalous strings
	- Values such as "never", "nan", and leading/trailing spaces in categorical variables
	- Require standardisation (e.g., strip, lower‑case, unify categories).

### Clean the data
- Created a working copy (cleaned_data = data.copy())	
	- Preserve the raw dataset for reproducibility and debugging.
- Dropped the car column	
	- More than 99 % missing – not recoverable and likely not informative.
- Dropped rows missing any of Bar, CoffeeHouse, CarryAway	
	- These three categorical “lifestyle” features are important predictors; their missingness was small (~1 %) so row‑wise deletion has - minimal impact.
- Imputed remaining categorical gaps (RestaurantLessThan20, Restaurant20To50) with column mode
	- Low missing percentage; mode preserves the existing distribution and is appropriate for unordered categories.
- String normalisation (gender = gender.str.strip().str.lower())	
	- Removes accidental spaces / capitalisation differences that would create spurious levels.
- Removed exact duplicate rows (cleaned_data.drop_duplicates(inplace=True))	
	- Prevents double‑counting in EDA and model training.
- Verified result (missing_data_summary(cleaned_data))	
	- Confirmed zero missing values in retained columns and 12 637 rows (loss: 47 rows from drops + duplicates).


---

## 💡 Recommendations
- 

---

## 📁 Repository Contents
- `coupon_analysis.ipynb`: Jupyter Notebook with full analysis and code.
- `data/`: Folder containing the dataset used.
- `images/`: Folder containing exported plots.
- `README.md`: Project overview and summary (this file).

---

## 🔗 Notebook Access
👉 [View the Jupyter Notebook here]()

---

## 🛠️ Tools Used
- Python
- Pandas
- Matplotlib & Seaborn
- Jupyter Notebook

---

## 📬 Contact
For questions or feedback, feel free to reach out via GitHub or email.

