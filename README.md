# 🎮 Hybrid Game Recommendation System

An advanced, production-ready Game Recommendation System built with Python, Streamlit, and Scikit-Learn. This project utilizes a sophisticated hybrid algorithm combining Content-Based Filtering and Collaborative Filtering to generate highly accurate, robust game recommendations while solving the traditional cold-start problem.

## 🌟 Key Features

*   **Classic Hybrid Recommender:** Suggests similar games based on combined tags/genres (TF-IDF) and mathematical user playtime overlap (K-Nearest Neighbors). Explains its reasoning dynamically.
*   **Mood-Based Engine:** Recommends top-tier games based on physical or emotional states (e.g., Action/High Energy, Relaxing/Chill, Competitive).
*   **User Segment Clustering:** Utilizes Unsupervised Machine Learning (K-Means) to automatically segment users into Casual, Moderate, and Hardcore players based on behavior patterns. 
*   **Playtime Bracket Filtering:** Recommends high-quality games specifically fitting a user’s available free time (Bite-Sized vs Lifestyle games).
*   **Deep Profile Engine:** Accepts up to 5 favorite games at once, amalgamating their combined content and collaborative vectors into a unified master profile match.
*   **Interactive Dashboard UI:** Fully designed Streamlit frontend displaying trending community stats, visual scatter plots, and algorithmic similarity explorations.

## 🛠️ Technology Stack

*   **Frontend:** [Streamlit](https://streamlit.io/) (for responsive analytical web app UI)
*   **Data Processing:** Pandas, NumPy 
*   **Machine Learning (Scikit-Learn):**
    *   `TfidfVectorizer` and `cosine_similarity` for Content analysis
    *   `NearestNeighbors` for Sparse Matrix Collaborative Filtering
    *   `KMeans` for User Segmentation
    *   `MinMaxScaler` for Engine blending
*   **Data Visualization:** Matplotlib, Seaborn

## 🚀 Installation & Setup

1. **Clone the repository:**
   ```bash
   git clone <your-github-repo-url>
   cd "game recommendation system final"
   ```

2. **Install core dependencies:**
   Make sure you have Python 3.8+ installed. 
   ```bash
   pip install -r requirements.txt
   ```

3. **Dataset Requirements:**
   To run this locally, ensure you have the required Steam dataset CSV files inside a `data/` directory at the project root. (Note: The `data/` folder is `.gitignore`d to prevent pushing massive files to GitHub).
   Required datasets:
   *   `steam.csv`
   *   `steam-200k.csv`
   *   `steam_media_data.csv`
   *   `steamspy_tag_data.csv`

4. **Run Preprocessing (First time only):**
   This script builds the matrices and cleans the datasets:
   ```bash
   python src/preprocess.py
   ```

5. **Launch the Application:**
   ```bash
   streamlit run app.py
   ```

## 📊 Evaluation Metrics

The system implements offline model validation utilizing holdout samples. 
* Evaluated strictly on `Precision@10` and `Recall@10`.
* The **Hybrid model** objectively outperforms isolated Content or Collaborative models by efficiently handling both historical player data constraints and semantic text relationships.

## 🚀 Deployment (Streamlit Cloud)

To deploy this application to the web:

1. **GitHub Setup**: Push this repository to a new GitHub repository.
2. **Include Data**: Ensure the required CSV files are pushed (the `.gitignore` has been pre-configured for this).
   ```bash
   git add data/cleaned_steam.csv data/cleaned_user_interactions.csv data/steam_media_data.csv
   git commit -m "Add required data for deployment"
   git push origin main
   ```
3. **Connect to Streamlit**:
   - Go to [Streamlit Community Cloud](https://share.streamlit.io/).
   - Click "New app" and select your repository.
   - Set the Main file path to `app.py`.
   - Click **Deploy**.
   - Your app will be live at a public URL!
