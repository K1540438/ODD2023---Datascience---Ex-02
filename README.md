# Ex-02_DS_Outlier_Detection_and_Removal
# AIM
To detect and remove the outliers in the given data set and save the final data.

# Explanation
Outlier is a data object that deviates significantly from the rest of the data objects and behaves in a different manner. They can be caused by measurement or execution errors. The analysis of outlier data is referred to as outlier analysis or outlier mining. The box plot is a useful graphical display for describing the behavior of the data in the middle as well as at the ends of the distributions. The box plot uses the median and the lower and upper quartiles (defined as the 25th and 75th percentiles). If the lower quartile is Q1 and the upper quartile is Q3, then the difference (Q3 - Q1) is called the interquartile range or IQ.

# ALGORITHM
## STEP 1
Import the required packages(pandas,numpy,scipy)
## STEP 2
Read the given csv file
## STEP 3
Convert the file into a dataframe and get information of the data.
## STEP 4
Remove the non numerical data columns using drop() method.
## STEP 5
Detect the outliers in the data set using z scores method.
## STEP 6
Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)
## STEP 7
Check if the outliers are removed from data set using graphical methods.
## STEP 8
Save the final data set into the file

# CODE
```
/* 

**Removing Outliers - bhp.csv**
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
*/
```
# OUPUT
## Removing Outliers - bhp.csv
![img1](https://user-images.githubusercontent.com/127843136/227731877-d2981784-8d77-4e17-8b4c-8df5a8321b2a.png)
![img2](https://user-images.githubusercontent.com/127843136/227731884-94c8cd3d-0eae-40f9-a6b5-38a051e3f4ab.png)
## Using IQR method to remove Outliers of price_per_sqft
![img3](https://user-images.githubusercontent.com/127843136/227731894-f461dc1f-1258-4fb4-9872-95ae140a67ae.png)
## Removing non-numerical columns
![img4](https://user-images.githubusercontent.com/127843136/227731899-78470890-7647-41f5-8495-243e529db14e.png)
## Using z-score of 3 method to remove Outliers of price_per_sqft
![img5](https://user-images.githubusercontent.com/127843136/227731907-6b7faad5-6998-4f20-8d14-a523b10bd287.png)
![img6](https://user-images.githubusercontent.com/127843136/227731919-7d562fca-d6e6-4998-9a2a-0abfda8655a4.png)
## Removing Outliers - height_weight.csv
![image1](https://user-images.githubusercontent.com/127843136/227731926-e0c01378-151d-47c8-a13d-233f595e9e8b.png)
## Removing non numerical columns
![image2](https://user-images.githubusercontent.com/127843136/227731941-4482a162-6557-41dc-9b45-0a3a7e651920.png)
![image3](https://user-images.githubusercontent.com/127843136/227731946-d4fbec8c-4656-412e-a324-c195052b2fed.png)
## Removing Outliers of weight using IQR
![image4](https://user-images.githubusercontent.com/127843136/227731951-659f8f76-12f0-437b-9a87-3697f12e6144.png)
## Removing Outliers of height using IQR
![image5](https://user-images.githubusercontent.com/127843136/227731957-7a9d4a25-6653-44ce-a230-2ad20969fb47.png)
# RESULT
Thus the outliers are detected and removed in the given file and the final data set is saved into the file.
