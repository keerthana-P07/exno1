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

# ------------------- BOXPLOT BEFORE OUTLIER REMOVAL -------------------
sns.boxplot(x='sepal_width', data=ir)
plt.title("Boxplot Before Removing Outliers")
plt.show()

# ------------------- SCATTER PLOT BEFORE CLEANING -------------------
ir.plot.scatter(x='sepal_length', y='sepal_width', title="Before Removing Outliers")
plt.show()

# ------------------- IQR METHOD -------------------
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

# ------------------- BOXPLOT AFTER IQR -------------------
sns.boxplot(x='sepal_width', data=ran)
plt.title("Boxplot After IQR")
plt.show()

# ------------------- SCATTER AFTER IQR -------------------
ran.plot.scatter(x='sepal_length', y='sepal_width', title="After IQR Outlier Removal")
plt.show()

# ------------------- Z-SCORE METHOD -------------------
z = np.abs(stats.zscore(ir['petal_length']))
z

ir1 = ir[z < 3]
ir1

# ------------------- SCATTER AFTER Z-SCORE -------------------
ir1.plot.scatter(x='petal_length', y='petal_width', title="After Z-score Outlier Removal")
plt.show()
<img width="457" height="447" alt="image" src="https://github.com/user-attachments/assets/fd6b9abb-6740-4949-a2e4-a3fedbd62fe3" />
<img width="742" height="617" alt="image" src="https://github.com/user-attachments/assets/d5d2cf50-1f1d-414c-a2b4-5afd3e8d68fa" />
<img width="812" height="615" alt="image" src="https://github.com/user-attachments/assets/a420c307-adc3-404e-b48d-ea4b03cf922f" />
<img width="63" height="21" alt="image" src="https://github.com/user-attachments/assets/82ef39c3-44a2-4ead-a109-3ce09c6d3dbb" />
<img width="393" height="125" alt="image" src="https://github.com/user-attachments/assets/6ed6537d-f443-4493-ba22-40bf7339c80e" />
<img width="542" height="292" alt="image" src="https://github.com/user-attachments/assets/0cccd314-3a9f-4578-ba43-4c338961d917" />
<img width="782" height="617" alt="image" src="https://github.com/user-attachments/assets/5f6218e0-fc3e-4e8d-91ac-2d7bd886a7b5" />
<img width="851" height="622" alt="image" src="https://github.com/user-attachments/assets/8f31945f-72c2-4626-a596-71a3875b0459" />
<img width="653" height="493" alt="image" src="https://github.com/user-attachments/assets/77589fc6-9cae-493f-bc0d-2e00a6f879a8" />
<img width="827" height="622" alt="image" src="https://github.com/user-attachments/assets/8ae7e7dc-202f-4bef-80ec-8479888510eb" />
```








# Result
Thus the given data successfully performed data cleaning and saved the cleaned data to a file
