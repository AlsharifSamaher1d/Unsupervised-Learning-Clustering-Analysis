# Unsupervised Learning & Clustering Analysis

This repository contains a practical exploration of **unsupervised learning techniques** using hourly electricity demand and weather data from U.S. cities.

The analysis combines electricity demand with weather variables such as temperature and humidity to discover hidden patterns without predefined target labels.

## Notebook

`Unsupervised_Learning_Clustering_Analysis.ipynb`

The notebook includes the executed outputs and visualizations from the analysis.

## Techniques Covered

- Principal Component Analysis (PCA)
- Feature standardization
- K-Means clustering
- Elbow method
- Silhouette Score
- Hierarchical clustering
- DBSCAN
- t-SNE
- Cluster profiling and interpretation

## Dataset

The analysis uses processed hourly electricity-demand data together with hourly weather observations for several U.S. cities.

Main variables include:

- Electricity Demand (MW)
- Temperature
- Humidity
- Hour of Day
- City
- Season

The compressed dataset is included as `data.zip`. After extraction, it contains the processed files used by the notebook:

- `merged_df.csv`
- `weather_clean.csv`

> Note: the extracted CSV files are substantially larger than the compressed archive, so the repository stores the ZIP archive rather than the expanded files.

## Objective

The objective is to apply dimensionality-reduction and clustering techniques to identify meaningful patterns in electricity demand and weather conditions, evaluate cluster quality, and translate the resulting groups into interpretable insights.

## Final Exercise

The final exercise applies K-Means clustering using three features:

- Average Temperature
- Average Electricity Demand
- Average Humidity

Several values of `k` were evaluated with the Silhouette Score:

| k | Silhouette Score |
|---:|---:|
| 2 | **0.436** |
| 3 | 0.307 |
| 4 | 0.333 |
| 5 | 0.344 |

The best solution was **k = 2**, with a **Silhouette Score of 0.436**.

### Cluster Interpretation

- **Cluster 0:** 667 city-days, average temperature **55.62°F**, average demand **91,195.79 MW**, and average humidity **0.69**.
- **Cluster 1:** 4,642 city-days, average temperature **64.26°F**, average demand **31,631.61 MW**, and average humidity **0.68**.

The clusters are separated mainly by electricity-demand level. Humidity is almost identical across the two clusters, so adding humidity did not substantially change the clustering story.

## Running the Notebook

1. Open the notebook in Google Colab or Jupyter Notebook.
2. Upload `data.zip` to your runtime.
3. Extract the archive.
4. Update `data_dir` if your extracted files are stored in a different location.
5. Run the notebook cells in order.

## Repository Structure

```text
Unsupervised-Learning-Clustering-Analysis/
├── README.md
├── Unsupervised_Learning_Clustering_Analysis.ipynb
└── data.zip
```
