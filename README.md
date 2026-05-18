# 📚 Book Recommendation Engine using KNN

A machine learning project that recommends books similar to a given title using the **K-Nearest Neighbors** algorithm. Built as part of the [freeCodeCamp Machine Learning with Python](https://www.freecodecamp.org/learn/machine-learning-with-python/) certification.

---

## 🧠 Overview

Given a book title, the engine returns 5 similar books ranked by cosine distance. It is trained on the [Book-Crossings dataset](http://www2.informatik.uni-freiburg.de/~cziegler/BX/), which contains over 1.1 million ratings of 270,000 books by 90,000 users.

---

## 💡 Example

```python
get_recommends("The Queen of the Damned (Vampire Chronicles (Paperback))")
```

```
[
  'The Queen of the Damned (Vampire Chronicles (Paperback))',
  [
    ['Catch 22', 0.79],
    ['The Witching Hour (Lives of the Mayfair Witches)', 0.74],
    ['Interview with the Vampire', 0.73],
    ['The Tale of the Body Thief (Vampire Chronicles (Paperback))', 0.54],
    ['The Vampire Lestat (Vampire Chronicles, Book II)', 0.52]
  ]
]
```

---

## ⚙️ How It Works

1. 👤 **Filter users** with fewer than 200 ratings to ensure statistical significance
2. 🔗 **Merge titles** from the books dataset before filtering (critical — some books span multiple ISBNs)
3. 📖 **Filter books** with fewer than 100 explicit ratings at the title level (not ISBN level)
4. 🔢 **Build a user-book matrix** — rows are book titles, columns are users, values are ratings
5. 🤖 **Train a KNN model** using cosine similarity on the sparse matrix
6. 📊 **Return 5 neighbors** sorted from furthest to closest similarity

---

## 🔑 Key Design Decision

The dataset assigns the same book title to multiple ISBNs (different editions). Filtering by ISBN-level rating count causes valid books to be incorrectly dropped. Filtering at the **title level** after merging solves this and ensures all relevant books survive into the matrix.

---

## 📂 Dataset

| Property | Value |
|---|---|
| 📦 Source | Book-Crossings dataset |
| ⭐ Ratings | 1.1 million (scale 0–10) |
| 📚 Books | 270,000 |
| 👥 Users | 90,000 |
| ✅ After filtering | ~673 books × ~888 users |

---

## 🛠️ Tech Stack

- 🐍 Python
- 🐼 pandas, NumPy
- 🤖 scikit-learn (`NearestNeighbors`)
- 🔬 SciPy (`csr_matrix`)
- ☁️ Google Colaboratory

---

## 🚀 Usage

Open the notebook in Google Colab and run all cells:

```python
get_recommends("Where the Heart Is (Oprah's Book Club (Paperback))")
```

```
[
  "Where the Heart Is (Oprah's Book Club (Paperback))",
  [
    ["I'll Be Seeing You", 0.8],
    ['The Weight of Water', 0.77],
    ['The Surgeon', 0.77],
    ['I Know This Much Is True', 0.77],
    ...
  ]
]
```

---

## ✅ Test Result

```
You passed the challenge! 🎉🎉🎉🎉🎉
```

---

## 👨‍💻 Author

**Yasandu Kethmika**  
Undergraduate
B.Sc.(Hons) Computer Science & Engineering 
University of Moratuwa
