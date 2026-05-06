<a href="https://github.com/John3Baskerville/SpotifyClustering">Project Link</a>

# Spotify Playlist Clustering Project

This project explores unsupervised machine learning by automatically grouping songs from my personal Spotify library into playlist-style clusters based on their audio characteristics. The goal was to identify meaningful listening patterns without using any manual labels or predefined genres.

---

## Data Collection

Before beginning the analysis, I first needed to collect and structure data from Spotify. To accomplish this, I used a lightweight Python wrapper, spotipy, for the Spotify Web API. Spotipy allowed me to authenticate with my personal Spotify account and programmatically extract playlist, track, and audio feature data directly from Spotify.

I used the Pandas library to transform the nested JSON responses returned by the API into structured tabular datasets for analysis.

Using each track’s Spotify ID, I gathered:
- Song metadata (title, artist, album, duration, etc.)
- Spotify audio features
- Track popularity metrics

The Spotify audio feature dataset included attributes such as:
- Danceability
- Energy
- Valence
- Tempo
- Acousticness
- Speechiness
- Instrumentalness
- Liveness

Each row in the final dataset represented a single song in my library.

### Dataset Overview
- ~1,600 songs
- 19 columns
- Combination of numerical and categorical features

<img src="ADD_DATASET_IMAGE_LINK" alt="spotify_dataset_example">

After extraction and transformation, the dataset was exported to CSV format for repeatable analysis and experimentation.

---

# Data Cleaning & Feature Engineering

Before clustering, several preprocessing steps were required to improve data quality and model performance.

### Cleaning Steps Included
- Removing duplicate tracks
- Handling missing or inconsistent values
- Standardizing numerical features
- Encoding categorical variables (cast categorical columns to str type for the K-Prototypes algorithm)
- Converting song duration into minutes
- Creating binary indicators for instrumental tracks

I also separated features into:
- **Continuous variables**  
  (energy, tempo, danceability, valence, etc.)

- **Categorical variables**  
  (musical key, mode, time signature, explicit/non-explicit, etc.)

Because clustering algorithms are highly sensitive to feature scale, continuous variables were normalized prior to modeling.

---

# Clustering Approach

To group similar songs together, I used the [K-Prototypes](https://towardsdatascience.com/the-k-prototype-as-clustering-algorithm-for-mixed-data-type-categorical-and-numerical-fe7c50538ebb/) clustering algorithm.

K-Prototypes was selected because the dataset contained a mixture of:
- Numerical features
- Categorical features

While traditional K-Means clustering performs well on purely numerical datasets, it is not well suited for categorical data because its distance calculations rely on Euclidean distance.

K-Prototypes extends K-Means by:
- Using Euclidean distance for numerical features
- Using dissimilarity matching for categorical features

This allowed the model to cluster songs using a more complete representation of musical characteristics.

---

# Model Evaluation

To determine the optimal number of clusters (`k`), I enabled the elbow method which looks a plot of k(number of clusters) vs cost.

Higher silhouette scores indicated better cluster separation and more meaningful playlist groupings.

Additional analysis included:
- Cluster feature averages
- Z-score comparisons against the global dataset
- Automatically generated cluster “themes”
- Distribution visualizations using violin plots and heatmaps

---

# Results

The clustering pipeline successfully grouped songs into distinct playlist-style categories based on shared audio characteristics.

Examples of automatically detected cluster themes included:
## Cluster Theme Summary

| Cluster | Songs | Theme |
|----------|-------|-------------|
| 0 | 115 | Wordy / Rap · Acoustic |
| 1 | 402 | Danceable · Produced |
| 2 | 254 | Low-Groove · Dark / Sad |
| 3 | 144 | Acoustic · Mellow |
| 4 | 152 | Live-Feel · High-Energy |
| 5 | 260 | Danceable · Dark / Sad |
| 6 | 262 | Upbeat · High-Energy |

### Cluster Distribution Overview
- Total Songs Clustered: **1,589**
- Total Clusters Generated: **7**
- Largest Cluster: **Cluster 1** (`Danceable · Produced`) — 402 songs
- Smallest Cluster: **Cluster 0** (`Wordy / Rap · Acoustic`) — 115 songs

To improve interpretability, I generated cluster labels by identifying the most statistically distinctive audio features within each cluster.

The visualizations below show how feature distributions vary across clusters.

<img src="ADD_VIOLIN_PLOT_LINK" alt="spotify_cluster_violinplots">

---

# Technologies Used

- Python
- Pandas
- NumPy
- Spotipy
- Scikit-Learn
- KModes / K-Prototypes
- Matplotlib
- Seaborn
- Jupyter Notebook

---

# Future Improvements

Potential future enhancements for the project include:
- Integrating song recommendation functionality
- Automatically generating Spotify playlists from clusters
- Applying dimensionality reduction with PCA or t-SNE
- Deploying the clustering pipeline as an interactive web application
- Comparing K-Prototypes performance against DBSCAN or hierarchical clustering
