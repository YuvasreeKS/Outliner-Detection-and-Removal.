# Ex:2 - Outlier_Detection_and_Removal
# AIM:
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them

# ALGORITHM:
STEP 1:
Read the given Data.

STEP 2:
Get the information about the data.

STEP 3:
Detect the Outliers using IQR method and Z score.

STEP 4:
Remove the outliers:

STEP 5:
Plot the datas using box plot.

# PROGRAM:
~
import pandas as pd
df=pd.read_csv("/content/bhp.csv")
df.head()
df.describe()
df.info()
df.shape

import seaborn as sns
sns.boxplot(x="price_per_sqft",data=df)
~
# removing ouliers of bhp.csv file using IQR
~
Q1=df['price_per_sqft'].quantile(0.25)
Q3=df['price_per_sqft'].quantile(0.75)
IQR=Q3-Q1
lower=Q1-1.5*IQR
upper=Q3+1.5*IQR
newdata=df[(df['price_per_sqft']>=lower) & (df['price_per_sqft']<=upper)] 
print(newdata)   #new dataframe.
outliers=df[(df['price_per_sqft']<lower) | (df['price_per_sqft']>upper)]
print(outliers)
newdata.shape
sns.boxplot(x="price_per_sqft",data=newdata)
~
# removing ouliers of bhp.csv file using Zscore of 3
~
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
# Using IQR detect height outliers and print them( height_weight.csv)
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
~
# Using IQR, detect weight outliers and print them( height_weight.csv)
~
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
~
# OUTPUT:
## bhp.csv:
### df.head():
i![image](https://github.com/Poojariyaa/Outlier/assets/127511817/13a055a7-5a94-42a0-9bf0-aa9c63cd0697)


### df.describe():
![image](https://github.com/Poojariyaa/Outlier/assets/127511817/5fdb5cca-b47b-4155-9638-692da87f29ba)


### df.info():
![image](https://github.com/Poojariyaa/Outlier/assets/127511817/a1b569d6-3690-494c-927a-5d6316383dbc)


### df.shape
![image](https://github.com/Poojariyaa/Outlier/assets/127511817/1b3dbf7a-0a41-4768-91a7-0e6f767645a2)


### BOXPLOT BEFORE REMOVING OUTLIERS
![image](https://github.com/Poojariyaa/Outlier/assets/127511817/fadced04-7f6d-434f-b466-18b0485310cf)


### NEWDATA USING IQR
![image](https://github.com/Poojariyaa/Outlier/assets/127511817/540213ae-9f0b-4f92-bd71-fa70ea0aba63)


### OUTLIERS
![image](https://github.com/Poojariyaa/Outlier/assets/127511817/81ac667e-ccfc-4af5-b5ee-ef97711b24ff)

### newdata2.shape
![image](https://github.com/Poojariyaa/Outlier/assets/127511817/206e151b-7d5f-4dab-99b6-3cc46dca3227)

### BOXPLOT AFTER REMOVING OUTLIERS USING Zscore
![image](https://github.com/Poojariyaa/Outlier/assets/127511817/a2d19eac-7994-4cd6-803a-38a8b9e13d32)


### height_weight.csv
![image](https://github.com/Poojariyaa/Outlier/assets/127511817/c077d5e2-f578-4aa5-8ebb-f521f8d9fb91)

### dataset.describe()
![image](https://github.com/Poojariyaa/Outlier/assets/127511817/5697b0b4-6c2b-4567-9154-9a7bc406a418)


### dataset.info()
![image](https://github.com/Poojariyaa/Outlier/assets/127511817/0655a0b6-c22a-4c8a-98cf-44f295da4717)


### BOXPLOT BEFORE REMOVING OUTLIERS
![image](https://github.com/Poojariyaa/Outlier/assets/127511817/b90a2686-e73b-4392-990e-c258d586a10c)


### HEIGHT OUTLIERS
![image](https://github.com/Poojariyaa/Outlier/assets/127511817/d7ee8917-1c52-40bf-b32a-56a907b08733)


### DATASET AFTER REMOVING HEIGHT OUTLIERS
![image](https://github.com/Poojariyaa/Outlier/assets/127511817/bb83f05b-4fb5-4a36-b198-aab0592426d8)


### BOXPLOT AFTER REMOVING HEIGHT OUTLIERS
![image](https://github.com/Poojariyaa/Outlier/assets/127511817/cd2234f2-5fc2-4d30-85d4-267e6d60d254)


### WEIGHT OUTLIERS
![image](https://github.com/Poojariyaa/Outlier/assets/127511817/8177ad0b-4ce9-40aa-9f8a-44bf6852fb88)


### DATASET AFTER REMOVING WEIGHT OUTLIERS
![image](https://github.com/Poojariyaa/Outlier/assets/127511817/aa4b9852-f198-4c33-8b59-9d98be545ab0)


### BOXPLOT AFTER REMOVING WEIGHT OUTLIERS
![image](https://github.com/Poojariyaa/Outlier/assets/127511817/311415ad-901b-4460-9564-968a08877d92)


# RESULT: 
  The given datasets are read and outliers are detected and are removed using IQR and z-score methods.
