# 🤖 Class 8 - Multiple Linear Regression & Support Vector Machines (SVM)

![Course Badge](https://img.shields.io/badge/Course-IT%20%26%20Japanese%20Language-blue)  
![Date Badge](https://img.shields.io/badge/Date-February%2015%2C%202025-brightgreen)  
![Platform Badge](https://img.shields.io/badge/Platform-Python%20%7C%20scikit--learn-yellow)  

**👨‍🏫 Instructors:** [Hafiz Muhammad Umair Munir](https://www.linkedin.com/in/hafiz-muhammad-umair-munir-b929b0173/), [Abdul Ahad](https://www.linkedin.com/in/ahad-pro-soft/), [Abdul Hanan Ashraf](https://www.linkedin.com/in/abdul-hanan-ashraf-156115157/)  
**🎓 Organized by:** [Plus W 株式会社](https://www.linkedin.com/company/plus-w) & [Pakistan Japan Centre](https://www.linkedin.com/company/pakistan-japan-centre)  
**🌐 Supported by:** [AOTS](https://www.linkedin.com/company/aotsjapan/) & [Overseas Employment Corporation (OEC)](https://oec.gov.pk/)  

---

## 🧠 Topics Covered

- 📈 Multiple Linear Regression
- 🧮 Optimizing linear models with Gradient Descent
- ✍️ Manual implementation of regression
- 🧠 Introduction to Support Vector Machines (SVM)
- 💠 RBF vs Linear Kernels
- 🔍 SVM for classification of handwritten digits
- 📊 Visualizing decision boundaries with matplotlib

---

## 📁 Class Summary

### 📌 Part 1: Multiple Linear Regression (MLR)

**Dataset Used:**
```python
data = {
    'X1': [1,2,3,4,5],
    'X2': [2,4,6,8,10],
    'Y':  [3,6,9,12,15]
}
```

**Model Implementation:**
```python
from sklearn.linear_model import LinearRegression

model = LinearRegression()
model.fit(X_train, Y_train)
print("Coefficient:", model.coef_)
print("Intercept:", model.intercept_)
```

📌 _Result:_
```
Coefficient: [0.6 1.2]
Intercept: ≈ 0
```

---

### 📌 Part 2: Gradient Descent Implementation (Project 1)

**Manual Optimization:**
```python
def gradient_descent(X, y, learning_rate=0.01, iterations=1000):
    m, c = 0, 0
    n = len(y)
    for _ in range(iterations):
        y_pred = m * X + c
        dm = (-2/n) * np.sum(X * (y - y_pred))
        dc = (-2/n) * np.sum(y - y_pred)
        m = m - learning_rate * dm
        c = c - learning_rate * dc
    return m, c
```

📌 _Output:_
```
Optimized Slope (m): ≈ 1.995
Optimized Intercept (c): ≈ 0.017
```

---

### 📌 Part 3: SVM with Linear & RBF Kernels

```python
from sklearn.svm import SVC

# Linear kernel
linear_svm = SVC(kernel='linear')
linear_svm.fit(X, y)

# RBF kernel
rbf_svm = SVC(kernel='rbf', gamma='scale')
rbf_svm.fit(X, y)
```

**Visualization Function:**
```python
def plot_decision_boundary(model, X, y, title):
    ...
    plt.title(title)
    plt.show()
```

📊 _Decision boundaries plotted using matplotlib._

---

### 📌 Part 4: Digit Classification with SVM (Project 2)

**Pipeline Overview:**
1. Load digit dataset
2. Split data (80/20)
3. Standardize using `StandardScaler`
4. Train `SVC(kernel='rbf', gamma=0.01, C=10)`
5. Predict and evaluate using `classification_report`

```python
from sklearn.datasets import load_digits
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from sklearn.svm import SVC
from sklearn.metrics import classification_report

digits = load_digits()
X_train, X_test, y_train, y_test = train_test_split(digits.data, digits.target, test_size=0.2)
scaler = StandardScaler()
X_train = scaler.fit_transform(X_train)
X_test = scaler.transform(X_test)

svm = SVC(kernel='rbf', gamma=0.01, C=10)
svm.fit(X_train, y_train)
y_pred = svm.predict(X_test)

print(classification_report(y_test, y_pred))
```

📷 _Visual output of test digits with predictions:_
```python
for ax in axes.flat:
    index = random.randint(0, len(y_test)-1)
    ax.imshow(digits.images[index], cmap='gray')
    ax.set_title(f"Pred: {y_pred[index]}")
    ax.axis("off")
```

---

## 📚 References

- [Scikit-learn documentation](https://scikit-learn.org/stable/)
- [NumPy documentation](https://numpy.org/doc/)
- Class slides & practical tasks from Class 8 (Feb 15, 2025)

---
