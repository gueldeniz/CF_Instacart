# Instacart Grocery Basket Analysis (by Career Foundry)

In this mock project, I worked as a junior data analyst for the online grocery store Instacart. Instacart is a real company with open online data.

## Objective
Instacart is an online store that operates through an app and has already very good sales. However, they want to uncover more information about their sales patterns to achieve more growth. My tasks consists of performing initial data and exploratory analysis according to the relevant business questions, deriving insights, and suggesting strategies for better segmentation using Python.

## Key Questions
- The sales team needs to know what the busiest days of the week and hours of the day
are (i.e., the days and times with the most orders) in order to schedule ads at times
when there are fewer orders.
- They also want to know whether there are particular times of the day when people spend
the most money, as this might inform the type of products they advertise at these times.
- Instacart has a lot of products with different price tags. Marketing and sales want to use
simpler price range groupings to help direct their efforts.
- Are there certain types of products that are more popular than others? The marketing
and sales teams want to know which departments have the highest frequency of product
orders.
- The marketing and sales teams are particularly interested in the different types of
customers in their system and how their ordering behaviors differ. For example:
  - What’s the distribution among users in regards to their brand loyalty?
  - Are there differences in ordering habits based on a customer’s loyalty status?
  - Are there differences in ordering habits based on a customer’s region?
  - Is there a connection between age and family status in terms of ordering habits?
  - What different classifications does the demographic information suggest?
  - What differences can you find in ordering habits of different customer profiles?

## Achievements
- First experience in the world of coding with Python
- Installing the suitable programming environment for conducting an analysis
- Wrangling data to align with the goals of an analysis, creating subsets, consistency check
- Combining and exporting data
- Deriving new variables
- Grouping data & aggregating new variables
- Visualizations with seaborn and matplotlib
- Answering business questions with a detailed reporting with Excel

## Data
The dataset comprises of Information following parameters:
- orders
- products
- customers

## Tools
- pandas -> for data analysis
- seaborn -> for visualization

## Executing the Code
The codes are available as jupyter notebooks, under /Scripts/

- Importing libraries for analysis and visualization:
````
#Importing libraries

import pandas as pd
import numpy as np
import os
import matplotlib.pyplot as plt
import seaborn as sns
import scipy
````
- I derived a new column called 'region' using information at Wikipedia article from given states for further analysis:
````
# Creating regional segmentation 

result = []

for value in df_all['state']:
    if (value == 'Maine') or (value == 'New Hampshire') or (value == 'Vermont') or (value == 'Massachusetts') or (value == 'Rhode Island') or (value == 'Connecticut') or (value == 'New York') or (value == 'Pennsylvania') or (value =='New Jersey'):
        result.append('Northeast')
    elif (value == 'Wisconsin') or (value == 'Michigan') or (value == 'Illinois') or (value == 'Indiana') or (value == 'Ohio') or (value == 'North Dakota') or (value == 'South Dakota') or (value == 'Nebraska') or (value == 'Kansas') or (value == 'Minnesota') or (value == 'Iowa') or (value == 'Missouri'):
        result.append('Midwest')
    elif (value == 'Deleware') or (value == 'Maryland') or (value == 'District of Columbia') or (value == 'Virginia') or (value == 'West Virginia') or (value == 'North Carolina') or (value == 'South Carolina') or (value == 'Georgia') or (value == 'Florida') or (value == 'Kentucky') or (value == 'Tennessee') or (value == 'Mississippi') or (value == 'Alabama') or (value == 'Oklahoma') or (value == 'Texas') or (value == 'Arkansas') or (value == 'Louisiana'):
        result.append('South')
    else:
        result.append('West')
df_all['region'] = result
````


- I created several crosstabs in order to compare and contrast various variables. Here I create crosstabs to compare ordering habits among regions and save it to the clipboard. Then, I create a bar chart to visualize the crosstab:

````
# Region crosstab by order frequency

regions_by_ordering = pd.crosstab(df_all['region'], df_all['frequency_flag'], dropna = False)
regions_by_ordering
regions_by_ordering.to_clipboard()

#Bar chart

region_ordering_bar = regions_by_ordering.plot(kind = 'bar', stacked = True, color = sns.color_palette('pastel', 3), title= 'Order habits by regions')
plt.xticks(rotation=0, horizontalalignment="center")
plt.tight_layout()
````
![Plot](https://github.com/gueldeniz/CF_Instacart/issues/1#issue-1161741016)

