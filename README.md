### <div align="center"> <h1> Exploratory Data Analysis on Loans Data </h1> </div>



<p align="center">
  <img src="https://github.com/Swagath123Koyada/FinancialInsightsEDA/assets/164196153/5c26e3c1-c676-40f2-bae9-a996e5a12018" alt="">
</p>



This project involves conducting exploratory data analysis (EDA) on a dataset containing loan information from a private financial firm. Through this analysis, we aim to gain insights into the characteristics of the loans, identify patterns, and detect any anomalies or outliers that may impact decision-making processes.

### Features

- Importing necessary modules including numpy, pandas, matplotlib.pyplot, datetime, and seaborn.

- Loading the dataset into a Jupyter Notebook for analysis.

- Performing EDA to understand the structure and content of the data.

- Handling naming conventions and data type conversions for consistency and clarity.

- Visualizing key aspects of the data using matplotlib and seaborn.

- Treating missing values to ensure data integrity.

- Identifying and addressing outliers using the interquartile range (IQR) method.

- Standardizing the data to facilitate comparisons and analyses.

### Tool Used : Jupyter Notebook

## Key Steps

**Data Import:** Utilize Python libraries such as pandas to import the dataset into a Jupyter Notebook for analysis.

**Data Exploration:** Explore the structure and content of the dataset to understand its features, data types, and overall distribution.

**Data Cleaning:**

Handle naming conventions and data type conversions for consistency and clarity.

Treat missing values using appropriate techniques to ensure data integrity.

**Data Visualization:** Utilize matplotlib and seaborn libraries to create visualizations such as histograms, box plots, and scatter plots to explore relationships and distributions within the data.

**Outlier Detection and Treatment:** Identify and address outliers using methods like the interquartile range (IQR) to ensure accurate analysis.

**Data Standardization:** Standardize the data to facilitate comparisons and analyses, ensuring consistency across variables.

## Let's Get Started :

**First of all Import all the necessary modules in the Jupyter Notebook.**

- import numpy as np                       for the 2-d matrices

- import pandas as pd                      for the data frames

- import matplotlib.pyplot as plt          for data vizualizations 

- import datetime as dt                    for the datetime data

- import seaborn as sns                    for the visualizations 

**Now Import the Dataset.**

LoansData= pd.read_csv('LoansData (1).csv')

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/aa199f8d-db97-41cd-b5fa-77385de9b3ef)

After Importing the dataset, Just check the shape. So that we can get an idea of the dimension of the dataframe and info to check if there are any necessary datatype conversions. 

**Now Perform the EDA.**

First we need to change the variable name as per naming convention

- names can be of any length

- always starts with letters

- should not start with a number or special characters.

- should not have spaces or any special characters except underscore.

We can use this code to change the variable name

LoansData.columns = [i.replace('.','_') for i in LoansData.columns]

**Performing necessary Datatype Conversions**

LoansData['Debt_To_Income_Ratio']= LoansData['Debt_To_Income_Ratio'].str.replace('%','').astype('float')

LoansData['Employment_Length'] = LoansData['Employment_Length'].str.replace('years','').str.replace('year','').str.replace('<','').str.replace('+','').astype('float')

LoansData['Interest_Rate'] = LoansData['Interest_Rate'].str.replace('%','').astype('float')

LoansData['Loan_Length'] = LoansData['Loan_Length'].str.replace('months','').astype('float')

LoansData['FICO_Range'] = LoansData['FICO_Range'].str.split('-',expand = True)[0].astype('float')

We have done all the necessary changes in our DataFrame

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/cb3170d1-7ef4-4310-8464-a2cd6491d67c)

**Now check the Distribution of customers by loan lengths**

print(LoansData['Loan_Length'].value_counts())

LoansData['Loan_Length'].value_counts().plot(kind = 'bar',color = 'blue',figsize = (5,5))

plt.title("Distribution of customers by their loan lengths.")

plt.xlabel("Loan length")

plt.ylabel("No of customers")

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/60a79fc8-5b68-4c38-a06a-54b934f8bf09)

**Check the Distribution of customers by State**

print(LoansData['State'].value_counts())

LoansData['State'].value_counts().plot(kind = 'bar',color = 'purple',figsize = (20,15))

plt.title("Distribution of customers by their State.")

plt.xlabel("States")

plt.ylabel("No of customers")

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/c652aa3e-9692-44a1-b305-22ef52edf270)

**Distribution of customers by loan purpose**

print(LoansData['Loan_Purpose'].value_counts())

LoansData['Loan_Purpose'].value_counts().plot(kind = 'bar',color = 'yellow',figsize = (10,5))

plt.title("Distribution of customers by their Loan_Purpose.")

plt.xlabel("Loan_Purpose")

plt.ylabel("No of customers")

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/7f0baf9f-0b16-44e9-868e-55af065cf09d)


































