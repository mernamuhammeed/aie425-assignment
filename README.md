# aie425-assignment
Intelligent Recommender Systems Assignment 1
# AIE425 – Intelligent Recommender Systems  
## Assignment 1: Neighborhood CF & Clustering in CF  

**Group Members:**  
- Merna Muhammed – 222101717  
- Shrouq Hesham Salman – 223108628  
- Hajar Mohammed – 222200040  

---

## 📚 Project Overview

This project explores **neighborhood-based collaborative filtering (CF)** and **clustering-based CF** techniques using the **MovieLens-20M dataset**.  

The main objectives are:  
1. Analyze rating statistics, sparsity, and popularity patterns.  
2. Understand the impact of rating bias and long-tail distribution.  
3. Implement user-based and item-based CF with multiple similarity metrics.  
4. Evaluate clustering strategies for CF to improve efficiency and handle cold-start users/items.  

---

## 🗂 Sections Overview

### **Section 1: Statistical Analysis & Popularity**

**Goal:** Understand the dataset structure and distribution before applying CF.  

**Key Steps:**  
- Counted ratings per user and item.  
- Calculated average ratings.  
- Grouped items into popularity bins (G1–G10).  
- Selected target users (U1–U3) and items (lowest-rated) for co-rating analysis.  
- Computed **co-rated users** and **co-rated items**.  
- Applied a threshold (β) for users with ≥30% overlap to identify strong neighbors.  

**Insights:**  
- Sparse matrix globally, but densely connected around popular items.  
- Stricter overlap thresholds drastically reduce strong neighbors.  
- Statistical analysis guides CF design by highlighting key dataset characteristics.  

---

### **Section 2: Matrix Sparsity, Rating Bias & Long-Tail Effects**

**Goal:** Explore patterns affecting CF performance.  

**Matrix Sparsity:**  
- The dataset is ~0.54% dense.  
- Popular movies act as hubs, connecting many users.  

**Rating Bias:**  
- Most ratings concentrate in high-score groups (G8–G10).  
- Users tend to rate items they expect to like → positive rating bias.  

**Long-Tail Popularity:**  
- Few movies receive most ratings; many items receive very few.  
- Popular items improve prediction accuracy; ignoring tail items reduces coverage and novelty.  

**Conclusion:**  
- Dataset is globally sparse but locally dense.  
- Bias and long-tail effects must be considered in CF design.  

---

### **Section 3: Collaborative Filtering & Clustering**

#### Collaborative Filtering Experiments

**Similarity Metrics Tested:**  
- Raw Cosine Similarity  
- Mean-Centered Cosine Similarity  
- Pearson Correlation Coefficient (PCC)  

**Significance Weighting:**  
- Discount Factor (DF) and Discounted Similarity (DS) improve reliability in sparse datasets.  

**Key Findings:**  
- Raw Cosine can be misleading with different rating scales.  
- Mean-centered similarity reduces bias and improves neighbor reliability.  
- PCC detects true agreement/disagreement in preferences.  
- Discounting stabilizes predictions and removes weak overlaps.  

#### Clustering Strategies

| Part | Method | Accuracy | Efficiency | Notes |
|------|--------|---------|------------|-------|
| 1 | Average Rating | Low | High | Fastest; ignores rating patterns |
| 2 | Co-Rating Stats | Medium | High | Handles sparsity; depends on overlap |
| 3 | Full Rating Patterns | High | Medium | Behavior-aware; computationally heavy |
| 4 | Hybrid (Co-Rating + Rating) | Highest | Balanced | Best accuracy and efficiency; robust for real-world use |

#### Cold-Start Handling
- Clustering assigns new users/items to clusters with minimal data.  
- Hybrid clustering (Part 4) performs best, even with few ratings.  
- Guidelines: start with simple features, update incrementally, apply significance weighting.  

**Overall Conclusion:**  
- Clustering improves efficiency and prediction accuracy.  
- Hybrid clustering provides the best trade-off between performance and scalability.  
- Sparsity, bias, and long-tail distributions are mitigated through clustering and proper similarity measures.  

---

## 🗄 Repository Structure

