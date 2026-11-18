**Harsh Kumar**

## 4. PCA

The first two principal components explain 72.7% of the variance, while three explain 85.2%. The loadings show each access point's contribution, and the 2-D plot compares actual rooms with K-Means clusters.

**Figures:** `pca_room_vs_cluster.png`, `pca_loadings.png`

## 9. Interpretation

AP1, AP5 and AP4 provide most of the useful information. Correlated access points share importance, explaining why AP4 has lower permutation importance than AP1 despite its high ANOVA score. Feature importance predicts failure impact, with a Spearman correlation of 0.79–0.96.

**Figures:** `interpretation_importance.png`, `decision_tree_top.png`

## 10. Limitations

The study uses one building, one time period and one device. It covers only four rooms, not exact positions. Correlated readings may make CV optimistic. Failures are simulated, and one error changes test accuracy by 0.25%.
