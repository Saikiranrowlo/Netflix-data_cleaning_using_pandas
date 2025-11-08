
# 🎬 Netflix Data Cleaning using Python (Pandas)

This project demonstrates how to clean and preprocess a Netflix dataset using **Python** and **Pandas**.  
It covers handling missing values, renaming columns, removing duplicates, formatting data, and saving a cleaned version of the dataset.

---

## 📁 Project Files

| File Name | Description |
|------------|-------------|
| `netflix1.csv` | Raw dataset containing Netflix show details |
| `Cleaned_Data.csv` | Cleaned and processed dataset |
| `data_cleaning.py` | Python script for cleaning the dataset |

---

## 🧠 Objective

The goal of this project is to:
- Perform **data cleaning and preprocessing** using Pandas  
- Prepare the dataset for **data analysis or visualization**  
- Demonstrate common **data wrangling operations** on a real dataset

---

## ⚙️ Steps Performed

1. Import Libraries
   ```python
   import pandas as pd
   
2.Load the Dataset
 ```python
data = pd.read_csv("netflix1.csv")

3.**Basic Data Inspection**
 ```python
data.head()
data.info()
data.columns


4.**Drop Unnecessary Columns**
 ```python
data.drop(columns="rating", inplace=True)


5.**Capitalize Column Names**
 ```python
new_columnNames = [i.capitalize() for i in data.columns]
data.columns = new_columnNames


6.**Check for Duplicates and Missing Values**
 ```python
data.duplicated().sum()
data.isna().sum()


7.**Transform Columns**

**Split the Show_id column and convert it to integer**
 ```python
data["Show_id"] = data["Show_id"].apply(lambda x : x.split("s")[1])
data["Show_id"] = data["Show_id"].astype(int)


**Replace “/” with “-” in Date_added**
 ```python
data["Date_added"] = data["Date_added"].apply(lambda x : x.replace("/", "-"))


**View Country Distribution**
 ```python
data["Country"].value_counts()


8.**Export the Cleaned Dataset**
 ```python
data.to_csv("Cleaned_Data.csv", index=False)
