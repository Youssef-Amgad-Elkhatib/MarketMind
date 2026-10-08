# MarketMind 🧠📈
**AI-Driven Customer Segmentation & Business Strategy**

MarketMind is an unsupervised machine learning pipeline designed to transform chaotic, high-dimensional marketing data into crystal-clear, actionable buyer personas. By leveraging dimensionality reduction (PCA) and K-Means clustering, this project moves beyond standard demographic sorting to group customers based on pure behavioral and financial vectors.

## 🔗 Project Links
* **Interactive Notebook:** [MarketMind on Kaggle](https://www.kaggle.com/code/youssefamgadelkhatib/marketmind)
* **Dataset:** [Customer Personality Analysis (Kaggle)](https://www.kaggle.com/datasets/imakash3011/customer-personality-analysis)
  
## 🎯 The Objective
Standard clustering algorithms on high-dimensional data often fall into the "Curse of Dimensionality," acting more like anomaly detectors than segmentation tools. The goal of this project was to engineer a robust ML pipeline that forces the algorithm to find balanced, highly distinct marketing tiers that a business can actually build ad campaigns around.

## 💡 Key Business Personas Discovered
The final K-Means model (k=3) successfully divided the customer base into three highly balanced, commercially distinct segments:

*   🍷 **The Educated Wine Parents (Cluster 0 | 865 Customers)**
    *   **Profile:** Middle-class parents ($50,200 median income) with large households. 37% hold PhDs.
    *   **Behavior:** Reliable mid-tier spenders ($425 annually). Their defining trait is dedicating **65% of their entire discretionary budget to wine**.
    *   **Strategy:** Target with bulk wine discounts, subscription boxes, and family-oriented loyalty programs. Do not waste ad spend on premium meats or sweets.

*   🛒 **The Budget Browsers (Cluster 1 | 642 Customers)**
    *   **Profile:** The youngest demographic with the lowest income ($29,878) and a high parent rate (82%).
    *   **Behavior:** Window shoppers with a terrible web-to-purchase ratio (0.29). They spend very little ($104 annually) but surprisingly over-index on entry-level gold/jewelry purchases (22%).
    *   **Strategy:** Minimize ad spend. Ignore promotional campaigns. Target strictly with heavy clearance sales or budget-friendly gift items.

*   🥩 **The Premium DINKs (Cluster 2 | 730 Customers)**
    *   **Profile:** Dual Income, No Kids (or single professionals). Highest median income ($73,263) and smallest household size (1.88). 
    *   **Behavior:** The high-rolling VIPs. They spend exponentially more ($1,260 annually), buy frequently (21 purchases), and have a massive web-to-purchase ratio (1.45) indicating high buying intent.
    *   **Strategy:** Pitch high-margin, premium items (Meat and Wine). They have the highest promotional acceptance rate (89%) and respond exceptionally well to direct marketing.

## 🛠️ Technical Architecture

*   🧹 **Data Cleaning & Feature Engineering:** Handled missing values, engineered the `isParent` flag, and corrected right-skewed financial distributions using `np.log1p` to stabilize variance.
*   ⚖️ **Preprocessing:** Scaled all continuous variables using `StandardScaler` to ensure uniform mathematical weighting.
*   🗜️ **Dimensionality Reduction (PCA):** Compressed 21+ features down to exactly 2 Principal Components (representing Financial Spending and Family Status). This neutralized multicollinearity (e.g., highly correlated income metrics) and bypassed the anomaly-detection trap seen in 21-dimensional space.
*   🧠 **Clustering & Benchmarking:** Evaluated Gaussian Mixture Models (GMM) and Agglomerative Clustering, both of which failed the business test by isolating microscopic groups of outliers (e.g., segments of 31 people). **K-Means** was selected for its rigid centroid boundaries, yielding beautifully balanced segments.
*   🏆 **Evaluation Metrics:** Achieved a **Silhouette Score of 0.4309** and a **Davies-Bouldin Index (DBI) of 0.7986**, representing mathematically dense and highly separated clusters.
