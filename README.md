











# Module 11 Challenge

https://bootcampspot.instructure.com/courses/6442/assignments/80394?module_item_id=1260807


In this Challenge, you’ll apply your understanding of the K-means algorithm and principal component analysis (PCA) to classify cryptocurrencies according to their price fluctuations across various timeframes. Specifically, you will examine price changes over intervals spanning 24 hours, 7 days, 30 days, 60 days, 200 days, and 1 year.

### Before You Begin

1. Create a new repository for this project called `CryptoClustering`.  **Do not add this homework to an existing repository** .
2. Clone the new repository to your computer.
3. Push your changes to GitHub.

### Files

Download the following files to help you get started:

[Module 11 Challenge files**Links to an external site.**](https://static.bc-edx.com/ai/ail-v-1-0/m11/lms/starter/M11_Starter_Code.zip)

### Instructions

1. Rename the `Crypto_Clustering_starter_code.ipynb` file as `Crypto_Clustering.ipynb`.
2. Load the `crypto_market_data.csv` into a DataFrame and set the index to the “coin_id” column.
3. Get the summary statistics to see what the data looks like before proceeding.

#### Prepare the Data

1. Use the `StandardScaler()` module from `scikit-learn` to normalize the data from the CSV file.
2. Create a DataFrame with the scaled data and set the "coin_id" index from the original DataFrame as the index for the new DataFrame.
   * The first five rows of the scaled DataFrame should appear as follows:
     ![The first five rows of the scaled DataFrame.](https://static.bc-edx.com/ai/ail-v-1-0/m11/lms/img/scaled_DataFrame.png)

#### Find the Best Value for k Using the Original Scaled DataFrame

Use the elbow method to find the best value for `k` by completing the following steps:

1. Create a list with the number of k values from 1 to 11.
2. Create an empty list to store the inertia values.
3. Create a `for` loop to compute the inertia with each possible value of `k`.
4. Create a dictionary with the data to plot the elbow curve.
5. Plot a line chart with all the inertia values computed with the different values of `k` to visually identify the optimal value for `k`.
6. Answer the following question in your notebook: What is the best value for `k`?

#### Cluster Cryptocurrencies with K-Means Using the Original Scaled Data

Use the following steps to cluster the cryptocurrencies for the best value for `k` on the original scaled data:

1. Initialize the K-means model with the best value for `k`.
2. Create an instance of K-means, define the number of clusters based on the best value of `k`, and then fit the model using the original scaled DataFrame.
3. Predict the clusters to group the cryptocurrencies using the original scaled DataFrame.
4. Create a copy of the original data and add a new column with the predicted clusters.
5. Create a scatterplot using pandas’ `plot` as follows:
   * Set the x-axis as "price_change_percentage_24h" and the y-axis as "price_change_percentage_7d".

#### Optimize Clusters with Principal Component Analysis

1. Using the original scaled DataFrame, perform a PCA and reduce the features to three principal components.
2. Retrieve the explained variance to determine how much information can be attributed to each principal component and then answer the following question in your notebook:
   * What is the total explained variance of the three principal components?
3. Create a new DataFrame with the PCA data and set the "coin_id" index from the original DataFrame as the index for the new DataFrame.
   * The first five rows of the PCA DataFrame should appear as follows:
     ![The first five rows of the PCA DataFrame.](https://static.bc-edx.com/ai/ail-v-1-0/m11/lms/img/PCA_DataFrame.png)

#### Find the Best Value for k Using the PCA Data

Use the elbow method on the PCA data to find the best value for `k` using the following steps:

1. Create a list with the number of k-values from 1 to 11.
2. Create an empty list to store the inertia values.
3. Create a `for` loop to compute the inertia with each possible value of `k`.
4. Create a dictionary with the data to plot the elbow curve.
5. Plot a line chart with all the inertia values computed with the different values of `k` to visually identify the optimal value for `k`.
6. Answer the following questions in your notebook:
   * What is the best value for `k` when using the PCA data?
   * Does it differ from the best k-value found using the original data?

#### Cluster Cryptocurrencies with K-Means Using the PCA Data

Use the following steps to cluster the cryptocurrencies for the best value for `k` on the PCA data:

1. Initialize the K-means model with the best value for `k`.
2. Create an instance of K-means, define the number of clusters based on the best value of `k`, and then fit the model using the PCA data.
3. Predict the clusters to group the cryptocurrencies using the PCA data.
4. Create a copy of the DataFrame with the PCA data and add a new column to store the predicted clusters.
5. Create a scatte rplot using pandas’ `plot` as follows:
   * Set the x-axis as "PC1" and the y-axis as "PC2".
6. Answer the following question:
   * What is the impact of using fewer features to cluster the data using K-Means?

#### Determine the Weights of Each Feature on Each Principal Component

1. Create a DataFrame that shows the weights of each feature (column) for each principal component by using the columns from the original scaled DataFrame as the index.
2. Which features have the strongest positive or negative influence on each component?

### Requirements

#### Find the Best Value for k Using the Original Scaled DataFrame (15 points)

To receive all points, you must:

* Code the elbow method algorithm to find the best value for k. Use a range from 1 to 11. (5 points)
* Visually identify the optimal value for k by plotting a line chart of all the inertia values computed with the different values of k. (5 points)
* Answer the following question: What’s the best value for k? (5 points)

#### Cluster Cryptocurrencies with K-Means Using the Original Scaled Data (10 points)

To receive all points, you must:

* Initialize the K-means model with four clusters by using the best value for k. (1 point)
* Fit the K-means model by using the original data. (1 point)
* Predict the clusters for grouping the cryptocurrencies by using the original data. Review the resulting array of cluster values. (3 points)
* Create a copy of the original data, and then add a new column of the predicted clusters. (1 point)
* Using pandas’ `plot`, create a scatter plot by setting `x="price_change_percentage_24h"` and `y="price_change_percentage_7d"`. (4 points)

#### Optimize the Clusters with Principal Component Analysis (10 points)

To receive all points, you must:

* Create a PCA model instance, and set `n_components=3`. (1 point)
* Use the PCA model to reduce the features to three principal components, then review the first five rows of the DataFrame. (2 points)
* Get the explained variance to determine how much information can be attributed to each principal component. (2 points)
* Answer the following question: What’s the total explained variance of the three principal components? (3 points)
* Create a new DataFrame with the PCA data. Be sure to set the `coin_id` index from the original DataFrame as the index for the new DataFrame. Review the resulting DataFrame. (2 points)

#### Find the Best Value for k by Using the PCA Data (10 points)

To receive all points, you must:

* Code the elbow method algorithm, and use the PCA data to find the best value for k. Use a range from 1 to 11. (2 points)
* Visually identify the optimal value for k by plotting a line chart of all the inertia values computed with the different values of k. (5 points)
* Answer the following questions: What’s the best value for k when using the PCA data? Does it differ from the best value for k that you found by using the original data? (3 points)

#### Cluster the Cryptocurrencies with K-Means by Using the PCA Data (10 points)

To receive all points, you must:

* Initialize the K-means model with four clusters by using the best value for k. (1 point)
* Fit the K-means model by using the PCA data. (1 point)
* Predict the clusters for grouping the cryptocurrencies by using the PCA data. Review the resulting array of cluster values. (3 points)
* Create a copy of the DataFrame with the PCA data, and then add a new column to store the predicted clusters. (1 point)
* Using pandas’ `plot`, create a scatter plot by setting `x="PC1"` and `y="PC2"`. (4 points)

#### Determine the Weights of Each Feature on Each Principal Component (15 points)

To receive all points, you must:

* Create a DataFrame that shows the weights of each feature (column) for each principal component by using the columns from the original scaled DataFrame as the index. (10 points)
* Answer the following question: Which features have the strongest positive or negative influence on each component? (5 points)

#### Coding Conventions and Formatting (10 points)

To receive all points, you must:

* Place imports at the top of the file, just after any module comments and docstrings, and before module globals and constants. (3 points)
* Name functions and variables with lowercase characters, with words separated by underscores. (2 points)
* Follow DRY (Don't Repeat Yourself) principles, creating maintainable and reusable code. (3 points)
* Use concise logic and creative engineering where possible. (2 points)

#### Deployment and Submission (10 points)

To receive all points, you must:

* Submit a link to a GitHub repository that’s cloned to your local machine and that contains your files. (4 points)
* Use the command line to add your files to the repository. (3 points)
* Include appropriate commit messages in your files. (3 points)

#### Code Comments (10 points)

To receive all points, your code must:

* Be well commented with concise, relevant notes that other developers can understand. (10 points)
