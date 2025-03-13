# Hyperspectral-Imaging-Data

---

**REPORT.md**

```markdown
# Short Report

## 1. Preprocessing Steps and Rationale

- **Data Cleaning:**  
  The dataset was loaded and inspected for missing values, outliers, and inconsistencies. Column names were stripped of extra whitespace to ensure proper target variable detection.

- **Feature Selection:**  
  Non-spectral columns (such as an ID column like `hsi_id`) were excluded. The target variable was identified as the DON concentration, defaulting to the last column if not explicitly named.

- **Normalization:**  
  Spectral reflectance features were standardized using `StandardScaler` so that each feature contributes equally, which is important for algorithms sensitive to feature scales.

- **Visualization:**  
  Boxplots, line plots (for average reflectance), and a heatmap were created to explore the data distribution and identify potential anomalies or patterns in the spectral data.

## 2. Insights from Dimensionality Reduction

- **PCA:**  
  By retaining components that explain 95% of the variance, PCA reduced the dimensionality effectively. The explained variance ratio suggests that a few principal components capture most of the information in the spectral features, indicating redundancy.

- **t-SNE:**  
  t-SNE provided a complementary 2D visualization, revealing natural clusters in the high-dimensional spectral data. This insight can help in understanding sample groupings and guiding further feature engineering.

## 3. Model Selection, Training, and Evaluation Details

- **Model Selection:**  
  A simple deep learning model (feedforward neural network) was chosen for its flexibility in capturing non-linear relationships in the data. This model architecture included dropout layers to mitigate overfitting.

- **Training:**  
  The dataset was split into 80% training and 20% testing sets. The model was trained over 100 epochs with a batch size of 32 using the Adam optimizer. Training and validation loss as well as MAE were monitored.

- **Evaluation:**  
  The model's performance was evaluated using regression metrics: Mean Absolute Error (MAE), Root Mean Squared Error (RMSE), and R² Score. An actual vs. predicted scatter plot was used to visually assess prediction accuracy.

## 4. Key Findings and Suggestions for Improvement

- **Key Findings:**
  - A small number of principal components capture the majority of variance, indicating correlated spectral features.
  - The deep learning model provided reasonable predictions, though further optimization could improve performance.

- **Suggestions for Improvement:**
  - **Model Enhancements:** Experiment with more advanced architectures (e.g., CNNs, transformers) that might better capture complex patterns in hyperspectral data.
  - **Hyperparameter Tuning:** Use systematic hyperparameter search techniques (like grid search or random search) for further optimization.
  - **Data Augmentation:** If the dataset is limited, consider augmenting data to improve model robustness.
  - **Feature Engineering:** Investigate domain-specific transformations to derive more meaningful features from the spectral data.

---

This report summarizes the methodology, insights, and potential improvements for your assignment. Adjust details as needed to reflect your experimental findings.
