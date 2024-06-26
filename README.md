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

### Interest_Rate Distribution through Histogram

plt.hist(LoansData['Interest_Rate'],color='green')

plt.title('Interest_Rate')

plt.show()

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/a814b43b-26cb-41ad-9f85-9f9550b6781c)

The following histogram represents the distribution of the Interest_Rate for a given dataset. Understanding the distribution of interest rates is essential for analyzing loan data, financial products, and market conditions.

The most frequent interest rate is around 12.5%, indicating this is the most common rate in the dataset.

### Debt_to_Income_Ratio Distribution through Histogram

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/f2993219-3274-481b-a813-c982cea74ac5)

The following histogram represents the distribution of the Debt_to_Income_Ratio for a given dataset. This metric is crucial for understanding the financial health of individuals or entities within the dataset.

The most frequent debt-to-income ratio is around 15%, indicating this is the most common ratio in the dataset.

### Checking for the Duplicate values in the Dataset

LoansData.duplicated().sum()

No Duplicate Data has been found in our DataFrame

## Renaming the variables

LoansData = LoansData.rename(columns = {'LoanID':'Loan_id','State':'States'})

## Missing Value Treatment

LoansData.isna().sum()

There are approximately 3% of Missing values in Employment Variable

**Creating a UDF which can automate the missing value treatment.**

def missing_value_treatment(s):
    
    if s.dtype == 'O':
        
        s = s.fillna(s.mode())
    
    else:
        
        s = s.fillna(s.median())
    
    return s

LoansData = LoansData.apply(missing_value_treatment)

Now there are no missing values in our data.

## Separating the Categorical variables and Numerical variables

Categorical = [var for var in LoansData.columns if LoansData[var].dtype == 'O']

Cat_Data = LoansData[Categorical]

Cat_Data['Loan_id'] = LoansData['Loan_id']

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/dfabe187-56b3-4769-9261-fe7191377051)

There are 2500 records and 4 variables in Cat_Data.

Numerical = [var for var in LoansData.columns if LoansData[var].dtype != 'O']

Num_Data = LoansData[Numerical]

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/5d16bd59-7399-44c6-95af-8d013b11e3f4)

There are 2500 records and 12 variables in Num_Data.

## Outlier Treatment

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/b7b6628e-b430-4985-9db9-5672db7ba668)

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/8f56aaa4-5831-467a-b743-dc3d4b8b8baf)

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/da139728-c78a-4d52-b904-6c44d3a16ffa)

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/594b789f-2143-47fc-a79f-7c559e866c21)

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/2d0a179d-f3d8-4290-93b3-a2b2dcb750eb)

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/28f9d218-2455-4a3b-9bef-3012566ca23d)

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/c47b1b42-c35a-4dca-afbf-e6278e1b1b32)

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/0750f3a2-785c-48a4-bf22-d4a02f1bfe04)

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/96b45e31-3c70-4ce3-b467-eab79b4e0c40)

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/6eb5cbfb-eba1-4049-9cf7-75b0f93504f8)

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/614881e3-7660-4111-8c53-3e6f69f462e6)

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/6fd65a2c-87ba-400d-bea5-308bf113dc6d)

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/c2165b92-f84b-4583-bc94-fa2f81fe6345)

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/6ba11f56-baad-4798-a147-4a5ca6d1ec60)

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/c4446928-c546-4e7f-a89f-6b7532030531)

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/6c121df6-5278-4cce-940b-7495fe9eae53)

## Outlier treatment using IQR Method

def outlier_IQR(s):
    
    m = s.quantile(0.5)
    
    q1 = s.quantile(0.25)
    
    q3 = s.quantile(0.75)
    
    q_1p = s.quantile(0.01)
    
    q_99p = s.quantile(0.99)
    
    iqr = q3 - q1
    
    lc = q1 - 1.5*iqr
    
    uc = q3 + 1.5*iqr
    
    result = pd.Series([m,q1,q3,q_1p,q_99p,iqr,lc,uc])
    
    result.index = ['median','first_quartile','third_quartile','pc_1','pc_99','iqr','lower_cutoff','upper_cutoff']
    
    return result

def outliertreat_IQR(d):
    
    m = d.quantile(0.5)
    
    q1 = d.quantile(0.25)
    
    q3 = d.quantile(0.75)
    
    q_1p = d.quantile(0.01)
    
    q_99p = d.quantile(0.99)
    
    iqr = q3 - q1
    
    lc = q1 - 1.5*iqr
    
    uc = q3 + 1.5*iqr
    
    return lc,uc

Num_Data.apply(outliertreat_IQR)

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/3f5727a8-460d-486f-b6a3-4b171b7fd2f9)

Num_Data.apply(outlier_IQR)

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/e07fb93e-3ed2-4b42-8275-79a62e20b255)

### Amount Requested

Num_Data['Amount_Requested'] = Num_Data.Amount_Requested.clip(lower = -10500.00, upper = 33500)

sns.boxplot(Num_Data.Amount_Requested)

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/7d5af6f0-fe99-423c-abc8-ccf236b87650)

### Amount_Funded_By_Investors

Num_Data['Amount_Funded_By_Investors'] = Num_Data.Amount_Funded_By_Investors.clip(lower = -9000, upper = 31000)

sns.boxplot(Num_Data.Amount_Requested)

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/ffeae620-62d0-4e30-b28f-6b8bbe3f989e)

### Interest Rate

Num_Data['Interest Rate'] = Num_Data.Interest_Rate.clip(lower = 1.70, upper = 24.26)

sns.boxplot(Num_Data.Interest_Rate)

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/b30a7381-f8b3-4f88-8212-5fb94b1cee57)

### FICO_Range

Num_Data['FICO_Range'] = Num_Data.FICO_Range.clip(lower = 612.5, upper = 792.5)

sns.boxplot(Num_Data.FICO_Range)

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/e55beb6e-022a-478c-9ae6-497adb35863d)

### Open_CREDIT_Lines

Num_Data['Open_CREDIT_Lines'] = Num_Data.Open_CREDIT_Lines.clip(lower = -2.0, upper = 22.0)

sns.boxplot(Num_Data.Open_CREDIT_Lines)

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/46d0145a-d1ed-4241-82f2-8cbe0d044110)

### Inquiries_in_the_Last_6_Months

Num_Data['Inquiries_in_the_Last_6_Months'] = Num_Data.Inquiries_in_the_Last_6_Months.clip(lower = -1.5, upper = 2.5)

sns.boxplot(Num_Data.Inquiries_in_the_Last_6_Months)

![image](https://github.com/Swagath123Koyada/EDA_on_LoansData/assets/164196153/5f20e02c-caa0-4288-ba25-19fea94fc6a6)
















