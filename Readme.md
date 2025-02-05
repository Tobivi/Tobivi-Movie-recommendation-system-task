# **Movie Recommendation System & Data Analysis**

## **Project Overview**  
This project involves cleaning and analyzing a movie dataset, followed by building a **content-based recommendation system** using **TF-IDF and cosine similarity**. The system suggests similar movies based on **genres, keywords, and overview**, while also factoring in **director match and popularity** for better recommendations.  

---

## **1. Data Cleaning & Preprocessing**  

### **Steps Taken:**  
✅ **Handled Missing Values:**  
   - Filled missing values in key columns (e.g., genres, keywords, overview) with placeholders or empty strings.  
   - Filled `director` as **"Unknown"** if missing.  
   - Replaced missing `popularity` and `revenue` with `0`.  

✅ **Transformed Text Features:**  
   - Converted `genres`, `keywords`, and `spoken_languages` into lists for easy processing.  
   - Merged `overview`, `genres`, and `keywords` into a **"combined_features"** column for similarity calculations.  

✅ **Normalized Numeric Features:**  
   - Converted `budget` and `popularity` into **log-scaled values** to reduce outlier impact.  

---

## **2. Exploratory Data Analysis (EDA)**  

### **Key Insights:**  
📌 **Top 10 Movies by Revenue:**  
   - Expected **blockbusters** like Avatar, Avengers, and Star Wars dominated.  
   - Some movies with **high production budgets** didn’t always translate to high revenue.  

📌 **Vote Average Distribution:**  
   - Most movies had an average rating between **5-8**.  
   - Some lesser-known movies had high ratings but low popularity.  

📌 **Genre & Language Distribution:**  
   - **Drama & Comedy** were the most common genres.  
   - English dominated the dataset, followed by **French and Spanish**.  

📌 **Outliers & Interesting Finds:**  
   - Some movies had **huge budgets ($300M+) but low revenue**, highlighting commercial failures.  
   - Missing budget/revenue values were frequent, requiring imputation or exclusion in some analyses.  

---

## **3. Recommendation System Implementation**  

### **Approach:**  
🔹 **Content-Based Filtering** using **TF-IDF + Cosine Similarity**  
   - Created a text-based similarity matrix using `overview`, `genres`, and `keywords`.  
   - Found **top 10 most similar movies** for a given title.  

🔹 **Hybrid Enhancement**  
   - Added **director matching** to prioritize movies from the same director.  
   - Boosted movies with **higher popularity scores** to favor well-received content.  

---

## **4. Challenges & Improvements**  

🚧 **Challenges Faced:**  
🔹 Some movies had missing **budget/revenue/popularity** values, affecting revenue-based rankings.  
🔹 Certain movies had **identical TF-IDF vectors** (e.g., generic descriptions like "A man finds his purpose"), leading to poor similarity calculations.  
🔹 The dataset contained **multiple formats** for genres (e.g., JSON-like text), requiring parsing and standardization.  

💡 **Future Improvements:**  
🔹 Add **collaborative filtering** (based on user ratings) to improve recommendations.  
🔹 Incorporate **release year** (e.g., suggest newer movies if a user prefers recent releases).  
🔹 Use **deep learning (BERT)** to analyze `overview` text for better understanding of movie themes.  

---

## **5. Example Usage**  

```python
recommend_movies_enhanced("Avatar", df_cleaned, cosine_sim)
