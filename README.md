# Airline Traveler Satisfaction Prediction (RapidMiner)

This repository demonstrates a **predictive analytics pipeline** built in RapidMiner to classify airline traveler satisfaction. The workflow includes data exploration, preparation, model training, evaluation, and ensemble improvement.

---

## 📌 Project Overview

- **Objective**: Predict traveler satisfaction from flight experience ratings.
- **Tool Used**: RapidMiner Studio 2024
- **Models**:
  - Decision Tree
  - k-Nearest Neighbors (k-NN)
  - Voting Ensemble (Decision Tree + k-NN)

---

## ⚙️ Workflow Demonstration

### 1. Data Exploration
- Imported traveler review dataset into RapidMiner.
- Compared ratings across cabin classes (Economy, Premium Economy, Business, First).
- Generated correlation matrix heatmap:
  - Strong correlation between **value for money** and **overall rating**.
  - Cabin staff and seat comfort strongly influence satisfaction.

<img width="643" height="458" alt="image" src="https://github.com/user-attachments/assets/37075f3e-b562-4514-ab0e-b1f3c9a6183c" />
<img width="902" height="275" alt="image" src="https://github.com/user-attachments/assets/272024c6-92aa-4e6b-b015-c5c5f85a10b9" />


---

### 2. Data Preparation
- Removed rows with missing values using **Filter Examples**.
- Created new attribute: `Traveler’s Satisfaction.`
  - `Satisfied` if overall rating > 5  
  - `Dissatisfied` if overall rating ≤ 5
- Set `Traveler’s Satisfaction` as the label attribute.

<img width="695" height="355" alt="image" src="https://github.com/user-attachments/assets/3008e044-1754-447b-917c-d8e2922847dc" />

---

### 3. Predictive Modeling
- **Decision Tree**:
  - Split data: 70% training, 30% testing.
  - Max depth = 5 to avoid overfitting.
  - Key predictor: **value for money rating**.
- **k-NN**:
  - k = 5, weighted voting.
  - Classified satisfaction based on 6 features.

**Performance Comparison:**

| Metric       | Decision Tree | k-NN   |
|--------------|---------------|--------|
| Accuracy     | 91.08%        | 90.82% |
| Kappa        | 0.813         | 0.808  |
| Precision (Satisfied) | 92.25% | 92.80% |
| Recall (Satisfied)    | 93.06% | 91.96% |

<img width="899" height="324" alt="image" src="https://github.com/user-attachments/assets/e9465c2c-c649-4b9b-8077-e5dd377c39fe" />
<img width="874" height="336" alt="image" src="https://github.com/user-attachments/assets/416c4d63-d504-4b16-b36e-27694bf843f4" />
<img width="778" height="287" alt="image" src="https://github.com/user-attachments/assets/5a9daf99-0346-4205-a744-ce1375b48834" />

---

### 4. Model Evaluation & Improvement
- Applied **3-fold cross-validation**.
- Built **Voting Ensemble**:
  - Decision Tree (depth 7 & 10)
  - k-NN (k = 10)

**Final Performance:**

| Metric       | Decision Tree | k-NN   | Voting Ensemble |
|--------------|---------------|--------|-----------------|
| Accuracy     | 91.08%        | 90.82% | 91.81%          |
| Kappa        | 0.813         | 0.808  | 0.829           |
| Precision (Satisfied) | 92.25% | 92.80% | 93.63% |
| Recall (Dissatisfied) | 88.03% | 89.07% | 90.34% |

<img width="897" height="264" alt="image" src="https://github.com/user-attachments/assets/e48e126d-07eb-41b9-a7b5-17d9b429e72f" />
<img width="820" height="361" alt="image" src="https://github.com/user-attachments/assets/2a900e6f-1850-4a2c-a1f5-732bfabb0a9a" />

---

## 🚀 How to Run the Pipeline in RapidMiner

1. **Open RapidMiner Studio**.
2. **Import Dataset**:
   - Load traveler review data (Excel/CSV).
3. **Data Preparation**:
   - Use *Filter Examples* to remove missing values.
   - Generate new attribute `Traveler’s Satisfaction`.
   - Set label role for prediction.
4. **Model Training**:
   - Add **Decision Tree** operator (max depth = 5).
   - Add **k-NN** operator (k = 5).
   - Use *Split Data* (70/30) for training/testing.
5. **Model Evaluation**:
   - Apply *Performance (Classification)* operator.
   - Compare accuracy, precision, recall, and Kappa.
6. **Ensemble Improvement**:
   - Add **Voting operator**.
   - Combine Decision Tree (depth 7 & 10) and k-NN (k = 10).
   - Run *Cross Validation* (3 folds).
7. **Results**:
   - View performance metrics in the *Results* panel.
   - Export charts and tables for reporting.

---

## ✅ Recommendations
- Deploy the **Voting Ensemble model** for production use in RapidMiner.
- Continuously retrain with new traveler reviews.
- Use insights to improve cabin staff service, seat comfort, and perceived value for money.


