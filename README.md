# Netflix Movie Recommendation System 🎬

A collaborative filtering recommendation system built with Python and the Surprise library to predict user ratings for movies from the Netflix Prize dataset.

---
## 📜 Project Overview

This project demonstrates an end-to-end data science workflow for building a recommendation system. The key steps include:
- **Data Engineering:** Parsing and cleaning a large-scale, semi-structured dataset of over 24 million ratings.
- **Data Filtering:** Implementing a strategy to reduce data sparsity by filtering out less active users and less popular movies.
- **Modeling:** Building and evaluating a collaborative filtering model using the **Singular Value Decomposition (SVD)** algorithm from the `scikit-surprise` library.
- **Recommendation:** Generating a list of top N movie recommendations for a specified user based on predicted ratings.

---
## 📊 Dataset and Model

This project uses the **Netflix Prize Dataset**, which was released for a recommendation algorithm competition.

-   **Source:** [Netflix Prize Data on Kaggle](https://www.kaggle.com/datasets/netflix-inc/netflix-prize-data)
-   **Size:** Over 100 million ratings from ~480k users on ~17k movies.
-   **Note:** Due to its large size, the dataset is not included in this repository. Please download it from the source link above to run the notebook.
-   The trained model (`.pkl` file) is too large for this repository and is hosted on Google Drive.

     [**Download the `recommendation_model.pkl` file here**](https://drive.google.com/file/d/1GYY6buZV3Av-HpfEDP32Ii8xjnUZSe7H/view?usp=sharing)
   
     Please download the file and place it in the main project directory before running the notebook.

---
## ⚙️ Methodology

1.  **Data Loading & Preprocessing:** The raw data file (`combined_data_1.txt`) was loaded into a Pandas DataFrame. A custom parsing script was developed to handle the unique format where movie IDs and user ratings are mixed.
2.  **Sparsity Reduction:** To improve model performance, the dataset was filtered. Movies and users with a low number of total ratings (below the 60th percentile) were removed, resulting in a more dense and computationally manageable dataset.
3.  **Model Training & Evaluation:** The `scikit-surprise` library was used to train an SVD model on a sample of 1 million ratings. The model's performance was evaluated using 3-fold cross-validation, achieving a baseline **Root Mean Squared Error (RMSE) of approximately 1.01**.
4.  **Prediction:** A function was created to take a `user_id` and generate predicted ratings for all movies that the user has not yet seen. These predictions are then sorted to produce a final list of top recommendations.

---
## 🚀 How to Use

1.  **Clone the repository:**
    ```bash
    git clone (https://github.com/Shashank-2207/Netflix-Movie-Recommender)
    ```
2.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```
3.  **Download the Dataset:** Download the dataset from the Kaggle link provided above and place the `combined_data_1.txt` and `movie_titles.csv` files into a relevant directory.
4.  **Update the Notebook:** Open the `.ipynb` file and update the file paths in the `pd.read_csv()` cells to point to where you saved the dataset.
5.  **Run the Notebook:** Execute the cells sequentially in a Jupyter or Google Colab environment.

---
## 🏆 Example Results

Here are the top 5 recommended movies for the example user (ID: 1331154):

| Movie Title                                 | Year | Predicted Rating |
| ------------------------------------------- | ---- | ---------------- |
| Gilbert and Sullivan: The Mikado            | 1982 | 3.88             |
| Arlington Road                              | 1999 | 3.80             |
| Mary Tyler Moore: Season 1                  | 1970 | 3.78             |
| Joseph Campbell and The Power of Myth       | 1988 | 3.77             |
| 55 Days at Peking                           | 1963 | 3.77             |
| ...                                         | ...  | ...              |

---
## 💡 Future Improvements

-   **Full Dataset Training:** Train the final model on the entire filtered dataset (~20 million ratings) to maximize accuracy.
-   **Hyperparameter Tuning:** Use `GridSearchCV` from the Surprise library to find the optimal parameters for the SVD model.
-   **Explore Other Algorithms:** Compare the SVD model's performance against other algorithms like SVD++, KNN, or Co-Clustering.
-   **Deployment:** Package the model and prediction logic into a web API using a framework like Flask or FastAPI.
