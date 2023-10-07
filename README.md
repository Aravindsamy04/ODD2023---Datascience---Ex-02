# Ex02-Outlier

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them

### ALGORITHM:
### STEP 1:
Read the given Data.

### STEP 2:
Get the information about the data.

### nSTEP 3:
Detect the Outliers using IQR method and Z score.

### STEP 4:
Remove the outliers:

### STEP 5:
Plot the datas using box plot.
### PROGRAM:

```
DEVELOPED BY: ARAVIND SAMY P
REGISTER NUMBER: 212222230011

import pandas as pd
df=pd.read_csv("/content/bhp.csv")
df.head()
df.describe()
df.info()
df.shape

import seaborn as sns
sns.boxplot(x="price_per_sqft",data=df)

### Removing ouliers of bhp.csv file using IQR
Q1=df['price_per_sqft'].quantile(0.25)
Q3=df['price_per_sqft'].quantile(0.75)
IQR=Q3-Q1
lower=Q1-1.5*IQR
upper=Q3+1.5*IQR
newdata=df[(df['price_per_sqft']>=lower) & (df['price_per_sqft']<=upper)] 
print(newdata)
#New dataframe.
outliers=df[(df['price_per_sqft']<lower) | (df['price_per_sqft']>upper)]
print(outliers)
newdata.shape
sns.boxplot(x="price_per_sqft",data=newdata)


### Removing ouliers of bhp.csv file using Zscore of 3

from scipy import stats
import numpy as np
z_score=np.abs(stats.zscore(df['price_per_sqft']))
newdata2=df[(z_score<3)]
print(newdata2)
outlier2=df[(z_score>=3)]
print(outlier2)
newdata2.shape
sns.boxplot(x="price_per_sqft",data=newdata2)

import pandas as pd
dataset=pd.read_csv("/content/height_weight.csv")
dataset.shape
dataset.describe()
dataset.info()
import seaborn as sns
sns.boxplot(x='height',data=dataset)

### Using IQR detect height outliers and print them( height_weight.csv)

Q1_height=dataset['height'].quantile(0.25)
Q3_height=dataset['height'].quantile(0.75)
IQR_HEIGHT=Q3_height-Q1_height
l_height=Q1_height-1.5*IQR_HEIGHT
u_height=Q3_height+1.5*IQR_HEIGHT
outliers_height=dataset[(dataset['height']<l_height) | (dataset['height']>u_height)]
print(outliers_height)
newdata_height=dataset[(dataset['height']>=l_height) & (dataset['height']<=u_height)]
print(newdata_height)
sns.boxplot(x='height',data=newdata_height)


### Using IQR, detect weight outliers and print them( height_weight.csv)

Q1_weight=dataset['weight'].quantile(0.25)
Q3_weight=dataset['weight'].quantile(0.75)
IQR_WEIGHT=Q3_weight-Q1_weight
l_weight=Q1_weight-1.5*IQR_WEIGHT
u_weight=Q3_weight+1.5*IQR_WEIGHT
outliers_weight=dataset[(dataset['weight']<l_weight) | (dataset['weight']>u_weight)]
print(outliers_weight)
newdata_weight=dataset[(dataset['weight']>=l_weight) & (dataset['weight']<=u_weight)]
print(newdata_weight)
sns.boxplot(x='weight',data=newdata_weight)
```

OUTPUT:


df.head():

