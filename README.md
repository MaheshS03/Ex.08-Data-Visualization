# Ex.08-Data-Visualization
# AIM:
  To Perform Data Visualization on a complex dataset and save the data to a file.

# EXPLANATION:
  Data visualization is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns in data.

# ALGORITHM:
## STEP-1:
Read the given Data.
## STEP-2:
Clean the Data Set using Data Cleaning Process.
## STEP-3:
Apply Feature generation and selection techniques to all the features of the data set.
## STEP-4:
Apply Data Visualization techniques to identify the patterns of the data.

# CODE:
import pandas as pd

import numpy as np

import seaborn as sns

import matplotlib.pyplot as plt

from google.colab import files

uploaded = files.upload()

df=pd.read_csv("SuperStore.csv",encoding='unicode_escape')

df

# Data Cleaning Process:
df.describe()

df.info()

df.drop('Row ID',axis=1,inplace=True)

df.drop('Order ID',axis=1,inplace=True)

df.drop('Customer ID',axis=1,inplace=True)

df.drop('Customer Name',axis=1,inplace=True)

df.drop('Country',axis=1,inplace=True)

df.drop('Postal Code',axis=1,inplace=True)

df.drop('Product ID',axis=1,inplace=True)

df.drop('Product Name',axis=1,inplace=True)

df.drop('Order Date',axis=1,inplace=True)

df.drop('Ship Date',axis=1,inplace=True)

df

df.isnull().sum()

# Segment has Highest sales:
sns.barplot(x="Segment",y="Sales",data=df)

plt.xticks(rotation = 90)

plt.show()

# City has Highest profit:
plt.figure(figsize=(30,8))

states=df1.loc[:,["City","Profit"]]

states=states.groupby(by=["City"]).sum().sort_values(by="Profit")

sns.barplot(x=states.index,y="Profit",data=states)

plt.xticks(rotation = 90)

plt.xlabel=("City")

plt.ylabel=("Profit")

plt.show()

# Ship mode is profitable:
sns.barplot(x="Ship Mode",y="Profit",data=df)

plt.show()

# Sales of the product based on Region:
states=df.loc[:,["Region","Sales"]]

states=states.groupby(by=["Region"]).sum().sort_values(by="Sales")

sns.barplot(x=states.index,y="Sales",data=states)

plt.xticks(rotation = 90)

plt.xlabel=("Region")

plt.ylabel=("Sales")

plt.show()

# Relation between sales and profit:
sns.lineplot(x="Sales",y="Profit",data=df,hue="Region",style="Region",markers=["o","<"])
# Relation between sales and profit based on Segment:
grouped_data = df.groupby('Segment')[['Sales', 'Profit']].mean()

fig, ax = plt.subplots()

ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')

ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')

ax.set_xlabel('Segment')

ax.set_ylabel('Value')

ax.legend()

plt.show()

# Relation between sales and profit based on City:
grouped_data = df.groupby('City')[['Sales', 'Profit']].mean()

fig, ax = plt.subplots()

ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')

ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')

ax.set_xlabel('City')

ax.set_ylabel('Value')

ax.legend()

plt.xticks(rotation = 90)

plt.show()

# Relation between sales and profit based on States:
grouped_data = df.groupby('State')[['Sales', 'Profit']].mean()

fig, ax = plt.subplots()

ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')

ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')

ax.set_xlabel('State')

ax.set_ylabel('Value')

ax.legend()

plt.xticks(rotation = 90)

plt.show()

# Relation between sales and profit based on Segment and Ship Mode:
grouped_data = df.groupby(['Segment', 'Ship Mode'])[['Sales', 'Profit']].mean()

pivot_data = grouped_data.reset_index().pivot(index='Segment', columns='Ship Mode', values=['Sales', 'Profit'])

fig, ax = plt.subplots()

pivot_data.plot(kind='bar', ax=ax)

ax.set_xlabel('Segment')

