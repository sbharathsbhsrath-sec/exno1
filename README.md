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
```
name:bharath
reg no:212225230031
```

```
import pandas as pd data=pd.read_csv("SAMPLEIDS.csv") data
```
<img width="1014" height="786" alt="image" src="https://github.com/user-attachments/assets/4ff50465-a969-486e-a34b-92e4af6c1777" />
```
data.head()
```
<img width="981" height="246" alt="image" src="https://github.com/user-attachments/assets/c2299813-cd97-4ed9-9673-abab2044f7a4" />
```
data.tail()
```
<img width="831" height="192" alt="image" src="https://github.com/user-attachments/assets/1a8feb07-7074-43bd-928a-b19e05d50c3c" />
```
data.isnull()
```
<img width="711" height="647" alt="image" src="https://github.com/user-attachments/assets/7560bc97-ef0e-494f-9bdf-d6258726f2f4" />
```
data.isnull().sum()
```
<img width="136" height="269" alt="image" src="https://github.com/user-attachments/assets/11d8083b-738b-4e17-9e13-2ad27d6bf859" />
```
data.isnull().any()
```
<img width="156" height="274" alt="image" src="https://github.com/user-attachments/assets/9eb5438c-57df-4e0e-810d-563dfa75a479" />
```
data.dropna()
```
<img width="792" height="392" alt="image" src="https://github.com/user-attachments/assets/1888c3e2-6c7c-4d68-99a7-54d4163c2ca7" />
```
data.fillna(0)
```
<img width="798" height="609" alt="image" src="https://github.com/user-attachments/assets/4fbff931-7961-4f12-a15f-2e793e2d8eda" />
```
data.fillna(method='ffill')
```
<img width="800" height="630" alt="image" src="https://github.com/user-attachments/assets/ab72f266-cf6b-4f53-af03-4f86757c11e1" />
```
data.fillna(method='bfill')
```
<img width="803" height="609" alt="image" src="https://github.com/user-attachments/assets/cdf216dc-5e66-4a3a-80d1-d751a0e294aa" />
```
data.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
<img width="801" height="608" alt="image" src="https://github.com/user-attachments/assets/bea7eee2-f45d-4ab7-8e4f-b86355b01b0f" />
```
IQR(Inter Quartile Range) import pandas as pd ir=pd.read_csv("iris.csv") ir
```
<img width="517" height="388" alt="image" src="https://github.com/user-attachments/assets/2c7468c5-a9e4-4d8a-85af-fae3dc8ec886" />
```
ir.describe()
```
<img width="442" height="279" alt="image" src="https://github.com/user-attachments/assets/0ba4b856-7612-4a4b-bd08-c89d43f1bb8c" />
```
ir.shape
```
<img width="105" height="49" alt="image" src="https://github.com/user-attachments/assets/256dca47-1396-40cc-88ee-950d345aae0c" />
```
ir.info()
```
<img width="385" height="241" alt="image" src="https://github.com/user-attachments/assets/02a7ec17-b8a6-4360-84f1-2a25f8bc1746" />
```
import seaborn as sns sns.boxplot(x='sepal_width',data=ir)
```
<img width="615" height="530" alt="image" src="https://github.com/user-attachments/assets/b2338c7b-3584-4f89-b507-0459df217054" />
```
q1=ir.sepal_width.quantile(0.25) q3=ir.sepal_width.quantile(0.75) iqr=q3-q1 print(iqr)
```
<img width="105" height="33" alt="image" src="https://github.com/user-attachments/assets/0a044fa2-c64c-4b6d-874c-ff95f4a6fe17" />
```
out=ir[((ir.sepal_width<(q1-1.5iqr))|(ir.sepal_width>(q3+1.5iqr)))] out['sepal_width']
```
<img width="355" height="104" alt="image" src="https://github.com/user-attachments/assets/30ad5371-3e8b-43df-8e1e-2c99ab3ef3df" />
```
<img width="355" height="104" alt="image" src="https://github.com/user-attachments/assets/9eeb721c-10fe-4e8b-9ef5-fe942ddbd205" />

```
<img width="355" height="104" alt="image" src="https://github.com/user-attachments/assets/0e30ff7a-346b-4c1c-b4dc-5339c75d201b" />
```
nor=ir[~((ir.sepal_width<(q1-1.5iqr))|(ir.sepal_width>(q3+1.5iqr)))] nor['sepal_width']
```
<img width="472" height="253" alt="image" src="https://github.com/user-attachments/assets/d92bd8c7-0d6e-4394-9fb4-4ad4f660a4f8" />
```
sns.boxplot(x='sepal_width',data=nor)
```
<img width="658" height="538" alt="image" src="https://github.com/user-attachments/assets/5136c6aa-122b-4635-a9eb-4db83d7c18df" />
```
Z-SCORE

import numpy as np import pandas as pd df=pd.read_csv("heights.csv") df
```
<img width="216" height="441" alt="image" src="https://github.com/user-attachments/assets/112d23da-0dc4-467d-9f2d-f61bd1318c3a" />
```
import scipy.stats as stats q1 = df['height'].quantile(0.25) q2 = df['height'].quantile(0.5) q3 = df['height'].quantile(0.75) iqr = q3-q1 iqr
```
<img width="207" height="48" alt="image" src="https://github.com/user-attachments/assets/bcca1a28-c7ee-4f48-a021-8d2106044623" />
```
low = q1 - 1.5iqr print(low) high = q3 + 1.5iqr print(high)
```
<img width="173" height="49" alt="image" src="https://github.com/user-attachments/assets/7061a71d-b8dc-487c-b0a0-f415d71a6c0e" />
```
df1 = df[((df['height'] >=low)& (df['height'] <=high))] df1
```
<img width="167" height="376" alt="image" src="https://github.com/user-attachments/assets/385774a4-ca2e-48ca-870d-32d6d413b8d3" />
```
z = np.abs(stats.zscore(df['height'])) z
```
<img width="331" height="300" alt="image" src="https://github.com/user-attachments/assets/2d02e371-8b2b-401f-bbf1-fb4541933e1a" />
```
df1 = df[z<3] df1
```
<img width="228" height="412" alt="image" src="https://github.com/user-attachments/assets/09451c86-70b8-48bc-9839-721540f8efdd" />

# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
