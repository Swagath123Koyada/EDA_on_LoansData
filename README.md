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

### Key Steps

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

- First we need to change the variable name as per naming convention

LoansData.columns = [i.replace('.','_') for i in LoansData.columns]

**Performing necessary Datatype Conversions**

LoansData['Debt_To_Income_Ratio']=LoansData['Debt_To_Income_Ratio'].str.replace('%','').astype('float')

LoansData['Employment_Length']=LoansData['Employment_Length'].str.replace('years','').str.replace('year','').str.replace('<','').str.replace('+','').astype('float')

LoansData['Interest_Rate']=LoansData['Interest_Rate'].str.replace('%','').astype('float')

LoansData['Loan_Length']=LoansData['Loan_Length'].str.replace('months','').astype('float')

LoansData['FICO_Range']=LoansData['FICO_Range'].str.split('-',expand = True)[0].astype('float')

We have done all the necessary changes in our DataFrame

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/cb3170d1-7ef4-4310-8464-a2cd6491d67c)

### Now check the Distribution of customers by loan lengths

print(LoansData['Loan_Length'].value_counts())

LoansData['Loan_Length'].value_counts().plot(kind = 'bar',color = 'blue',figsize = (5,5))

plt.title("Distribution of customers by their loan lengths.")

plt.xlabel("Loan length")

plt.ylabel("No of customers")

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/60a79fc8-5b68-4c38-a06a-54b934f8bf09)

**1952 Customers has chosen the loan length of 36.0**

### Check the Distribution of customers by State

print(LoansData['State'].value_counts())

LoansData['State'].value_counts().plot(kind = 'bar',color = 'purple',figsize = (20,15))

plt.title("Distribution of customers by their State.")

plt.xlabel("States")

plt.ylabel("No of customers")

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/c652aa3e-9692-44a1-b305-22ef52edf270)

**CA State has the most number of Customers of 433**

### Distribution of customers by loan purpose

print(LoansData['Loan_Purpose'].value_counts())

LoansData['Loan_Purpose'].value_counts().plot(kind = 'bar',color = 'yellow',figsize = (10,5))

plt.title("Distribution of customers by their Loan_Purpose.")

plt.xlabel("Loan_Purpose")

plt.ylabel("No of customers")

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/7f0baf9f-0b16-44e9-868e-55af065cf09d)

**1307 Customers has the loan purpose of debt_consolidation**

### Distribution of customers by Home ownership

print(LoansData['Home_Ownership'].value_counts())

LoansData['Home_Ownership'].value_counts().plot(kind = 'bar',color = 'Maroon',figsize = (8,5))

plt.title("Distribution of customers by their Home_Ownership.")

plt.xlabel("Home_Ownership")

plt.ylabel("No of customers")

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/399c7ca4-c1e4-4618-9257-5e0c19b1489d)

**Most of the Customers has a Home Ownership of Mortgage and Rent**

### Distribution of Employment Length by their loan lengths

print(LoansData['Loan_Length'].value_counts())

LoansData['Loan_Length'].value_counts().plot(kind = 'line',color = 'black',figsize = (8,5))

plt.title("Distribution of Employment.Length by their loan lengths.")

plt.xlabel("Loan length")

plt.ylabel("Employment.Length")

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/2a43f54d-d5ae-495c-9f50-f262be69f7dc)

**Most of the Cuatomers has a Loan Length of 36 months.**

### Amount Requested compared to the corresponding Interest Rate

plt.scatter(LoansData['Amount_Requested'],LoansData['Interest_Rate'])

plt.title("Comparison of Amount Requested and Interest Rate")

plt.xlabel('Amount_Requested')

plt.ylabel('Interest_Rate')

plt.colorbar()

plt.show()

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/791dc0d9-89db-4f4c-84bb-5b5fb314d9d2)

**Most of the Customers has requested the amount of upto  10000−15000 and the Interest Rate being 5.0-17.5**

## Interest_Rate Distribution through Histogram

plt.hist(LoansData['Interest_Rate'],color='green')

plt.title('Interest_Rate')

plt.show()

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/a814b43b-26cb-41ad-9f85-9f9550b6781c)

## Debt_to_Income_Ratio Distribution through Histogram

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/f2993219-3274-481b-a813-c982cea74ac5)

The following histogram represents the distribution of the Debt_to_Income_Ratio for a given dataset. This metric is crucial for understanding the financial health of individuals or entities within the dataset.

The most frequent debt-to-income ratio is around 15%, indicating this is the most common ratio in the dataset.