![image](https://github.com/Aravindsamy04/ODD2023---Datascience---Ex-02/assets/113497037/83981ba8-fd6c-4e87-b548-861a2b589886)
df.describe():

![image](https://github.com/Aravindsamy04/ODD2023---Datascience---Ex-02/assets/113497037/0bae0a39-d9e5-4cc0-89b7-c0b2adedfc63)
df.info():


![image](https://github.com/Aravindsamy04/ODD2023---Datascience---Ex-02/assets/113497037/2c0c5a3d-c536-43c5-9ecb-df1d6ae10238)

df.shape:

![image](https://github.com/Aravindsamy04/ODD2023---Datascience---Ex-02/assets/113497037/34298bd7-a38b-4dd8-b086-c110f8c754e5)

BOXPLOT BEFORE REMOVING OUTLIERS:

![image](https://github.com/Aravindsamy04/ODD2023---Datascience---Ex-02/assets/113497037/65c4c528-4ee3-4ebd-8737-5548a2248217)

NEWDATA USING IQR:

![image](https://github.com/Aravindsamy04/ODD2023---Datascience---Ex-02/assets/113497037/10e5520c-28a4-407f-adad-9c25c1bc8f7d)

OUTLIERS:

![image](https://github.com/Aravindsamy04/ODD2023---Datascience---Ex-02/assets/113497037/90d7da5c-a431-4642-8689-9dbbbe0c0573)

newdata.shape:


![image](https://github.com/Aravindsamy04/ODD2023---Datascience---Ex-02/assets/113497037/8e87d4c7-e38e-43a3-b974-64d14147019d)


BOXPLOT AFTER REMOVING OUTLIERS USING IQR:

![image](https://github.com/Aravindsamy04/ODD2023---Datascience---Ex-02/assets/113497037/c21729d1-299f-4f9d-a93b-d170a22350ff)


Zscore of 3:
NEWDATA USING Zscore:

![image](https://github.com/Aravindsamy04/ODD2023---Datascience---Ex-02/assets/113497037/ff03d0ac-bb5c-43f5-8b92-987e06cce3ed)

OUTLIERS:

![image](https://github.com/Aravindsamy04/ODD2023---Datascience---Ex-02/assets/113497037/326018ff-c570-435a-97f1-fc01b5ee730a)

newdata2.shape:

![image](https://github.com/Aravindsamy04/ODD2023---Datascience---Ex-02/assets/113497037/32550c1e-e779-42d1-9754-9a8c4e14c71a)


BOXPLOT AFTER REMOVING OUTLIERS USING Zscore:

![image](https://github.com/Aravindsamy04/ODD2023---Datascience---Ex-02/assets/113497037/13f51c6a-ab0a-4378-848d-b128a57e809a)

height_weight.csv:

![image](https://github.com/Aravindsamy04/ODD2023---Datascience---Ex-02/assets/113497037/acc920ec-07ea-4be8-a3e2-a3af45116461)

dataset.describe():


![image](https://github.com/Aravindsamy04/ODD2023---Datascience---Ex-02/assets/113497037/a654e7bb-ca23-427e-8ac0-71549493ecca)

dataset.info():

![image](https://github.com/Aravindsamy04/ODD2023---Datascience---Ex-02/assets/113497037/dc7661be-39f4-40fd-a081-38bec3c986f1)



BOXPLOT BEFORE REMOVING OUTLIERS:

![image](https://github.com/Aravindsamy04/ODD2023---Datascience---Ex-02/assets/113497037/a584737a-2709-4e42-870a-8d2d8fdf3e1c)

HEIGHT OUTLIERS:

![image](https://github.com/Aravindsamy04/ODD2023---Datascience---Ex-02/assets/113497037/3c9192df-424c-4d9d-960c-6a40d60988f0)

DATASET AFTER REMOVING HEIGHT OUTLIERS:

![image](https://github.com/Aravindsamy04/ODD2023---Datascience---Ex-02/assets/113497037/c21f2f5f-1757-48c9-bb33-6a00bb2669cc)

BOXPLOT AFTER REMOVING HEIGHT OUTLIERS:

![image](https://github.com/Aravindsamy04/ODD2023---Datascience---Ex-02/assets/113497037/bab55de5-0dce-4f29-9e9b-6bb88937f371)

WEIGHT OUTLIERS:

![image](https://github.com/Aravindsamy04/ODD2023---Datascience---Ex-02/assets/113497037/f5d18c77-583f-4365-85f0-bef27c5f47af)


DATASET AFTER REMOVING WEIGHT OUTLIERS:

![image](https://github.com/Aravindsamy04/ODD2023---Datascience---Ex-02/assets/113497037/0944b001-897f-4256-a907-9254784740dd)



BOXPLOT AFTER REMOVING WEIGHT OUTLIERS:


![image](https://github.com/Aravindsamy04/ODD2023---Datascience---Ex-02/assets/113497037/45512c5c-6621-492e-b673-7aed17e60fea)

RESULT:

The given datasets are read and outliers are detected and are removed using IQR and z-score methods.





















