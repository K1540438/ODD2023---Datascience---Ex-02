# Ex02-Outlier

# Aim:
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them

# ALGORITHM:
# STEP 1:
Read the given Data.

# STEP 2:
Get the information about the data.

# STEP 3:
Detect the Outliers using IQR method and Z score.

# STEP 4:
Remove the outliers:

# STEP 5:
Plot the datas using box plot.

# PROGRAM:
  ```python
import pandas as pd
import seaborn as sns
age = [1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af=pd.DataFrame(age)
af
```
<img width="49" alt="image" src="https://github.com/TejaswiniGugananthan/ODD2023---Datascience---Ex-02/assets/121222763/3e07b80e-68d3-47bf-8617-675a82f7f76d">

```python
sns.boxplot(data=af)
```
<img width="286" alt="image" src="https://github.com/TejaswiniGugananthan/ODD2023---Datascience---Ex-02/assets/121222763/b2e694ee-5d35-41aa-8135-81fcbeae529a">

```python
sns.scatterplot(data=af)
```
<img width="290" alt="image" src="https://github.com/TejaswiniGugananthan/ODD2023---Datascience---Ex-02/assets/121222763/d7ea0bd1-b3be-4931-85b2-0688cf837cf1">

```python
q1=af.quantile(0.25)
q2=af.quantile(0.5)
q3=af.quantile(0.75)
iqr=q3-q1
irq=af.quantile(0.5)
```
```python
low=q1-1.5*iqr
low
```
<img width="69" alt="image" src="https://github.com/TejaswiniGugananthan/ODD2023---Datascience---Ex-02/assets/121222763/3f44bada-feca-42d2-a602-75ef93fadda8">

```python
high=q3+1.5*iqr
high
```
<img width="66" alt="image" src="https://github.com/TejaswiniGugananthan/ODD2023---Datascience---Ex-02/assets/121222763/8a8e591b-7862-40ff-80f1-d351fcb1c780">

```python
aq=af[((af>=low)&(af<=high))]
aq.dropna()
```
<img width="52" alt="image" src="https://github.com/TejaswiniGugananthan/ODD2023---Datascience---Ex-02/assets/121222763/3a42186f-b1da-4646-b62b-b659152036c5">

```python
sns.boxplot(data=af)
```
<img width="283" alt="image" src="https://github.com/TejaswiniGugananthan/ODD2023---Datascience---Ex-02/assets/121222763/5efbc140-3782-45b1-b723-4b04cbf9e87f">

```python
af=af[((af>=low)&(af<=high))]
af.dropna()
```
<img width="52" alt="image" src="https://github.com/TejaswiniGugananthan/ODD2023---Datascience---Ex-02/assets/121222763/d991b2e9-4ad5-4e78-afa0-f244ca53ff19">

```python
sns.boxplot(data=af)
```
<img width="285" alt="image" src="https://github.com/TejaswiniGugananthan/ODD2023---Datascience---Ex-02/assets/121222763/9733583f-c1de-486d-9f35-5eb9850e1c9f">

```python
sns.scatterplot(data=af)
```
<img width="282" alt="image" src="https://github.com/TejaswiniGugananthan/ODD2023---Datascience---Ex-02/assets/121222763/05f71607-e5c0-499a-b397-0b10f88e0009">
  
```python
import pandas as pd
import numpy as np
import seaborn as sns
import pandas as pd
from scipy import stats
```
```python
data = {'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}
df=pd.DataFrame(data)
df
```
<img width="52" alt="image" src="https://github.com/TejaswiniGugananthan/ODD2023---Datascience---Ex-02/assets/121222763/9666a946-ca20-4801-95d4-25a68b5aec77">

```python
sns.boxplot(data=df)
```
<img width="286" alt="image" src="https://github.com/TejaswiniGugananthan/ODD2023---Datascience---Ex-02/assets/121222763/bd33df32-2dea-4b33-8be6-2d1b81eab374">

```python
z=np.abs(stats.zscore(df))
print(df[z['weight']>3])
```
<img width="53" alt="image" src="https://github.com/TejaswiniGugananthan/ODD2023---Datascience---Ex-02/assets/121222763/7a647b1c-2f99-4394-8de3-021557977e78">

```python
val=[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,69,202,72,75,78,81,84,232,87,90,93,96,99,258]
df=pd.DataFrame(data)
```
```python
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
```
```python
op=d_o(val)
op
``
<img width="68" alt="image" src="https://github.com/TejaswiniGugananthan/ODD2023---Datascience---Ex-02/assets/121222763/80263fed-d9b8-4069-93d2-d194f424a419">

```python
import pandas as pd
import numpy as np
import seaborn as sns
from scipy import stats
```
```pyhton
id=pd.read_csv("iris.csv")
id
```
<img width="272" alt="image" src="https://github.com/TejaswiniGugananthan/ODD2023---Datascience---Ex-02/assets/121222763/2a34017f-c89a-48c4-8f22-6f1e0df886ff">

```pyhton
sns.boxplot(x='sepal_width',data=id)
```
<img width="277" alt="image" src="https://github.com/TejaswiniGugananthan/ODD2023---Datascience---Ex-02/assets/121222763/fbacb6f4-4d89-469c-829e-25a3b3ee38ac">

```pyhton
c1=id.sepal_width.quantile(0.25)
c3=id.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
<img width="29" alt="image" src="https://github.com/TejaswiniGugananthan/ODD2023---Datascience---Ex-02/assets/121222763/2143cf85-e8bd-4f03-bb72-562dc0bfc7f2">

```python
rid=id[((id.sepal_width<(c1-1.5*iq))|(id.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
<img width="206" alt="image" src="https://github.com/TejaswiniGugananthan/ODD2023---Datascience---Ex-02/assets/121222763/0c6bd8aa-e54d-4824-8011-827c3e0485f9">

```python
delid=id[~((id.sepal_width<(c1-1.5*iq))|(id.sepal_width>(c3+1.5*iq)))]
delid
```
<img width="268" alt="image" src="https://github.com/TejaswiniGugananthan/ODD2023---Datascience---Ex-02/assets/121222763/bc3a76ca-73fb-4406-8f9a-590fe97b0f48">

```python
sns.boxplot(x='sepal_width',data=delid)
```
<img width="269" alt="image" src="https://github.com/TejaswiniGugananthan/ODD2023---Datascience---Ex-02/assets/121222763/212cc2fc-03cd-4fe6-a484-a2c2a182a51e">

# Result:
Hence the given set of data is read and the outliers are removed using the IQR method and Zscore method.





