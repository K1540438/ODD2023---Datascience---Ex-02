# Ex02-Outlier
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them

# CODE AND OUTPUT
```python
import pandas as pd
import numpy as np
df = pd.read_csv('/content/bhp.csv')
df.head(10)
df.boxplot()
df.shape
q1=df.price_per_sqft.quantile(0.25)
q3=df.price_per_sqft.quantile(0.75)
IQR=q3-q1
lower_limit=q1-1.5*IQR
upper_limit=q3+1.5*IQR
lower_limit,upper_limit
df[(df.price_per_sqft<lower_limit)|(df.price_per_sqft>upper_limit)]
df[(df.price_per_sqft<=lower_limit)&(df.price_per_sqft>=upper_limit)]
df = df.drop(["location","size","bhk"],axis=1) 
from scipy import stats
z=np.abs(stats.zscore(df))
z
df2=df.copy()
df2=df2[(z<3).all(axis=1)]
df2
df2.boxplot()

**Removing Outliers - height_weight.csv**
import pandas as pd
import numpy as np
df1 = pd.read_csv('/content/height_weight.csv')
df1.head(10)
df1.drop("gender",axis=1)
df1.boxplot()
q1=df1.weight.quantile(0.25)
q3=df1.weight.quantile(0.75)
IQR=q3-q1
lower_limit=q1-1.5*IQR
upper_limit=q3+1.5*IQR
lower_limit,upper_limit
df1_new=df1[(df1.weight<lower_limit)&(df1.weight>upper_limit)]
df1_new.boxplot()
q1=df1.height.quantile(0.25)
q3=df1.height.quantile(0.75)
IQR=q3-q1
lower_limit=q1-1.5*IQR
upper_limit=q3+1.5*IQR
lower_limit,upper_limit
df1_new=df1[(df1.weight<lower_limit)&(df1.weight>upper_limit)]
df1_new.boxplot()


## OUTPUT

<img width="376" alt="Screenshot 2023-10-13 201032" src="https://github.com/K1540438/ODD2023---Datascience---Ex-02/assets/84171243/fd34042b-72b8-4d64-97a3-8c0d0d75a1b6">

<img width="371" alt="Screenshot 2023-10-13 201042" src="https://github.com/K1540438/ODD2023---Datascience---Ex-02/assets/84171243/82ba5f19-d9e3-48e8-a307-201ca60c2e8b">

<img width="379" alt="Screenshot 2023-10-13 201052" src="https://github.com/K1540438/ODD2023---Datascience---Ex-02/assets/84171243/9d9b08d1-9898-476e-94d6-213a0d20de2e">

<img width="372" alt="Screenshot 2023-10-13 201059" src="https://github.com/K1540438/ODD2023---Datascience---Ex-02/assets/84171243/c192ec23-8810-477a-b8a8-3ba4dd525ced">

<img width="375" alt="Screenshot 2023-10-13 201106" src="https://github.com/K1540438/ODD2023---Datascience---Ex-02/assets/84171243/228feb85-6afa-4263-aa66-5e0f2722c122">

<img width="298" alt="Screenshot 2023-10-13 201134" src="https://github.com/K1540438/ODD2023---Datascience---Ex-02/assets/84171243/146e8d01-f05e-406e-8bd2-b8d1e5ee0f6b">

<img width="258" alt="Screenshot 2023-10-13 201141" src="https://github.com/K1540438/ODD2023---Datascience---Ex-02/assets/84171243/0a6c6589-33bf-445b-b576-c8570197a23f">

<img width="257" alt="Screenshot 2023-10-13 201147" src="https://github.com/K1540438/ODD2023---Datascience---Ex-02/assets/84171243/517b434c-a85f-42c3-af40-992f29ce7540">

<img width="266" alt="Screenshot 2023-10-13 201153" src="https://github.com/K1540438/ODD2023---Datascience---Ex-02/assets/84171243/96be6604-ca67-40f0-bfa2-10aee4fe2fd3">

<img width="194" alt="Screenshot 2023-10-13 201202" src="https://github.com/K1540438/ODD2023---Datascience---Ex-02/assets/84171243/f1e62767-ddca-40ce-a892-6f69a6ccfe92">

<img width="209" alt="Screenshot 2023-10-13 201209" src="https://github.com/K1540438/ODD2023---Datascience---Ex-02/assets/84171243/e47eacce-210a-4f3e-afc1-1ae6f877f7ed">



