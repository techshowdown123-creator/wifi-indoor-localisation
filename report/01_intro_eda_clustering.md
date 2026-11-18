**Philem Arjun**

## 1. Introduction and Data

This project uses Wi-Fi signal strength (RSSI) to identify indoor rooms, where GPS is unreliable. The UCI dataset contains 2,000 readings from 7 access points across 4 balanced rooms, with no missing or duplicate values. It was split into 80% training (1,600) and 20% testing (400) using stratified sampling (seed 42).

## 2. Exploratory Data Analysis

Room 2 has strong AP1 and AP4 signals (around -37 dBm), while Room 4 has a strong AP5 signal (around -49 dBm). Room 1 has weak signals, and Room 3 falls in between. AP2 provides little information (ANOVA F = 19), while AP1 and AP4 are highly correlated (r = 0.92).

**Figures:** `eda_hist_per_ap.png`, `eda_box_per_room.png`, `eda_corr_anova.png`, `eda_pairplot.png`

## 3. Unsupervised Learning: K-Means

K-Means was used to group readings without room labels.

| Setting | Silhouette | ARI vs Rooms |
|---|---:|---:|
| K = 2 | 0.338 ± 0.004 | 0.295 ± 0.022 |
| **K = 4 (chosen)** | 0.294 ± 0.001 | **0.820 ± 0.036** |
| K = 4 (raw dBm) | – | 0.881 ± 0.026 |

K = 2 had a higher silhouette score, but K = 4 was chosen because there are four actual rooms and its ARI was much higher. Raw dBm values gave better clustering than scaled values.

**Figure:** `kmeans_elbow_silhouette_ari.png`
