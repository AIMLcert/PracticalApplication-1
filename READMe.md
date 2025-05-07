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


### Hypothesis
- People who visit bars more than once a month are more likely to accept bar coupons.
- Younger drivers (under 30 years old) tend to accept coupons more than older drivers.
- Drivers who don’t have kids in the car are more open to accepting bar coupons.
- Widowed drivers are less likely to accept coupons compared to others.
- If a person goes to inexpensive restaurants often and earns less than $50,000, they are more likely to accept coupons — they value - savings.
- Occupation matters too — people in non-physical or social jobs are more likely to accept bar coupons than those in jobs like farming or fishing.

## Independent Analysis
- Coffee House Coupon Acceptance:
	- By Passenger:
		- Passengers like friends and partners significantly increase acceptance rates.
		- Drivers alone are less likely to accept coffee house coupons.
		- Drivers with kids accept coffee coupons at moderate rates — not as high as with friends or partners.
	- By Time:
		- Highest acceptance is seen in the morning (10AM), likely aligning with coffee consumption habits.
		- Acceptance dips slightly at 2PM and 6PM, suggesting less interest in coffee later in the day.
	- By Weather:
		- Sunny weather shows the highest coupon acceptance.
		- Rainy and snowy days lead to lower acceptance, possibly due to reduced willingness to detour.
	- By Age:
		- Younger drivers (particularly 21–30 age range) accept coffee coupons more frequently.
		- Older age groups (above 40) show lower acceptance, hinting that younger demographics are more spontaneous or coffee-inclined.

- Carry Out & Take Away Coupon Acceptance:
	- By Passenger:
		- Drivers alone show the highest acceptance — likely because carryout is convenient when driving solo.
		- Passengers like kids or friends lead to moderate acceptance.
		- Partner passengers slightly reduce acceptance, possibly due to joint meal planning or dine-in preference.
	- By Time:
		- 2PM and 6PM are the peaks for acceptance — aligning with lunch and dinner times.
		- Morning (10AM) has noticeably low acceptance, since carryout food is less relevant at that hour.
	- By Weather:
		- Sunny days again yield higher acceptance.
		- Snowy days significantly reduce carryout coupon usage — likely due to comfort, safety, or logistics.
	- By Age:
		- Acceptance is steady across all age groups, but slightly higher among those under 35, possibly due to lifestyle convenience.
		- Older age groups (50+) still show decent acceptance, indicating that carryout is broadly appealing.

## 💡 Recommendations
- 

---

## 📁 Repository Contents
- `prompt.ipynb`: Jupyter Notebook with full analysis and code.
- `data/`: Folder containing the dataset used.
- `images/`: Folder containing exported plots.
- `README.md`: Project overview and summary (this file).

---

## 🔗 Notebook Access
👉 [View the Jupyter Notebook here](https://github.com/AIMLcert/PracticalApplication-1/blob/develop/prompt.ipynb)

---

## 🛠️ Tools Used
- Python
- Pandas
- Matplotlib & Seaborn
- Jupyter Notebook

---

## 📬 Contact
For questions or feedback, feel free to reach out via GitHub or email.

