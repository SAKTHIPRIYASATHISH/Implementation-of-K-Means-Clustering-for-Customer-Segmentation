# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Import the required libraries .
2. Read the data frame using pandas.
3. Get the information regarding the null values present in the dataframe.
4. Apply label encoder to the non-numerical column inoreder to convert into numerical values.
5. Determine training and test data set.
6. Apply k means clustering for customer segmentation.

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by:S.Sakthi Priya 
RegisterNumber: 212222040140 
*/
import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv("Mall_Customers.csv")
data.head()
data.info()
data.isnull().sum()
from sklearn.cluster import KMeans
wcss=[]   #Within-Cluster Sum of Squares.

for i in range(1,11):
    kmeans=KMeans(n_clusters=i, init="k-means++")
    kmeans.fit(data.iloc[:,3:])
    wcss.append(kmeans.inertia_)
    
plt.plot(range(1,11),wcss)
plt.xlabel("No.of Clusters")
plt.ylabel("wcss")
plt.title("ELBOW METHOD GRAPH")
plt.show()
km = KMeans(n_clusters=5)
km.fit(data.iloc[:,3:])
y_pred=km.predict(data.iloc[:,3:])
y_pred
data["cluster"]=y_pred
df0 = data[data["cluster"]==0]
df1 = data[data["cluster"]==1]
df2 = data[data["cluster"]==2]
df3 = data[data["cluster"]==3]
df4 = data[data["cluster"]==4]

plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="green",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="purple",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="blue",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="gold",label="cluster4")
plt.legend()
plt.title("Customer Segments")
```

## Output:
data.head()
![s1](https://github.com/SAKTHIPRIYASATHISH/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/119104282/f05c156a-f246-4423-bb6b-b9d01a2e4cae)


data.info()
![s2](https://github.com/SAKTHIPRIYASATHISH/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/119104282/1d57f09e-83bf-4b3c-b8eb-5cfbce7eab28)

data.isnull().sum()
![s3](https://github.com/SAKTHIPRIYASATHISH/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/119104282/63993717-fb80-4adb-a5f3-291dae4c074e)

Elbow method graph
![s4](https://github.com/SAKTHIPRIYASATHISH/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/119104282/ade5c693-cf22-49d7-b1ba-27582e17049a)

KMeans clusters

![s5](https://github.com/SAKTHIPRIYASATHISH/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/119104282/4e06a748-2033-4b73-97e1-d2118ea1ed2e)

Y_Pred

![s6](https://github.com/SAKTHIPRIYASATHISH/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/119104282/20743007-df93-4a1f-bf20-b55368de014d)

Customers Segment Graph
![s7](https://github.com/SAKTHIPRIYASATHISH/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/119104282/ea595ecf-4564-4c4e-8b80-18fc7f431685)













## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
