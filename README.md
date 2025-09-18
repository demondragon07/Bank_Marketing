# Bank_Marketing
A Logistic Regression Model

## Project Overview
This project analyzes the **Bank Marketing dataset**, which comes from a Portuguese bank’s direct marketing campaigns. The main objective is to **predict whether a client will subscribe to a term deposit** based on client attributes, campaign details, and economic indicators.  
The problem is framed as a **binary classification task** (`yes` or `no`).

---------------------------------------------------------------------------------------------------------------------------------------------------

## Dataset
- **File Used:** `bank-full.csv`  
- **Records:** 45,211 rows  
- **Features:** 16 input variables + 1 target (`y`)  

### Target Variable
- `y = yes` → Client subscribed to a term deposit  
- `y = no` → Client did not subscribe  

### Feature Categories
1. **Client Attributes**: `age`, `job`, `marital`, `education`, `default`, `housing`, `loan`  
2. **Current Campaign**: `contact`, `month`, `day_of_week`, `duration`, `campaign`  
3. **Previous Campaigns**: `pdays`, `previous`, `poutcome`  
4. **Economic Indicators**: `emp.var.rate`, `cons.price.idx`, `cons.conf.idx`, `euribor3m`, `nr.employed`  

---------------------------------------------------------------------------------------------------------------------------------------------------------

## Exploratory Data Analysis (EDA)
- **Target Distribution:** Highly imbalanced (`No ~89%`, `Yes ~11%`)  
- **Numerical Features:**  
  - `age`: Most clients are between 30–40 years old  
  - `duration`: Strongly linked with outcome (longer calls → more “Yes”)  
  - `campaign`: Most clients contacted < 5 times  
- **Categorical Features:**  
  - Jobs: Admin, blue-collar, technician most common  
  - Marital: Majority married  
  - Education: Mostly secondary education  
  - Housing loans: Many clients have them  

------------------------------------------------------------------------------------------------------------------------------------------------------------

##  Data Preprocessing
- **Encoding:** Label Encoding for categorical variables  
- **Splitting:** 70% training, 30% testing  
- **Scaling:** Not applied (Logistic Regression works fine with encoded categorical features)  

-------------------------------------------------------------------------------------------------------------------------------------------------------------

##  Model Training
- **Algorithm:** Logistic Regression  
- **Hyperparameters:**  
  - `solver = liblinear`  
  - `max_iter = 500`  

-----------------------------------------------------------------------------------------------------------------------------------------------------------------

## Model Evaluation
### Classification Report
| Class | Precision | Recall | F1-score | Support |
|-------|-----------|--------|----------|---------|
| **0 (No)** | 0.90 | 0.98 | 0.94 | 11977 |
| **1 (Yes)** | 0.60 | 0.21 | 0.31 | 1587 |
| **Overall Accuracy** | **0.89** |  |  | 13564 |

### Key Observations
- Strong at predicting **non-subscribers** (Class 0)  
- Weak at predicting **subscribers** (Class 1) due to imbalance  
- Recall for Class 1 = **21%**, meaning many potential subscribers are missed  

------------------------------------------------------------------------------------------------------------------------------------------------------------

## Results & Insights
- Logistic Regression achieved **89% accuracy** overall.  
- The model struggles with predicting subscribers (minority class).  
- Class imbalance significantly impacts performance.  
- Future improvements could include:  
  - Using **SMOTE / oversampling**  
  - Trying **tree-based models (Random Forest, XGBoost, etc.)**  
  - Applying **class weights** in Logistic Regression  

-----------------------------------------------------------------------------------------------------------------------------------------------------------------

## How to Run
```bash
# Clone repo (if applicable)
git clone <repo-link>
cd bank-marketing

# Install dependencies
pip install -r requirements.txt

# Run the analysis
python bank_marketing.py
```

------------------------------------------------------------------------------------------------------------------------------------------------------------------
 
