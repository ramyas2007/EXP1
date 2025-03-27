![WhatsApp Image 2025-03-27 at 14 41 29_e05aabe6](https://github.com/user-attachments/assets/a92a7834-1e5a-478c-ad69-44da36abb844)# Exno:1
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
```
            REG NO : 212224040268
            NAME   : RAMYA S
```
```
import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS (1) (2).csv")
df
```
![image](https://github.com/user-attachments/assets/92213297-1224-484c-9390-137f098e028c)
```
df.isnull()
```
![image](https://github.com/user-attachments/assets/39634b20-575b-4031-a333-07c18fcc5bf5)
```
df.notnull()
```

![image](https://github.com/user-attachments/assets/0dd39cee-740c-4acb-8298-39b25b529831)

```
df.dropna(axis=1)
```

![image](https://github.com/user-attachments/assets/2977e683-1149-454b-9963-a802b26f8099)
```
df.dropna(axis=0)
```

![image](https://github.com/user-attachments/assets/60560bcb-7ab8-480d-9e44-2a8b9f9c0d5c)
```
dfs=df[df['TOTAL']>270]
```

![image](https://github.com/user-attachments/assets/22d30e27-c84a-4531-9a29-9af94e2bc9a0)
```
dfs=df[df['NAME'].str.startswith(('A','C'))&(df['TOTAL']>250)]
dfs
```

![image](https://github.com/user-attachments/assets/5a40668c-72de-4338-9c53-07fda11ad7d3)


```
dfs=df[df['NAME'].str.startswith(('A','C'))&(df['TOTAL']>250)]
dfs
```


![image](https://github.com/user-attachments/assets/3e18cb0f-c26c-4aa2-83fc-14f50ac056c5)

```
df.iloc[:4]
```

![image](https://github.com/user-attachments/assets/f9f92361-687a-4372-9c2a-cbd66ae7c5be)
```
df.iloc[0:4, 1:4]
```

![image](https://github.com/user-attachments/assets/b9b50a6d-0e3d-4af9-9c93-9d17b6a03af2)
```
df.iloc[[1,3,5],[1,3]]
```

![image](https://github.com/user-attachments/assets/36f7f4ee-8a59-472b-a497-e0805e48d064)
```
df
```

![image](https://github.com/user-attachments/assets/2626fd66-6f41-4bcd-adb4-b836dc7f0c3c)
```
dff=df.fillna(0)
dff
```

![image](https://github.com/user-attachments/assets/48fddf80-e47c-4b38-9f04-4d259b00e7e7)
```
df['TOTAL'].fillna(value=df['TOTAL'].mean())
```

![image](https://github.com/user-attachments/assets/ec532a53-7825-4cc1-a854-bad46bbfde02)
```
df.fillna(method='ffill')
```

![image](https://github.com/user-attachments/assets/eb97b544-55d7-4c13-83e6-379e8119ab80)
```
df.fillna(method='bfill')
```

![image](https://github.com/user-attachments/assets/a3a398ba-6f7b-4830-afc1-7eaf541697d1)
```
df['TOTAL'].fillna(value=df['TOTAL'].mean(), inplace=True)

```

![image](https://github.com/user-attachments/assets/5dd0f6ea-ab98-4650-8df6-2eaa929c04f7)
```
OUTLINE DECTION AND REMOVAL USING IQR

import pandas as pd
import seaborn as sns
import numpy as np
age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af=pd.DataFrame(age)
af
```

![image](https://github.com/user-attachments/assets/5b2932e1-d747-4cbe-9650-a37e7225eaca)
```
sns.boxplot(data=af)
```

![image](https://github.com/user-attachments/assets/2f0f4a97-f1d7-4cec-a39d-60fe97a17fee)
```
sns.scatterplot(data=af)
```

![image](https://github.com/user-attachments/assets/d515ffc1-00f1-48d2-9a40-40912a6f1f12)
```
q1=af.quantile(0.25)
q2=af.quantile(0.5)
q3=af.quantile(0.75)
iqr=q3-q1
iqr
```

![image](https://github.com/user-attachments/assets/cb0ae940-ed9d-40ca-adff-288e17c26206)
```
Q1=np.percentile(af,25)
Q3=np.percentile(af,75)
IQR=Q3-Q1
IQR
```

![image](https://github.com/user-attachments/assets/3c32f246-940c-4c07-aee7-82314852e72c)
```
lower_bound=Q1-1.5*IQR
upper_bound=Q3+1.5*IQR
lower_bound
```

![image](https://github.com/user-attachments/assets/f265219e-9ef5-41c1-873f-c290e6356040)
```
outliers=[x for x in age if x<lower_bound or x>upper_bound]
print("Q1:",Q1)
print("Q3:",Q3)
print("IQR:",IQR)
print("Lower bound:",lower_bound)
print("Upper bound:",upper_bound)
print("Outliers:",outliers)
```

![image](https://github.com/user-attachments/assets/0d594ce3-6502-4726-9186-e5571f8d8ede)
```
af=af[((af>=lower_bound)&(af<=upper_bound))]
af
```

![image](https://github.com/user-attachments/assets/8848bf82-e03c-4a92-9adf-c846985d20ff)
```
af.dropna()
```

![image](https://github.com/user-attachments/assets/24a7539b-e4a4-40c1-b8bc-f256e008edd9)
```
sns.boxplot(data=af)
```

![image](https://github.com/user-attachments/assets/a4f9a46e-58c7-471b-a23d-cdd005ac9fcf)
```
sns.scatterplot(data=af)
```

![image](https://github.com/user-attachments/assets/45cc7f14-b445-410a-8bb4-45adcc35342f)
```
data=[1,2,2,2,3,1,1,15,2,2,2,3,1,1,2]
mean=np.mean(data)
std=np.std(data)
print('mean of the dataset is',mean)
print('std. deviation is',std)
```

![image](https://github.com/user-attachments/assets/b5327bf4-355b-4107-8e80-281308091e1a)
```
threshold=3
outlier=[]
for i in data:
  z=(i-mean)/std
  if z>threshold:
    outlier.append(i)
print('outlier in dataset is',outlier)
```


![image](https://github.com/user-attachments/assets/5a0924f8-92a6-4c0b-a2ba-98223a3a505b)
```
data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}
import pandas as pd
import numpy as np
import seaborn as sns
import pandas as pd
from scipy import stats
data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}
df=pd.DataFrame(data)
df
```

![image](https://github.com/user-attachments/assets/57af119b-d7f3-4c93-8916-e53ef0198ee6)
```
z=np.abs(stats.zscore(df))
print(df[z['weight']>3])
```

![image](https://github.com/user-attachments/assets/d72d7a5a-9b4b-4861-a759-c2c3927c6d6c)
```
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
```

![image](https://github.com/user-attachments/assets/c596156b-d337-4b7f-86ad-82614ab31e93)


































# Result
          <<include your Result here>>
