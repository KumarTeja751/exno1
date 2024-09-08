# Exno:1-Data Cleaning Process
### Name:NARAMALA KUMARTEJA
### Register Number: 212223230132
### Department : Artificial Intelligence amd Data Science
# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
### Colab Link:
https://colab.research.google.com/drive/1NyAt4-fQSF9rTfg_UV2anMBzG6PZnj5Q?usp=sharing
### Cleaning process
```
import pandas as pd
data={'Name':['Alice','Bob','Charlie','Dave','Eve'],'Age':[25,32,None,41,28],'Salary':[50000,None,70000,90000,60000]}
df=pd.DataFrame(data)
df
```
![image](https://github.com/user-attachments/assets/2ce35b35-e6fb-4168-9e4f-1fa3b4bd70b5)
```
#remove the missing value in the salary with the particular row
df_clean=df.dropna(subset=['Salary'])
df_clean
```
![image](https://github.com/user-attachments/assets/62259927-911a-4883-8729-625536053563)
```
#the row with complete missing value then the row get deleted
df_clean_all=df.dropna(how='all')
df_clean_all
```
![image](https://github.com/user-attachments/assets/912054e9-bb08-46e7-b4ac-8338e0b72ad0)
```
#delete the row which contain one missing value
df_cleaned_any=df.dropna(how='any')
df_cleaned_any
```
![image](https://github.com/user-attachments/assets/107b33c4-9141-4297-8508-01f2d7911572)
```
import pandas as pd
import numpy as np
data={'Name':['Alice','Bob','Charlie','Dave','Eve','Bob','Charlie'],'Age':[25,np.nan,35,41,np.nan,np.nan,85],'Salary':[50000,np.nan,70000,np.nan,60000,np.nan,70000]}
df=pd.DataFrame(data)
df
```
![image](https://github.com/user-attachments/assets/962948e9-812e-40a4-9c2e-c04ee04ca319)
```
~df.duplicated()
```
![image](https://github.com/user-attachments/assets/718615dd-d61a-4d50-91ec-e3a25936b877)
```
df_clean=df.dropna(how='any')
df_clean
```
![image](https://github.com/user-attachments/assets/33b1bd43-443b-402e-866a-9de1f9fb42f1)
```
#replace the nan with replace of an value
df_filled=df.fillna(0)
df_filled
```
![image](https://github.com/user-attachments/assets/60239c1f-9e3d-46e4-a4f3-cc4a28b6d4ca)
```
#forward fill where it will fill the before data set
df_ffill=df.fillna(method='ffill')
df_ffill
```
![image](https://github.com/user-attachments/assets/a088b480-2e0f-4cc6-b668-960e780ec8e1)
```
#where it will fill the back ward data into the current data
df_bfill=df.bfill()
df_bfill
```
![image](https://github.com/user-attachments/assets/04119735-bbd2-42b5-9212-b71fa5c0c78f)
```
#to find the mean of an age
df_mean=df.fillna(df['Age'].mean())
df_mean
```
![image](https://github.com/user-attachments/assets/cfd56279-797f-463f-9486-7b096b192c17)

### Outlier detection and removal process
```
import pandas as pd
import seaborn as sns
import numpy as np
df=pd.read_csv('iris (1).csv')
df
```
![image](https://github.com/user-attachments/assets/e9799a2d-aace-4095-b503-abc86f2ddaa1)
```
sns.boxplot(data=df['sepal_width'])
```
![image](https://github.com/user-attachments/assets/dae8d1da-c90f-41d7-a782-1be5a92d3ced)
```
sns.boxenplot(data=df['sepal_width'])
```
![image](https://github.com/user-attachments/assets/91f2e9d8-ddb5-48f6-9625-eb0fa599d081)
```
q1=df['sepal_width'].quantile(0.25)
q3=df['sepal_width'].quantile(0.75)
IQR=q3-q1
IQR
```
![image](https://github.com/user-attachments/assets/c836c0ad-cab1-4742-b6b1-9266f97b8454)
```
lower_bound=q1-1.5*IQR
upper_bound=q3+1.5*IQR
print(lower_bound,upper_bound)
```
![image](https://github.com/user-attachments/assets/9171fd15-ffd3-4bf7-89d8-b742bf6f56e8)
```
print("Q1:",q1)
print("Q3:",q3)
print("IQR:",IQR)
print("Lower Bound:",lower_bound)
print("Upper_bound:",upper_bound)
```
![image](https://github.com/user-attachments/assets/b0a5510b-11ba-4acb-b6b6-081f6026712b)
```
dt=df[(df['sepal_width']>=lower_bound) & (df['sepal_width']<=upper_bound)]
dt
```
![image](https://github.com/user-attachments/assets/1a7ba40a-23ff-4c6e-87bc-01759bb1d5d8)
```
dt['sepal_width'].dropna()
```
![image](https://github.com/user-attachments/assets/650b2f56-1b47-4e0f-9ff1-add24d87486d)
```
sns.boxplot(data=dt['sepal_width'])
```
![image](https://github.com/user-attachments/assets/fc395e69-5c8c-486e-b83f-24c0db706775)
```
sns.boxenplot(data=dt['sepal_width'])
```
![image](https://github.com/user-attachments/assets/9052e7c9-a291-4b2e-bb7a-0faf27b0a21a)
```
sns.scatterplot(data=dt['sepal_width'])
```
![image](https://github.com/user-attachments/assets/9fdd34c2-d9d0-4962-8b61-c5bbb713021c)


# Result
Hence,the data cleaning process and the detection of outlier and removal of it has been done successfully.
