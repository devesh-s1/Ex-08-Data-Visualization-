# Ex-08-Data-Visualization-

## AIM
To Perform Data Visualization on the given dataset and save the data to a file. 

# Explanation
Data visualization is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns in data.

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature generation and selection techniques to all the features of the data set
### STEP 4
Apply data visualization techniques to identify the patterns of the data.


# CODE

Data Pre-Processing
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
df=pd.read_csv("/content/Superstore.csv",encoding="ISO-8859-1")
df
df.isnull.sum()
df.info()
df.describe()
```

Which Segment has Highest sales?
```
sns.lineplot(x="Segment",y="Sales",data=df,marker='o')
plt.title("Segment vs Sales")
plt.xticks(rotation = 90)
plt.show()

sns.barplot(x="Segment",y="Sales",data=df)
plt.xticks(rotation = 90)
plt.show()
```

Which City has Highest profit?
```
df.shape
df1 = df[(df.Profit >= 60)]
df1.shape

plt.figure(figsize=(30,8))
states=df1.loc[:,["City","Profit"]]
states=states.groupby(by=["City"]).sum().sort_values(by="Profit")
sns.barplot(x=states.index,y="Profit",data=states)
plt.xticks(rotation = 90)
plt.xlabel=("City")
plt.ylabel=("Profit")
plt.show()
```

Which ship mode is profitable?
```
sns.barplot(x="Ship Mode",y="Profit",data=df)
plt.show()
sns.lineplot(x="Ship Mode",y="Profit",data=df)
plt.show()


Sales of the product based on region.
```
states=df.loc[:,["Region","Sales"]]
states=states.groupby(by=["Region"]).sum().sort_values(by="Sales")
sns.barplot(x=states.index,y="Sales",data=states)
plt.xticks(rotation = 90)
plt.xlabel=("Region")
plt.ylabel=("Sales")
plt.show()
```
df.groupby(['Region']).sum().plot(kind='pie', y='Sales',figsize=(6,9),pctdistance=1.7,labeldistance=1.2)
```

Find the relation between sales and profit.
```
df["Sales"].corr(df["Profit"])
df_corr = df.copy()
df_corr = df_corr[["Sales","Profit"]]
df_corr.corr()
sns.pairplot(df_corr, kind="scatter")
plt.show()
```

Segment
```
grouped_data = df.groupby('Segment')[['Sales', 'Profit']].mean()
#Create a bar chart of the grouped data
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('Segment')
ax.set_ylabel('Value')
ax.legend()
plt.show()
```

City
```
grouped_data = df.groupby('City')[['Sales', 'Profit']].mean()
#Create a bar chart of the grouped data
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('City')
ax.set_ylabel('Value')
ax.legend()
plt.show()
```

States
```
grouped_data = df.groupby('State')[['Sales', 'Profit']].mean()
#Create a bar chart of the grouped data
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('State')
ax.set_ylabel('Value')
ax.legend()
plt.show()
```

Segment and Ship Mode
```
grouped_data = df.groupby(['Segment', 'Ship Mode'])[['Sales', 'Profit']].mean()
pivot_data = grouped_data.reset_index().pivot(index='Segment', columns='Ship Mode', values=['Sales', 'Profit'])
#Create a bar chart of the grouped data
fig, ax = plt.subplots()
pivot_data.plot(kind='bar', ax=ax)
ax.set_xlabel('Segment')
ax.set_ylabel('Value')
plt.legend(title='Ship Mode')
plt.show()
```

Segment, Ship mode and Region
```
grouped_data = df.groupby(['Segment', 'Ship Mode','Region'])[['Sales', 'Profit']].mean()
pivot_data = grouped_data.reset_index().pivot(index=['Segment', 'Ship Mode'], columns='Region', values=['Sales', 'Profit'])
sns.set_style("whitegrid")
sns.set_palette("Set1")
pivot_data.plot(kind='bar', stacked=True, figsize=(10, 5))
plt.xlabel('Segment - Ship Mode')
plt.ylabel('Value')
plt.legend(title='Region')
plt.show()
```

# OUPUT

Data Pre-Processing

![image](https://github.com/collinsjoel10/Ex-08-Data-Visualization-/assets/118626456/b4f6d9dd-41c8-42f9-b6b0-95a0683dbb43)

![image](https://github.com/collinsjoel10/Ex-08-Data-Visualization-/assets/118626456/3924effa-d103-404a-b338-edc4adbfa87e)

![image](https://github.com/collinsjoel10/Ex-08-Data-Visualization-/assets/118626456/5bae2404-cca8-4c26-96bd-3aa0eff2447d)

![image](https://github.com/collinsjoel10/Ex-08-Data-Visualization-/assets/118626456/0a9b73c0-01c6-4a87-8879-f3a02bf5c24a)

Which Segment has Highest sales?

![image](https://github.com/collinsjoel10/Ex-08-Data-Visualization-/assets/118626456/52112455-12e6-4818-8e44-88cb6d9d488c)

![image](https://github.com/collinsjoel10/Ex-08-Data-Visualization-/assets/118626456/053b3d21-18d2-4b33-85cd-c246f82cdf0a)

Which City has Highest profit?

![image](https://github.com/collinsjoel10/Ex-08-Data-Visualization-/assets/118626456/01f2da27-0b2f-49bc-9795-4e5139523cd0)

Which ship mode is profitable?

![image](https://github.com/collinsjoel10/Ex-08-Data-Visualization-/assets/118626456/521d9227-6f81-4a0f-ad77-66ad2b755b77)

Sales of the product based on region.

![image](https://github.com/collinsjoel10/Ex-08-Data-Visualization-/assets/118626456/bbb2c97e-5af9-40be-98cc-04fa7cdcea03)

![image](https://github.com/collinsjoel10/Ex-08-Data-Visualization-/assets/118626456/3825f632-da39-40fb-99de-3c88a38725e1)

Find the relation between sales and profit

![image](https://github.com/collinsjoel10/Ex-08-Data-Visualization-/assets/118626456/e381e185-7797-4c23-915a-6d2c87a5e6d1)

Find the relation between sales and profit based on the following category.

Segment

![image](https://github.com/collinsjoel10/Ex-08-Data-Visualization-/assets/118626456/f2699849-8f64-433f-91c2-e8175f8a9efb)

City

![image](https://github.com/collinsjoel10/Ex-08-Data-Visualization-/assets/118626456/c1783769-bf02-4067-a844-f0ffc2245733)

States

![image](https://github.com/collinsjoel10/Ex-08-Data-Visualization-/assets/118626456/663f47d9-9fad-4a0a-b7d4-9c789b0a19fe)

Segment and Ship Mode

![image](https://github.com/collinsjoel10/Ex-08-Data-Visualization-/assets/118626456/fadbc6c4-ce58-4dec-a797-a0ffb74feaa7)


Segment, Ship mode and Region

![image](https://github.com/collinsjoel10/Ex-08-Data-Visualization-/assets/118626456/bcf73997-d138-4a45-9d62-87cc011bd36d)

## Result

Thus, Data Visualization is performed on the given dataset and save the data to a file.
