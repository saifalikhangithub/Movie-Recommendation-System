# Movie-recommendation-system

# Movie Recommendation System

This project implements a content-based movie recommendation system using Python. The system recommends movies based on the similarity of their `overview` and `genre` descriptions.

## Table of Contents

* [About the Project](#about-the-project)
* [Features](#features)
* [Technologies Used](#technologies-used)
* [Dataset](#dataset)
* [Installation](#installation)
* [Usage](#usage)
* [How it Works](#how-it-works)

## About The Project

In today's vast cinematic landscape, finding the next movie to watch can be overwhelming. This project tackles that challenge by providing a recommendation engine that suggests movies similar to ones you already enjoy. It leverages the textual content of movie descriptions and genres to identify related films, offering a personalized viewing experience.

## Features

* **Content-Based Filtering:** Recommends movies based on the `overview` (synopsis) and `genre` of a given movie.
* **Text Vectorization:** Converts textual movie descriptions into numerical representations using the Bag of Words (BoW) model.
* **Cosine Similarity:** Utilizes cosine similarity to measure the likeness between movie vectors, ensuring relevant recommendations.
* **Simple and Efficient:** A straightforward implementation that demonstrates the core concepts of content-based recommendation.

## Technologies Used

* **Python 3.x**
* **pandas:** For data manipulation and analysis.
* **scikit-learn:** For text vectorization (`CountVectorizer`) and similarity calculation (`cosine_similarity`).
* **Jupyter Notebook:** The project is developed and demonstrated in a Jupyter Notebook (`Main.ipynb`).

## Dataset

The project uses a dataset named `moviesdataset.csv`. This dataset is expected to contain at least the following columns:
* `id`: Unique identifier for the movie.
* `title`: The title of the movie.
* `overview`: A brief summary or synopsis of the movie.
* `genre`: The genre(s) of the movie (e.g., "Drama,Crime").

## Installation

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/your-username/movie-recommendation-system.git](https://github.com/your-username/movie-recommendation-system.git)
    cd movie-recommendation-system
    ```
2.  **Create a virtual environment (recommended):**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
    ```
3.  **Install the required packages:**
    ```bash
    pip install pandas scikit-learn
    ```
4.  **Place the dataset:**
    Ensure that `moviesdataset.csv` is in the same directory as the `Main.ipynb` file.

## Usage

1.  **Open the Jupyter Notebook:**
    ```bash
    jupyter notebook Main.ipynb
    ```
2.  **Run all cells:**
    Execute all cells in the notebook.
3.  **Get recommendations:**
    At the end of the notebook, there's a function `recommand("Movie Title")`. You can call this function with the title of a movie (e.g., `"The Godfather"`) to get 5 recommendations.

    Example:
    ```python
    recommand("The Godfather")
    ```

## How It Works

The recommendation system follows these steps:

1.  **Data Loading:** The `moviesdataset.csv` is loaded into a pandas DataFrame.
2.  **Feature Combination:** The `overview` and `genre` columns are combined into a new `tags` column. This `tags` column serves as the primary text feature for similarity calculation.
3.  **Text to Vector Conversion:** The `tags` text data is transformed into numerical vectors using `CountVectorizer`. This process counts the occurrences of words, creating a high-dimensional vector representation for each movie. Common English stop words are removed to improve relevance.
4.  **Cosine Similarity Calculation:** The cosine similarity is calculated between all movie vectors. Cosine similarity measures the angle between two vectors; a smaller angle (closer to 1) indicates higher similarity.
5.  **Recommendation Generation:** When a user requests recommendations for a specific movie, the system finds that movie's vector, identifies other movies with the highest cosine similarity to it, and then returns the titles of the top similar movies.
