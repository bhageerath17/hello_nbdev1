# Item clustering
> Cluster the product items and find out the KVI's


## Pages

Description of each page

- _Data_: This page takes through the steps of the queries used, data collected and saved. The data saved in these steps is used for the analysis and modeling. The data is saved in the `nbs/data` folder

    The data generated from this page is saved in the following format:
    - `nbs/data/raw` - The original, immutable data dump.
    - `nbs/data/interim` folder - Intermediate data that has been transformed.
    - `raw/data/processed` folder - The final, canonical data sets for modeling.
    - `raw/data/external` folder - Data from external sources (outside snowflake or in excel sheets or csv files)

- _Analysis_: The data collected in the `data` module is used to understand the features and generate profile reports. The reports are saved in the `nbs/reports` folder of the repo
    
    The reports generated from this page is saved in the following format:
    - `nbs/reports/figures` - Any matplotlib or bokeh plots here that are generated from the notebooks. Any images or plots included in the notebooks/documentation will be saved here.

- _Models_: Clustering algorithms are used to understand the item segments. The steps outlined in this page takes you through the several algorithms used, best parameters dervied using hyper parameter optmization etc.

    The models developed from this page is saved in the following format:
    - `nbs/models/dbscan-*` - This folder contains the results of the dbscan clustering algorithm. Each subfolder that starts with `dbscan-*` hosts several iterations of the model based on any changes to the data. The iterations are named after the date that used to train the model (ex: `20210128`).

- _Feature importance_: Feature importance for clusters is computed using quantile distance. This page takes you through the method used and any example that may be helpful to understand the concept

- _Validation_: Validating the clusters produced is critical to understand which parameters are best for the model

## Installation

`pip install item_clustering`
