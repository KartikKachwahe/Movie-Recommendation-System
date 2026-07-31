# 🎬 Movie Recommendation System

A content-based movie recommendation engine that suggests similar movies using **TF-IDF vectorization** and **cosine similarity**, served through a **FastAPI** backend and an interactive **Streamlit** frontend, with live posters and metadata pulled from **TMDB**.

**Live app 👉 [Open on Streamlit](https://your-app-name.streamlit.app)**

<!-- Replace the link above with your actual Streamlit Community Cloud URL -->

---

## ✨ Features

- 🔍 **Search-as-you-type** — autocomplete suggestions while typing a movie title
- 🎯 **Content-based recommendations** — TF-IDF + cosine similarity on movie overviews/metadata
- 🎭 **Genre-based recommendations** — fallback "More like this" suggestions by genre
- 🏠 **Home feed** — browse Trending, Popular, Top Rated, Now Playing, and Upcoming movies
- 🖼️ **Rich movie details** — poster, backdrop, overview, release date, and genres via TMDB
- ⚡ **Fast & cached** — API responses cached client-side for a snappy UI
- 🖥️ **Clean, responsive UI** — custom-styled Streamlit interface with a configurable poster grid

---

## 🧠 How It Works

1. Movie metadata (`movies_metadata.csv`) is cleaned and processed in `movies.ipynb`.
2. A **TF-IDF matrix** is built over movie descriptions/keywords using `scikit-learn` and stored as `tfidf.pkl` / `tfidf_matrix.pkl`.
3. **Cosine similarity** between the TF-IDF vectors is used to find the most similar movies to a selected title (`indices.pkl` maps titles to their positions in the matrix).
4. A **FastAPI** backend (`main.py`) exposes endpoints for search, home feed, movie details, and recommendations, enriching results with live poster/backdrop data from the **TMDB API**.
5. The **Streamlit** frontend (`app.py`) consumes this API to render a searchable, browsable movie recommendation interface.

---

## 🗂️ Project Structure
