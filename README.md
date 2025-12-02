# DBMS_Project_MongoDB_FSM
This is a project done by our group submitted to Mr Ashok Harnal as part of our course requirements
# 🎮 Steam Marketplace Analytics: Strategic Pricing & User Sentiment

### 📊 Project Overview
This project involves a comprehensive visual analysis of over **40,000 video games** published on the Steam platform. By leveraging **MongoDB Atlas** and **MongoDB Charts**, our team built an interactive dashboard to analyze the relationship between game genres, pricing strategies, and customer satisfaction ratings.

The goal was to determine if "AAA" (high-price) titles consistently outperform budget "Indie" titles in terms of user engagement and review scores.

**🔗 [View Live Interactive Dashboard](https://charts.mongodb.com/charts-steam_project-mbfwbkj/public/dashboards/1a89cbfc-3072-4e47-97ce-46f14c10231f)**

---

### 👥 Group Members
* **Aranya Singh** (ID: 341065)
* **Gursimran Singh** (ID: 341078)
* **Shreya Singh** (ID: 341106)

---

### 🛠️ Technical Stack & Data Source
* **Database:** MongoDB Atlas (Cloud-hosted NoSQL Database)
* **Visualization Tool:** MongoDB Atlas Charts
* **Data Management:** MongoDB Compass
* **Dataset:** [Steam Games Dataset (Kaggle)](https://www.kaggle.com/datasets/fronkongames/steam-games-dataset/data)
* **Data Archive:** [Project Drive Folder](https://drive.google.com/drive/folders/1kVQmAaWeUF7uZq6AnaCnqHQwd5W5sF2q?usp=sharing)

---

### 🧹 Data Cleaning & ETL Process
The raw data from Kaggle required significant transformation to be suitable for visualization. We performed the following operations using MongoDB Aggregation Pipelines and Calculated Fields:

1.  **Type Conversion:** Converted `Price`, `Positive` (reviews), and `Negative` (reviews) from Strings to Integers/Doubles to allow for mathematical aggregation.
2.  **Date Parsing:** Created a `Real_Date` field to convert string timestamps (e.g., "Oct 21, 2008") into ISO Date objects for time-series analysis.
3.  **Array Unwinding:** Transformed the comma-separated `Tags` string into iterable Arrays using `$split` and `$unwind` operations.
4.  **Sentiment Calculation:** Engineered a `Review_Score` field:
    ```javascript
    (Positive / (Positive + Negative)) * 100
    ```
5.  **Noise Filtering:** Implemented intersection logic (`Final_Tags`) to filter out 300+ niche tags (e.g., "Gore", "Nudity", "Software") and focus purely on the Top 5 major genres (Action, Adventure, Indie, RPG, Strategy).

---

### 📈 Key Visualizations & Insights

#### 1. Genre ROI Matrix (Heatmap)
* **Objective:** Identify the "Sweet Spot" for pricing vs. customer value.
* **Analysis:** We mapped specific game tags against pricing tiers ($0–$60).
* **Insight:** The highest concentration of positive reviews (Dark Blue) is found in the **$0–$15 range** for **Indie** and **Strategy** games. Higher-priced Simulation games showed diminishing returns in user satisfaction.

#### 2. The Price-Quality Paradox (Scatter Plot)
* **Objective:** Determine if paying more guarantees a better game.
* **Analysis:** A multi-dimensional scatter plot comparing `Price` (X-axis) vs. `Review_Score` (Y-Axis), sized by `Player_Count`.
* **Insight:** There is a **reverse correlation** in many sectors. Massive "Indie" hits (like *Terraria* or *Hollow Knight*) appear in the top-left quadrant (Low Price, High Score), proving that budget titles frequently outperform expensive "AAA" games in user sentiment.

#### 3. Genre Market Share Evolution (Stacked Area Chart)
* **Objective:** Visualize the historical growth of the industry.
* **Analysis:** A time-series analysis of release volume by genre from 1997 to 2024.
* **Insight:** The chart reveals the **"Indie Boom"** starting in 2014. While "Action" games dominated the early 2000s, Independent developers (Yellow/Orange bands) now account for the vast majority of annual releases, signaling a democratization of game development.

---

### 🏁 Conclusion
Our analysis concludes that the Steam marketplace has shifted from a publisher-dominated model to an open market driven by independent creators. For developers, the data suggests that maintaining a lower price point ($10–$20) significantly increases the probability of achieving a "Very Positive" user rating compared to the risky $60+ price bracket.

---

### 📸 Screenshots

#### 1. Genre ROI Matrix (Heatmap)
*Analyzing the "Sweet Spot" for pricing vs. customer value.*
![Genre ROI Matrix](images/Genre%20ROI%20Matrix_%20Price%20Point%20vs.%20User%20Satisfaction.png)

#### 2. The Price-Quality Paradox (Scatter Plot)
*Comparing Price vs. Review Score, sized by Player Count.*
![Scatter Plot](images/Market%20Valuation%20vs.%20User%20Sentiment.png)

#### 3. Genre Market Share Evolution (Stacked Area Chart)
*Visualizing the rise of Indie & Action games from 1997–2024.*
![Market Share Evolution](images/Genre%20Market%20Share%20Evolution%20(1997–2024).png)
