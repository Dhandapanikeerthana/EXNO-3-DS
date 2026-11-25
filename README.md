## EXNO-3-DS

# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1:Read the given Data.
STEP 2:Clean the Data Set using Data Cleaning Process.
STEP 3:Apply Feature Encoding for the feature in the data set.
STEP 4:Apply Feature Transformation for the feature in the data set.
STEP 5:Save the data to the file.

# FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

# CODING AND OUTPUT:
```
import pandas as pd
df=pd.read_csv("/content/Encoding Data.csv")
df
```
<img width="366" height="461" alt="image" src="https://github.com/user-attachments/assets/6e40bdd2-49ef-4dfc-9179-e7443a00e80d" />

```
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
pm=['Hot','Warm','Cold']
e1=OrdinalEncoder(categories=[pm])
e1.fit_transform(df[["ord_2"]])
```
<img width="322" height="292" alt="image" src="https://github.com/user-attachments/assets/c9a76210-5cfd-4259-b715-4c31e9f51a03" />
```
df['bo2']=e1.fit_transform(df[["ord_2"]])
df
```
<img width="307" height="356" alt="image" src="https://github.com/user-attachments/assets/8afdd417-c1b1-4c1d-84af-b9f488e4f236" />

```
le=LabelEncoder()
dfc=df.copy()
dfc['ord_2']=le.fit_transform(dfc['ord_2'])
dfc
```
<img width="312" height="351" alt="image" src="https://github.com/user-attachments/assets/4d80ff77-7120-4217-9180-c2d6ee57b4a7" />
```
from sklearn.preprocessing import OneHotEncoder
ohe = OneHotEncoder(sparse_output=False)
df2=df.copy()
enc=pd.DataFrame(ohe.fit_transform(df2[['nom_0']]))
df2=pd.concat([df2,enc], axis=1)
df2
```
<img width="417" height="352" alt="image" src="https://github.com/user-attachments/assets/c6c17e4d-f3d4-410b-adf0-97333351e337" />

```
pd.get_dummies (df2,columns=["nom_0"])
```
<img width="637" height="357" alt="image" src="https://github.com/user-attachments/assets/3a5c9925-9865-4719-8b95-e25e7fbc1917" />

```
df=pd.read_csv("/content/data.csv")
df
```
<img width="462" height="358" alt="image" src="https://github.com/user-attachments/assets/11a79b68-96ac-491d-94d1-f26b95858909" />

# RESULT:
       # INCLUDE YOUR RESULT HERE

       
