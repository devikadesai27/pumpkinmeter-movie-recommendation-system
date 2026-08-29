# 🎬 PumpkinMeter Movie Recommendation System

A scalable movie recommendation system built using **Apache Spark, PySpark, and Alternating Least Squares (ALS)** to generate personalized movie recommendations from large-scale user rating data.

The project demonstrates how distributed data processing and collaborative filtering can be used to analyze user preferences, generate personalized recommendations, and support content discovery.

---

## 🎯 Project Objective

The goal of PumpkinMeter was to develop a scalable recommendation system capable of:

- Processing large-scale movie rating data using Apache Spark
- Identifying patterns in user preferences
- Generating personalized movie recommendations
- Evaluating recommendation performance using RMSE
- Comparing recommendation diversity under different movie-rating thresholds
- Translating recommendation results into meaningful business insights

---

## 📊 Dataset

This project uses the **MovieLens Dataset** provided by **GroupLens Research at the University of Minnesota**.

Two versions of the MovieLens dataset were used:

- **ml-latest-small** — used for ALS model testing and parameter tuning
- **ml-latest (Full Dataset)** — used for final recommendation generation

The full dataset contains approximately:

- **33.8 million ratings**
- **330,000+ users**
- **86,000+ movies**

### Raw Data Source

The original MovieLens datasets can be accessed from:

**GroupLens MovieLens Datasets:**  
https://grouplens.org/datasets/movielens/

> **Note:** The raw datasets are not included in this repository due to their size. They can be downloaded directly from GroupLens.

---

## 🛠️ Technologies & Tools

- **Python**
- **PySpark**
- **Apache Spark**
- **Spark RDDs**
- **Spark MLlib**
- **Alternating Least Squares (ALS)**
- **Jupyter Notebook**

---

## 🔄 Project Workflow

### 1. Data Preparation

The MovieLens datasets were loaded and processed using Apache Spark.

Key preparation steps included:

- Loading movie ratings and movie information
- Parsing CSV files
- Transforming rating data into Spark RDD format
- Filtering movie-rating records
- Preparing movie and rating datasets for recommendation modeling
- Caching data to improve processing performance

Spark RDD transformations used throughout the analysis included:

- `map()`
- `filter()`
- `reduceByKey()`
- `join()`
- `union()`
- `sortBy()`
- `cache()`

### 2. Model Development & Evaluation

The recommendation engine was developed using **Spark MLlib's Alternating Least Squares (ALS)** collaborative filtering algorithm.

The smaller MovieLens dataset was divided into:

- Training data
- Validation data
- Test data

Multiple ALS parameter combinations were evaluated, and **Root Mean Squared Error (RMSE)** was used to compare model performance.

The selected model parameters were:

| Parameter | Value |
|---|---:|
| Rank | 8 |
| Iterations | 10 |
| Regularization | 0.1 |
| Seed | 5 |

The selected model was then applied to the full MovieLens dataset for recommendation generation.

### 3. Recommendation Scenarios

Two movie filtering thresholds were evaluated to understand how minimum rating counts influence recommendation results:

**Scenario 1 — 25+ Ratings**

Movies with at least 25 ratings were considered for recommendation generation.

**Scenario 2 — 100+ Ratings**

Movies with at least 100 ratings were considered for recommendation generation.

The two scenarios were compared to examine the trade-off between **recommendation diversity and movie popularity**.

### 4. Personalized Recommendations

Two different user profiles were created with different movie preferences.

The ALS model generated personalized recommendations for each user under both rating-threshold scenarios.

This resulted in four recommendation cases:

- User 1 → 25+ rating threshold
- User 1 → 100+ rating threshold
- User 2 → 25+ rating threshold
- User 2 → 100+ rating threshold

---

## 🔍 Key Insights

The analysis produced several important findings:

- The recommendation system generated different movie recommendations based on individual user preferences.
- The **25+ rating threshold produced more diverse recommendations**, including niche and lesser-known movies.
- The **100+ rating threshold favored more popular and widely rated movies**.
- Several movies appeared across multiple scenarios, indicating that ALS consistently identified strong user-content matches.
- Collaborative filtering successfully learned stable preference patterns from user rating behavior.
- Apache Spark enabled recommendation generation using the full MovieLens dataset containing **33.8 million ratings**.

---

## 💼 Business Applications

A recommendation system like PumpkinMeter can support streaming and digital entertainment platforms by:

- Delivering personalized content recommendations
- Improving movie and content discovery
- Increasing user engagement
- Supporting customer retention
- Exposing users to relevant niche content
- Balancing recommendation diversity with content popularity
- Supporting data-driven recommendation strategies at scale

The scenario analysis also demonstrates how recommendation-system design choices can influence the type of content presented to users.

---

## 🚀 Future Enhancements

Potential improvements to PumpkinMeter include:

- Incorporating genres, tags, and movie descriptions
- Using implicit feedback such as watch history, clicks, and browsing behavior
- Developing a hybrid recommendation system combining collaborative and content-based filtering
- Reducing popularity bias
- Supporting real-time recommendation updates as new user interactions are generated

---

## 📁 Repository Structure

```text
pumpkinmeter-movie-recommendation-system/
│
├── Scripts/
│   ├── DTC-Pumpkinmeter.ipynb
│   └── DTC-Pumpkinmeter.html
│
├── DTC-Pumpkinmeter.pptx
├── Business Proposal Report.docx
└── README.md
```

### Repository Contents

**Jupyter Notebook (`.ipynb`)**  
Contains the PySpark implementation, data preparation, ALS model development, model evaluation, and recommendation workflow.

**HTML Notebook (`.html`)**  
Provides a rendered version of the notebook for easier viewing of the code, analysis, and outputs.

**Project Presentation (`.pptx`)**  
Summarizes the methodology, recommendation results, key findings, and business implications.

**Business Proposal Report (`.docx`)**  
Provides detailed documentation of the project objectives, technical implementation, results, challenges, and business recommendations.

---

## 📌 Project Highlights

- Processed **33.8 million movie ratings** using Apache Spark
- Worked with data from **330K+ users and 86K+ movies**
- Built a collaborative filtering recommendation system using **Spark MLlib ALS**
- Used Spark RDDs for distributed data processing
- Performed ALS parameter tuning and **RMSE-based model evaluation**
- Generated personalized recommendations for two user profiles
- Compared **25+ and 100+ rating thresholds**
- Identified the trade-off between recommendation diversity and popularity
- Translated technical recommendation results into business insights

---

