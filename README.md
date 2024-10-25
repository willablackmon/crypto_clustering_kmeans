# Clustering Cryptocurrencies with K-Means

This project applies clustering techniques to a cryptocurrency dataset to identify patterns in market data and group cryptocurrencies by their performance. The focus is on using machine learning models to cluster cryptocurrencies by various market performance indicators.

**[Data](#data)** : [Sourcing](#sourcing) | [Pre-Processing
](#pre-processing)**[Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)** : [Optimize with Principal Component Analysis (PCA)](#optimize-clusters-with-principal-component-analysis-pca) | [Feature Weights for each Principal Component](#feature-weights-for-each-principal-component) | [Hyperparameter Tuning](#hyperparameter-tuning)
**[Modeling](#modeling)** : [K-Means Clustering](#k-means-clustering) | [Original Data vs PCA Data](#original-data-vs-pca-data)
**[Technologies and Tools](#technologies-and-tools)**

---

## Abstract

The project clusters cryptocurrency market data using the unsupervised Machine Learning algorithm  **k-means clustering** . The goal is to identify and group cryptocurrencies based on their price change percentages over different timeframes. The analysis involves cleaning and transforming the data, performing exploratory data analysis (EDA), and applying clustering to find patterns.

---

## Data

### Sourcing

Data is for cryptocurrency market performance metrics, including percentage changes in price over different time intervals (24 hours, 7 days, 14 days, etc.).

<figure>
    <figcaption><em></em></figcaption>
    <img src="images/1721440070906.png" style="width: 100%; max-width: 700px;" 
         alt="1721440070906.png">
</figure>

### Pre-Processing

* Missing data was handled by dropping rows with insufficient data.
* `StandardScaler()` module from `scikit-learn` used to to normalize the market performance indicators (price changes) to ensure uniformity before clustering.

---

## Exploratory Data Analysis (EDA),

#### Optimize with Principal Component Analysis (PCA)

* **PCA Model** was created with `n_components = 3` to reduce the dataset to three principal components, simplifying the dataset while retaining as much of the original information as possible.
* **Explained Variance** was calculated to determine how much information is captured by each principal component, identifying how much of the total variance in the data can be attributed to each component.  For PCA1, PCA2, PCA3, variance was 37.2%, 34.7% and 17.6%, respectively.
* The **total explained variance** of the three principal components is  **89.5%**, indicating that the majority of the information present in the original dataset is retained in these three components.  This makes PCA an effective technique for dimensionality reduction in this case.

```
pca.explained_variance_ratio_ =  [0.3719856 , 0.34700813, 0.17603793]
sum(pca.explained_variance_ratio_) = 0.895031657030984

```

#### Feature Weights for each Principal Component

Features with the strongest positive or negative weights (influence) on each PCA component.

* **PCA1:**   Features with the largest impact on **PCA1** are features with the **longest** time periods:

  * price_change_percentage: 200d (~59%), _1y (~57%), _60d (~32%), _30d (~19%).
  * The features with the two longest periods  **(200 day, 1 year) ** have the most significant impacts.
* **PCA2:**   Features that have the largest impact on **PCA2** are features with **shorter** time periods.

  * price_change_percentage: 30 day (~56%), 14 day (~54%), 60 day (~43%), 24 hour (~35%), 7 day (~22%).
  * The longest two periods (1 year, 200 days) have very little impact on **PCA2**.
* **PCA3:** Features that have the largest impact on **PCA3** are skew towards 1-2 week periods  **(7d, 14d)**, but also include the 1 year.

  * price_change_percentage: 7 day (~78%),  14 day (~35%),  1 year (~21%).
  * **7 day** is the feature with the largest positive influence on the PCA values at **78%**.

Tables for each principal component (sorted by PCA1, PCA2, PCA3):

<figure>
    <figcaption><em>Top Feature Weights for PCA 1 (sorted by PCA 1 column):</em></figcaption>
    <img src="images/1721439129611.png" style="width: 100%; max-width: 350px;" 
         alt="Feature Weights on PCA">
</figure>

<figure>
    <figcaption><em>Top Feature Weights for PCA 2 (sorted by PCA 2 column):</em></figcaption>
    <img src="images/1721439129611.png" style="width: 100%; max-width: 350px;" 
         alt="Feature Weights on PCA">
</figure>

<figure>
    <figcaption><em>Top Feature Weights for PCA 3 (sorted by PCA 3 column):</em></figcaption>
    <img src="images/1721439129611.png" style="width: 100%; max-width: 350px;" 
         alt="Feature Weights on PCA">
</figure>

#### Hyperparameter Tuning

* **Elbow method** used to determine optimal number of clusters by analyzing the inertia values across different k values.  k=4 shows the largest change in slop
* The best value for k was the same with the PCA data as determined using the original data.

<figure>
    <img src="images/1721440125862.png" style="width: 100%; max-width: 400px;"
    <figcaption><em></em></figcaption>
</figure>

## Modeling

Modeling was performed with the **k-Means clustering** algorithm to group cryptocurrencies based on their price performance over various time intervals.

Optimal n_clusters = 4 was determined in a previous step and applied it to the **original data** and the reduced **PCA data** (to see if any significant differences existed).

**Fig 1:** Scatter plot for the Original Data, **price_change_percentage_24h vs. price_change_percentage_7d**, displaying predicted clusters in different colors:

<figure>
    <img src="images/1721439634067.png" style="width: 100%; max-width: 400px;" 
         alt=""K-Means clustering for on the original data">
    <figcaption><em>Fig 1: K-Means on the original data:</em></figcaption>
</figure>

**Fig 2**: Scatter plot for **PCA1 vs. PCA2**, displaying predicted clusters, color-coded:

<figure>
    <img src="images/1721439564256.png" style="width: 100%; max-width: 400px;" alt="K-Means on PCA data">
<figcaption><em>`Fig 2: K-Means on PCA data:</em></figcaption>
</figure>

---

## Technologies and Tools

* **Data Scaling** : Utilized **StandardScaler** from **scikit-learn** to normalize features before clustering.
* **Dimensionality Reduction** : **Principal Component Analysis (PCA)** for feature decomposition, reducing the dataset to key principal components while preserving ~89% of the variance.
* **Clustering Algorithm** : Applied **k-means** from **scikit-learn** to perform clustering analysis.
* **Visualizations** : Generated histograms, scatter plots, and correlation heatmaps using **matplotlib** and **seaborn** to explore data distribution and relationships.
* **Elbow Plot** : Used the **Elbow method** to determine the optimal number of clusters for k-means by plotting inertia values.
* **Tools and Libraries** : Python, Pandas, and Jupyter Notebook for data analysis for data cleaning and preparation to handle missing data and ensure consistent formatting across the dataset.
