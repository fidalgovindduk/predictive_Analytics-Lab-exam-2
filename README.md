# Binary Classification with Logistic Regression
## Student-Friendly Exam Study Guide

---

## 📚 Project Overview
This project implements a **binary classification model** using **Logistic Regression** to predict whether a sample belongs to class "Yes" or "No" based on two features.

**Key Learning Objectives:**
- Data Exploration & Visualization
- Data Cleaning & Preprocessing
- Model Training & Evaluation
- Performance Metrics & Interpretation

---

## 📊 Dataset Summary

| Aspect | Value |
|--------|-------|
| **Total Samples** | 999 |
| **Features** | Feature1, Feature2 |
| **Target Classes** | Binary (No, Yes) |
| **Class Distribution** | No: 784 (78.5%), Yes: 215 (21.5%) |
| **Class Imbalance Ratio** | 3.65:1 (No:Yes) |

### Feature Statistics
- **Feature1 Range:** [Min, Max] values provided in EDA
- **Feature2 Range:** Larger scale (~100× Feature1)
- **Correlation with Target:** Both features show positive correlation

---

## 🔧 Project Workflow

### 1. **Data Loading & Exploration (EDA)**
```
Raw Dataset → Data Types Check → Summary Statistics → Missing Values Check
```
**Key Steps:**
- Load CSV file using pandas
- Display basic info (shape, dtypes, describe)
- Check for missing values
- Identify and visualize data distribution

### 2. **Data Cleaning & Preprocessing**
```
Drop Missing Target Values → Remove Outliers → Feature Scaling
```
**Actions Taken:**
- Removed rows where Target is missing (cannot train without labels)
- Used IQR method to detect Feature1 outliers
- Rows after cleaning: 999 → ~990 (exact count depends on outliers)
- **Scaling Method:** StandardScaler (z-score normalization)
  - Formula: `(x - mean) / std`
  - **Why?** Logistic Regression uses gradient descent, which performs better with scaled features

### 3. **Train-Test Split**
```
Data → Stratified 80-20 Split (random_state=42)
```
**Configuration:**
- Test Size: 20%
- Stratification: Ensures class distribution is preserved
- Random State: 42 (reproducibility)

### 4. **Model Training**
```
X_train → [StandardScaler] → Logistic Regression
```
**Model Parameters:**
- Algorithm: Logistic Regression
- C (Regularization): 1.0
- Max Iterations: 1000
- Class Weight: 'balanced' (handles imbalance)
- Learned Coefficients shown in notebook

### 5. **Cross-Validation**
```
5-Fold Stratified Cross-Validation
```
**Results:**
- **CV Accuracy:** ~0.52 ± 0.03
- **CV ROC-AUC:** ~0.53 ± 0.03
- **Significance:** Consistent performance across different data splits

### 6. **Model Evaluation**
Multiple metrics used to assess performance:

#### Test Set Performance
| Metric | Value |
|--------|-------|
| **Accuracy** | 55.50% |
| **Precision (Yes)** | 27% |
| **Recall (Yes)** | 65% |
| **F1-Score (Yes)** | 0.39 |
| **ROC-AUC** | 0.5392 |

#### Confusion Matrix Interpretation
```
                Predicted
           No (0)    Yes (1)
Actual  No    TP        FP
        Yes   FN        TP
```
- **True Positives (TP):** Correctly predicted Yes
- **False Positives (FP):** Incorrectly predicted Yes
- **True Negatives (TN):** Correctly predicted No
- **False Negatives (FN):** Incorrectly predicted No

---

## 📈 Key Metrics Explained (Exam Focus)

### Accuracy
$$\text{Accuracy} = \frac{TP + TN}{TP + TN + FP + FN}$$
- **Meaning:** Percentage of correct predictions
- **Limitation:** Misleading with imbalanced classes

### Precision
$$\text{Precision} = \frac{TP}{TP + FP}$$
- **Meaning:** Of all predicted "Yes," how many are actually "Yes"?
- **Use Case:** When false positives are costly

### Recall (Sensitivity)
$$\text{Recall} = \frac{TP}{TP + FN}$$
- **Meaning:** Of all actual "Yes," how many did we catch?
- **Use Case:** When missing positives is costly (e.g., fraud detection)

### F1-Score
$$F1 = 2 \times \frac{\text{Precision} \times \text{Recall}}{\text{Precision} + \text{Recall}}$$
- **Meaning:** Harmonic mean of Precision and Recall
- **Use:** Balanced evaluation for imbalanced datasets

### ROC-AUC
- **Meaning:** Area Under the ROC Curve
- **Range:** 0 to 1
  - 0.5 = Random classifier
  - 1.0 = Perfect classifier
- **This Model:** 0.5392 (slightly better than random)

---

## 🎯 Model Performance Interpretation

| Aspect | Observation | Implication |
|--------|-------------|-------------|
| **Accuracy: 55.5%** | Moderate | Better than random (50%) but not great |
| **Precision: 27%** | Low | Many false alarms (27 out of 100 "Yes" predictions are wrong) |
| **Recall: 65%** | Good | Catches most actual "Yes" cases (65%) |
| **ROC-AUC: 0.54** | Moderate | Limited discriminative ability |

### What This Means:
✅ **Good at:** Finding positive cases (high recall)
❌ **Bad at:** Precise predictions (low precision)
⚠️ **Overall:** Model performs only slightly better than random guessing

## 📊 Visualizations Generated

| Visualization | Purpose |
|--------------|---------|
| **class_distribution.png** | Shows class counts - identifies imbalance |
| **feature_distributions.png** | Shows Feature1 & Feature2 distribution (histogram + KDE) |
| **boxplots_by_class.png** | Feature distributions split by target class |
| **scatter_by_class.png** | 2D scatter plot with class coloring |
| **correlation_heatmap.png** | Feature-target correlations |
| **decision_boundary.png** | Logistic Regression decision boundary |
| **confusion_matrix.png** | Confusion matrix heatmap |
| **roc_curve.png** | ROC curve for performance visualization |

---

## 🚀 Key Takeaways

1. **Data Quality First:** Cleaning and preprocessing are crucial
2. **Metrics Matter:** Use multiple metrics, not just accuracy
3. **Class Imbalance:** Always check and handle carefully
4. **Validation:** Use cross-validation for robust evaluation
5. **Interpretation:** Understand what each metric tells you
6. **Visualization:** Use plots to gain insights

---

## 📚 Python Libraries Used

| Library | Purpose |
|---------|---------|
| **pandas** | Data loading and manipulation |
| **numpy** | Numerical operations |
| **sklearn** | Machine learning models and metrics |
| **matplotlib & seaborn** | Data visualization |

---

## ✅ Model Summary

**Type:** Binary Classification  
**Algorithm:** Logistic Regression  
**Features:** 2 (Feature1, Feature2)  
**Training Samples:** ~790  
**Test Samples:** ~200  
**Best Metric:** Recall (65% - detects most positive cases)  
**Limitation:** Low precision and moderate ROC-AUC  

---

