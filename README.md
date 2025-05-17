# K-Means Clustering for Patient Segmentation to Support Healthcare Cost Optimization

## Overview

This project uses k-means clustering to segment patients into two distinct groups based on vitamin D levels, total medical charges, and the interaction between these two variables. The purpose of this segmentation is to explore whether underlying patterns in patient profiles can inform more cost-effective and targeted healthcare delivery strategies. Clustering enables a hospital to examine similarities among patients without requiring labeled outcomes, supporting strategic planning based on shared clinical and financial characteristics.

---

## Project Objectives

- **Primary Goal**: Identify natural groupings among patients using unsupervised learning on selected medical and billing variables.
- **Use Case**: Support hospital decision-making around resource allocation, preventive care prioritization, and treatment planning based on patient segments.
- **Methodology**: Perform data cleaning, feature engineering, and scaling, then apply k-means clustering. Use the elbow method and silhouette scores to determine the optimal number of clusters. Visualize and interpret resulting clusters using PCA.

---

## Research Question

How can patients be grouped based on clinical and cost-related variables such as vitamin D levels and total charges to identify distinct profiles that support more targeted and cost-effective care?

This project explores whether unsupervised clustering can reveal meaningful patient segments that differ in healthcare needs or financial impact, enabling more efficient care planning and resource allocation.
---

## Dataset Summary

The dataset consists of 10,000 anonymized patient records from a hospital system. Features used for clustering include:

- **TotalCharge** – total medical charges for a patient
- **VitD_levels** – measured vitamin D levels
- **Interaction_VitD_Charges** – engineered feature representing the product of vitamin D level and total charge

These attributes were selected for their potential to reflect both patient health and financial burden.

---

## Dataset Summary

The dataset includes over 3,100 rows with features such as medical charges, vitamin D levels, chronic condition flags, and demographic information. This blend of clinical, lifestyle, and financial data enables rich modeling of healthcare trends.

### Sample of the Dataset

| Total Medical Charges ($) | Vitamin D Level (ng/mL) | Days Admitted | Readmitted? | High Blood Pressure | Diabetes | Complication Risk | Annual Income ($) | Age (Years) |
|---------------------------|--------------------------|----------------|--------------|----------------------|----------|--------------------|--------------------|--------------|
| 3726.70                   | 19.14                    | 10.59          | No           | Yes                  | Yes      | Medium             | 86575.93           | 53           |
| 4193.19                   | 18.94                    | 15.13          | No           | Yes                  | No       | High               | 46805.99           | 51           |
| 2434.23                   | 18.06                    | 4.77           | No           | Yes                  | Yes      | Medium             | 14370.14           | 53           |
| 2127.83                   | 16.58                    | 1.71           | No           | No                   | No       | Medium             | 39741.49           | 78           |
| 2113.07                   | 17.44                    | 1.25           | No           | No                   | No       | Low                | 1209.56            | 22           |

---

## Cluster Evaluation

### Elbow Method

![image](https://github.com/user-attachments/assets/f2dd5484-66ef-4480-9192-cd298b8728cc)

The elbow method shows a clear bend at **k = 2**, indicating a natural separation in the data. Inertia drops sharply from k = 1 to k = 2, and then flattens, suggesting minimal gain from additional clusters.

---

### Silhouette Score

![image](https://github.com/user-attachments/assets/eb0d44ea-3a81-4407-8533-a483f8bd8148)

Silhouette scores also confirm that **k = 2** yields the most coherent clustering structure, with the highest average silhouette score of **0.5358**. Scores gradually decline as the number of clusters increases.

---

## Final Clustering Results

After selecting **k = 2**, the k-means algorithm was applied:

- **Cluster 0**: 5,050 patients
- **Cluster 1**: 4,950 patients

### Cluster Centers (Standardized Scale)

```
Cluster 0: [-0.011, -0.937, -0.901]
Cluster 1: [ 0.011,  0.955,  0.919]
```

These values indicate that patients in **Cluster 1** tend to have **higher vitamin D levels, higher total charges, and stronger interaction effects** than those in Cluster 0.

---

## Cluster Visualization

![image](https://github.com/user-attachments/assets/9546a00d-ef53-48d6-a35a-c9e43f243f1b)

PCA was used to reduce the three-dimensional feature space—comprising total charges, vitamin D levels, and their interaction—into two principal components for visualization purposes. This dimensionality reduction preserves the majority of variance in the original data while making it easier to interpret the clustering results visually.

The resulting plot shows that the two clusters are clearly separable in the reduced space, suggesting that the input features capture a meaningful underlying structure in the patient data. This separation supports the idea that distinct patient profiles exist and reinforces the validity of using unsupervised learning in this context.

---

## Interpretation and Insights

- **Cluster 0** contains patients with generally **lower vitamin D levels and lower total medical charges**. This group may represent individuals with less intensive care needs, fewer procedures, or shorter treatment durations. From a resource planning perspective, they could reflect lower-risk or more routine cases.

- **Cluster 1**, on the other hand, is made up of patients with **higher vitamin D levels and higher overall medical costs**. This could point to patients undergoing more frequent testing, specialized treatments, or longer hospital stays. It might also include individuals with chronic conditions requiring ongoing care, even if their vitamin D levels are not deficient.

- The inclusion of the **interaction term (vitamin D × total charges)** proved helpful in distinguishing patients who have both high vitamin D levels and high associated costs. This may indicate more closely monitored or complex cases—patients who are generally healthier in one respect but require higher-cost interventions, possibly for unrelated or comorbid conditions.

Overall, these patterns suggest that even with a limited set of features, it’s possible to uncover meaningful differences in patient profiles. The segmentation hints at differences in care intensity, financial impact, and possibly clinical complexity. To better understand the real-world implications, it would be useful to compare these clusters with known diagnoses, treatment outcomes, or follow-up data. That next step could help validate the clinical relevance of the clusters and guide how such segmentation might be used in decision-making or care planning.

---

## Tools and Technologies

- **Python** – Analysis and scripting
- **Pandas & NumPy** – Data manipulation and cleaning
- **Scikit-learn** – KMeans, preprocessing, PCA, silhouette scoring
- **Matplotlib & Seaborn** – Data visualization

---

## Conclusion

This project grouped patients into two distinct segments using just three features: total medical charges, vitamin D levels, and their interaction. Even with a small set of variables, the clustering revealed clear differences between patient groups that could reflect variations in care needs or treatment complexity.

While we didn’t use any outcome labels or perform supervised learning, the patterns uncovered suggest real potential for applying this approach in healthcare settings. Segmenting patients in this way could help hospitals plan more targeted care, manage resources more efficiently, and better understand patient populations.

Looking ahead, it would be valuable to compare these clusters with real clinical outcomes—like readmission rates or disease progression—to see how meaningful the groupings really are. Adding more features, such as lab results or comorbidity scores, could also sharpen the insights and make the segmentation more actionable in practice.

