# 🏠 House Price Prediction using Machine Learning

A data science major project that explores a real-estate dataset and builds a **Linear Regression** model to predict house prices from property features such as living area, bedrooms, bathrooms, condition, and year built.

---

## 📌 Table of Contents
- [Overview](#-overview)
- [Dataset](#-dataset)
- [Tech Stack](#-tech-stack)
- [Project Workflow](#-project-workflow)
- [Model Performance](#-model-performance)
- [Key Observations](#-key-observations)
- [Future Improvements](#-future-improvements)
- [How to Run](#-how-to-run)
- [Project Structure](#-project-structure)
- [Author](#-author)

---

## 📖 Overview

The goal of this project is to understand which factors influence house prices and to build a baseline regression model that estimates the price of a house. The notebook covers the complete beginner-to-intermediate data science pipeline: data loading, cleaning, exploratory data analysis (EDA), model training, and evaluation.

## 📊 Dataset

- **File:** `house_price_dataset.csv`
- **Size:** 4,600 rows × 18 columns
- **Target variable:** `price`
- **Region:** Houses located in Washington State, USA (Seattle, Bellevue, Kent, Redmond, Shoreline, etc.)

| Column | Description |
|---|---|
| `date` | Date of sale |
| `price` | Sale price (target) |
| `bedrooms`, `bathrooms` | Number of bedrooms / bathrooms |
| `sqft_living`, `sqft_lot` | Interior living area and lot size (sq ft) |
| `floors` | Number of floors |
| `waterfront`, `view` | Waterfront flag and view rating |
| `condition` | Condition rating of the house |
| `sqft_above`, `sqft_basement` | Area above ground and basement area |
| `yr_built`, `yr_renovated` | Year built and year renovated |
| `street`, `city`, `statezip`, `country` | Location details |

## 🛠 Tech Stack

- **Language:** Python 3
- **Libraries:** Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn
- **Environment:** Jupyter Notebook / Google Colab

## 🔄 Project Workflow

1. **Data Loading** – Read the CSV and inspect the first rows, data types, and statistical summary.
2. **Data Cleaning**
   - Checked for missing values (none found) and handled them with `dropna()`.
   - Checked for duplicate rows (none found) and removed duplicates.
3. **Exploratory Data Analysis**
   - Histogram of house price distribution
   - Correlation heatmap of numeric features
   - Scatter plot of living area (`sqft_living`) vs. price
4. **Feature Selection** – Kept the 12 numeric features and dropped text/date columns (`date`, `street`, `city`, `statezip`, `country`).
5. **Train–Test Split** – 80% training (3,680 rows) and 20% testing (920 rows), `random_state=42`.
6. **Model Training** – Trained a `LinearRegression` model.
7. **Evaluation** – Measured MAE, MSE, RMSE, and R², and plotted actual vs. predicted prices.

## 📈 Model Performance

| Metric | Value |
|---|---|
| MAE | ≈ 210,908 |
| MSE | ≈ 9.87 × 10¹¹ |
| RMSE | ≈ 993,439 |
| R² Score | ≈ 0.032 |

## 🔍 Key Observations

- The baseline Linear Regression model has a **low R² (~0.03)**, meaning it explains very little of the price variance on the test set.
- The RMSE is much larger than the MAE, which points to **extreme outliers** in the price column (e.g., very expensive houses and possibly houses with a price of 0) that heavily affect the squared-error metrics.
- Location (city / zip code) is a major price driver in real estate, but it was **not used** in this baseline because only numeric columns were selected.

## 🚀 Future Improvements

- Handle outliers (remove or cap extreme/zero prices) or apply a **log transformation** to `price`
- Encode location features (`city`, `statezip`) using one-hot or target encoding
- Engineer new features such as house age, renovation flag, and price per sq ft
- Try stronger models: **Random Forest, Gradient Boosting, XGBoost**
- Use cross-validation and hyperparameter tuning
- Deploy the final model as a web app with **Streamlit** or **FastAPI**

## ▶️ How to Run

1. **Clone the repository**
   ```bash
   git clone https://github.com/<your-username>/<your-repo-name>.git
   cd <your-repo-name>
   ```

2. **Install dependencies**
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn jupyter
   ```

3. **Add the dataset** – Place `house_price_dataset.csv` in the project folder and update the file path in the notebook:
   ```python
   df = pd.read_csv("house_price_dataset.csv")
   ```
   *(The notebook currently reads from `/content/house_price_dataset.csv`, which is the Google Colab path.)*

4. **Launch the notebook**
   ```bash
   jupyter notebook "DS(Major_Project)House_Price_Detection.ipynb"
   ```

## 📁 Project Structure

```
├── DS(Major_Project)House_Price_Detection.ipynb   # Main notebook
├── house_price_dataset.csv                        # Dataset
└── README.md                                      # Project documentation
```

## 👤 Author

**Abhinav Yadav**
Aspiring Data Analyst | Hyderabad, India
---

⭐ If you found this project useful, consider giving it a star!
