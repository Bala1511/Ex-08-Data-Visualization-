# Ex-07-Data-Visualization-

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

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
df=pd.read_csv("/content/Superstore (1).csv",encoding="ISO-8859-1")
df


df.isnull()


df.describe()

sns.lineplot(x="Segment",y="Sales",data=df,marker='o')
plt.title("Segment vs Sales")
plt.xticks(rotation = 90)
plt.show()

sns.barplot(x="Segment",y="Sales",data=df)
plt.xticks(rotation = 90)
plt.show()

df.shape
df1 = df[(df.Profit >= 60)]
df1.shape

plt.figure(figsize=(90,70))
states=df1.loc[:,["City","Profit"]]
states=states.groupby(by=["City"]).sum().sort_values(by="Profit")
sns.barplot(x=states.index,y="Profit",data=states)
plt.xticks(rotation = 90)
plt.xlabel=("City")
plt.ylabel=("Profit")
plt.show()

sns.barplot(x="Ship Mode",y="Profit",data=df)
plt.show()

sns.lineplot(x="Ship Mode",y="Profit",data=df)
plt.show()

states=df.loc[:,["Region","Sales"]]
states=states.groupby(by=["Region"]).sum().sort_values(by="Sales")
sns.barplot(x=states.index,y="Sales",data=states)
plt.xticks(rotation = 90)
plt.xlabel=("Region")
plt.ylabel=("Sales")
plt.show()

df.groupby(['Region']).sum().plot(kind='pie', y='Sales',figsize=(6,9),pctdistance=1.7,labeldistance=1.2)

df["Sales"].corr(df["Postal Code"])

df_corr = df.copy()
df_corr = df_corr[["Sales","Postal Code"]]
df_corr.corr()

sns.pairplot(df_corr, kind="scatter")
plt.show()

grouped_data = df.groupby('Segment')[['Sales', 'Profit']].mean()
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('Segment')
ax.set_ylabel('Value')
ax.legend()
plt.show()

grouped_data = df.groupby('City')[['Sales', 'Profit']].mean()
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('City')
ax.set_ylabel('Value')
ax.legend()
plt.show()

grouped_data = df.groupby('State')[['Sales', 'Profit']].mean()
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('State')
ax.set_ylabel('Value')
ax.legend()
plt.show()

grouped_data = df.groupby(['Segment', 'Ship Mode'])[['Sales', 'Profit']].mean()
pivot_data = grouped_data.reset_index().pivot(index='Segment', columns='Ship Mode', values=['Sales', 'Profit'])
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
pivot_data.plot(kind='bar', ax=ax)
ax.set_xlabel('Segment')
ax.set_ylabel('Value')
plt.legend(title='Ship Mode')
plt.show()

grouped_data = df.groupby(['Segment', 'Ship Mode','Region'])[['Sales', 'Profit']].mean()
pivot_data = grouped_data.reset_index().pivot(index=['Segment', 'Ship Mode'], columns='Region', values=['Sales', 'Profit'])
sns.set_style("whitegrid")
sns.set_palette("Set1")
pivot_data.plot(kind='bar', stacked=True, figsize=(10, 5))
plt.xlabel('Segment - Ship Mode')
plt.ylabel('Value')
plt.legend(title='Region')
plt.show()


# OUPUT

![ex8 1](https://github.com/Bala1511/Ex-08-Data-Visualization-/assets/118680410/e9cdbdfe-bbbc-40af-903d-cf0e37e54234)

![ex8 2](https://github.com/Bala1511/Ex-08-Data-Visualization-/assets/118680410/8a79c0a5-41ed-4bf7-bf6c-4ff53ad46a33)

![ex8 3](https://github.com/Bala1511/Ex-08-Data-Visualization-/assets/118680410/0235ae31-4e67-4f8b-a42e-4cf40201baba)

![ex8 4](https://github.com/Bala1511/Ex-08-Data-Visualization-/assets/118680410/d52ac472-9abe-48f0-b07e-b1c227c5a52c)

![ex8 5](https://github.com/Bala1511/Ex-08-Data-Visualization-/assets/118680410/6f1ca42c-e640-44e3-bd38-a10ab1f7daa6)

![ex8 6](https://github.com/Bala1511/Ex-08-Data-Visualization-/assets/118680410/a9918cfa-2519-43d2-9855-caf6b55cd4a6)

![ex8 7](https://github.com/Bala1511/Ex-08-Data-Visualization-/assets/118680410/b9013e03-2bab-4ec3-8ea7-0433ca957315)

![ex8 9](https://github.com/Bala1511/Ex-08-Data-Visualization-/assets/118680410/f4bc39bb-7d25-4a50-996c-de977de7cf33)

![ex8 10](https://github.com/Bala1511/Ex-08-Data-Visualization-/assets/118680410/a341abb9-f9e8-4418-8e42-a16e83709a00)

![ex8 11](https://github.com/Bala1511/Ex-08-Data-Visualization-/assets/118680410/d3f0cd13-9a5d-4e19-a319-8a067affb296)

![ex8 12](https://github.com/Bala1511/Ex-08-Data-Visualization-/assets/118680410/5890478b-fe32-44a9-bb85-a1e0fea11e72)

![ex8 13](https://github.com/Bala1511/Ex-08-Data-Visualization-/assets/118680410/a8c1be60-9819-4ed8-9950-7bd4741c7735)

![ex8 14](https://github.com/Bala1511/Ex-08-Data-Visualization-/assets/118680410/f14df965-aa86-478a-ad8b-bedb38b4d0c4)

![ex8 15](https://github.com/Bala1511/Ex-08-Data-Visualization-/assets/118680410/b588000c-9005-46a3-b856-c45938bb87f7)

![ex8 16](https://github.com/Bala1511/Ex-08-Data-Visualization-/assets/118680410/1f0f023d-7d19-449e-aeb6-1f6a6a402146)

![ex8 17](https://github.com/Bala1511/Ex-08-Data-Visualization-/assets/118680410/ccf782b2-7fd4-4efb-b8f1-caac692d6fce)
```
Result:
Thus, Data Visualization is performed on the given dataset and save the data to a file.
```