ax.set_ylabel('Value')

plt.legend(title='Ship Mode')

plt.show()

# Relation between sales and profit based on Segment , Ship Mode and Region:
grouped_data = df.groupby(['Segment', 'Ship Mode','Region'])[['Sales', 'Profit']].mean()

pivot_data = grouped_data.reset_index().pivot(index=['Segment', 'Ship Mode'], columns='Region', values=['Sales', 'Profit'])

sns.set_style("whitegrid")

sns.set_palette("Set1")

pivot_data.plot(kind='bar', stacked=True, figsize=(10, 5))

plt.legend(title='Region')

plt.show()


# OUTPUT:
# Data Cleaning Process:
![Screenshot (56)](https://github.com/MaheshS03/Ex.08-Data-Visualization/assets/128498431/764e73bb-2ec4-4110-baf4-42a7d304ad9c)

![Screenshot (58)](https://github.com/MaheshS03/Ex.08-Data-Visualization/assets/128498431/a46c543f-0ea4-4027-a5ce-37b83f21e9a0)

![Screenshot (59)](https://github.com/MaheshS03/Ex.08-Data-Visualization/assets/128498431/e7362347-d25d-4f8b-8322-99be0854d692)

![Screenshot (60)](https://github.com/MaheshS03/Ex.08-Data-Visualization/assets/128498431/35e55608-3c4a-4090-824c-72e8e75ba676)

![Screenshot (61)](https://github.com/MaheshS03/Ex.08-Data-Visualization/assets/128498431/fd42caf2-cddd-4979-bb44-4ea470def381)
# Segment has Highest sales: 
![Screenshot (63)](https://github.com/MaheshS03/Ex.08-Data-Visualization/assets/128498431/5f8a77ac-ad91-422d-8700-2cf0259a8b14)
# City has Highest profit:
![Screenshot (64)](https://github.com/MaheshS03/Ex.08-Data-Visualization/assets/128498431/ca443e66-55cd-4bf4-8a93-86faff566e30)
# Ship mode is profitable:
![Screenshot (65)](https://github.com/MaheshS03/Ex.08-Data-Visualization/assets/128498431/5035128e-8384-4615-81e9-13d3be037802)
# Sales of the product based on Region:
![Screenshot (66)](https://github.com/MaheshS03/Ex.08-Data-Visualization/assets/128498431/ec41368b-0f37-4d80-a5c3-0d922f13773a)
# Relation between sales and profit:
![Screenshot (67)](https://github.com/MaheshS03/Ex.08-Data-Visualization/assets/128498431/68f32b3a-bf9b-410a-934c-6099776b776c)
# Relation between sales and profit based on Segment:
![Screenshot (68)](https://github.com/MaheshS03/Ex.08-Data-Visualization/assets/128498431/28849514-7c12-4ac1-8b48-efdcc3dc8282)
# Relation between sales and profit based on City:
![Screenshot (69)](https://github.com/MaheshS03/Ex.08-Data-Visualization/assets/128498431/a4842eb1-979e-4b53-882a-16d590ba8cf0)
# Relation between sales and profit based on States:
![Screenshot (72)](https://github.com/MaheshS03/Ex.08-Data-Visualization/assets/128498431/ae821d2d-a61f-4cc3-b567-af8cd9d59ef0)
# Relation between sales and profit based on Segment and Ship Mode:
![Screenshot (70)](https://github.com/MaheshS03/Ex.08-Data-Visualization/assets/128498431/aa0321f1-6afb-486b-99aa-d36ec7058e60)
# Relation between sales and profit based on Segment , Ship Mode and Region:
![Screenshot (71)](https://github.com/MaheshS03/Ex.08-Data-Visualization/assets/128498431/fc787479-f340-4510-a4ad-e0be79eadff6)

# RESULT:
  Thus the Data Visualization techniques was performed for the given dataset and output was verified successfully.
