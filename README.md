# MLM-Project---1-Unsupervised-Learning
# Unsupervised Learning: International Trade Analysis

## Overview

This project uses unsupervised machine learning techniques to analyze a dataset of international trade transactions. The goal is to uncover hidden patterns, segment trade data, and provide actionable insights for improving logistics, marketing, and supply chain management.

## Dataset

### Source

-   **Link:** [Kaggle Dataset - Imports/Exports](https://www.kaggle.com/datasets/chakilamvishwas/imports-exports-15000)
-   **Description:** This dataset contains 15,000 rows of international trade transactions, providing information on imports and exports. It's suitable for business analytics, economic research, and financial modeling.
- **Data Size:** 2.69 MB
- **Data Type:** Panel
- **Data Dimensions:** 15000 Rows, 16 Columns

### Features

The dataset includes the following features:

-   **Transaction\_ID:** Unique identifier for each transaction.
-   **Country:** Country of origin or destination.
-   **Product:** Product being traded.
-   **Import\_Export:** Type of transaction (import or export).
-   **Quantity:** Amount of product traded.
-   **Value:** Monetary value (USD).
-   **Date:** Date of transaction.
-   **Category:** Product category (e.g., Electronics).
-   **Port:** Port of entry or departure.
-   **Customs\_Code:** Customs/HS code.
-   **Weight:** Product weight (kg).
-   **Shipping\_Method:** Shipping method (Air, Sea, Land).
-   **Supplier:** Supplier/manufacturer name.
-   **Customer:** Customer/recipient name.
-   **Invoice\_Number:** Unique invoice number.
-   **Payment\_Terms:** Payment terms (Net 30, etc.).

### Data Variable Types

-   **Numerical:**
    -   Quantity (int64)
    -   Value (float64)
    -   Customs\_Code (int64)
    -   Weight (float64)
    -   Invoice\_Number (int64)
-   **Categorical:**
    -   Transaction\_ID (object)
    -   Country (object)
    -   Product (object)
    -   Import\_Export (object)
    -   Date (object)
    -   Category (object)
    -   Port (object)
    -   Shipping\_Method (object)
    -   Supplier (object)
    -   Customer (object)
    -   Payment\_Terms (object)

## Project Objectives

1.  **Data Preparation:**
    -   Clean and preprocess the dataset.
    -   Handle missing data.
    -   Scale numerical features.
    -   Identify and remove outliers.
2.  **Dimensionality Reduction:**
    -   Use Principal Component Analysis (PCA) to reduce the number of features while preserving variance.
3.  **Cluster Analysis:**
    -   Apply K-Means, Birch, and DBSCAN clustering to segment trade transactions.
4.  **Evaluation of Clustering Methods:**
    -   Compare the performance of clustering algorithms using metrics like Silhouette Score, Davies-Bouldin Index, and Calinski-Harabasz Score.
5.  **Cluster Profiling:**
    -   Analyze each cluster to understand trade patterns, logistics, and customer segments.
6.  **Managerial Recommendations:**
    -   Provide data-driven recommendations for business improvements.

## Methodology

### Data Preprocessing

1.  **Missing Data Analysis:**
    -   Checked for missing values both by variable and by record.
    -   The dataset was found to have no missing values.
2.  **Data Subsetting:**
    -   Divided data into numerical and categorical subsets for targeted preprocessing.
3.  **Numerical Encoding:**
    -   Applied ordinal encoding to categorical variables.
    -   Recognized the potential for bias with ordinal encoding, suggesting one-hot encoding as an alternative.
4.  **Rescaling and Transformation:**
    -   Used `MinMaxScaler` to rescale numerical features to a 0-1 range.
    -   Applied a log transformation to reduce skewness.
5.  **Outlier Detection and Removal:**
    -   Used the Interquartile Range (IQR) method to detect outliers.
    -   Removed 1092 rows (~22%) identified as outliers.
    -   Generated box plots to visualize the distribution.

### Unsupervised Learning

1.  **Dimensionality Reduction:**
    -   Used PCA to reduce dimensionality to 5 components, retaining 100% of the variance.
2.  **Clustering Analysis:**
    -   **K-Means:**
        -   Identified 6 clusters as optimal.
        -   Silhouette Score: 0.215
        -   Davies-Bouldin Index: 1.206
    -   **Birch:**
        -   Identified 6 clusters.
        -   Silhouette Score: 0.131
        -   Davies-Bouldin Index: 1.601
    -   **DBSCAN:**
        -   Identified 2 clusters.
        -   Silhouette Score: 0.249
        -   Noise was present.

### Clustering Naming and Reasoning

- **K-Means Clusters (6 Clusters)**
    - **Cluster 0: Premium Trade:** High-value, consistent trade patterns.
    - **Cluster 1: Bulk Commodities:** High-volume, moderate-value.
    - **Cluster 2: Lightweight Essentials:** Small, critical deliveries.
    - **Cluster 3: Regional Dominance:** Region-specific trade.
    - **Cluster 4: Specialized Logistics:** Low-frequency, high-complexity.
    - **Cluster 5: Low-Frequency Anomalies:** Rare or unusual shipments.

- **Birch Clusters (7 Clusters)**
    - **Cluster 0: High-Value Transactions:** High monetary value, moderate weight.
    - **Cluster 1: Light Bulk Commodities:** Low-to-moderate weight, high frequency.
    - **Cluster 2: Regional Essentials:** Region-specific recurring trade.
    - **Cluster 3: Special Cases:** Niche or infrequent transactions.
    - **Cluster 4: Heavy-Duty Logistics:** Large weight, significant value.
    - **Cluster 5: Mid-Range Operations:** Balanced value, weight, frequency.
    - **Cluster 6: Niche High-Value Shipments:** Low-frequency, high-value.

- **DBSCAN Clusters (2 Clusters + Noise)**
    - **Cluster 0: Core Trade Patterns:** Established trade patterns.
    - **Cluster 1: Emerging Markets:** Localized or growing trade routes.
    - **Noise:** Irregular or sparse transactions.

### Key observations

- **K-Means** is the most suitable algorithm for this dataset, because it has balanced clusters and practical applicability.
- **Birch** is useful for subgroup analysis, while **DBSCAN** is useful for anomalies.

## Managerial Insights

1.  **Customer Segmentation:**
    -   Identified six distinct customer segments.
    -   **Cluster 4** (Premium Trade) should be prioritized for premium services.
    -   **Cluster 1** (Bulk Commodities) should focus on cost-efficient handling.
2.  **Logistics Optimization:**
    -   High-weight shipments (Clusters 0 and 4) should use land-based transport.
    -   High-value, low-weight shipments (Cluster 4) should use air shipping.
3.  **Revenue Growth Opportunities:**
    -   Target **Cluster 4** for high-value product bundles or loyalty programs.
    -   Offer bulk discounts or incentives to **Cluster 0** clients.
4.  **Regional Insights:**
    -   Customize marketing for regions with high-value transactions (Cluster 4).
    -   Offer flexible payment terms for regions in **Cluster 0**.
5.  **Operational Efficiency:**
    -   Maintain a separate analysis pipeline for outliers.

## Recommendations

-   **Preprocessing Enhancements:**
    -   Consider one-hot encoding for categorical data.
    -   Validate outliers with domain experts.
-   **Clustering Refinements:**
    -   Use hybrid approaches (e.g., K-Means followed by DBSCAN).
    -   Visualize clusters with PCA.
-   **Future Directions:**
    -   Investigate Customs\_Code and Invoice\_Number for domain insights.
    -   Refine DBSCAN parameters.

## Conclusion

This project successfully utilized unsupervised learning to segment international trade data, providing valuable insights for improving business strategies. K-Means clustering was identified as the most effective technique for generating well-defined customer segments. The project highlights how data-driven decisions can lead to improved logistics, customer targeting, and revenue growth.

## Code

The code for this project is available in the [https://colab.research.google.com/drive/1fuqmpdzxVSN_ZEOMPYyvXMBjuPTyxjkE?usp=sharing].

## Contributors

- Aayush Garg (055001)
- Rushil Kohli (055027)



# Follow Me on GitHub : https://github.com/Rushil-K

