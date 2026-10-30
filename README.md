# 🎵 SoundSpace: Spotify Music Analytics & Recommendation System

**SoundSpace** is an interactive, web-based analytics and recommendation platform powered by **Unsupervised Machine Learning** and **Streamlit**. It processes Spotify audio features (such as acousticness, danceability, energy, and valence) using **Principal Component Analysis (PCA)** for dimensionality reduction and **Cosine Similarity** to generate real-time, content-based music recommendations.

---

## 🚀 Key Features

### 1. 📊 Dataset Information & Exploration
- High-level overview of the track catalog (track count, feature count, duplicate detection).
- Sample records preview with metadata (artist, track title, genre).
- Column types, missing value detection, and descriptive statistical summaries.

### 2. 🔍 Exploratory Data Analysis (EDA)
- **Feature Distributions:** Univariate histograms for all musical attributes.
- **Correlation Heatmap:** Pearson correlation analysis among audio properties (e.g., energy vs. loudness, acousticness vs. energy).
- **Outlier Detection:** Boxplots across audio dimensions.
- **Bi-variate Analysis:** Interactive scatter relationship plots (e.g., Danceability vs. Energy).
- **Popularity Insights:** Distribution of Spotify popularity scores across tracks.

### 3. 🎧 Content-Based Music Recommendation Engine
- Select any seed song from a curated multi-genre library with quick search.
- Computes **Cosine Similarity** on the PCA-transformed latent feature space.
- Displays top recommendations ($N \in \{5, 10, 15, 20\}$) with similarity match percentages, genre, and popularity scores.

### 4. 🧠 PCA & Model Performance Analytics
- **Optimal Dimensionality Reduction:** Dynamically selects the number of principal components needed to retain at least **95% cumulative variance**.
- **Performance Metrics:** Reports Reconstruction Mean Squared Error (MSE), feature reduction ratio, and K-Means **Silhouette Score**.
- **Visual Diagnostics:**
  - 2D PCA cluster projection scatter plot.
  - Cumulative Explained Variance curve with the 95% retention threshold.
  - Variance explained breakdown per principal component.

---

## 🛠️ Tech Stack

- **Frontend & App Framework:** [Streamlit](https://streamlit.io/)
- **Machine Learning & Modeling:** [Scikit-learn](https://scikit-learn.org/) (`PCA`, `StandardScaler`, `KMeans`, `cosine_similarity`)
- **Data Manipulation:** [Pandas](https://pandas.pydata.org/), [NumPy](https://numpy.org/)
- **Data Visualization:** [Matplotlib](https://matplotlib.org/), [Seaborn](https://seaborn.pydata.org/)

---

## 📁 Project Structure

```text
spotify_unsupervised/
├── app.py                  # Main Streamlit application
├── SpotifyFeatures.csv     # Spotify audio features dataset
├── requirements.txt        # Project dependencies
├── .gitignore              # Files and folders to ignore in Git
└── README.md               # Project documentation
```

---

## ⚙️ Installation & Setup

### 1. Clone the Repository
```bash
git clone https://github.com/Devikakjijith/spotify_recommendation_streamlit.git
cd spotify_recommendation_streamlit
```

### 2. Create and Activate a Virtual Environment

**On Windows (PowerShell):**
```powershell
python -m venv venv
venv\Scripts\Activate.ps1
```

**On macOS / Linux:**
```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

*(Or install directly if `requirements.txt` is not yet created)*:
```bash
pip install streamlit pandas numpy scikit-learn matplotlib seaborn
```

### 4. Ensure the Dataset is Present
Make sure `SpotifyFeatures.csv` is placed in the project root directory.

---

## ▶️ Running the Application

Launch the Streamlit dashboard by running:
```bash
streamlit run app.py
```

Once started, open your web browser at:
```
http://localhost:8501
```

---

## 📈 Unsupervised Learning Pipeline

```text
[ Raw Audio Features ]
         │
         ▼
[ Data Cleaning & Imputation ]
         │
         ▼
[ StandardScaler Normalization ]
         │
         ▼
[ Principal Component Analysis (PCA) ] ──▶ (Retains ≥ 95% Variance)
         │
         ▼
[ Cosine Similarity Computation ] ───────▶ (Top-N Similar Song Recommendations)
```

1. **Standardization:** Audio features vary in scales (e.g., loudness in dB vs. danceability from 0 to 1). Features are standardized using `StandardScaler` ($\mu = 0, \sigma = 1$).
2. **Dimensionality Reduction (PCA):** Eliminates collinearity and reduces noise while preserving 95% of information.
3. **Similarity Calculation:** Calculates cosine similarity vectors between the selected track and all catalog tracks to output closest acoustic matches.

---

## 📜 License
This project is for educational and research purposes.

