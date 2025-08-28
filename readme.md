# 🎌 Anime Recommendation System

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue)](https://python.org)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.15%2B-orange)](https://tensorflow.org)
[![Scikit-learn](https://img.shields.io/badge/Scikit--learn-1.0%2B-green)](https://scikit-learn.org)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

> An intelligent anime recommendation system using Content-Based Filtering and Collaborative Filtering techniques to help users discover anime that match their preferences.

This project implements two sophisticated machine learning approaches to provide personalized anime recommendations, developed as a final project for the [Dicoding Machine Learning Course](https://www.dicoding.com/academies/319).

## 📋 Table of Contents

- [🎯 Features](#-features)
- [🏗️ System Architecture](#️-system-architecture)
- [🚀 Quick Start](#-quick-start)
- [💻 Installation](#-installation)
- [🔧 Usage](#-usage)
- [🛠️ Technology Stack](#️-technology-stack)
- [📊 Dataset](#-dataset)
- [📈 Model Performance](#-model-performance)
- [📖 Detailed Documentation](#-detailed-documentation)
- [🤝 Contributing](#-contributing)
- [📄 License](#-license)
- [👨‍💻 Author](#-author)

## 🎯 Features

- **🎭 Content-Based Filtering**: Recommends anime based on genre similarities using TF-IDF and Cosine Similarity
- **👥 Collaborative Filtering**: Provides personalized recommendations using Neural Network embeddings
- **📊 Comprehensive Evaluation**: Includes Precision, Recall, F1-Score for content-based and RMSE for collaborative filtering
- **🔍 Flexible Recommendation**: Get recommendations for any anime in the dataset
- **📈 Performance Metrics**: Detailed analysis of model performance and accuracy

## 🏗️ System Architecture

```
User Input → [Content-Based Filter] → Genre-Based Recommendations
           ↘ [Collaborative Filter] → Rating-Based Recommendations
```

The system employs two complementary approaches:
1. **Content-Based**: Analyzes anime genres to find similar content
2. **Collaborative**: Learns from user rating patterns to predict preferences

## 🚀 Quick Start

```bash
# Clone the repository
git clone https://github.com/muhwira27/anime-recommendation-system.git
cd anime-recommendation-system

# Install dependencies
pip install -r requirements.txt

# Run the Jupyter notebook
jupyter notebook notebook.ipynb
```

## 💻 Installation

### Prerequisites

- Python 3.8 or higher
- Jupyter Notebook or JupyterLab
- At least 8GB RAM (recommended for large dataset processing)

### Step-by-step Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/muhwira27/anime-recommendation-system.git
   cd anime-recommendation-system
   ```

2. **Create a virtual environment** (recommended)
   ```bash
   python -m venv anime-rec-env
   source anime-rec-env/bin/activate  # On Windows: anime-rec-env\Scripts\activate
   ```

3. **Install required packages**
   ```bash
   pip install -r requirements.txt
   ```

4. **Download the dataset**
   - The dataset is automatically downloaded from [Kaggle](https://www.kaggle.com/datasets/dbdmobile/myanimelist-dataset) when running the notebook
   - Ensure you have a Kaggle account and API key configured

## 🔧 Usage

### Content-Based Recommendations

```python
# Get recommendations based on anime genre similarity
anime_recommendations("Your Anime Title", similarity_data, items, k=5)
```

### Collaborative Filtering Recommendations

```python
# Get personalized recommendations based on user ratings
# The model will predict ratings for unrated anime and recommend top-k items
model.predict([user_id, anime_id])
```

### Example Output

**Content-Based Filtering Results:**
```
Recommendations for "Seishun Buta Yarou wa Bunny Girl Senpai no Yume wo Minai":
1. Kokoro Connect (Drama, Romance, Supernatural)
2. Charlotte (Drama, Romance, Supernatural) 
3. Angel Beats! (Drama, Comedy, Supernatural)
4. Clannad (Drama, Romance, Slice of Life)
5. Toradora! (Romance, Comedy, Drama)
```

## 🛠️ Technology Stack

- **🐍 Python 3.8+**: Core programming language
- **🧠 TensorFlow 2.15+**: Neural network implementation for collaborative filtering
- **📊 Scikit-learn**: TF-IDF vectorization and cosine similarity
- **🐼 Pandas**: Data manipulation and analysis
- **🔢 NumPy**: Numerical computing
- **📈 Matplotlib**: Data visualization
- **📓 Jupyter**: Interactive development environment

## 📊 Dataset

The project uses three comprehensive datasets from [MyAnimeList](https://www.kaggle.com/datasets/dbdmobile/myanimelist-dataset):

| Dataset | Records | Features | Description |
|---------|---------|----------|-------------|
| **Anime Dataset** | 24,901 | 24 | Anime information including genres, ratings, episodes |
| **User Details** | 731,290 | 16 | User profiles and watching statistics |
| **User Ratings** | 24.3M | 5 | User ratings for anime (1-10 scale) |

### Key Features Used:
- **Anime**: `anime_id`, `Name`, `Genres`, `Score`, `Episodes`
- **Users**: `user_id`, `Mean Score`, `Total Entries`
- **Ratings**: `user_id`, `anime_id`, `rating`

## 📈 Model Performance

### Content-Based Filtering
- **Precision**: 95.02% - Highly relevant recommendations
- **Recall**: 100% - Finds all relevant items
- **F1-Score**: 97.45% - Excellent balance of precision and recall

### Collaborative Filtering
- **Training RMSE**: 0.0658 - Low prediction error on training data
- **Validation RMSE**: 0.2519 - Good generalization to unseen data
- **Model Architecture**: Neural Network with user/item embeddings

## 📖 Detailed Documentation

<details>
<summary><strong>📋 Business Understanding & Problem Statement</strong></summary>

### Problem Statements

- **Discovery Challenge**: Users struggle to find anime that match their personal preferences among thousands of available titles
- **Relevance Issues**: Existing recommendation systems often provide irrelevant or inaccurate suggestions, leading to user dissatisfaction  
- **Time Inefficiency**: Users spend more time searching for interesting anime than actually watching them

### Goals

- Develop a **rating-based recommendation system** that analyzes user rating data to provide personalized recommendations
- Create a **genre-based recommendation system** using anime genre information for relevant suggestions
- **Combine both approaches** to deliver comprehensive, efficient, and satisfying recommendations

### Solution Approaches

#### 🎭 Content-Based Filtering
- **Method**: Uses anime genre information with TF-IDF vectorization and Cosine Similarity
- **Advantages**: 
  - No need for extensive user data
  - Provides relevant recommendations based on content features
- **Limitations**: 
  - Limited to feature-based similarities
  - Cannot recommend diverse content outside user's previous preferences

#### 👥 Collaborative Filtering  
- **Method**: Neural Network model analyzing user rating patterns
- **Advantages**:
  - Highly personalized and accurate recommendations
  - Can discover new content beyond user's typical preferences
- **Limitations**:
  - Requires substantial user interaction data
  - Cold start problem for new users/items

</details>

<details>
<summary><strong>🔧 Data Preparation & Processing</strong></summary>

### Data Cleaning Steps

1. **Data Type Conversion**: Convert Score, Episodes, Rank columns to appropriate numeric types
2. **Missing Value Handling**: Fill NaN values with appropriate defaults (0 for numeric, 'Unknown' for categorical)
3. **Data Quality**: Remove entries with 'UNKNOWN' genres to ensure recommendation quality

### Feature Engineering

#### TF-IDF Vectorization
```python
# Convert genre text to numerical vectors
tfidf_vectorizer = TfidfVectorizer()
tfidf_matrix = tfidf_vectorizer.fit_transform(anime_genres)
```

#### Cosine Similarity Matrix
```python
# Calculate similarity between anime based on genres
cosine_similarity_matrix = cosine_similarity(tfidf_matrix)
```

### Neural Network Architecture
- **Embedding Layers**: User and item representations in latent space
- **Bias Terms**: Account for user and item-specific preferences
- **Dense Layers**: Learn complex interaction patterns
- **Output**: Predicted rating score (1-10 scale)

</details>

<details>
<summary><strong>🧪 Model Evaluation & Results</strong></summary>

### Content-Based Filtering Evaluation

**Metrics Used**: Precision, Recall, F1-Score on 5,000 random samples

| Metric | Score | Interpretation |
|--------|-------|---------------|
| Precision | 95.02% | 95% of recommendations are relevant |
| Recall | 100% | System finds all relevant items |
| F1-Score | 97.45% | Excellent balance of precision/recall |

### Collaborative Filtering Evaluation

**Metric Used**: Root Mean Squared Error (RMSE)

- **Final Training RMSE**: 0.0658
- **Final Validation RMSE**: 0.2519
- **Performance**: Model shows good predictive accuracy with manageable overfitting

![Training Progress](https://i.ibb.co.com/R3pc7bm/image.png)

*RMSE progression during training showing model convergence*

### Sample Recommendations

**Content-Based Example:**
- **Input**: "Seishun Buta Yarou wa Bunny Girl Senpai no Yume wo Minai" (Drama, Romance, Supernatural)
- **Output**: 5 anime with matching/similar genres

![Content-Based Results](https://i.ibb.co.com/C1h2Wf7/image.png)

**Collaborative Filtering Example:**
- **User**: 11142 (likes Comedy anime)
- **Top anime**: "Ijiranaide, Nagatoro-san" (Comedy)
- **Output**: 10 personalized recommendations based on rating predictions

![Collaborative Results](https://i.ibb.co.com/P5Sm9ZT/image.png)

</details>

## 🤝 Contributing

We welcome contributions to improve the anime recommendation system! Here's how you can help:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/AmazingFeature`)
3. **Commit** your changes (`git commit -m 'Add some AmazingFeature'`)
4. **Push** to the branch (`git push origin feature/AmazingFeature`)
5. **Open** a Pull Request

### Areas for Contribution
- 🔄 Hybrid recommendation algorithms
- 🎨 Web interface development
- 📊 Additional evaluation metrics
- 🌐 API development
- 📚 Documentation improvements

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👨‍💻 Author

**Muh. Wira**
- 🌐 GitHub: [@muhwira27](https://github.com/muhwira27)
- 📧 Email: [muhwira27@example.com](mailto:muhwira27@example.com)
- 🎓 Dicoding Machine Learning Student

---

### 🌟 Acknowledgments

- [Dicoding Indonesia](https://www.dicoding.com/) for the comprehensive Machine Learning curriculum
- [MyAnimeList](https://myanimelist.net/) community for the comprehensive anime database
- [Kaggle](https://www.kaggle.com/) for hosting the dataset

---

<div align="center">
  <sub>Built with ❤️ for the anime community</sub>
</div>
