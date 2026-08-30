# Unsupervised Learning & Clustering Analysis

A hands-on data science analysis exploring how **unsupervised learning** can reveal hidden patterns in electricity-demand and weather data from U.S. cities.

Rather than predicting a predefined target, this project focuses on discovering structure in the data through **dimensionality reduction, clustering, visualization, cluster-quality evaluation, and interpretation**.

## Project Overview

Electricity consumption varies across locations, time periods, and weather conditions. This notebook combines processed hourly electricity-demand observations with weather information and applies multiple unsupervised-learning techniques to investigate whether naturally occurring groups can be identified.

The workflow moves from understanding and preparing the features to visualizing high-dimensional structure, applying several clustering algorithms, evaluating their quality, and interpreting the resulting groups in practical terms.

## Objectives

The main objectives of this analysis are to:

- Explore patterns in electricity demand and weather variables without predefined labels.
- Prepare and standardize numerical features for distance-based algorithms.
- Use dimensionality-reduction techniques to visualize structure in the data.
- Apply and compare multiple clustering approaches.
- Evaluate K-Means solutions using the Elbow Method and Silhouette Score.
- Profile the resulting clusters and translate them into interpretable insights.
- Investigate whether adding humidity provides additional separation between city-day groups.

## Dataset

The repository includes `data.zip`, which contains the processed datasets used by the notebook:

- `merged_df.csv` — electricity-demand observations merged at the sub-region/hour level.
- `weather_clean.csv` — cleaned hourly weather observations at the city level.

The analysis works with variables including:

| Feature | Description |
|---|---|
| Electricity Demand | Hourly electricity demand measured in MW |
| Temperature | Weather temperature observations |
| Humidity | Relative humidity information |
| Hour of Day | Time-based feature used to explore daily demand patterns |
| City | Geographic grouping variable |
| Season | Seasonal context for demand and weather patterns |

The final clustering exercise aggregates the observations to the **city-day** level and uses average temperature, average electricity demand, and average humidity.

## Analysis Workflow

### 1. Data Preparation

The electricity and weather datasets are loaded, cleaned, aligned, and combined for analysis. Numerical variables are standardized before applying methods that depend on distances so that features with larger numerical scales do not dominate the clustering process.

### 2. Principal Component Analysis (PCA)

**Principal Component Analysis (PCA)** is used to reduce dimensionality while retaining as much variation as possible. PCA provides a lower-dimensional representation that helps visualize structure and understand how the original features contribute to major directions of variation.

### 3. K-Means Clustering

**K-Means** partitions observations into groups by minimizing within-cluster distances. Multiple values of `k` are explored instead of assuming the number of clusters in advance.

Two complementary approaches are used to evaluate the number of clusters:

- **Elbow Method** — examines how within-cluster variation changes as `k` increases.
- **Silhouette Score** — measures how well each observation fits its assigned cluster relative to neighboring clusters.

### 4. Hierarchical Clustering

**Hierarchical clustering** is explored to understand nested relationships between observations and how groups can form at different levels of similarity.

### 5. DBSCAN

**DBSCAN (Density-Based Spatial Clustering of Applications with Noise)** is used as a density-based alternative to K-Means. Unlike K-Means, DBSCAN does not require specifying the number of clusters beforehand and can identify observations that behave like noise or outliers.

### 6. t-SNE Visualization

**t-SNE** is used as a nonlinear dimensionality-reduction technique for visual exploration. It helps reveal local neighborhood structure and provides another perspective on how observations may group in a low-dimensional space.

### 7. Cluster Profiling

After clustering, the groups are summarized using their average feature values. This step turns cluster labels into interpretable descriptions rather than treating them simply as numerical IDs.

## Final Exercise: Temperature, Demand & Humidity

The final exercise extends the clustering analysis by adding **average humidity** to average temperature and average electricity demand.

The three clustering features are:

1. Average Temperature
2. Average Electricity Demand
3. Average Humidity

The features are standardized and K-Means is evaluated for `k = 2, 3, 4, 5` using the Silhouette Score.

### Silhouette Results

| Number of Clusters (`k`) | Silhouette Score |
|---:|---:|
| **2** | **0.436** |
| 3 | 0.307 |
| 4 | 0.333 |
| 5 | 0.344 |

The highest score is obtained with **k = 2**, giving a **Silhouette Score of 0.436**. Therefore, two clusters are selected for the final model.

## Final Cluster Profile

| Cluster | City-Days | Avg. Temperature (°F) | Avg. Demand (MW) | Avg. Humidity |
|---:|---:|---:|---:|---:|
| 0 | 667 | 55.62 | 91,195.79 | 0.69 |
| 1 | 4,642 | 64.26 | 31,631.61 | 0.68 |

### Interpretation

**Cluster 0** represents a smaller group of city-days characterized by substantially higher average electricity demand. Its average temperature is lower than Cluster 1, while its average humidity is approximately 0.69.

**Cluster 1** contains the majority of city-days and is characterized by much lower average electricity demand, a somewhat higher average temperature, and average humidity of approximately 0.68.

The strongest distinction between the two clusters is therefore **electricity demand**. Average humidity is nearly identical across the groups (**0.69 vs. 0.68**), indicating that adding humidity did **not substantially change the clustering story** in this experiment.

## Key Takeaways

- Unsupervised learning can reveal structure without requiring labeled outcomes.
- Feature scaling is important because clustering methods such as K-Means rely on distances.
- Different clustering algorithms make different assumptions about cluster shape and density.
- Cluster-quality metrics are useful for model selection, but interpretation of the resulting groups is equally important.
- For the final three-feature experiment, **two clusters produced the strongest Silhouette Score** among the tested values.
- The final clusters were separated mainly by **electricity-demand level**, while humidity contributed little additional separation.

## Techniques & Libraries

**Techniques**

- Data preprocessing and aggregation
- Feature standardization
- Principal Component Analysis (PCA)
- K-Means clustering
- Elbow Method
- Silhouette Score
- Hierarchical clustering
- DBSCAN
- t-SNE
- Cluster profiling
- Data visualization

**Python Libraries**

- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`
- `scikit-learn`

## Repository Structure

```text
Unsupervised-Learning-Clustering-Analysis/
├── README.md
├── Unsupervised_Learning_Clustering_Analysis.ipynb
└── data.zip
```

## Running the Notebook

1. Clone or download this repository.
2. Open `Unsupervised_Learning_Clustering_Analysis.ipynb` in Google Colab or Jupyter Notebook.
3. Extract `data.zip` in the notebook runtime.
4. Ensure `data_dir` points to the directory containing `merged_df.csv` and `weather_clean.csv`.
5. Run the notebook cells in order.

The committed notebook includes the executed outputs and visualizations so the analysis and results can also be reviewed directly on GitHub.

## Author

**Samaher Alsharif**

Data Science | Machine Learning | Unsupervised Learning
