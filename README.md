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

import pandas as pd
import numpy as np
import seaborn as sns
import scipy.stats as stats
import matplotlib.pyplot as plt

# Read dataset
df = pd.read_csv("SAMPLEIDS.csv")
df
df.head()
df.tail()
df.info()
df.describe()
df.isnull().sum()
df.isnull().any()

df.dropna()
df.fillna(0)
df.fillna(method='ffill')
df.fillna({'GENDER':'MALE','NAME':'SRI'})

# Iris dataset
ir = pd.read_csv("iris.csv")
ir
ir.describe()


sns.boxplot(x='sepal_width', data=ir)
plt.title("Boxplot Before Removing Outliers")
plt.show()


ir.plot.scatter(x='sepal_length', y='sepal_width', title="Before Removing Outliers")
plt.show()


Q1 = ir.sepal_width.quantile(0.25)
Q3 = ir.sepal_width.quantile(0.75)
IQR = Q3 - Q1
print(IQR)

# Outliers
ran = ir[((ir.sepal_width < (Q1 - 1.5 * IQR)) | (ir.sepal_width > (Q3 + 1.5 * IQR)))]
ran['sepal_width']

# Remove outliers
ran = ir[~((ir.sepal_width < (Q1 - 1.5 * IQR)) | (ir.sepal_width > (Q3 + 1.5 * IQR)))]
ran['sepal_width']


sns.boxplot(x='sepal_width', data=ran)
plt.title("Boxplot After IQR")
plt.show()


ran.plot.scatter(x='sepal_length', y='sepal_width', title="After IQR Outlier Removal")
plt.show()


z = np.abs(stats.zscore(ir['petal_length']))
z

ir1 = ir[z < 3]
ir1


ir1.plot.scatter(x='petal_length', y='petal_width', title="After Z-score Outlier Removal")
plt.show()

<img width="490" height="446" alt="Screenshot 2026-04-29 220025" src="https://github.com/user-attachments/assets/97882817-950c-47db-a9b4-9893f48e67b4" />

<img width="783" height="617" alt="Screenshot 2026-04-29 162157" src="https://github.com/user-attachments/assets/394806df-ed10-49dd-bf6d-9d8383c4c217" />

<img width="813" height="615" alt="Screenshot 2026-04-29 161822" src="https://github.com/user-attachments/assets/585a1d19-eea8-4232-a96d-90f672a3c6c9" />

<img width="64" height="21" alt="Screenshot 2026-04-29 161915" src="https://github.com/user-attachments/assets/eab094e1-c46a-4096-9b90-150bb40edf2c" />

<img width="394" height="125" alt="Screenshot 2026-04-29 161950" src="https://github.com/user-attachments/assets/24b9f349-801b-4cb9-9aff-0da9e81c15b7" />

<img width="542" height="292" alt="Screenshot 2026-04-29 162057" src="https://github.com/user-attachments/assets/49df0993-9a5e-44c7-98e9-64d9427219b6" />

<img width="742" height="618" alt="Screenshot 2026-04-29 161741" src="https://github.com/user-attachments/assets/601903e7-5b9b-42d3-a1a7-75ff85f2416f" />

<img width="851" height="622" alt="Screenshot 2026-04-29 214632" src="https://github.com/user-attachments/assets/db5877ea-13cb-4665-b539-5979eb78e01d" />

<img width="654" height="494" alt="Screenshot 2026-04-29 214725" src="https://github.com/user-attachments/assets/ead16b98-e296-43cb-9758-1917afe6d179" />

<img width="827" height="623" alt="Screenshot 2026-04-29 214806" src="https://github.com/user-attachments/assets/1fc2387b-b241-465b-9109-35f8e1519e24" />


















# Result
Thus the given data successfully performed data cleaning and saved the cleaned data to a file
