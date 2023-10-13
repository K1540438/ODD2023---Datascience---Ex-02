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





