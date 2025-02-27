# 📊 India Census 2011 Data Analysis  

## 📌 Overview  
This project analyzes the **India Census 2011 dataset**, exploring key demographic aspects such as **population distribution, literacy rates, religious composition, and sex ratios**. Various **data visualization techniques** using **Pandas, Matplotlib, and Seaborn** were employed to uncover meaningful insights.  

---

## 🚀 Features & Insights  

### ✅ **State-wise Population Distribution**  
- Aggregated **total population** by state.  
- Used a **bar chart** to visualize the distribution.  

```python
State = data.groupby('State name')[['Male', 'Female']].sum().sort_values(by='Male')

plt.figure(figsize=(12, 6))
sns.barplot(x="State name", y="Population", data=data, ci=None)
plt.xticks(rotation=90)
plt.title("State-wise Population Distribution (2011 Census)")
plt.xlabel("State")
plt.ylabel("Population")
plt.show()
```

---

### ✅ **Religious Composition in India**  
- Summarized population based on **major religions**.  
- Used a **pie chart** for visual representation.  

```python
religion_totals = data[["Hindus", "Muslims", "Christians", "Sikhs", "Buddhists", "Jains"]].sum()
colors = ['orange', 'green', 'red', 'blue', 'yellow', 'purple']

plt.pie(religion_totals, startangle=140, colors=colors, autopct='%1.1f%%', explode=(0,0.1,0.2,0.2,0.1,0))
plt.title("Religious Composition of India (2011 Census)")
plt.legend(labels=religion_totals.index, loc="upper right")
plt.show()
```

---

### ✅ **Literacy Rate Distribution**  
- Used **boxplots** to analyze literacy rates across **all states** and **selected states** (West Bengal, Karnataka, Andhra Pradesh, Kerala).  
- Visualized **district-wise literacy** for West Bengal.  

```python
sns.boxplot(x="State name", y="Literate_Education", data=data)
plt.xticks(rotation=90)
plt.title("Literacy Rate Distribution Across States")
plt.xlabel("State")
plt.ylabel("Literacy Rate (%)")
plt.show()
```

#### 📌 **3D Literacy Rate Visualization** (West Bengal, Maharashtra & Karnataka)  

```python
fig = plt.figure(figsize=(12, 8))
ax = fig.add_subplot(111, projection='3d')

ax.scatter(filtered_data["District Numeric"], filtered_data["State Numeric"], filtered_data["Literate_Education"],
           c=filtered_data["Literate_Education"], cmap="viridis", marker="o")

ax.set_xlabel("District")
ax.set_ylabel("State")
ax.set_zlabel("Literacy Rate (%)")
ax.set_title("3D Literacy Rate Distribution Across Karnataka & West Bengal")

plt.show()
```

---

### ✅ **Comparison of Literacy Rates in West Bengal & Karnataka**  
- Used **bar charts** to compare literacy rates across districts.  

```python
fig, axes = plt.subplots(1, 2, figsize=(14, 6), sharey=True)

axes[0].bar(wb_data["District name"], wb_data["Literate_Education"], color="royalblue")
axes[0].set_title("Literacy Rate in West Bengal Districts")
axes[0].set_xlabel("District")
axes[0].set_ylabel("Literacy Rate (%)")
axes[0].tick_params(axis="x", rotation=90)

axes[1].bar(ka_data["District name"], ka_data["Literate_Education"], color="darkorange")
axes[1].set_title("Literacy Rate in Karnataka Districts")
axes[1].set_xlabel("District")
axes[1].tick_params(axis="x", rotation=90)

plt.tight_layout()
plt.show()
```

---

### ✅ **State-wise Sex Ratio Analysis**  
- **Calculated Sex Ratio** (Females per 1000 Males) and added it to the dataset.  
- Used a **bar chart** to visualize **gender balance** across states.  

```python
if "Male" in data.columns and "Female" in data.columns:
    data["Sex Ratio"] = (data["Female"] / data["Male"]) * 1000
    data.to_csv("updated_file_i_census_2011.csv", index=False)
    print("Sex Ratio column added and saved to 'updated_file.csv'.")
```

```python
plt.figure(figsize=(12, 6))
sns.barplot(x="State name", y="Sex Ratio", data=state_sex_ratio, palette="coolwarm")
plt.title("State-wise Sex Ratio (Females per 1000 Males)")
plt.xlabel("State Name")
plt.ylabel("Sex Ratio (Females per 1000 Males)")
plt.xticks(rotation=90)
plt.grid(axis="y", linestyle="--", alpha=0.6)
plt.show()
```

---

### ✅ **Pairplot Analysis: Correlation Between Key Census Indicators**  
- Explored **relationships between Population, Literacy, Sex Ratio, and Workforce**.  

```python
sns.pairplot(data[["Population", "Literate", "Sex Ratio", "Workers"]])
plt.show()
```

---

## 📁 Dataset  
The dataset used for this project is **India Census 2011**, which contains demographic statistics for various states and districts.

- **Columns include:**  
  - `State name`
  - `District name`
  - `Population`
  - `Male`, `Female`
  - `Literate`, `Literate_Education`
  - `Workers`
  - `Religious Composition`
  - `Sex Ratio (calculated column)`

---

## 🛠️ Tech Stack  
- **Python 🐍**  
- **Pandas 📊**  
- **Matplotlib 🎨**  
- **Seaborn 🔥**  
- **3D Plotting (mpl_toolkits.mplot3d) 🏗️**  

---

## 🔥 Key Learnings  
✔️ **Data Wrangling & Cleaning** using Pandas.  
✔️ **Data Visualization** for trend analysis & comparison.  
✔️ **Statistical Insights** from boxplots, pairplots & 3D scatter plots.  
✔️ **Geographical & Demographic Comparisons** based on Census data.  

---

## 📢 How to Use  
1. Clone the repository:  
   ```bash
   git clone https://github.com/Soumyadeep143/CENSUS_2011_IND.git
   ```
2. Install dependencies:  
   ```bash
   pip install pandas matplotlib seaborn
   ```
3. Run the analysis scripts:  
   ```bash
   python analysis.py
   ```
4. View visualizations & insights!  

---

## 🤝 Let's Connect  
💬 **Interested in discussing data science & analytics?** Connect with me!  

📌 **GitHub**: [https://github.com/Soumyadeep143]  
📌 **LinkedIn**: [https://www.linkedin.com/in/soumyadeep-sarkar-57ab6426a/]  

---

### 📢 **If you found this project insightful, don’t forget to ⭐ the repository!**  

#DataScience #Python #CensusAnalysis #DataVisualization #MachineLearning #BigData #IndiaCensus
