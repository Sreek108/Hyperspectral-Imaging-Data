# Hyperspectral Imaging Analysis for Mycotoxin Prediction
## Technical Report

### 1. Data Preprocessing

#### Steps Implemented
- **Data Loading and Inspection**: The hyperspectral dataset was loaded and inspected for data structure, missing values, and basic statistics.
- **Target Variable Identification**: The script automatically identifies the target variable (DON concentration) by checking for various naming conventions.
- **Feature Selection**: Non-spectral columns like 'hsi_id' were excluded from the feature set to focus only on spectral bands.
- **Outlier Detection**: Early-stage outlier detection was performed using boxplots to visualize the first five spectral bands.
- **Standardization**: All spectral features were standardized using `StandardScaler` to have zero mean and unit variance.

#### Rationale
Standardization was crucial for this dataset because:
1. Hyperspectral bands may have different ranges and scales, which could bias machine learning algorithms toward features with larger magnitudes.
2. Both PCA and neural networks perform better with standardized input features.
3. Standardizing helps in faster convergence during neural network training.

Outlier detection was performed to identify potential data quality issues, as hyperspectral sensors can sometimes produce anomalous readings that need to be addressed.

### 2. Insights from Dimensionality Reduction

#### Principal Component Analysis (PCA)
PCA was implemented with an adaptive approach, retaining enough components to explain 95% of the variance in the data. This resulted in a significant reduction in dimensionality while preserving most of the information.

Key insights:
- The analysis revealed that the spectral data contains considerable redundancy, as expected in hyperspectral imaging where adjacent bands are often highly correlated.
- The visualization of the first two principal components showed a clear relationship with DON concentration, indicating that the reduced representation captures meaningful patterns related to mycotoxin levels.
- The explained variance ratio distribution suggests that most of the relevant information is concentrated in a small subset of the components.

#### t-SNE Visualization
The t-SNE implementation provided complementary insights:
- It revealed local structures and clusters in the data that may not be apparent in linear methods like PCA.
- The visualization showed potential groupings of samples with similar DON concentrations, suggesting that the spectral signatures contain discriminative information for mycotoxin prediction.

Together, these techniques confirmed that the high-dimensional hyperspectral data can be effectively represented in a lower-dimensional space while maintaining its predictive power for mycotoxin concentration.

### 3. Model Selection, Training, and Evaluation

#### Model Architecture
A deep neural network was selected for this regression task with the following structure:
- Input layer matching the dimensionality of the spectral features
- First hidden layer with 128 neurons and ReLU activation
- Dropout layer (rate = 0.2) for regularization
- Second hidden layer with 64 neurons and ReLU activation
- Output layer with a single neuron (for regression)

#### Training Process
The model was trained using:
- Adam optimizer
- Mean Squared Error (MSE) loss function
- 100 epochs with a batch size of 32
- 20% validation split from the training data
- Mean Absolute Error (MAE) as an additional metric during training

The training history indicated:
- Convergence of both training and validation loss
- No significant signs of overfitting, as validation metrics tracked closely with training metrics

#### Evaluation Results
The model was evaluated on the held-out test set with the following metrics:
- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- R² Score

The actual vs. predicted plot showed a strong correlation between predicted and actual DON concentrations, with most points clustering around the ideal prediction line.

### 4. Key Findings and Suggestions for Improvement

#### Key Findings
1. Hyperspectral data contains valuable information for predicting mycotoxin concentration in corn samples.
2. Dimensionality reduction techniques effectively compress the spectral information while preserving predictive power.
3. Deep learning models can learn complex relationships in the data and provide accurate predictions of DON concentration.

#### Suggestions for Improvement
1. **Feature Engineering**: 
   - Consider spectral derivatives or ratios of specific bands known to correlate with mycotoxin presence.
   - Implement band selection techniques to identify the most informative regions of the spectrum.

2. **Advanced Models**:
   - Implement Convolutional Neural Networks (CNNs) that can better capture the sequential nature of spectral data.
   - Explore attention mechanisms or transformers as mentioned in the bonus section of the assignment.
   - Test ensemble methods combining multiple model predictions.

3. **Data Augmentation**:
   - Generate synthetic samples by adding controlled noise to existing spectra.
   - Implement spectral mixing techniques to create additional training examples.

4. **Hyperparameter Optimization**:
   - Perform a more extensive hyperparameter search using techniques like Bayesian optimization.
   - Experiment with different network architectures, varying the number of layers and neurons.

5. **Interpretability**:
   - Implement SHAP values or similar techniques to identify which spectral regions contribute most to the predictions.
   - This could provide valuable insights for future sensor development or data collection protocols.

6. **Streamlit Application**:
   - Develop the suggested Streamlit application for interactive predictions from user-uploaded spectral data.
   - Include visualizations of the spectral data and model explanations to enhance user understanding.


