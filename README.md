# 🎬 Movie Recommendation System

Movie Recommendation System is an AI-powered web application that recommends movies similar to a user's selected movie using **Content-Based Filtering** and **Cosine Similarity**. The system analyzes movie metadata such as genres, keywords, cast members, directors, and plot overviews to identify movies with similar characteristics and provide personalized recommendations.

The application is built using **Python**, **Machine Learning**, and **Streamlit**, and integrates with the **TMDB API** to dynamically fetch movie posters.

---

# 📌 Project Overview

With thousands of movies available across different genres and platforms, finding relevant content can be challenging. Recommendation systems help users discover movies that match their interests and viewing preferences.

This project helps users by:

* Recommending movies based on content similarity
* Analyzing movie metadata rather than user ratings
* Providing fast and interactive recommendations
* Displaying movie posters for better user experience
* Demonstrating the practical application of NLP and Machine Learning techniques

---

# 🚀 Features

* ✅ Content-Based Movie Recommendation System
* ✅ Recommendation of Top 5 Similar Movies
* ✅ Interactive Streamlit Web Interface
* ✅ Dynamic Movie Poster Retrieval using TMDB API
* ✅ Natural Language Processing for Feature Engineering
* ✅ Count Vectorization for Text Representation
* ✅ Cosine Similarity-Based Recommendation Engine
* ✅ Fuzzy Movie Search using Difflib
* ✅ Precomputed Similarity Matrix for Faster Predictions

---

# 🧠 Machine Learning Pipeline

## 1. Data Collection

Dataset Source:

* TMDB 5000 Movies Dataset
* TMDB 5000 Credits Dataset

Dataset Files:

* tmdb_5000_movies.csv
* tmdb_5000_credits.csv

The datasets contain information such as:

* Movie Titles
* Genres
* Keywords
* Cast
* Crew
* Plot Overviews

---

## 2. Data Preparation

The movie and credits datasets are merged using the movie title.

Only relevant features are selected:

```text
movie_id
title
overview
genres
keywords
cast
crew
```

Missing values are removed before further processing.

---

## 3. Feature Engineering

Important information is extracted from nested JSON-like columns:

### ✔ Genre Extraction

Movie genres are extracted and converted into a list format.

### ✔ Keyword Extraction

Keywords describing movie themes are extracted.

### ✔ Cast Extraction

Only the top three actors are retained to capture the most important cast information.

### ✔ Director Extraction

Director names are extracted from the crew column.

### ✔ Text Cleaning

Spaces are removed from names to maintain consistency.

Example:

```text
Sam Worthington → SamWorthington
James Cameron → JamesCameron
```

---

## 4. Tag Generation

A unified feature representation called **tags** is created by combining:

* Overview
* Genres
* Keywords
* Cast
* Director

Example:

```text
Avatar action adventure fantasy
SamWorthington ZoeSaldana
JamesCameron
```

This combined text serves as the basis for similarity calculations.

---

## 5. Text Vectorization

The generated tags are converted into numerical vectors using:

```python
CountVectorizer(max_features=5000, stop_words='english')
```

This transforms textual information into machine-readable feature vectors.

---

## 6. Similarity Calculation

Movie similarity is calculated using:

```python
cosine_similarity()
```

Cosine Similarity measures how closely two movies are related based on their feature vectors.

A similarity matrix is generated containing similarity scores between all movies in the dataset.

---

## 7. Recommendation Generation

When a user selects a movie:

1. The selected movie is located within the dataset.
2. Similarity scores are retrieved.
3. Movies are ranked based on similarity.
4. Top 5 most similar movies are returned.

---

# 🤖 Recommendation Technique

## Content-Based Filtering

This project uses Content-Based Filtering.

Instead of relying on user ratings or collaborative behavior, recommendations are generated based on movie attributes such as:

* Genres
* Keywords
* Cast
* Director
* Plot Description

---

# 📊 Output Example

### Input Movie

```text
Avengers
```

### Recommended Movies

```text
Avengers: Age of Ultron
Iron Man
Captain America: Civil War
Thor
Guardians of the Galaxy
```

(Results may vary depending on preprocessing and similarity scores.)

---

# 🛠️ Technologies Used

## Programming Language

* Python

## Machine Learning

* Scikit-learn
* CountVectorizer
* Cosine Similarity

## Data Processing

* Pandas
* NumPy

## Web Application

* Streamlit

## API Integration

* TMDB API

## Model Serialization

* Pickle

---

# 📂 Project Structure

```bash
movie-recommendation-system/
│
├── app.py
├── Movie Recommendation.ipynb
├── requirements.txt
├── dataset.zip
├── README.md
├── .gitignore
│
├── Generated Files
│   ├── movie_list.pkl
│   └── similarity.pkl
```

---

# 📈 Reproducibility

To reproduce the project:

1. Extract dataset.zip
2. Open Movie Recommendation.ipynb
3. Run all notebook cells
4. Generate:

```text
movie_list.pkl
similarity.pkl
```

5. Launch the Streamlit application:

```bash
streamlit run app.py
```

---

# ⚠️ Limitations

* Recommendations are based only on movie content.
* User preferences are not considered.
* Ratings and reviews are not incorporated.
* Similarity quality depends on available metadata.
* No personalized recommendation mechanism is implemented.

---

# 👨‍💻 Author

**Zubair Fakhar**

---

If you found this project useful, consider giving it a ⭐ on GitHub.
