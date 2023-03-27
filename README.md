# Ex02-Outlier

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them
 # Aim:
  TO detect and remove the outliers in the given data set and save the final data.
  
### Step 1:
Import the required packages(pandas,numpy,scipy)

### Step 2:
Read the given csv file

### Step3:
Convert the file into a dataframe and get information of the data.

### Step 4:
Remove the non numerical data columns using drop() method.

### Step 5:
Detect the outliers in the data set using z scores method.

### Step 6:
Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)

### Step 7:
Check if the outliersare removed from data set using graphical methods.

### Step 8:
Save the final data set into the file.

# Program:
## (1) & (2) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe.
```python
DEVELOPED BY: HARITHA SHREE V, 
REGISTER NUMBER: 212222230046
import pandas as pd
import numpy as np
import seaborn as sns
df = pd.read_csv("/content/bhp.csv")
df
df.head()
df.describe()
df.info()
df.isnull().sum()
df.shape
sns.boxplot(x="price_per_sqft",data=df)
q1 = df['price_per_sqft'].quantile(0.25)
q3 = df['price_per_sqft'].quantile(0.75)
print("First Quantile =",q1,"\nSecond Quantile =",q3)
IQR = q3-q1
ul = q3+1.5*IQR
ll = q1-1.5*IQR
df1 =df[((df['price_per_sqft']>=ll)&(df['price_per_sqft']<=ul))]
df1
df1.shape
sns.boxplot(x="price_per_sqft",data=df1)
```
## (3)Examine price_per_sqft column and use zscore of 3 to remove outliers.
```
from scipy import stats
z = np.abs(stats.zscore(df['price_per_sqft']))
df2 = df[(z<3)]
df2
print(df2.shape)
sns.boxplot(x="price_per_sqft",data=df2)
```
## (4)(i) For the data set height_weight.csv detect weight outliers using IQR method.
```
import pandas as pd
import numpy as np
import seaborn as sns
df = pd.read_csv("/content/height_weight - Sheet1.csv")
df
df.head()
df.info()
df.describe()
df.isnull().sum()
df.shape
print("First Quantile =",q1,"\nSecond Quantile =",q3)
IQR = q3-q1
ul = q3+1.5*IQR
ll = q1-1.5*IQR
df1 =df[((df['weight']>=ll)&(df['weight']<=ul))]
df1
df1.shape
sns.boxplot(x="weight",data=df1)
```
## (4)(ii) For the data set height_weight.csv detect height outliers using IQR method.
```
sns.boxplot(x="height",data=df)
q1 = df['height'].quantile(0.25)
q3 = df['height'].quantile(0.75)
print("First Quantile =",q1,"\nSecond Quantile =",q3)
IQR = q3-q1
ul = q3+1.5*IQR
ll = q1-1.5*IQR
df2 =df[((df['height']>=ll)&(df['height']<=ul))]
df2
df2.shape
sns.boxplot(x="height",data=df2)
```
# OUTPUT:
## df.head()
![image](https://user-images.githubusercontent.com/121285701/227851788-5ff1e238-4f7a-412c-88c4-d16f525241a4.png)
## df.describe()
![image](https://user-images.githubusercontent.com/121285701/227851937-b081d286-ba00-465a-867a-11b357725c0d.png)
## df.info()
![image](https://user-images.githubusercontent.com/121285701/227852102-6b93d3ef-9ae1-472d-a625-9c3d09d84b71.png)
## df.shape
![image](https://user-images.githubusercontent.com/121285701/227852272-617fd24f-a8cb-4d6d-ba7f-1f631e5c9f0f.png)
## BOXPLOT BEFORE REMOVING OUTLIERS
![image](https://user-images.githubusercontent.com/121285701/227852420-efd0ef34-01fa-4538-ac4c-47d43b6a7a72.png)
## NEWDATA USING IQR
![image](https://user-images.githubusercontent.com/121285701/227852596-b69600ed-9642-4c11-902e-b9e8526929b0.png)
## OUTLIERS
![image](https://user-images.githubusercontent.com/121285701/227852844-d0247a50-1998-4a0d-8361-a0cf6ef19088.png)
## newdata.shape
![image](https://user-images.githubusercontent.com/121285701/227853125-8fd18885-c96c-4ddf-9621-eb091c5319e2.png)
## BOXPLOT AFTER REMOVING OUTLIERS USING IQR
![image](https://user-images.githubusercontent.com/121285701/227853311-8409389c-6452-4e0e-94a3-5e5852a46c43.png)
## Zscore of 3
## NEWDATA USING Zscore
![image](https://user-images.githubusercontent.com/121285701/227853617-fc4bd806-ed54-4ecd-b70d-691ed4bc217d.png)
## OUTLIERS
![image](https://user-images.githubusercontent.com/121285701/227853882-df105888-2e10-460a-8731-b5a9fbe68527.png)
## newdata2.shape
![image](https://user-images.githubusercontent.com/121285701/227854197-f8f34036-eaca-4f74-8236-f031e73e8c5a.png)
## BOXPLOT AFTER REMOVING OUTLIERS USING Zscore
![image](https://user-images.githubusercontent.com/121285701/227854394-3ac1a11a-4824-4ab4-b83c-ce69c6997c5e.png)
## height_weight.csv
### dataset.shape ![image](https://user-images.githubusercontent.com/121285701/227854806-4685d095-943e-4c47-8104-6e20b70046de.png)
## dataset.describe()
![image](https://user-images.githubusercontent.com/121285701/227855117-17492adf-cf36-4869-a4ab-428c2244e6f0.png)
## dataset.info()
![image](https://user-images.githubusercontent.com/121285701/227855222-2f0daa4b-b4a8-4d12-94fc-78f501118aa6.png)
## BOXPLOT BEFORE REMOVING OUTLIERS
![image](https://user-images.githubusercontent.com/121285701/227855371-7c42947e-31fa-4519-b536-c3c923b6e576.png)
## HEIGHT OUTLIERS
![image](https://user-images.githubusercontent.com/121285701/227855482-88dc0c08-9ac7-4707-8d12-7f7722dfaca2.png)
## DATASET AFTER REMOVING HEIGHT OUTLIERS
![image](https://user-images.githubusercontent.com/121285701/227855584-60ea850b-8117-4c3b-b775-03e27b8f6c9f.png)
## BOXPLOT AFTER REMOVING HEIGHT OUTLIERS
![image](https://user-images.githubusercontent.com/121285701/227855721-2812eecd-36f7-4307-acf7-cbb338bbbdbc.png)
## WEIGHT OUTLIERS
![image](https://user-images.githubusercontent.com/121285701/227855870-bdfb429c-8496-4745-bb1b-effeb1c5824d.png)
## DATASET AFTER REMOVING WEIGHT OUTLIERS
![image](https://user-images.githubusercontent.com/121285701/227855959-72794ff4-c1cf-4dc1-a722-54b148363148.png)
## BOXPLOT AFTER REMOVING WEIGHT OUTLIERS
![image](https://user-images.githubusercontent.com/121285701/227856048-5c0857af-620c-4b84-a12b-ae6c7c9c3f92.png)
## RESULT
The given datasets are read and outliers are detected and are removed using IQR and z-score methods.




















