
# 📊 Data Visualization with Matplotlib and Seaborn - Class 6

Welcome to the Class 6 repository! This class covers **Data Visualization** using **Matplotlib** and **Seaborn**. In this class, we explored various plotting techniques, including line plots, scatter plots, 3D plots, and customizing visuals. You'll also find examples of data manipulation using `pandas` and working with missing data.

---

## 📝 Table of Contents
1. [📚 Overview](#overview)
2. [💻 Class Resources](#class-resources)
3. [🖼️ Visualizations in Python](#visualizations-in-python)
4. [🔧 Class Assignments](#class-assignments)
5. [🔗 Useful Links](#useful-links)

---

## 📚 Overview
In **Class 6**, we focused on:
- **Matplotlib** for data visualization.
- **Creating various types of plots**: Line Plots, Scatter Plots, 3D Scatter Plots, and more.
- **Data manipulation** with `pandas`: Handling missing values, filtering data, and merging dataframes.
- **Customizing plots**: Adjusting markers, colors, and adding annotations.

### 🗣️ Key Topics:
- Line plots: Display trends over time.
- Scatter plots: Display relationships between variables.
- 3D scatter plots: Visualize three variables in space.
- Customizations: Line styles, markers, color mappings.

---

## 💻 Class Resources

### 📑 **IPython Notebook**:
- The notebook contains all the code examples from the class, including creating line plots, scatter plots, 3D plots, and applying data transformations.
  
You can find the notebook [here](./Lecture_6_Code.ipynb).

---

## 🖼️ Visualizations in Python

Here are a few examples of what we've created during Class 6:

### 1. **Stock Market Trend Analysis** 📈
```python
import numpy as np
import matplotlib.pyplot as plt

# Simulated stock prices 
days = np.arange(1, 31)
prices = np.cumsum(np.random.randn(30) * 2 + 100)  # Randomized stock prices 
plt.figure(figsize=(10, 5), dpi=100)
plt.plot(days, prices, linestyle='-', marker='o', color='b', markersize=6, label="Stock Price")
# Adding labels, title, and legend 
plt.xlabel("Day")
plt.ylabel("Price (USD)")
plt.title("Stock Price Trend")
plt.legend()
plt.grid(True)
# Show the plot 
plt.show()
```

### 2. **Customizing Temperature Trends with Line Styles and Markers** 🌡️
```python
import matplotlib.pyplot as plt 
import numpy as np 

days = np.arange(1, 11) 
temp_day = np.random.randint(25, 35, size=10) 
temp_night = np.random.randint(15, 25, size=10) 

plt.figure(figsize=(8, 5))

# Day temperature 
plt.plot(days, temp_day, linestyle='--', marker='o', color='r', markersize=8, label="Day Temperature")

# Night temperature 
plt.plot(days, temp_night, linestyle='-', marker='s', color='b', markersize=8, label="Night Temperature")

# Adding labels, title, and legend 
plt.xlabel("Days") 
plt.ylabel("Temperature (°C)") 
plt.title("Daily Temperature Variation") 
plt.legend() 
plt.grid() 

plt.show()
```

### 3. **Population Growth Visualization** 🌍
```python
import matplotlib.pyplot as plt 
import numpy as np 

# Sample data 
countries = ["USA", "China", "India", "Brazil", "Germany"] 
pop_growth = np.array([0.8, 1.2, 1.5, 0.9, 0.5])  # Growth in percentage 
population = np.array([331, 1441, 1380, 213, 83])  # Population in millions 

# Scatter plot with size variation 
plt.figure(figsize=(8, 5)) 
plt.scatter(pop_growth, population, c=population, cmap='viridis', s=population * 2, alpha=0.6)

# Labels 
plt.xlabel("Population Growth (%)") 
plt.ylabel("Total Population (millions)") 
plt.title("Population Growth vs. Total Population")

# Adding annotations 
for i, country in enumerate(countries): 
    plt.annotate(country, (pop_growth[i], population[i]), fontsize=10, ha='right')

plt.colorbar(label="Population (millions)") 
plt.grid() 
plt.show()
```

### 4. **Customer Segmentation with Scatter Plot (Color Categories)** 🛒
```python
import matplotlib.pyplot as plt 
import numpy as np 

# Simulated customer data 
np.random.seed(42) 
age = np.random.randint(18, 60, 100) 
spending_score = np.random.randint(20, 100, 100) 
categories = np.random.choice([1, 2, 3, 4], 100)  # 4 different customer types

# Scatter plot with category-based colors 
plt.figure(figsize=(8, 5)) 
scatter = plt.scatter(age, spending_score, c=categories, cmap='jet', alpha=0.7)

plt.xlabel("Age") 
plt.ylabel("Spending Score") 
plt.title("Customer Segmentation Analysis") 
plt.colorbar(label="Customer Category")

plt.grid() 
plt.show()
```

### 5. **3D Scatter Plot of Sales Data** 🛍️
```python
import numpy as np 
import matplotlib.pyplot as plt 
from mpl_toolkits.mplot3d import Axes3D 

# Sample sales data 
np.random.seed(42) 
region = np.random.randint(1, 6, 50)  # 5 regions 
sales = np.random.randint(500, 10000, 50) 
profit = np.random.randint(50, 1000, 50)

fig = plt.figure(figsize=(10, 6)) 
ax = fig.add_subplot(111, projection='3d')

# Scatter plot 
scatter = ax.scatter(region, sales, profit, c=profit, cmap='coolwarm', s=50, alpha=0.7)

# Labels 
ax.set_xlabel("Region") 
ax.set_ylabel("Sales") 
ax.set_zlabel("Profit") 
ax.set_title("3D Sales Performance Analysis") 
fig.colorbar(scatter, label="Profit")

plt.show()
```

---

## 🔗 Useful Links

- [Matplotlib Documentation](https://matplotlib.org/stable/contents.html)  
- [Seaborn Documentation](https://seaborn.pydata.org/)  
- [Pandas Documentation](https://pandas.pydata.org/pandas-docs/stable/)

---