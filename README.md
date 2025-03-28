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

    REG NO : 212224040268
    NAME   : RAMYA S


import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS (1).csv")
df

![image](https://github.com/user-attachments/assets/15a41b32-9b69-4788-82ed-c09181d9463e)

df.isnull()

![image](https://github.com/user-attachments/assets/74d86fab-2d07-4b48-a362-6997474f8a10)

df.notnull()

![image](https://github.com/user-attachments/assets/255eac22-9b90-4f3a-baed-4c3c18ef38ee)

df.dropna(axis=1)

![image](https://github.com/user-attachments/assets/4009b6d2-cbb1-40b6-bf2e-1bc64116cf99)

df.dropna(axis=0)

![image](https://github.com/user-attachments/assets/b84f9e07-d501-4fd5-be21-a0d689606092)

dfs=df[df['TOTAL']>270]
dfs

![image](https://github.com/user-attachments/assets/65a835a3-86e7-4fdf-b681-31ae89476f0a)

dfs=df[df['NAME'].str.startswith(('A','C'))&(df['TOTAL']>250)]
dfs

![image](https://github.com/user-attachments/assets/f99e8d33-1104-4645-9bef-fcdaa4d21045)

df.iloc[:4]

![image](https://github.com/user-attachments/assets/b2607f2b-f704-4c8b-9a93-9f68c1495d84)

df.iloc[0:4,1:4]

![image](https://github.com/user-attachments/assets/387143ac-dec8-4567-9781-530dc33589df)

df.iloc[[1,3,5],[1,3]]

![image](https://github.com/user-attachments/assets/7fbcd8d4-d140-4b11-bdee-7ad8943ef3c4)

dff=df.fillna(0)
dff

![image](https://github.com/user-attachments/assets/da9adaa6-a031-4c4d-9858-1d98977a400a)

df['TOTAL'].fillna(value=df['TOTAL'].mean())

![image](https://github.com/user-attachments/assets/ed6d8871-e654-4361-a959-629c72c96080)

df.fillna(method='ffill')

![image](https://github.com/user-attachments/assets/517a482a-42cd-4e79-9dba-7ee06c53fac1)

df.fillna(method='bfill')

![image](https://github.com/user-attachments/assets/abeac8cb-bab4-4fed-b173-7290dabd4cc8)

df['TOTAL'].fillna(value=df['TOTAL'].mean(),inplace=True)
df

![image](https://github.com/user-attachments/assets/439dbb76-debb-4c22-a8d6-0603e8ba770d)

0UTLIERS DETECTION AND REMOVAL USING IQR

import seaborn as sns
age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af=pd.DataFrame(age)
af

![image](https://github.com/user-attachments/assets/391fb7cd-8e3f-45fb-8c40-6756d0636bdf)

sns.boxplot(data=af)

![image](https://github.com/user-attachments/assets/16181738-c2b9-4fb9-a018-f5858d6e5102)

sns.scatterplot(data=af)

![image](https://github.com/user-attachments/assets/447de853-af34-48f5-b6a6-df9eb10fd083)

q1=af.quantile(0.25)
q2=af.quantile(0.5)
q3=af.quantile(0.75)
iqr=q3-q1
iqr

![image](https://github.com/user-attachments/assets/1ddd848d-9859-4bbd-b228-a1d48fe5c85e)

Q1=np.percentile(af,25)
Q3=np.percentile(af,75)
IQR=Q3-Q1
IQR

![image](https://github.com/user-attachments/assets/e45f611c-ccef-4c16-aa1e-4430f5da203d)

lower_bound=Q1-1.5*IQR
upper_bound=Q3+1.5*IQR
lower_bound

![image](https://github.com/user-attachments/assets/5065350a-745e-4954-a38c-bea0d931caab)

upper_bound

![image](https://github.com/user-attachments/assets/86adf43b-1304-477e-aee1-4ba3510e7bc1)

outliers=[x for x in age if x<lower_bound or x>upper_bound]
print("Q1:",Q1)
print("Q3:",Q3)
print("IQR",IQR)
print("Lower bound:",lower_bound)
print("Upper bound:",upper_bound)
print("Outliers:",outliers)

![image](https://github.com/user-attachments/assets/bd9ee991-ea4f-4259-ac4b-608a3119ad75)

af=af[((af>=lower_bound)&(af<=upper_bound))]
af

![image](https://github.com/user-attachments/assets/d6e57b04-6bd9-473a-b78b-05a9fca7cdaa)

af.dropna()

![image](https://github.com/user-attachments/assets/caa344fc-d063-4d51-95eb-429037887941)

sns.boxplot(data=af)

![image](https://github.com/user-attachments/assets/ba8e11c4-b887-44aa-9997-33586f9f405f)

sns.scatterplot(data=af)

![image](https://github.com/user-attachments/assets/838b27ce-6bff-47b5-8653-173302c6ed67)

data=[1,2,2,2,3,1,1,15,2,2,2,3,1,1,2]
mean=np.mean(data)
std=np.std(data)
print("mean of the dataset is",mean)
print("standard deviation is",std)

![image](https://github.com/user-attachments/assets/97691a8d-55e3-429f-9959-e8f60e7a2649)

threshold=3
outlier=[]
for i in data:
  z=(i-mean)/std
  if z>threshold:
    outlier.append(i)
print("outlier in dataset is",outlier)

![image](https://github.com/user-attachments/assets/ce58795a-df5c-44a0-a1a2-f606715f0426)

from scipy import stats
data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,202,72,75,78,81,84,232,87,90,93,96,99,258,]}
df=pd.DataFrame(data)
df

![image](https://github.com/user-attachments/assets/938a2825-38e0-473d-8352-57cfd5520b26)

z=np.abs(stats.zscore(df))
print(df[z['weight']>3])

![image](https://github.com/user-attachments/assets/60324583-ade4-4304-8866-759f87138928)

val=[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,202,72,75,78,81,84,232,87,90,93,96,99,258,]
out=[]
def d_o(val):
  ts=3
  m=np.mean(val)
  sd=np.std(val)
  for i in val:
    z=(i-m)/sd
    if np.abs(z)>ts:
      out.append(i)
  return out
op=d_o(val)
op

![image](https://github.com/user-attachments/assets/db164048-27b5-45db-a9de-f2862f9bcae4)

# Result
 Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score
