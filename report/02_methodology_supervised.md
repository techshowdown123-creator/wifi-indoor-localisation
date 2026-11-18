**Dhruv Rangan**

## 5. Methodology

The pipeline used median imputation, StandardScaler and a classifier (scaling was skipped for trees). All steps were fitted inside CV folds to prevent data leakage. Macro-F1 was used because it treats all rooms equally, while accuracy measured overall performance. Models were tuned using 5-fold GridSearchCV and evaluated with nested 5 × 5 cross-validation.

## 6. Supervised Results

| Model | Owner | Best Hyperparameters | Nested-CV Macro-F1 | Test Macro-F1 |
|---|---|---|---:|---:|
| Dummy | Harsh | – | 0.254 ± 0.037 | 0.238 |
| Logistic Regression | Harsh | C = 100 | 0.979 ± 0.011 | 0.983 |
| KNN | Dhruv | k = 5, distance, Manhattan | **0.984 ± 0.004** | **0.990** |
| SVM (RBF) | Dhruv | C = 1, γ = 0.1 | 0.981 ± 0.008 | 0.980 |
| Decision Tree | Harsh | Unpruned, Gini | 0.974 ± 0.007 | 0.973 |
| Random Forest | Yashveer | 200 trees, max_features = 0.5 | 0.981 ± 0.008 | 0.983 |

KNN achieved the highest test score (0.990), but its difference from Random Forest was not significant (0.004 ± 0.006). Most errors occurred between Room 2 and Room 3.

**Figures:** `cv_model_comparison.png`, `cv_confusion_matrices.png`
