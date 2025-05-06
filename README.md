# Exno:1
Data Cleaning Process

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

Name : N.Lakshanya
Reg No: 212224230136
```
import pandas as pd
df=pd.read_csv("/content/DS SAMPLEIDS (1).csv")
df
```
![image](https://github.com/user-attachments/assets/21a29c08-2ee6-4e56-829a-0e5d79568e4a)
```
df.shape
```
![image](https://github.com/user-attachments/assets/0c0b751d-114c-4bf2-bd1c-3ce166639d95)

```
df.describe()
```
![image](https://github.com/user-attachments/assets/c4b56ed5-24e6-45d3-8331-5b14c92aafae)
```
df.info()
```
![image](https://github.com/user-attachments/assets/6eaae985-6fda-4b7c-a023-2f7e74b2f031)
```
df.head(10)
```
![image](https://github.com/user-attachments/assets/696de049-a2d9-4733-887a-af59442a9f56)
```

df.tail(10)
```
![image](https://github.com/user-attachments/assets/9b2f5bee-78eb-4391-afe5-289322de64cf)
```
df.isna().sum()
```
![image](https://github.com/user-attachments/assets/2829c324-a1fd-44cf-a440-c7112fc815af)
```
df.dropna(how='any').shape
```
![image](https://github.com/user-attachments/assets/47e10cae-3941-4a17-b97d-0c9da3b4c478)
```
df.shape
```
![image](https://github.com/user-attachments/assets/c3f939c8-985c-4d11-8121-bee2ce38b4ad)
```
x=df.dropna(how='any')
x
```
![image](https://github.com/user-attachments/assets/3979bef8-f0cf-4f81-9627-835f17db7c82)
```
mn=df.TOTAL.mean()
mn
```
![image](https://github.com/user-attachments/assets/4e1ea274-3254-4648-8d08-7966a3f2aaae)

```
df.TOTAL.fillna(mn,inplace=True)
df
```
![image](https://github.com/user-attachments/assets/e7fb1373-b478-42b8-95c2-d525ccdae895)
```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/6c4f2fd7-fa09-46d6-82be-06671e968566)
```
df.M1.fillna(method='ffill',inplace=True)
df
```
![image](https://github.com/user-attachments/assets/1a42144d-53a7-4ce6-b367-89fd34fcd99f)
```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/073ff215-c5b6-4c7c-9143-934a0e2d1b5f)

```
df.M2.fillna(method='ffill',inplace=True)
df
```
![image](https://github.com/user-attachments/assets/bbed6de2-475f-4503-9ad6-1357167c41ca)
```
df.isna().sum()
```
![image](https://github.com/user-attachments/assets/6d90b44a-222c-4ccd-8f39-0874524ec496)
```
df.M3.fillna(method='ffill',inplace=True)
df
```
![image](https://github.com/user-attachments/assets/60a7c4d8-2380-4357-9e2f-d7f30158f0a2)
```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/f40f5587-e09f-4b3c-b5eb-a9767564e185)
```
df.duplicated()
```
![image](https://github.com/user-attachments/assets/a3dedaac-8522-4e49-b1b3-92a2fc1e82dc)
```
df.drop_duplicates(inplace=True)
df
```
![image](https://github.com/user-attachments/assets/73983133-e527-4c57-8c4c-95aa284f9831)
```
df.duplicated()
```
![image](https://github.com/user-attachments/assets/27c6bf5a-121b-4110-9d9e-8d338773dea9)
```
df['DOB']
```
![image](https://github.com/user-attachments/assets/67dfffb0-30de-4f03-8f03-c605e197d04c)
```
import seaborn as sns
sns.heatmap(df.isnull(),yticklabels=False,annot=True)
```
![image](https://github.com/user-attachments/assets/7b8ab075-127e-476e-bc99-a36b6a27c924)
```
df.dropna(inplace=True)
sns.heatmap(df.isnull(),yticklabels=False,annot=True)
```
![image](https://github.com/user-attachments/assets/010ce521-6eea-4832-880b-31a92e98a91d)
```
import pandas as pd
```
```
import seaborn as sns
```
```
import numpy as np
```
```
age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
df=pd.DataFrame(age)
df
```
![image](https://github.com/user-attachments/assets/3edbade4-6dd5-4409-a27d-a529107f3d5a)
```
sns.boxplot(data=df)
```
![image](https://github.com/user-attachments/assets/66eecb6e-b0ab-4d1d-b9fc-2fa662496a49)
```
sns.scatterplot(data=df)
```
![image](https://github.com/user-attachments/assets/fdeee2e5-5870-4475-9917-0056ce5b60e9)
```
q1=df.quantile(0.25)
q2=df.quantile(0.5)
q3=df.quantile(0.75)
iqr=q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/ca01951f-ddf7-476b-aa4e-cb7b28ea64eb)
```
Q1=np.percentile(df,25)
Q3=np.percentile(df,75)
IQR=Q3-Q1
IQR
```
![image](https://github.com/user-attachments/assets/fc6c6582-0b3f-4f4c-affa-42aeb7188072)
```
lower_bound=Q1-1.5*IQR
upper_bound=Q3+1.5*IQR
lower_bound
```
![image](https://github.com/user-attachments/assets/d51436eb-0f07-456f-80f2-9ad326e73b0e)
```
outliers=[x for x in age if x<lower_bound or x>upper_bound]
print("Q1:",Q1)
print("Q3:",Q3)
print("IQR:",IQR)
print("Lower Bound:",lower_bound)
print("Upper Bound:",upper_bound)
print("Outliers:",outliers)
```
![image](https://github.com/user-attachments/assets/f3f29dcf-25d9-41d5-9789-f228c9594be3)
```
df=df[((df>=lower_bound)&(df<=upper_bound))]
df
```
![image](https://github.com/user-attachments/assets/48c1bbdf-4467-4f00-8e42-66b7c57978d5)
```
df=df.dropna()
df
```
![image](https://github.com/user-attachments/assets/8bc0d611-48d6-43e2-816c-3ace8462e372)
```
sns.boxplot(data=df)
```
![image](https://github.com/user-attachments/assets/c042be27-bd42-4cd0-863f-31109623427e)
```
sns.scatterplot(data=df)
```
![image](https://github.com/user-attachments/assets/b6352417-f0ed-405e-90bd-7075bc32bed6)
```
data=[1,2,2,2,3,1,1,15,2,2,2,3,1,1,2]
mean=np.mean(data)
std=np.std(data)
print('mean of the dataset is',mean)
print('std.deviation is',std)
```
![image](https://github.com/user-attachments/assets/4a92b86b-4d0b-452e-b7ba-b01ba736b628)
```
threshold=3
outlier=[]
for i in data:
   z=(i-mean)/std
   if z>threshold:
     outlier.append(i)
print('outlier in dataset is',outlier)
```
![image](https://github.com/user-attachments/assets/a36479e2-77f7-4788-b76d-8eb23281e0c6)
```
import pandas as pd
import numpy as np
import seaborn as sns
from scipy import stats
data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,
66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}
df=pd.DataFrame(data)
df
```
![image](https://github.com/user-attachments/assets/68a02e9a-d9fc-43aa-85be-04babdd5ad13)

![image](https://github.com/user-attachments/assets/394b1fcc-fb72-4b7d-a591-4d276e0f9c49)
```
z=np.abs(stats.zscore(df))
print(df[z['weight']>3])
```

![image](https://github.com/user-attachments/assets/73587145-5d9a-43d1-8268-3aaf94ba8f21)

# Result
         Thus, the given data and perform data cleaning and save the cleaned data to a file.
