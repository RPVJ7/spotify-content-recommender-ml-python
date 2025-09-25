# 🎵 Spotify Content-Based Recommender

This project builds a **content-based song recommender system** using data from the [Spotify Web API](https://developer.spotify.com/documentation/web-api/) and a Kaggle dataset of audio features.  
It is designed as a portfolio piece demonstrating **data collection, modeling, and machine learning** with music data.

---

## ✨ Project Overview

The notebook walks through the complete process of building a recommender:

1. **Data Acquisition**
   - Connect to Spotify API using the [`spotipy`](https://spotipy.readthedocs.io) library.
   - Retrieve a curated list of top artists with their IDs, popularity, and followers.
   - For each artist:
     - Fetch albums (only `album` and `single`, excluding compilations).
     - Filter to keep only solo albums.
     - Retrieve tracks for each album and filter out collaborations.
   - Enrich the track data with **audio features** (danceability, energy, valence, etc.) from a Kaggle dataset.

2. **Data Modeling**
   - Follow a **star schema** design to avoid redundancy:
     - `artist_df` – artist IDs, names, popularity, followers.
     - `album_df` – album IDs, names, release dates, artist references.
     - `track_df` – track IDs, names, album references, artist references, and audio features.

3. **Machine Learning**
   - Normalize audio feature columns so they are on the same scale.
   - Fit a **k-Nearest Neighbors (kNN)** model with cosine similarity.
   - Given a seed track, recommend 10 similar tracks based on audio features.

4. **Interactive Demo**
   - Wrapper cell in Jupyter lets you type a song name.
   - System returns the seed track + 10 most similar songs with similarity scores.

## 📂 Repository Structure

├── README.md # Project documentation
├── Spotify_Recommender_GitHub.ipynb # Main Jupyter Notebook with recommender system
└── kaggle_spotify_dataset.csv # Kaggle dataset containing audio features

## Install dependencies

pip install spotipy scikit-learn pandas numpy

## Set up Spotify API credentials

- Go to Spotify Developer Dashboard
- Create a new app and copy your Client ID and Client Secret.
- Add a redirect URI (e.g. http://localhost:8888/callback).
- Update the following variables in the notebook:

    CLIENT_ID = "your_client_id"
    CLIENT_SECRET = "your_client_secret"
    REDIRECT_URI = "http://localhost:8888/callback"

⚠️ Note: You must replace these with your own credentials or the API calls will fail.

## Run the notebook

Open Jupyter Notebook or JupyterLab and run through the cells.
🎯 Example Usage: After running the setup cells, type a song name in the interactive recommender cell:

🧑‍💻 Skills Demonstrated:

  -API integration (Spotify Web API via Spotipy)
  -Data modeling (star schema design)
  -Data wrangling with Pandas
  -Feature scaling & nearest neighbor search
  -Building a recommender system
  -Interactive prototyping in Jupyter
