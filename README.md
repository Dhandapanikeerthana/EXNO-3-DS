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

```
pip install --upgrade category_encoders
```

```
from category_encoders import BinaryEncoder
df
```
<img width="472" height="367" alt="image" src="https://github.com/user-attachments/assets/47af89e6-731e-4981-8b12-aba7181d1953" />

```
be=BinaryEncoder()
nd=be.fit_transform(df ['Ord_2'])
dfb=pd.concat([df,nd], axis=1)
dfb1=df.copy()
dfb
```

<img width="672" height="358" alt="image" src="https://github.com/user-attachments/assets/659ab412-c518-4112-bacd-549850cc75f2" />

```

from category_encoders import TargetEncoder
te=TargetEncoder()
cc=df.copy()
new=te.fit_transform(X=cc["City"], y=cc["Target"])
cc=pd.concat([cc,new], axis=1)
cc

```

<img width="542" height="355" alt="image" src="https://github.com/user-attachments/assets/d7ff61f4-f9cc-4d9b-9c59-90f6852a25f8" />


```
import pandas as pd 
from scipy import stats 
import numpy as np 
df=pd.read_csv("/content/Data_to_Transform.csv") 
df

```

<img width="655" height="490" alt="image" src="https://github.com/user-attachments/assets/408412f3-d091-4480-9b3b-d51dda222f61" />

```

df.skew()
```
<img width="332" height="205" alt="image" src="https://github.com/user-attachments/assets/e06a85ab-a4f2-4f0f-bf23-1b43c594df8a" />

```
np.log(df["Highly Positive Skew"])

```

<img width="273" height="520" alt="image" src="https://github.com/user-attachments/assets/497c99c3-f292-4bf0-bde3-3552a8f87a9f" />

```
np.reciprocal(df["Moderate Positive Skew"])

```

<img width="348" height="523" alt="image" src="https://github.com/user-attachments/assets/e2683a60-e0c4-4328-948a-99da52159c74" />

```
np.sqrt(df["Highly Positive Skew"])

```

<img width="287" height="513" alt="image" src="https://github.com/user-attachments/assets/9f78f68f-c667-42d7-a729-613c33dfe6d9" />

```
np.square(df["Highly Positive Skew"])

```

<img width="301" height="520" alt="image" src="https://github.com/user-attachments/assets/ceef693b-44a8-4232-ad91-747b9a2dd551" />

```
df["Highly Positive Skew_boxcox"], parameters=stats.boxcox(df["Highly Positive Skew"]) 
df

```

<img width="1137" height="490" alt="image" src="https://github.com/user-attachments/assets/70ee8b93-d108-417b-b89f-5dd751e13032" />

```
df["Moderate Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df["Moderate Negative Skew"]) 
df.skew()

```

<img width="440" height="303" alt="image" src="https://github.com/user-attachments/assets/8f937a5e-badf-430e-8cd3-58197cf7a381" />


```
from sklearn.preprocessing import QuantileTransformer 
qt=QuantileTransformer(output_distribution='normal') 
df["Moderate Negative Skew_1"]=qt.fit_transform(df[["Moderate Negative Skew"]]) 
df

```

<img width="1701" height="427" alt="image" src="https://github.com/user-attachments/assets/6c39d3c6-ed1b-4b76-953d-b537a11aec82" />

```
import seaborn as sns 
import statsmodels.api as sm 
import matplotlib.pyplot as plt 
sm.qqplot(df["Moderate Negative Skew"],line='45') 
plt.show()

```

<img width="577" height="435" alt="image" src="https://github.com/user-attachments/assets/6c4b8648-c058-4414-9dc9-a0d8cd8de43d" />

```
sm.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45') 
plt.show()

```
<img width="572" height="425" alt="image" src="https://github.com/user-attachments/assets/c046c326-2c7b-4b90-81c3-d79956f8957b" />

```
from sklearn.preprocessing import QuantileTransformer
df["Moderate Negative Skew"]=qt.fit_transform(df[["Moderate Negative Skew"]])
sm.qqplot(df["Moderate Negative Skew"],line='45') 
plt.show()

```
<img width="563" height="432" alt="image" src="https://github.com/user-attachments/assets/c0b2830d-5c8a-4b48-a7ee-81eba3d55aa5" />

```
df["Highly Negative Skew_1"]=qt.fit_transform(df[["Highly Negative Skew"]])
sm.qqplot(df['Highly Negative Skew'], line='45')
plt.show()

```

<img width="563" height="431" alt="image" src="https://github.com/user-attachments/assets/b86160c4-6894-494a-830a-e5f81f1ee472" />

```
sm.qqplot(df['Highly Negative Skew_1'], line='45')
plt.show()

```
<img width="558" height="428" alt="image" src="https://github.com/user-attachments/assets/f76fe2fe-24db-43d0-a384-0418d19af72d" />

# RESULT:
      

       
