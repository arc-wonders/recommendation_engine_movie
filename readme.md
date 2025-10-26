## Overview

This project demonstrates how to build a **movie recommendation engine** that suggests similar movies based on their metadata — such as **genres, plot keywords, cast, director, and IMDb scores**.

Unlike collaborative filtering (which needs user ratings), this approach works with just the movie dataset itself.  
You’ll learn how to:

- Clean and preprocess tabular + textual data  
- Extract features using **TF-IDF (Term Frequency–Inverse Document Frequency)**  
- Combine text and numeric signals  
- Compute **cosine similarity** between movies  
- Generate human-interpretable recommendations  

--- 
##  How It Works

### 1️ Data Cleaning
- Fixes missing values, formats columns, and standardizes names.

### 2️ Feature Engineering
- Merges key metadata (`genres`, `actors`, `director`, `keywords`, etc.) into one text profile per movie.

### 3️ TF-IDF Vectorization
- Converts text metadata into high-dimensional numeric vectors.  
  Common words get lower weights, unique words get higher importance.

### 4️ Numeric Features
- Adds extra continuous features (IMDB score, year, duration, budget, etc.).  
- Scaled between 0–1 for fair weighting.

### 5️ Combine & Normalize
- Merge TF-IDF (text) and numeric vectors into a single feature space.  
- Normalize with **L2 norm** to prepare for similarity search.

### 6️ Cosine Similarity
- Measures the angle between movie vectors — the smaller the angle, the more similar the movies.

### 7️ Recommendation Function
- Input: movie title  
- Output: Top-K similar movies ranked by similarity score.

---

git clone https://github.com/<your-username>/recommendation_engine_movie.git
cd recommendation_engine_movie


pip install -r requirements.txt

run engine.ipynb code cells ( 0 -11)

--- 

## Why Cosine Similarity?

Cosine similarity focuses on the direction of vectors, not their magnitude —
perfect for text-based vectors where some movies have longer metadata than others.


1.0 → identical movies

0.0 → totally unrelated movies

It ensures the system finds semantically similar movies rather than just those with many common words.

## Why Not Classification?

Classification predicts fixed labels (e.g., genre = Action).
Recommendation instead finds the most similar items in a continuous feature space.
Hence we use similarity search, not multi-label classification.