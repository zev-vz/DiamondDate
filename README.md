# 💎 Diamond Data Analysis: Predictive Modeling of Luxury Market Pricing

## 🎯 Executive Summary
This project analyzes **R's comprehensive diamonds dataset** to build predictive models for diamond pricing and discover market segmentation patterns. Through extensive exploratory data analysis, clustering, and predictive modeling, I:
- Achieved **98.3% prediction accuracy** with XGBoost modeling (RMSE: $525.69)
- Identified a **Quality Paradox**: Lower-grade cuts command 15-20% higher median prices due to relationship between lower-grade cuts and sides
- Found that a **Three-tier market structure** emerges naturally from unsupervised clustering
- Learned that **Carat size dominates final price** with exponential relationship patterns

## 📊 Dataset Overview
<table>
<tr>
<td><strong>Source</strong></td>
<td>R's built-in diamonds dataset (ggplot2 package)</td>
</tr>
<tr>
<td><strong>Size</strong></td>
<td>53,940 diamond sales, each with 10 attributes</td>
</tr>
<tr>
<td><strong>Price Range</strong></td>
<td>$326 - $18,823 (mean: $3,933)</td>
</tr>
<tr>
<td><strong>⚖Weight Range</strong></td>
<td>0.20 - 5.01 carats (mean: 0.80 carats)</td>
</tr>
</table>

### 🔍 Variable Analysis
| Variable | Type | Distribution | Key Insights |
|----------|------|-------------|--------------|
| **Price** | Continuous | Right-skewed, bimodal | Strong clustering at <$2,500 and ~$5,000 |
| **Carat** | Continuous | Right-skewed | 75% under 1.04 carats, exponential price relationship |
| **Cut** | Ordinal | Heavily skewed | 40.0% Ideal, only 3.0% Fair quality |
| **Color** | Ordinal | Semi-uniform | D-J scale, G most common (20.9%) |
| **Clarity** | Ordinal | Multi-modal | SI1 dominates (24.2%), premium grades rare |
| **Depth** | Continuous | Near-normal | Tightly clustered 61-62% (technical precision) |
| **Table** | Continuous | Multi-modal | Multiple peaks suggest cutting standards |
| **X,Y,Z** | Continuous | Size-correlated | Strong linear relationships, few outliers |

---

## 🏆 Key Discoveries

### The Quality Paradox
**Counter-intuitive finding**: Lower quality grades often command higher prices
<div align="center">

| Quality Grade | Median Price | Explanation |
|---------------|--------------|-------------|
| **Fair Cut** | $3,282 | Larger stones compensate for poor craftsmanship |
| **Good Cut** | $3,050 | Size-quality tradeoff in market |
| **Very Good** | $2,648 | Balanced quality-size distribution |
| **Premium** | $3,185 | Marketing premium vs. technical quality |
| **Ideal Cut** | $1,810 | Smaller, precisely cut stones |

</div>

### 📈 Market Segmentation Analysis
**K-means clustering reveals three distinct market tiers:**

<div align="center">

| Cluster | Size | Avg Carat | Avg Price | Market Position |
|---------|------|-----------|-----------|-----------------|
| **Premium** | 13.4% | 1.70 | $12,076 | Luxury/Investment pieces |
| **Mid-Range** | 40.4% | 0.95 | $4,524 | Engagement/Special occasion |
| **Budget** | 46.2% | 0.40 | $1,059 | Fashion/Starter jewelry |

</div>

### 🎯 Predictive Model Performance
**Comprehensive comparison across modeling approaches:**

| Model | R² Score | RMSE | Key Features | Strengths |
|-------|----------|------|--------------|-----------|
| **Linear Regression** | 91.9% | $1,132.74 | carat, cut, color, clarity, x | Interpretable, fast |
| **Random Forest** | 98.2% | $530.53 | All variables | Feature importance, robust |
| **XGBoost** | **98.3%** | **$525.69** | All variables | Best performance, handles non-linearity |

### 🔬 Statistical Deep Dives

**Distribution Characteristics:**
- **Carat**: Strongly right-skewed (mean: 0.798, sd: 0.474) with clear preference points at 0.5, 1.0, 1.5 carats
- **Price**: Right-tailed with bimodal tendencies, suggesting distinct buyer segments
- **Cut Quality**: 65.6% of diamonds are Premium or Ideal grade (quality inflation in market)
- **Color Grades**: More uniform distribution than expected, D-F (colorless) only 41.5% of market

**Relationship Patterns:**
- **Carat vs Price**: Exponential relationship (R² = 0.85 with log transformation)
- **Size Dimensions**: X, Y, Z highly correlated (r > 0.97) enabling dimensional predictions
- **Quality vs Size**: Negative correlation between cut quality and carat weight (-0.14)

---

## ⚙️ Technical Implementation

### 📊 Exploratory Data Analysis
- **Univariate Analysis**: 40+ visualizations across histogram, density, boxplot, and ECDF formats
- **Bivariate Analysis**: Correlation matrices, scatter plots with GAM smoothing, hexbin density plots
- **Categorical Breakdowns**: Faceted distributions, violin plots, and proportional analysis

### 🤖 Machine Learning Pipeline
- **Model Selection**: Best subset selection using AIC/BIC criteria via `regsubsets`
- **Cross-Validation**: 70/30 train-test splits with stratified sampling
- **Hyperparameter Tuning**: Grid search for Random Forest mtry, XGBoost learning rates

### 📈 Clustering Methodology
- **K-Means**: Elbow method optimization (k=3 optimal), scaled features
- **Hierarchical**: Ward's method with Euclidean distance, dendrogram analysis
- **Validation**: Within-cluster sum of squares minimization, silhouette analysis

---

## 🛠️ Repository Structure
```
💎 DiamondDate/
├── Diamond Data.pdf                 #PDF of final report
├── README.md                        #This comprehensive documentation 
└── SourceCode                       #Raw code used to generate report
```

**Technologies**: R, tidyverse, ggplot2, randomForest, xgboost, caret, dbscan, leaps
