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
![image](https://github.com/Sathya-006/ODD2023---Datascience---Ex-02/assets/121661327/154d88b2-635e-4577-905b-ccf1463cf43e)
```
low = q1 - 1.5*iqr
low
```
![image](https://github.com/Sathya-006/ODD2023---Datascience---Ex-02/assets/121661327/718e75b0-3d7a-494f-9391-d561f5704beb)
```
high = q3 + 1.5*iqr
high
```
![image](https://github.com/Sathya-006/ODD2023---Datascience---Ex-02/assets/121661327/0f44de37-41ae-4f01-b454-1688420e62c2)
```
df1 = df[((df['weight'] >=low) & (df['weight']<= high))]
df1
```
![image](https://github.com/Sathya-006/ODD2023---Datascience---Ex-02/assets/121661327/51c0ef54-36a9-4f79-8eb1-14ee14aa1554)
```
z = np.abs(stats.zscore(df1['weight']))
z
```
![image](https://github.com/Sathya-006/ODD2023---Datascience---Ex-02/assets/121661327/bbd4d6c6-5bcf-4030-a27e-437149f89d2f)
```
df2 = df1[z<3]
df2
```
![image](https://github.com/Sathya-006/ODD2023---Datascience---Ex-02/assets/121661327/91c489f3-98eb-4d21-8202-9f4194fb6965)
```
from google.colab import files
uploaded = files.upload()
```
![image](https://github.com/Sathya-006/ODD2023---Datascience---Ex-02/assets/121661327/33a11039-9f86-4d69-82c3-40e15fa4d8e2)
```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
iqr = q3-q1
iqr
```
![image](https://github.com/Sathya-006/ODD2023---Datascience---Ex-02/assets/121661327/a3d43407-3603-4ccf-8cd5-7f2f3fb5494d)
```
low = q1 - 1.5*iqr
low
```
![image](https://github.com/Sathya-006/ODD2023---Datascience---Ex-02/assets/121661327/1e1e9762-bfdb-444b-9bc3-055a0cf9df4e)
```
high = q3 + 1.5*iqr
high
```
![image](https://github.com/Sathya-006/ODD2023---Datascience---Ex-02/assets/121661327/276de29f-c41b-4d72-b5ce-3b5638fb3ea5)
```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/Sathya-006/ODD2023---Datascience---Ex-02/assets/121661327/79514613-93a5-453f-9a3e-1679f735d29f)
```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/Sathya-006/ODD2023---Datascience---Ex-02/assets/121661327/0c0b6cf1-77f9-4dab-8b35-3916e1e90112)
```
df1 = df[z<3]
df1
```
![image](https://github.com/Sathya-006/ODD2023---Datascience---Ex-02/assets/121661327/a0673928-4b6f-4d43-9cc4-c71b304aa2e5)
