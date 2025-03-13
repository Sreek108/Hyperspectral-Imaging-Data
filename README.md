# Hyperspectral Imaging for Mycotoxin Prediction

This repository contains code and analysis for predicting DON mycotoxin concentration in corn samples using hyperspectral imaging data.

## Project Overview

Hyperspectral imaging captures information across the electromagnetic spectrum, providing rich data that can be used to detect various properties of agricultural products. This project uses machine learning techniques to:

1. Process and visualize hyperspectral data
2. Perform dimensionality reduction using PCA and t-SNE
3. Train a deep learning model to predict DON concentration
4. Evaluate model performance and provide insights

## Repository Structure

- `hyperspectral_analysis.py`: Main Python script containing all analysis code
- `requirements.txt`: List of required packages
- `report.md`: Technical report detailing methodology and findings
- `README.md`: This file with setup and usage instructions

## Prerequisites

- Python 3.8 or higher
- pip package manager

## Installation

1. Clone this repository:
```bash
git clone https://github.com/yourusername/hyperspectral-mycotoxin-prediction.git
cd hyperspectral-mycotoxin-prediction
```

2. Create a virtual environment (optional but recommended):
```bash
python -m venv venv
source venv/bin/activate  # On Windows, use: venv\Scripts\activate
```

3. Install the required packages:
```bash
pip install -r requirements.txt
```

## Usage

1. Place your hyperspectral dataset in the project directory or update the file path in the script.
   - The script expects a CSV file with spectral bands as columns and samples as rows
   - The target variable (DON concentration) should be included as a column named 'DON' or 'don'

2. Run the analysis script:
```bash
python hyperspectral_analysis.py
```

3. Alternatively, to run the script as a Jupyter notebook:
```bash
jupyter notebook
```
Then open and run `Hyperspectral_Imaging_Data.ipynb`

## Features

- **Automatic target variable detection**: Script identifies the DON/don column
- **Comprehensive data visualization**:
  - Boxplots for outlier detection
  - Average reflectance across spectral bands
  - Heatmap visualization of spectral data
- **Dimensionality reduction**:
  - PCA with adaptive component selection (95% variance)
  - t-SNE visualization for non-linear patterns
- **Deep learning model**:
  - Two-layer neural network with dropout
  - Training visualization with loss and metrics
  - Performance evaluation using standard regression metrics

## Results

The model achieves:
- Low RMSE (Root Mean Squared Error)
- Strong R² score indicating good fit
- Visualization of actual vs. predicted values shows strong correlation

Detailed results and analysis can be found in the `report.md` file.

## Customization

You can modify the following parameters in the script:
- Neural network architecture (layers, neurons)
- Training parameters (batch size, epochs)
- Test/train split ratio
- PCA variance threshold

## Contact

For questions or feedback, please contact:
- Email: akasreek00@gmail.com
- GitHub: [@Sreek108](https://github.com/Sreek108)
