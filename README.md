# Customer Segmentation – Clustering Project

## Project Overview
Customer segmentation is the process of grouping customers based on similar characteristics and behaviors.  
In this project, clustering techniques are used to better understand customer purchasing behavior and enable **targeted marketing strategies**.

The dataset includes **customer, order, and product information**, which is analyzed and transformed into meaningful customer segments using **RFM analysis** and **unsupervised learning algorithms**.

---

## Technologies & Libraries
- **Python**
- **Pandas / NumPy** – data manipulation
- **Matplotlib / Seaborn** – data visualization
- **Scikit-learn** – clustering and preprocessing
- **SQLite** – data storage
- **Yellowbrick** – cluster visualization

---

## Data Understanding
- Dataset shape: **4194 rows × 181 columns**
- Data sources:
  - Customers
  - Orders
  - Products
- High number of missing values handled implicitly by focusing on RFM-related features.

---

## Data Preparation
### Table Separation
The dataset was split into three logical tables:
- `customers`
- `orders`
- `products`

These tables were stored in a **SQLite database** and later merged for analysis.

---

## RFM Analysis
RFM (Recency, Frequency, Monetary) metrics were calculated to represent customer value:

- **Recency**: Days since last purchase  
- **Frequency**: Number of unique orders  
- **Monetary**: Total spending  

```text
Recency  → How recently a customer purchased  
Frequency → How often a customer purchased  
Monetary → How much a customer spent
Only customers with positive monetary values were retained.

---

## Feature Scaling
RFM features were standardized using **StandardScaler** to ensure equal contribution during clustering.

---

## Clustering with K-Means

### Optimal Cluster Selection
- **Elbow Method** used to evaluate inertia (WCSS)
- **Silhouette Score** used to validate clustering quality

Silhouette results showed strong separation:
- Scores ranged from **0.92 – 0.98**
- Optimal cluster count selected as **4**

---

## Final K-Means Model
- **Number of clusters:** 4  
- **Silhouette Score:** ~0.95 (very strong clustering quality)

### Segment Summary

| Segment | Recency | Frequency | Monetary | Customer Count |
|--------|---------|-----------|----------|----------------|
| 0 | Low | Medium | Medium | 215 |
| 1 | Low | Low | Low | 2828 |
| 2 | Low | High | Very High | 10 |
| 3 | Low | Very High | Extremely High | 1 |

---

## Hierarchical Clustering
- **Ward linkage** with Euclidean distance  
- Dendrogram visualization confirms cluster separations and supports K-Means results.

---

## Conclusion
- Customer behavior can be effectively segmented using **RFM + K-Means**
- The model successfully identified:
  - Low-value customers
  - Regular customers
  - High-value and VIP customers
- High silhouette scores indicate **clear and reliable clusters**

This segmentation can be directly used for:
- Personalized marketing campaigns
- Loyalty programs
- Revenue optimization strategies
