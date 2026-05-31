# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Import the necessary packages using import statement.
2. Read the given csv file using read_csv() method and print the number of contents to be displayed using df.head().
3. Import KMeans and use for loop to cluster the data.
4. Predict the cluster and plot data graphs.
5. Print the outputs and end the program


## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: MOHAMMED JASITH J
RegisterNumber:  212225230180
*/
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans

data=pd.read_csv("Mall_Customers (1).csv")
data.head()
data.info()
data.isnull()
data.isnull().sum()

wcss= []

for i in range(1,11):
    kmeans=KMeans(n_clusters = i,init = "k-means++")
    kmeans.fit(data.iloc[:,3:])
    wcss.append(kmeans.inertia_)
plt.plot(range(1,11),wcss)
plt.xlabel("No. of clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")

km=KMeans(n_clusters = 5)
km.fit(data.iloc[:,3:])

y_pred=km.predict(data.iloc[:,3:])
y_pred

data["cluster"]=y_pred
df0=data[data["cluster"]==0]
df1=data[data["cluster"]==1]
df2=data[data["cluster"]==2]
df3=data[data["cluster"]==3]
df4=data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="black",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="cyan",label="clustter1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="yellow",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="blue",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="green",label="cluster4")
plt.legend()
plt.title("Customer Segments")
```

## Output:
<img width="872" height="292" alt="image" src="https://github.com/user-attachments/assets/bd0866a1-6c9d-4a39-b8b9-29f36185737e" />
<img width="405" height="175" alt="image" src="https://github.com/user-attachments/assets/5f398935-d187-43f9-8300-51c312c9f2b9" />
<img width="635" height="330" alt="image" src="https://github.com/user-attachments/assets/a1721b4a-f56e-4c2e-8181-a22fd5e10840" />
<img width="868" height="283" alt="image" src="https://github.com/user-attachments/assets/61712256-ce48-44e0-a36a-3eab2bf9f9b4" />
<img width="665" height="482" alt="image" src="https://github.com/user-attachments/assets/25d19731-c661-4196-ae8b-5a1119f78098" />
<img width="612" height="461" alt="image" src="https://github.com/user-attachments/assets/e91893b7-e4a6-4f6e-a47f-101f762fea64" />



## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
