# 🎬 Movie Recommendation System

A content-based movie recommendation engine that suggests similar movies using **TF-IDF vectorization** and **cosine similarity**, served through a **FastAPI** backend and an interactive **Streamlit** frontend, with live posters and metadata pulled from **TMDB**.

**Live app 👉 [Open on Streamlit](movie-recommendation-system ∙ main ∙ app.py)**

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

Movie-Recommendation-System/
├── app.py # Streamlit frontend (UI, search, recommendations display)
├── main.py # FastAPI backend (API routes for search, details, recommendations)
├── movies.ipynb # Data cleaning, EDA, and TF-IDF model building
├── movies_metadata.csv # Raw movie metadata dataset
├── df.pkl # Preprocessed movie dataframe
├── indices.pkl # Title → index mapping for similarity lookups
├── tfidf.pkl # Fitted TF-IDF vectorizer
├── tfidf_matrix.pkl # TF-IDF feature matrix
├── requirements.txt # Python dependencies
└── README.md

---

## 🛠️ Tech Stack

| Layer                | Technology |
|-----------------------|------------|
| Frontend              | [Streamlit](https://streamlit.io/) |
| Backend / API         | [FastAPI](https://fastapi.tiangolo.com/) + Uvicorn |
| ML / Recommendation   | scikit-learn (TF-IDF, cosine similarity), pandas, numpy, scipy |
| External Data         | [TMDB API](https://www.themoviedb.org/documentation/api) |
| HTTP Client           | requests / httpx |
| Deployment            | Streamlit Community Cloud (frontend) + Render (backend API) |

---

## 🚀 Getting Started

### Prerequisites

- Python 3.9+
- A free [TMDB API key](https://www.themoviedb.org/settings/api)

### 1. Clone the repository

```bash
git clone https://github.com/KartikKachwahe/Movie-Recommendation-System.git
cd Movie-Recommendation-System
```

### 2. Create a virtual environment & install dependencies

```bash
python -m venv venv
source venv/bin/activate      # On Windows: venv\Scripts\activate
pip install -r requirements.txt
```

### 3. Set up environment variables

Create a `.env` file in the project root:

```env
TMDB_API_KEY=your_tmdb_api_key_here
```

### 4. Run the backend API (FastAPI)

```bash
uvicorn main:app --reload
```

The API will be available at `http://127.0.0.1:8000`.

### 5. Run the Streamlit frontend

In a separate terminal:

```bash
streamlit run app.py
```

The app will open at `http://localhost:8501`.

> **Note:** `app.py` points to a deployed backend URL by default (`API_BASE` in `app.py`). Update this variable to `http://127.0.0.1:8000` if you're running the backend locally.

---

## 📡 API Endpoints (FastAPI backend)

| Endpoint | Description |
|---|---|
| `GET /tmdb/search?query=` | Search movies by title (TMDB) |
| `GET /home?category=&limit=` | Home feed by category (trending, popular, top_rated, now_playing, upcoming) |
| `GET /movie/id/{tmdb_id}` | Full movie details by TMDB ID |
| `GET /movie/search?query=` | Bundled TF-IDF + genre recommendations for a title |
| `GET /recommend/genre?tmdb_id=&limit=` | Genre-based recommendations |

---

## 📸 Preview

<!-- Add a screenshot or GIF of the app here -->
<!-- ![App Screenshot](assets/demo.png) -->

---

## 🗺️ Roadmap

- [ ] Add collaborative filtering (user-based recommendations)
- [ ] Add a "watchlist" / favorites feature
- [ ] Improve cold-start recommendations for new users
- [ ] Add unit tests for the FastAPI endpoints
- [ ] Dockerize the full stack

---

## 🤝 Contributing

Contributions are welcome! Feel free to open an issue or submit a pull request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

# 👨‍💻 Author

## Kartik Kachwahe

**Aspiring Data Scientist | Data Analyst | Machine Learning | SQL | Power BI | Python**

📧 Email: kartikkachwahe25@gmail.com

💼 LinkedIn: https://www.linkedin.com/in/kartikkachwahe021

💻 GitHub: https://github.com/KartikKachwahe

---

## ⭐ Support

If you found this project useful, consider giving the repository a star.

Your support motivates future projects and helps others discover this work.

---

**Thank you for visiting this repository ❤️**
