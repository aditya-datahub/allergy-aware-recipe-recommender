# 🥗 Allergy-Aware Recipe Recommender

A content-based recipe recommendation system that suggests recipes based on the ingredients you want to use, while **filtering out recipes that contain ingredients you're allergic to**.

Built with **TF-IDF vectorization** and **cosine similarity**, with an interactive **Streamlit** web interface.

---

## ✨ Features

- 🔍 **Ingredient-based search** – type an ingredient or keyword (e.g. `apples`, `milk`) and get the most relevant recipes
- 🚫 **Allergy filtering** – exclude recipes containing ingredients you want to avoid
- 🗂️ **Category grouping** – results grouped by category (Desserts, Breakfast & Brunch, Salad, Sides, Drinks, Bread)
- 📊 **Similarity scores** – each recommendation shows how closely it matches your query
- 🖥️ **Streamlit UI** – simple web app to try the recommender in your browser

---

## 🧠 How It Works

1. **Load data** – recipes are read from category text files in `DataFiles/`
2. **Vectorize** – each recipe's ingredient list is converted into a TF-IDF vector
3. **Filter** – recipes containing any of the user's allergens are removed
4. **Match** – the query is vectorized and compared with every recipe using cosine similarity
5. **Recommend** – the top 5 most similar recipes are returned with their category and score

```
User query ──► TF-IDF vector ──► Cosine similarity vs. recipes ──► Top-N results
                                        ▲
                         Allergy filter removes unsafe recipes
```

---

## 📁 Project Structure

```
allergy-aware-recipe-recommender/
├── DataFiles/              # Recipe data (one .txt file per category)
│   ├── Salad.txt
│   ├── Sides.txt
│   ├── Drinks.txt
│   ├── Desserts.txt
│   ├── Breakfast and Brunch.txt
│   └── Bread.txt
├── UI.py                   # Streamlit web app
├── code.ipynb              # Exploration: TF-IDF model, graph & RL experiments, metrics
├── code2.ipynb             # Allergy-aware recommender + evaluation & charts
├── requirements.txt
└── README.md
```

---

## 🚀 Getting Started

### 1. Clone the repository
```bash
git clone https://github.com/aditya-datahub/allergy-aware-recipe-recommender.git
cd allergy-aware-recipe-recommender
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Run the web app
```bash
streamlit run UI.py
```
Then open the link shown in the terminal (usually `http://localhost:8501`).

### 4. Explore the notebooks
```bash
jupyter notebook code2.ipynb
```

---

## 💡 Example

**Allergies:** `chilli powder`
**Query:** `apples`

| Category | Recipe (ingredients) | Score |
|---|---|---|
| Desserts | 1 cup all-purpose flour, 3/4 cup white sugar, 3 eggs, 5 apples… | 0.48 |
| Desserts | 2 apples, 2 tbsp brown sugar, 1 tsp nutmeg, 1 tsp cinnamon… | 0.47 |
| Desserts | 4 apples, 1 cup rolled oats, 1/4 cup brown sugar… | 0.47 |

---

## 🛠️ Tech Stack

- **Python 3.12**
- **scikit-learn** – TF-IDF vectorizer, cosine similarity, metrics
- **Streamlit** – web interface
- **pandas / NumPy** – data handling
- **Matplotlib / NetworkX** – visualizations

---

## ⚠️ Limitations

- Allergy filtering uses simple text matching, so it may miss hidden allergens (e.g. *gluten* in *flour*). **Do not rely on it for medical or safety-critical decisions.**
- TF-IDF matches exact words only, so spelling mistakes (e.g. `flor`) and synonyms aren't recognized.
- Recipes currently contain ingredient lists only, without recipe names or cooking steps.
- The graph-clustering and reinforcement-learning sections in `code.ipynb` are early experiments using sample data.

---

## 🔮 Future Improvements

- [ ] Allergen-to-ingredient mapping (e.g. gluten → flour, wheat, bread)
- [ ] Sentence embeddings (e.g. Sentence-BERT) for typo-tolerant, semantic search
- [ ] Add recipe names, images, and instructions
- [ ] Allergy input in the Streamlit app
- [ ] Evaluation on a hand-labeled set of test queries
- [ ] Deploy on Streamlit Community Cloud

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).

## 👤 Author

**Aditya Sharma** – [@aditya-datahub](https://github.com/aditya-datahub)
