# Unsupervised Machine Learning and Cryptocurrencies
<img src="images/cryptocurrencies-header.jpg" width="1000" height="400">

## Project Overview
A prominent investment bank is interested in offering a new cryptocurrency investment portfolio for its customers. The company, however, is lost in the vast universe of cryptocurrencies. So, they've asked me to create a report that includes what cryptocurrencies are on the trading market and how they could be grouped to create a classification system for this new investment. Since there is no known output for what I'm looking for, I used unsupervised learning. To group the cryptocurrencies, I decided on a clustering algorithm and I'll use the data visualizations to share the findings with the board.

## Resources
- **Data Source**: `crypto_data.csv`
- **Software and Tools**: Python, Pandas, Anaconda, Jupyter Notebook & Git Bash

## Challenge Deliverables and Results

### **Deliverable 1: Preprocessing the Data for PCA**
Using my knowledge of Pandas, I preprocessed the dataset in order to perform PCA. The following steps were performed:
- All cryptocurrencies that are not being traded were removed
- The IsTrading column was dropped
- All the rows that have at least one null value were removed 
- All the rows that do not have coins being mined were removed
- The CoinName column was dropped
- A new DataFrame was created that stores all cryptocurrency names from the CoinName column and retained the index from the crypto_df DataFrame
- The get_dummies() method was used to create variables for the text features, which were then stored in a new DataFrame
- The features from the new DataFrame were standardized using the StandardScaler fit_transform() function 

### **Deliverable 2: Reducing Data Dimensions Using PCA**
Using my knowledge of how to apply the Principal Component Analysis (PCA) algorithm, I reduced the dimensions of the scaled DataFrame to three principal components and placed these dimensions in a new DataFrame, `pcs_df`.

### **Deliverable 3: Clustering Cryptocurrencies Using K-means**
Using my knowledge of the K-means algorithm, I created an elbow curve using hvPlot to find the best value for K from the `pcs_df` DataFrame. Next, I ran the K-means algorithm to predict the K clusters for the cryptocurrencies’ data.

<img src="images/Delv 3_Elbow Curve.PNG">

Then, I created a new DataFrame `clustered_df` by joining two that were created in Deliverables 1 and 2 and added a column that holds the predictions.

<img src="images/Delv 3_clustered_df.PNG">

### **Deliverable 4: Visualizing Cryptocurrencies Results**
Using my knowledge of creating scatter plots with Plotly Express and hvplot, the following steps were performed to visualize the cryptocurrency results:
- I created a 3D visualization that shows the distinct groups that correspond to the three principal components from Deliverable 2.
<img src="images/Delv 4_3Dscatterplot.png">

- I created a table with all the currently tradable cryptocurrencies using the hvplot.table() function.
<img src="images/Delv 4_hvplot.table.PNG">

- I found there are a total of 532 tradable cryptocurrencies
- I created an hvplot scatter plot where the X-axis is "TotalCoinsMined", the Y-axis is "TotalCoinSupply", the data is ordered by "Class", and it shows the CoinName when you hover over the data point 
<img src="images/Delv 4_scatterplot.PNG">
