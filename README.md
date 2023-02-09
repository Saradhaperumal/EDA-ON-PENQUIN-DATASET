# EDA-ON-PENQUIN-DATASET
EXPLORATORY DATA ANALYSIS ON PENQUIN DATASET
# EXPLORATORY DATA ANALYSIS ON PENQUIN DATASET

It is a dataset comprising various measurements of three different penguin species, namely Adelie, Gentoo, and Chinstrap. Same as Iris data which had measurements of three different species of the Iris flower. Anyway, both are great for what they are made of.

![image.png](attachment:8ff26671-cec1-4dc4-b420-af41a70ed2df.png)

The rigorous study was conducted in the islands of the Palmer Archipelago, Antarctica. These data were collected from 2007 to 2009 by Dr. Kristen Gorman with the Palmer Station Long Term Ecological Research Program, part of the US Long Term Ecological Research Network.

The original GitHub repo contains the source code. You may download the dataset from Kaggle. It has two datasets, each with 344 observations. The dataset we will be using is a curated subset of the raw dataset.

# UNDERSTANDING DATASET:

**Of the 7 columns, 3 are categorical ( species , island , sex ) and the rest are numeric**

**island :** a factor denoting island in Palmer Archipelago, Antarctica (Biscoe,
         Dream or Torgersen)

**culmen_length_mm :** a number denoting bill length (millimeters)

**culmen_depth_mm :** a number denoting bill depth (millimeters)

**flipper_length_mm :** an integer denoting flipper length (millimeters)

**body_mass_g :** an integer denoting body mass (grams)

**sex :** a factor denoting penguin sex (female, male)

**Let's understand culmen width and culmen depth of penquin
**
![image.png](attachment:2348296f-6c32-4783-ba53-620147cfadc7.png)

**Let's understand flipper length**

![image.png](attachment:75799624-84a6-49f3-836b-c314e8bcc030.png)
![image.png](attachment:41a970cb-bd78-46fd-99b8-685bc12f66da.png)



# EXPLORING DATA:

The first step is to import packages that are needed to explore the data from penquin dataset.

import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Next step is reading our dataset

pdata=pd.read_csv('/kaggle/input/penquin-dataset/penguins_size.csv')
pdata

pdata.info()

# REMOVING NULL VALUES FROM DATASET

df=pdata
df.dropna()

df=df.dropna()
df.shape

#  HOW MANY SPECIES ARE THERE?

pdata.species.value_counts() #### NUMBER OF SPECIES

df.species.value_counts() ##### AFTER REMOVING NAN VALUES

pdata.species.value_counts().plot(kind='bar',color=['r','g','b'],title="How many species?",xlabel='Type of Species',ylabel='count')

# HOW MANY ISLANDS ARE THERE?

pdata.island.value_counts()

pdata.island.value_counts().plot(kind='bar',color=['blue','green','black'],figsize=[10,6],xlabel='Type of Species',ylabel='count')

# HOW MANY PENQUINS ARE THERE IN EACH GENDER?

pdata.sex.value_counts()

pdata.sex.value_counts().plot(kind='pie',autopct='%.2f',figsize=[8,8],title='Male/Female')

# RELATION (CULMEN LENGTH / BODY MASS)

sns.relplot(data=pdata,x='culmen_length_mm',y='body_mass_g',hue='sex')#### BASED ON GENDER

sns.relplot(data=pdata,x='culmen_length_mm',y='body_mass_g',hue='species')#### BASED ON SPECIES

sns.regplot(data=pdata,x='culmen_length_mm',y='body_mass_g')

#  RELATION (FLIPPER LENGTH / BODY MASS)

sns.scatterplot(data=pdata,x='flipper_length_mm',y='body_mass_g',hue='sex') #### BASED ON GENDER

sns.scatterplot(data=pdata,x='flipper_length_mm',y='body_mass_g',hue='species')#### BASED ON SPECIES

# RELATION (CULMEN DEPTH / BODY MASS)

sns.scatterplot(data=pdata,x='culmen_depth_mm',y='body_mass_g',hue='sex') #### BASED ON GENDER

sns.scatterplot(data=pdata,x='culmen_depth_mm',y='body_mass_g',hue='species') #### BASED ON SPECIES

sns.pairplot(data=df,hue='species')

# AVERAGE CULMEN LENGTH,DEPTH OF EACH SPECIES

grps=df.groupby('species')

grps.mean()

df.describe()

grps.std()

grps.cov()

grps.corr()

# CONCLUSION

 So ,this is all about exploratory data analysis done on penquin dataset.Here are some takeaways from this.
 
* Understanding the dataset and figuring out categorical and numerical values 
* How the barchart,piechart,scatterplot,regression plot,pair plot,relation plot is applied on numerical values to get realtively good insights about the data
* Finally finding out the mean,standard deviation,covariance and correlation on numerical values in dataset

