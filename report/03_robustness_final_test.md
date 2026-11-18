## **7. Robustness**

We tested how well different machine learning models perform when the Wi-Fi signal becomes weaker or when one access point (router) stops working.

First, we added noise to the Wi-Fi signal readings. When the noise was small (+2 dBm), most models still performed well. However, when the noise increased to +5 dBm, their accuracy decreased.

We also tested what happens when one access point is missing. The results showed that AP5 caused the biggest performance drop for most models, while AP1 had the biggest impact on the Decision Tree model.

Another test involved replacing a missing router's signal value with -100 dBm. This caused problems for Logistic Regression and SVM because the value was outside their normal range. Decision Tree, Random Forest and KNN handled this situation better.

Finally, we trained the models again using only six access points. Their worst-case performance improved to above 0.93. This suggests that if a router stops working, the system should detect the failure and switch to a model trained to work with the remaining access points.

**Figures:**

- `figures/robust_noise.png`
- `robust_ap_failure_heatmaps.png`

**Results:** The detailed results are saved in the CSV files inside the `results` folder.

## **8. Final Test Evaluation**

After completing model training and comparison, we tested the selected model on a separate test dataset that had not been used during training or model selection.

K-Nearest Neighbors (KNN) was selected through nested cross-validation before performing the final test. It achieved a macro-F1 score of **0.990**, making only **4 incorrect predictions out of 400 samples**.

The final test results were very close to the cross-validation results. This shows that the model performs consistently on new, unseen data and that it has not simply memorised the training data.

**Figure:**

\- `figures/test_confusion_matrices.png`