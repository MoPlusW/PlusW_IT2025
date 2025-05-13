
# 📊 Class 7 – Regression-Based Prediction Systems  
![Course Badge](https://img.shields.io/badge/Course-IT%20%26%20Japanese%20Language-blue)  
![Date Badge](https://img.shields.io/badge/Date-February%208%2C%202025-brightgreen)  
![Platform Badge](https://img.shields.io/badge/Platform-Python%20%7C%20scikit--learn-yellow)

**👨‍🏫 Instructors:** [Hafiz Muhammad Umair Munir](https://www.linkedin.com/in/hafiz-muhammad-umair-munir-b929b0173/), [Abdul Ahad](https://www.linkedin.com/in/ahad-pro-soft/), [Abdul Hanan Ashraf](https://www.linkedin.com/in/abdul-hanan-ashraf-156115157/)

**🎓 Organized by:** [Plus W 株式会社](https://www.linkedin.com/company/plus-w) & [Pakistan Japan Centre](https://www.linkedin.com/company/pakistan-japan-centre)

**🌐 Supported by:** [AOTS](https://www.linkedin.com/company/aotsjapan/) & [Overseas Employment Corporation (OEC)](https://oec.gov.pk/)

---

## 🧠 Topics Covered

- 🏡 Linear Regression for house and salary prediction
- 📈 OLS and cost functions (MSE, R²)
- 🔁 Manual implementation of Gradient Descent
- 📉 Logistic Regression for churn classification
- 🔌 Data preprocessing and one-hot encoding
- 🌍 Streamlit dashboards for deployment

---

## 📁 Notebook Summary

### 📌 Part 1: House Price Prediction

**Dataset Features:**
- Square footage, bedrooms, age, and location

**Model:**
```python
from sklearn.linear_model import LinearRegression

model = LinearRegression()
model.fit(X_train, y_train)
print(model.coef_, model.intercept_)
```

📌 _Metric Results:_  
```text
R²: 0.87  
Adjusted R²: 0.85  
MSE: 21345.9
```

---

### 📌 Part 2: Salary Prediction

**Input Features:** Experience, education, role, city  
**One-hot Encoding Example:**
```python
df = pd.get_dummies(df, columns=["JobRole", "City"], drop_first=True)
```

📌 _Streamlit Deployment:_  
```bash
streamlit run salary_predictor.py
```

---

### 📌 Part 3: Stock Price Trend Forecasting

**Tool Used:** `yfinance`  
**Data:** Apple Inc. (AAPL)

```python
import yfinance as yf
df = yf.download('AAPL', start='2022-01-01', end='2023-01-01')
```

**Model + Plot:**
```python
model = LinearRegression()
model.fit(df[["Volume"]], df["Close"])
plt.plot(df["Close"])
```

📊 _Streamlit Interface:_ Allows input of volume, outputs predicted close price.

---

### 📌 Part 4: Customer Churn Classification (Logistic Regression)

**Input:** Monthly charges, contract type, support calls

```python
from sklearn.linear_model import LogisticRegression
model = LogisticRegression()
model.fit(X_train, y_train)
```

**Evaluation:**
```python
from sklearn.metrics import confusion_matrix, classification_report
print(classification_report(y_test, y_pred))
```

📊 _Output:_ Confusion matrix with color-coded heatmap (Seaborn)

---

### 📌 Part 5: Energy Consumption Regression

**Dataset:** `owid-energy-data.csv`  
**Target:** Annual electricity consumption

**Gradient Descent Implementation:**
```python
def gradient_descent(X, y, lr=0.001, epochs=500):
    m, c = 0, 0
    for _ in range(epochs):
        y_pred = m * X + c
        m -= lr * (-2 * (X * (y - y_pred)).mean())
        c -= lr * (-2 * (y - y_pred).mean())
    return m, c
```

📌 _Results:_  
```text
Final slope: ≈ 0.73  
Final intercept: ≈ 102.3
```

---

## 💻 Running Instructions

### ✅ Install Packages
```bash
pip install pandas numpy matplotlib seaborn scikit-learn streamlit yfinance
```

### ▶️ Run Streamlit Dashboards
```bash
streamlit run [project_file].py
```

Examples:
```bash
streamlit run stock_price_prediction.py
streamlit run churn_classifier.py
```

---

## 📚 References

- [Scikit-learn documentation](https://scikit-learn.org/stable/)
- [NumPy documentation](https://numpy.org/doc/)
- [Yahoo Finance API](https://pypi.org/project/yfinance/)
- [Our World in Data Energy Dataset](https://ourworldindata.org/energy)

---