# Model cards

Model cards are used to display the model summary and the model parameters when needed. The subfolders (to this files) hosts all the models that are available in the library.

## DBSCAN

DBSCAN is a clustering algorithm that groups the data points into clusters. It is a density-based clustering algorithm. The algorithm is based on the idea that the density of a point is a function of its connectivity with other points.

Each subfolder that starts with `dbscan-*` hosts several iterations of the model based on any changes to the data. The iterations are named after the date that used to train the model (ex: `20210128`).

The changes made to the data will be mentioned in this document 


### dbscan-2021-01-28

A product can be added to the cart in any sequence. However, if the product is added as the first item in the cart, the choice of selection of the item _may_ provided insights into the customer's behavior.

Hence, in this iteration, `dbscan-2021-01-28`, the algorithm was trained on the data where the first item in the cart is used as a feature in the model

#### Results

**Based on the model metrics, we can select  `min_samples` is at `3` and the `eps` is at `2` for DBSCAN.**

**eps 2 and min_samples 3**

|   label |   product count |   kvi_mean |   kvis_in_label |   kvi_percentage |
|--------:|----------------:|-----------:|----------------:|-----------------:|
|      -1 |             410 |       0.48 |             196 |            12.22 |
|       0 |           44680 |       0.03 |            1390 |            86.66 |
|       1 |               3 |       0    |               0 |             0    |
|       2 |              35 |       0    |               0 |             0    |
|       3 |               4 |       1    |               4 |             0.25 |
|       4 |              36 |       0.06 |               2 |             0.12 |
|       5 |               5 |       0.67 |               3 |             0.19 |
|       6 |               3 |       1    |               3 |             0.19 |
|       7 |               3 |       1    |               3 |             0.19 |
|       8 |               3 |       0    |               0 |             0    |
|       9 |              11 |       0    |               0 |             0    |
|      10 |               4 |       0    |               0 |             0    |
|      11 |               3 |       1    |               3 |             0.19 |
|      12 |               3 |       0    |               0 |             0    |
|      13 |               3 |       0.67 |               2 |             0.12 |


> Note: Even though the silhouette coefficient is higher for the `eps` at 2 and `min_samples` at [15, 30], the number of clusters is only `1`, which doesnt provide information into the KVI's that are present in the data.

> Note: Half of the outliers (`label -1`) when epsilon is at `2` and min_samples is  `3` are KVI's. And the outlier KVI's correspond to `~12%` of the total number of KVI's.

The biggest cluster (`label 0`) has around `1390` KVI's which is ~`86%` of the total KVI's. However, the `KVI's` occupy only small portion of total products in that cluster. So, `cluster 0` is not as interesting as the anomalies and other clusters that have higher coverage and lower product count in the cluster

There are few cluster with `kvi_mean` at `1`. These small clusters, even though has limited products, can be used to identify the KVI's in the data. Some of the interesting small clusters are `label 3`, `label 6`, `label 7` and `label 11`


**eps 2 and min_samples 6**

> Note: Half of the outliers (`label -1`) when epsilon is at `2` and min_samples is `6` are KVI's. And the outlier KVI's correspond to `~15%` of the total number of KVI's.

The biggest cluster (`label 0`) has around `1367` KVI's which is ~`85%` of the total KVI's. However, the `KVI's` occupy only small portion of total products in that cluster

|   label |   product count |   kvi_mean |   kvis_in_label |   kvi_percentage |
|--------:|----------------:|-----------:|----------------:|-----------------:|
|      -1 |             485 |       0.49 |             237 |            14.78 |
|       0 |           44636 |       0.03 |            1367 |            85.22 |
|       1 |              35 |       0    |               0 |             0    |
|       2 |              36 |       0.06 |               2 |             0.12 |
|       3 |               9 |       0    |               0 |             0    |
|       4 |               5 |       0    |               0 |             0    |