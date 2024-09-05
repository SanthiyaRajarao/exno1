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
```
REG NO : 212223230192
NAME : SANTHIYA R
```
```
import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS.csv")
df
```
![Screenshot 2024-09-05 205231](https://github.com/user-attachments/assets/f94240dc-63f3-420a-b273-3f950cc0db32)
```
df.shape
```
![Screenshot 2024-09-05 205244](https://github.com/user-attachments/assets/6ee9bd9a-c25c-4c17-a7d0-c1ed7d5ad8f1)
```
df.describe()
```
![Screenshot 2024-09-05 205254](https://github.com/user-attachments/assets/7abb8766-cb14-4f60-98a6-7d54cccc84ba)
```
df.info()
```
![Screenshot 2024-09-05 205308](https://github.com/user-attachments/assets/201776a6-5ba0-40e4-951b-bc792bce9f0d)
```
df.head(10)
```
![Screenshot 2024-09-05 205317](https://github.com/user-attachments/assets/a72a0179-7c0a-42e2-a8e4-d7fbb1b6f16e)
```
df.tail(10)
```
![Screenshot 2024-09-05 205325](https://github.com/user-attachments/assets/d8008d35-b2fb-44f4-a628-9695b54d58a5)
```
df.isna().sum()
```
![Screenshot 2024-09-05 205336](https://github.com/user-attachments/assets/5570db60-c520-4ab5-990a-7b6111a4811c)
```
df.dropna(how='any').shape
```
![Screenshot 2024-09-05 205348](https://github.com/user-attachments/assets/7f66cb3e-e5f3-4b67-a1aa-b4b29c151b67)
```
df.shape
```
![Screenshot 2024-09-05 205354](https://github.com/user-attachments/assets/5aa1d9f0-1c9f-4e8f-8a7c-af144f05dbbd)

```
x=df.dropna(how='any')
x
```
![Screenshot 2024-09-05 205402](https://github.com/user-attachments/assets/f22d6529-6112-425f-aece-80e06164156b)
```
mn=df.TOTAL.mean()
mn
```
![Screenshot 2024-09-05 205410](https://github.com/user-attachments/assets/95d27f6e-2708-4349-8642-152d4dfba4f6)
```
df.TOTAL.fillna(mn,inplace=True)
df
```
![Screenshot 2024-09-05 205420](https://github.com/user-attachments/assets/3b74ab22-45a1-42de-a4ea-71798e455c88)
```
df.isnull().sum()
```
![Screenshot 2024-09-05 205432](https://github.com/user-attachments/assets/a69d0cae-75a8-4100-b034-8a16cf66d483)
```
df.M1.fillna(method='ffill',inplace=True)
df
```
![Screenshot 2024-09-05 205450](https://github.com/user-attachments/assets/47d8901d-1fc0-4b33-bc41-d4b68fc4a3d6)
```
df.isnull().sum()
```
![Screenshot 2024-09-05 205500](https://github.com/user-attachments/assets/171550a7-4ea9-4c7e-8219-39792631a34b)
```
df.M2.fillna(method='ffill',inplace=True)
df
```
![Screenshot 2024-09-05 205522](https://github.com/user-attachments/assets/ebdbc9ac-0071-4e3c-8ff4-a61fe84a148c)
```
df.isna().sum()
```
![Screenshot 2024-09-05 205532](https://github.com/user-attachments/assets/b09c1367-ea66-4606-9910-ad504d6390bc)
```
df.M3.fillna(method='ffill',inplace=True)
df
```
![Screenshot 2024-09-05 205551](https://github.com/user-attachments/assets/1a3ccd99-f048-40a0-9e91-197bbdd7f8f6)
```
df.isnull().sum()
```
![Screenshot 2024-09-05 205600](https://github.com/user-attachments/assets/84085154-c694-4f33-bf96-7d2f44acbe1a)

```
df.duplicated()
```
![Screenshot 2024-09-05 205609](https://github.com/user-attachments/assets/f10fc957-fdc5-4eab-ab0b-10f83299f986)
```
df.drop_duplicates(inplace=True)
df
```
![Screenshot 2024-09-05 205622](https://github.com/user-attachments/assets/b6a6f3b3-af65-4538-a7f6-bcb906c54789)
```
df.duplicated()
```
![Screenshot 2024-09-05 205631](https://github.com/user-attachments/assets/9036527d-32ec-4fa2-b3bb-52ccd2ea1210)
```
df['DOB']
```
![Screenshot 2024-09-05 205639](https://github.com/user-attachments/assets/91b19d2e-7a13-4d38-9a42-29276f1c53d3)
```
import seaborn as sns
sns.heatmap(df.isnull(),yticklabels=False,annot=True)
```
![Screenshot 2024-09-05 205650](https://github.com/user-attachments/assets/3e4dc73c-4969-4456-9ceb-e6135ccd423b)
```
df.dropna(inplace=True)
sns.heatmap(df.isnull(),yticklabels=False,annot=True)
```
![Screenshot 2024-09-05 205711](https://github.com/user-attachments/assets/0e0998bc-73c8-4250-a541-af5a4916df26)
# 0UTLIERS DETECTION AND REMOVAL USING IQR
```
age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
df=pd.DataFrame(age)
df
```
![Screenshot 2024-09-05 205754](https://github.com/user-attachments/assets/cd51b715-f400-44d9-9423-b28cecde4ffb)
```
sns.boxplot(data=df)
```
![Screenshot 2024-09-05 205806](https://github.com/user-attachments/assets/fb692f13-077a-4bed-8e23-41d2ea8f4d4c)
```
sns.scatterplot(data=df)
```
![Screenshot 2024-09-05 205815](https://github.com/user-attachments/assets/7f22c03c-c443-45f1-a712-ceb2eedd60c9)
```
q1=df.quantile(0.25)
q2=df.quantile(0.5)
q3=df.quantile(0.75)
iqr=q3-q1
iqr
```
![Screenshot 2024-09-05 205822](https://github.com/user-attachments/assets/8fea8fd2-2bbc-4ca9-8578-8226698438c8)
```
Q1=np.percentile(df,25)
Q3=np.percentile(df,75)
IQR=Q3-Q1
IQR
```
![Screenshot 2024-09-05 205829](https://github.com/user-attachments/assets/ed0c6d17-98a5-4154-841a-9e32daf81988)
```
lower_bound=Q1-1.5*IQR
upper_bound=Q3+1.5*IQR
lower_bound
```
![Screenshot 2024-09-05 205835](https://github.com/user-attachments/assets/b4c74e85-3d5a-4e15-92fd-59788056df3d)
```
upper_bound
```
![Screenshot 2024-09-05 205841](https://github.com/user-attachments/assets/3555938e-6e6a-4cca-a7b1-2b1a4bb8ee1f)
```
outliers=[x for x in age if x<lower_bound or x>upper_bound]
print("Q1:",Q1)
print("Q3:",Q3)
print("IQR:",IQR)
print("Lower Bound:",lower_bound)
print("Upper Bound:",upper_bound)
print("Outliers:",outliers)
```
![Screenshot 2024-09-05 205847](https://github.com/user-attachments/assets/e9ddd4af-c578-4716-b8a9-56295e09cfc1)
```
df=df[((df>=lower_bound)&(df<=upper_bound))]
df
```
![Screenshot 2024-09-05 205854](https://github.com/user-attachments/assets/c9b381af-6b9d-4511-aefe-4dbb5a7de422)
```
df=df.dropna()
df
```
![Screenshot 2024-09-05 205901](https://github.com/user-attachments/assets/46189f35-9c91-43aa-98d2-3c564ae91b9b)
```
sns.boxplot(data=df)
```

![Screenshot 2024-09-05 205909](https://github.com/user-attachments/assets/72e1a48b-74fe-4737-a009-008dc94a2566)
```
sns.scatterplot(data=df)
```

![Screenshot 2024-09-05 205917](https://github.com/user-attachments/assets/4343d87b-7357-43be-a785-97ee86449f87)
```
data=[1,2,2,2,3,1,1,15,2,2,2,3,1,1,2]
mean=np.mean(data)
std=np.std(data)
print('mean of the dataset is',mean)
print('std.deviation is',std)
```

![Screenshot 2024-09-05 205941](https://github.com/user-attachments/assets/db977eee-e61b-4666-aba7-8fc89d16feab)
```
threshold=3
outlier=[]
for i in data:
  z=(i-mean)/std
  if z>threshold:
    outlier.append(i)
print('outlier in dataset is',outlier)
```

![Screenshot 2024-09-05 205948](https://github.com/user-attachments/assets/4f5bb1c6-9c2c-4b0a-ad3b-07eeadc9d79a)
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

![Screenshot 2024-09-05 210012](https://github.com/user-attachments/assets/7177c2d3-8f74-4067-ba5e-aaacd68ce4d7)
```
z=np.abs(stats.zscore(df))
print(df[z['weight']>3])
```

![Screenshot 2024-09-05 210027](https://github.com/user-attachments/assets/1d701938-f0da-4cec-a4dc-d330c368101e)







# Result
          <<include your Result here>>
