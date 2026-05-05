# Series Recommendation System

## Project Overview

This project is a **Series Recommendation System** built as part of the CSC 309 Artificial Intelligence course. The system recommends TV series to users based on their watching history and ratings. It uses a technique called **Collaborative Filtering** combined with **Cosine Similarity** to find users with similar taste and suggest series they have not yet watched.

The project was built in two versions:
- A **Python version** that runs in the terminal
- A **Web version** built with HTML, CSS, and JavaScript that runs in any browser

---

## Project Details

| Field | Details |
|---|---|
| Course | CSC 309 — Artificial Intelligence |
| Project Type | Simple Recommendation System |
| Concept | Collaborative Filtering, Cosine Similarity |
| Tools | Python, Pandas, NumPy, HTML, CSS, JavaScript |
| Author | Chidiebube |

---

## How It Works

The system works in three main steps:

### Step 1 — Ratings Table
A table is created where each row represents a user and each column represents a TV series. Each cell contains a rating from 1 to 5 given by that user to that series. A value of 0 means the user has not watched that series yet.

### Step 2 — Cosine Similarity
The system compares every user to every other user using a mathematical formula called Cosine Similarity. This formula measures how similar two users' rating patterns are and returns a score between 0 and 1.

- A score of **1.0** means the two users have identical taste
- A score of **0.0** means they have completely different taste

The formula used is:

```
similarity(A, B) = (A · B) / (||A|| × ||B||)
```

Where:
- `A · B` is the dot product of both users' rating vectors
- `||A||` and `||B||` are the magnitudes of each user's ratings

### Step 3 — Generating Recommendations
For a target user, the system finds all series they have not watched (rating = 0). For each unwatched series, it calculates a predicted score using a weighted average of ratings from similar users. Users with higher similarity scores carry more weight in the calculation. The top 3 series with the highest predicted scores are recommended.

---

## Users and Series in the System

**Users:**
- Ebube
- Jude
- Emma
- Mark
- Chikum
- Adaeze

**Series:**
- Peaky Blinders
- Lucifer
- Breaking Bad
- Game of Thrones
- The Sandman
- Stranger Things
- The Witcher
- Money Heist
- Squid Game
- The Boys

---

## Project Files

```
series-recommender/
│
├── index.html                  # Web version (HTML + CSS + JavaScript)
├── series_recommendation.py    # Python version
└── README.md                   # Project documentation (this file)
```

---

## How to Run — Python Version

### Requirements
Make sure Python is installed along with the required libraries.

```bash
pip install pandas numpy
```

### Run the Program
```bash
python series_recommendation.py
```

### Expected Output
1. The full ratings table showing all users and their ratings
2. The user similarity matrix showing how similar every pair of users is
3. Top 3 recommendations for Ebube, Emma, and Chikum automatically
4. An interactive prompt where you can type any username to get recommendations

---

## How to Run — Web Version

### Option 1 — Open Locally in Chrome
1. Download the `index.html` file
2. Right-click the file
3. Select **Open with → Google Chrome**

### Option 2 — Live Server in VS Code
1. Install the **Live Server** extension in VS Code
2. Open `index.html` in VS Code
3. Right-click inside the file and select **Open with Live Server**

### Option 3 — GitHub Pages (Live Online Link)
1. Upload `index.html` to a GitHub repository
2. Go to **Settings → Pages**
3. Set the branch to `main` and save
4. Your project will be live at: `https://yourusername.github.io/series-recommender`

---

## Web Version Features

- **User Selection** — Click on any user's name to select them
- **Get Recommendations** — Click the button to see the top 3 recommended series with predicted scores and animated score bars
- **Ratings Table** — Full table showing all users and their ratings displayed at the bottom of the page
- **Similarity Matrix** — Full table showing how similar every user is to every other user
- Works completely offline — no internet connection needed after opening

---

## Concepts Used

### Collaborative Filtering
A recommendation technique that makes suggestions based on the behaviour and preferences of other users. It assumes that if two users agree on some series, they are likely to agree on others as well.

There are two types of collaborative filtering:
- **User-Based** (used in this project): Find users similar to the target user and recommend what they liked
- **Item-Based**: Find series similar to what the target user already liked and recommend those

### Cosine Similarity
A mathematical method for measuring similarity between two vectors. In this project, each user's ratings are treated as a vector, and cosine similarity is used to measure the angle between those vectors. A smaller angle means more similar taste.

### User-Item Matrix
A table that organises user ratings in a structured format. It is the foundation of the recommendation system and allows the program to quickly look up how any user rated any series.

### Weighted Average
When calculating the predicted score for an unwatched series, the system uses a weighted average instead of a plain average. This means users who are more similar to the target user have more influence over the predicted score.

---

## Limitations

- **Cold Start Problem**: New users with no ratings cannot receive recommendations because there is no data to compare with other users
- **Small Dataset**: The system uses only 6 users and 10 series. Real-world systems like Netflix have millions of users which makes recommendations significantly more accurate
- **Sparse Data**: If two users have rated very few of the same series, their similarity score may not be reliable
- **No Content Awareness**: The system does not know anything about the series themselves such as genre, cast, or release year. It only works based on human ratings

---

## Sample Output

```
==============================================================
      SERIES RATINGS TABLE (1=Bad, 5=Great, 0=Not Watched)
==============================================================
        Peaky Blinders  Lucifer  Breaking Bad  ...
Ebube              5        4             5
Jude               4        0             5
Emma               0        5             3
Mark               5        3             0
Chikum             0        4             0
Adaeze             3        0             4

==============================================================
      TOP 3 RECOMMENDATIONS FOR: EBUBE
==============================================================
  1. The Sandman          Predicted Score: 4.52
  2. Money Heist          Predicted Score: 4.31
  3. Game of Thrones      Predicted Score: 4.10
```

---

## Technologies Used

| Technology | Purpose |
|---|---|
| Python | Core programming language for the terminal version |
| Pandas | Creating and managing the user-item ratings table |
| NumPy | Mathematical calculations including dot product and magnitude |
| HTML | Structure of the web page |
| CSS | Styling and visual design of the website |
| JavaScript | Recommendation logic and interactivity in the browser |

---

## References

- Collaborative Filtering — [Wikipedia](https://en.wikipedia.org/wiki/Collaborative_filtering)
- Cosine Similarity — [Wikipedia](https://en.wikipedia.org/wiki/Cosine_similarity)
- Pandas Documentation — [pandas.pydata.org](https://pandas.pydata.org)
- NumPy Documentation — [numpy.org](https://numpy.org)
