# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1.Load and preprocess data: Import data, inspect it, and handle missing values if any.

2.Determine optimal clusters: Use the Elbow Method to identify the number of clusters by plotting WCSS against cluster numbers.

3.Fit the K-Means model: Apply K-Means with the chosen number of clusters to the selected features.

4.Assign cluster labels to each data point.

5.Plot data points in a scatter plot, color-coded by cluster assignments for interpretation.
## Program:
```python
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Janagiraman.M
RegisterNumber:  212224230101
*/
```
```python
import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv("/content/Mall_Customers.csv")
```
```python
data.info()
```
```python
data.isnull().sum()
```
```python
from sklearn.cluster import KMeans
wcss = []
for i in range(1,11):
    kmeans = KMeans(n_clusters = i,init = "k-means++",n_init=10)
    kmeans.fit(data.iloc[:,3:])
    wcss.append(kmeans.inertia_)plt.plot(range(1,11),wcss)
plt.xlabel("No. of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")
```
```pyhton
km = KMeans(n_clusters=5, n_init=10)
km.fit(data.iloc[:, 3:])
y_pred = km.predict(data.iloc[:,3:])
y_pred
```
```python
data["cluster"] = y_pred
df0 = data[data["cluster"]==0]
df1 = data[data["cluster"]==1]
df2 = data[data["cluster"]==2]
df3 = data[data["cluster"]==3]
df4 = data[data["cluster"]==4]
```
```python
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster1")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster2")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster3")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster4")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="magenta",label="cluster5")
plt.legend()
plt.title("Customer Segments")
```


## Output:
<img width="883" height="317" alt="Screenshot 2025-10-23 133304" src="https://github.com/user-attachments/assets/682871d3-7deb-4bc0-833d-47ecf206780e" />
<img width="862" height="278" alt="Screenshot 2025-10-23 133317" src="https://github.com/user-attachments/assets/9f23e9f4-5a50-49be-ba5d-95a82b31c192" />
<img width="866" height="345" alt="Screenshot 2025-10-23 133342" src="https://github.com/user-attachments/assets/76e91387-0ecd-4448-9341-3af32cfcceea" />
<img width="853" height="617" alt="Screenshot 2025-10-23 133351" src="https://github.com/user-attachments/assets/ed0f5b56-dc68-4c84-85ea-04ac98372aed" />
<img width="855" height="234" alt="Screenshot 2025-10-23 133359" src="https://github.com/user-attachments/assets/fd11b963-802e-4e58-a8aa-de356d9ea3de" />
<img width="889" height="581" alt="Screenshot 2025-10-23 133407" src="https://github.com/user-attachments/assets/95521851-c013-408b-8d1c-c09cbe337d3a" />


## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
