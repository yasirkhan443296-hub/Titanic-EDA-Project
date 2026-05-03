# Titanic-EDA-Project
🚢 Titanic EDA | Analysis of 1,309 passengers. Covers Univariate &amp; Bivariate Analysis, Missing Value Treatment (IterativeImputer/MICE), Feature Engineering (family_type, title, individual_fare) &amp; Data Visualization. Tools: Python, Pandas, Seaborn, Matplotlib, Sklearn.


# 🚢 Titanic EDA — Complete Project Description

---

## 🌟 Introduction

This project is a complete Exploratory Data Analysis 
performed on the famous Titanic dataset. The Titanic 
was a British passenger ship that sank on April 15, 
1912, after hitting an iceberg in the North Atlantic 
Ocean. Out of 2,224 passengers and crew members, more 
than 1,500 people lost their lives, making it one of 
the deadliest peacetime maritime disasters in history.

The dataset contains information about 1,309 passengers 
including personal details, ticket information, and 
whether they survived or not. Every row represents a 
real person. Through data analysis, we tried to 
understand what factors influenced survival.

---

## 🛠️ Tools and Technologies

| Tool | Purpose |
|------|---------|
| 🐼 Pandas | Data manipulation & cleaning |
| 🔢 NumPy | Numerical operations |
| 📊 Matplotlib | Basic visualizations |
| 🎨 Seaborn | Advanced statistical plots |
| 🤖 Scikit-learn | IterativeImputer (MICE) |
| ☁️ Google Colab | Cloud notebook environment |

---

## 📥 Step 1: Data Loading & Concatenation

- Train dataset: **891 rows × 12 columns**
- Test dataset: **418 rows × 11 columns**
- Combined dataset: **1,309 rows × 12 columns**

> ✅ Train and test were concatenated **immediately**
> after loading — before any analysis or feature 
> engineering. This is critical best practice.

---

## 🔍 Step 2: Dataset Understanding

| Column | Type | Missing | Description |
|--------|------|---------|-------------|
| PassengerId | Numerical | 0 | Unique ID |
| Survived | Categorical | 418 (test) | 0=No, 1=Yes |
| Pclass | Categorical | 0 | 1, 2, 3 class |
| Name | Text | 0 | Full name |
| Sex | Categorical | 0 | male/female |
| Age | Numerical | 263 (20%) | Age in years |
| SibSp | Numerical | 0 | Siblings/spouse |
| Parch | Numerical | 0 | Parents/children |
| Ticket | Text | 0 | Ticket number |
| Fare | Numerical | 1 | Ticket price |
| Cabin | Text | 1014 (77%) | Cabin number |
| Embarked | Categorical | 2 | Boarding port |

---

## 📈 Step 3: Univariate Analysis

Analyzed every column independently for distribution,
dispersion, outliers and missing values.

### 🔢 Numerical Columns
- **Age** — Approximately normal, 20% missing, 
  outliers above 65
- **Fare** — Highly right-skewed, max value 512, 
  contains group fares

### 🔤 Categorical Columns
- **Sex** — Male 64%, Female 36%
- **Survived** — Not survived 61%, Survived 39%
- **Pclass** — Class 3: 55%, Class 1: 24%, Class 2: 20%
- **SibSp** — 68.2% traveled alone
- **Parch** — 76% had no parents/children aboard
- **Embarked** — Southampton 72.4%, Cherbourg 18.9%,
  Queenstown 8.7%

---

## 🔗 Step 4: Bivariate Analysis

### 👩 Sex vs Survival
| Sex | Survived | Not Survived |
|-----|----------|--------------|
| Female | 74% | 26% |
| Male | 19% | 81% |

> Females were **4x more likely** to survive 🚨

### 🎫 Pclass vs Survival
| Class | Survival Rate |
|-------|--------------|
| 1st Class | 63% |
| 2nd Class | 47% |
| 3rd Class | 24% |

### 🚉 Embarked vs Survival
| Port | Survival Rate |
|------|--------------|
| Cherbourg (C) | 55% |
| Queenstown (Q) | 39% |
| Southampton (S) | 34% |

### 👶 Age vs Survival
- Children under 10 had higher survival rates
- Young adults 20-35 had lowest survival
- Senior passengers had very low survival

---

## 🧹 Step 5: Missing Value Treatment

| Column | Missing % | Method | Reason |
|--------|-----------|--------|--------|
| Age | 20.09% | IterativeImputer (MICE) | Best for 10-25% missing |
| Fare | 0.07% | Median fill | Very few missing |
| Embarked | 0.15% | Mode fill (S) | Categorical |
| Cabin | 77.5% | Fill Unknown | Too high to impute |

### 🧠 IterativeImputer (MICE) for Age
- Uses Pclass, Fare, SibSp, Parch to predict Age
- Runs **10 iterations** — each improves accuracy
- random_state=42 for reproducibility
- KDE before/after plot confirmed distribution 
  was well preserved ✅
- Negative values clipped with clip(lower=0)

---

## ⚙️ Step 6: Feature Engineering

| New Feature | Formula | Purpose |
|-------------|---------|---------|
| individual_fare | Fare/(SibSp+Parch+1) | Actual fare per person |
| family_size | SibSp+Parch+1 | Total family members |
| family_type | alone/small/large | Family size category |
| title | Extracted from Name | Social status indicator |
| surname | Extracted from Name | Family group identifier |

### 👨‍👩‍👧 Family Type vs Survival
- **Small families (2-4)** — Best survival rate ✅
- **Alone** — Moderate survival
- **Large families (5+)** — Lowest survival ❌

---

## 🏆 Final Key Insights

> 🥇 **Gender** — Females survived 74% vs males 19%
>
> 🥈 **Class** — 1st class 63% vs 3rd class 24%
>
> 🥉 **Family Size** — Small families survived most
>
> 👶 **Age** — Children had higher survival rates
>
> 🚉 **Port** — Cherbourg passengers survived most

---

## 🚀 Next Steps

- [ ] Outlier Treatment (IQR method)
- [ ] Encode categorical columns
- [ ] Build ML models (Logistic Regression,
      Random Forest, XGBoost)
- [ ] Evaluate with AUC-ROC, F1 Score

---

## 💡 Personal Learning

This project taught me that data science is not 
just about running code. It is about asking smart 
questions and letting data tell its story. Every 
number in this dataset represents a real human life 
on that ship. 🎯

---

## 📁 Files in This Repository

| File | Description |
|------|-------------|
| final_titanic_eda.ipynb | Complete EDA notebook |
| Titanic_EDA_Report.docx | Full project report |
| train.csv | Training dataset |
| test.csv | Test dataset |
