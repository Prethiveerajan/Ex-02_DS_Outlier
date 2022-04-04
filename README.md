## AIM:
To detect and remove outliers from the given data and save the final data.

EXPLANATION:
Outlier is a data object that deviates significantly from the rest of the data objects and behaves in a different manner. They can be caused by measurement or execution errors. The analysis of outlier data is referred to as outlier analysis or outlier mining. The box plot is a useful graphical display for describing the behavior of the data in the middle as well as at the ends of the distributions. The box plot uses the median and the lower and upper quartiles (defined as the 25th and 75th percentiles). If the lower quartile is Q1 and the upper quartile is Q3, then the difference (Q3 - Q1) is called the interquartile range or IQ.

## ALGORITHM:
## STEP 1
Import the packages(pandas,numpy)

## STEP 2
Read the csv file and convert them into Dataframe.

## STEP 3
Use drop function to remove a column "Gender" from the Dataframe.

## STEP 4
Apply Graphical Method "Box plot",which exhibits the Outliers.

## STEP 5
Apply Z-score function defined in scipy library to detect the outliers.

## STEP 6
Apply Statistical Method "Interquartile Range(IQR)" ,to remove the Outliers from the Dataset.

## CODE:
'''
Developed By: Prethiveerajan P
Register No: 212221230079
'''
```
import pandas as pd
df=pd.read_csv("weight.csv")
df
df.drop("Gender",axis=1,inplace=True)
df
df.boxplot()
from scipy import stats
import numpy as np
z=np.abs(stats.zscore(df))
z
df1=df.copy()
df1=df1[(z<3).all(axis=1)]
df1
df1.boxplot()
df2=df.copy()
q1=df2.quantile(0.25)
q3=df2.quantile(0.75)
IQR=q3-q1
df2_new=df2[((df2>=q1-1.5*IQR)&(df2<=q3+1.5*IQR)).all(axis=1)]
df2_new
```
## OUTPUT:
## Initial data set:
![output](ot2.png)
## Data set after removing non numerical sets:
![output](ot3.png)

## Graph displaying initial dataset with outliers:
![output](ot4.png)
## Z scores to detect outliers:
![output](ot5.png)
## Data set after removing outliers in weight using z scores and list manupilation:
![output](ot6.png)
## Graph after removing outliers in weight:
![output](ot7.png)
## Data set after removing outliers in height using Interquartile Range(IQR):
![output](ot9.png)
## Final graph after removing all outliers:
![output](ot10.png)
## Final data set:

![output](ot11.png)


## Result:
The Outliers are detected and removed from the Dataset.


