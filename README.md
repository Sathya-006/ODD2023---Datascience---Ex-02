# Ex02-Outlier
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them
CODE AND OUTPUT:
```
import pandas as pd
import seaborn as sns
from scipy import stats
import numpy as np
```
```
from google.colab import files
uploaded = files.upload()
```
![image](https://github.com/Sathya-006/ODD2023---Datascience---Ex-02/assets/121661327/7821b902-d149-42b7-8aea-328202d95401)

```
df = pd.read_csv("bhp.csv")
q1 = df['price_per_sqft'].quantile(0.25)
q2 = df['price_per_sqft'].quantile(0.5)
q3 = df['price_per_sqft'].quantile(0.75)
iqr = q3-q1
iqr
```
![image](https://github.com/Sathya-006/ODD2023---Datascience---Ex-02/assets/121661327/3fdfc721-54d6-4cbc-80e5-9ebb8ed45a31)

```
low = q1-1.5*iqr
low
```
![image](https://github.com/Sathya-006/ODD2023---Datascience---Ex-02/assets/121661327/ce7e7507-f257-45ba-b170-b0001eeca596)

```
high = q3+1.5*iqr
high
```
![image](https://github.com/Sathya-006/ODD2023---Datascience---Ex-02/assets/121661327/d33cb30e-c1ec-4861-81b9-6a6095237399)

```
df = df[((df['price_per_sqft']>=low) & (df['price_per_sqft']<=high))]
df
```
![image](https://github.com/Sathya-006/ODD2023---Datascience---Ex-02/assets/121661327/5a0d8c01-2763-4d8e-997c-b5d6e524c026)

```
z = np.abs(stats.zscore(df['price_per_sqft']))
z
```
![image](https://github.com/Sathya-006/ODD2023---Datascience---Ex-02/assets/121661327/9f4ade31-3ae8-4859-b38d-f9914c51f3fc)

```
df1 = df[z<3]
df1
```
![image](https://github.com/Sathya-006/ODD2023---Datascience---Ex-02/assets/121661327/c4ded9af-3435-4247-80a2-cbdf8948012b)

```
from google.colab import files
uploaded = files.upload()
```
![image](https://github.com/Sathya-006/ODD2023---Datascience---Ex-02/assets/121661327/9251703c-27ac-4077-9b87-22acc7cdba61)
```
df = pd.read_csv("height_weight.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
iqr = q3-q1
iqr
```
![image](https://github.com/Sathya-006/ODD2023---Datascience---Ex-02/assets/121661327/739c0b5d-a45b-4a2d-a000-c69442fda9ad)
```
low = q1 - 1.5*iqr
low
```
![image](https://github.com/Sathya-006/ODD2023---Datascience---Ex-02/assets/121661327/efac0b2e-71e3-4008-a447-cafcae6311a4)
```
high = q3+1.5*iqr
high
```
![image](https://github.com/Sathya-006/ODD2023---Datascience---Ex-02/assets/121661327/06308326-91ed-4e35-9b20-4c29ddc3454f)
```
df = df[((df['height'] >=low) & (df['height']<= high))]
df
```
![image](https://github.com/Sathya-006/ODD2023---Datascience---Ex-02/assets/121661327/385d844f-2fab-44dd-bd85-983e74a400a9)

```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/Sathya-006/ODD2023---Datascience---Ex-02/assets/121661327/c0e4833b-e75f-4677-9c60-f7921052de53)
```
df1 = df[z<3]
df1
```
![image](https://github.com/Sathya-006/ODD2023---Datascience---Ex-02/assets/121661327/1b74e6f1-6d52-4a04-8788-cf8e8df2457a)
```
df = pd.read_csv("height_weight.csv")
q1 = df['weight'].quantile(0.25)
q2 = df['weight'].quantile(0.5)
q3 = df['weight'].quantile(0.75)
iqr = q3-q1
iqr
```
