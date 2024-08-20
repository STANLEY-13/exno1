# Exno:1
Data Cleaning Process
# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.
# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.
# Algorithm
STEP 1: Read the given Data
STEP 2: Get the information about the data
STEP 3: Remove the null values from the data
STEP 4: Save the Clean data to the file
STEP 5: Remove outliers using IQR
STEP 6: Use zscore of to remove outliers

# Coding and Output
            <<include your coding and its corressponding output screen shots here>>
## Data Cleaning
```
import pandas as pd
df=pd.read_csv("SAMPLEIDS (1).csv")
df
```
![image](https://github.com/user-attachments/assets/e21fa19d-d78e-44d6-9413-8104dcee89b5)
```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/9047c155-afcd-4dd2-bd82-7d888145d0b8)
```
df.isnull().any()
```
![image](https://github.com/user-attachments/assets/4bb8cc69-956e-45f7-b8f5-f86eb0f76cb7)
```
df.dropna()
```
![image](https://github.com/user-attachments/assets/efa8c9c7-db12-4eec-ae8f-07fdd9646560)
```
df.fillna(0)
```
![image](https://github.com/user-attachments/assets/c786d8c9-fdce-44d4-bcfa-269102bd7e93)
```
df.fillna(method = 'ffill')
```
![image](https://github.com/user-attachments/assets/10f935f7-fc7d-4555-aa42-c49f7e4fa090)
```
df_dropped = df.dropna()
df_dropped
```
![image](https://github.com/user-attachments/assets/3a5ccdf4-7320-4407-8903-80570d5a9218)
```
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![image](https://github.com/user-attachments/assets/434abc36-bc12-49c7-8470-322d712c81be)

## IQR(Inter Quartile Range)
```
import pandas as pd
ir=pd.read_csv('iris.csv')
ir
```
![image](https://github.com/user-attachments/assets/f119b712-e32b-4fcc-ad99-ccba6b1deae0)
```
ir.describe()
```
![image](https://github.com/user-attachments/assets/f9643717-d79f-4418-84c1-ab811b1e7b74)
```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/user-attachments/assets/bbfb18e6-6b08-4681-b216-b86f36e2e74a)
```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/user-attachments/assets/a18d5443-9780-411a-9928-10f8bfad941c)
```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/343d4c52-a2ad-4950-b7f2-5884015e801c)
```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/user-attachments/assets/3507bec4-6096-4186-81d1-b23e760ac013)
```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/2c407e8c-3b27-4b63-b5e7-a38c64c84089)
## Z-Score
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("heights.csv")
dataset
```
![image](https://github.com/user-attachments/assets/3ea82faf-9f6a-4e49-b8f3-205b377e8d61)
```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
iqr = q3-q1
iqr
```
```
low = q1 - 1.5*iqr
low
```
![image](https://github.com/user-attachments/assets/413057de-2739-4ed2-9f8b-10c54fdda8be)
```
high = q3 + 1.5*iqr
high
```
![image](https://github.com/user-attachments/assets/2355a3c5-c3cc-4e5d-be09-55ba1bc6a08e)
```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/user-attachments/assets/60bd81f8-97ff-4e5f-a31c-0970e56c1abb)
```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/user-attachments/assets/64e10ac4-1a0b-43a9-96cf-58d49462bccd)
```
df1 = df[z<3]
df1
```
![image](https://github.com/user-attachments/assets/42c39502-2e20-47ad-98f9-1c027c8191ec)

# Result
          <<include your Result here>>
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
