# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Unsupervised ML project that clusters ~1,600 songs from a personal Spotify "Liked Songs" library into thematic playlists using K-Prototypes clustering (handles mixed categorical + continuous features). Songs are extracted via the Spotify Web API, preprocessed, and grouped into 7 clusters visualized with violin plots.

## Environment Setup

Create a `.env` file from `.env.example` with valid Spotify developer credentials (`CLIENT_ID`, `CLIENT_SECRET`). The virtual environment is at `.venv/`.

Install dependencies:
```bash
pip install pandas numpy spotipy scikit-learn kmodes scipy matplotlib seaborn python-dotenv
```

## Notebook Execution Order

The raw data (`spotifyLibrary.csv`) is already checked in — no need to re-run the API extraction notebook.

1. **`Juypter Notebooks/SpotifyClustering2.ipynb`** — Primary analysis: imports `spotifyLibrary.csv` directly, preprocessing, skewness correction, MinMax scaling, K-Prototypes clustering (n_clusters=7), violin plot visualization, outputs `songDataKProto.csv`
2. **`Juypter Notebooks/Spotify EDA & Clustering Models.ipynb`** — Optional EDA: correlation heatmaps, K-Means/Agglomerative comparisons, PCA

## Architecture & Data Flow

```
spotifyLibrary.csv              (1,597 songs × 20 columns, raw — already checked in)
    → Skewness transforms       (Box-Cox / log for instrumentalness, duration, liveness, etc.)
    → MinMaxScaler              (10 continuous features → 0–1)
    → K-Prototypes              (categorical cols: key[2], mode[4], time_signature[12])
    → songDataKProto.csv        (clustered, with kproto label column)
    → Violin plots / heatmaps
```

**Why K-Prototypes over K-Means:** Euclidean distance fails for categorical features (key, mode, time_signature); K-Prototypes uses a hybrid dissimilarity measure.

## Key Data Files

| File | Description |
|------|-------------|
| `spotifyLibrary.csv` | Raw API extract |
| `spotifyLibraryNames.csv` | Raw data + song names |
| `songDataKProto.csv` | Final clustered output |
| `projectImages/` | Saved visualizations (heatmap, violin plots, word clouds) |

## Spotify API Authentication

The extraction notebook uses Spotipy's `SpotifyOAuth`. Credentials must come from environment variables or a `.env` file — do not hardcode `CLIENT_ID`/`CLIENT_SECRET` in notebooks.
