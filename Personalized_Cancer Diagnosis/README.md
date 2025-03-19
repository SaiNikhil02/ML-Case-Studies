# Genetic Mutation Classification - Kaggle Competition

## Overview
This project aims to classify genetic mutations based on clinical evidence (text) using machine learning techniques. The dataset comprises genetic mutations and their associated clinical evidence, linked via an ID field. The challenge is to model clinical evidence to accurately classify mutations into nine distinct categories.

## Dataset Description
The dataset consists of two files:
1. `training_variants.csv` / `test_variants.csv` - Contains information about genetic mutations.
2. `training_text.csv` / `test_text.csv` - Contains clinical evidence (text) that was used to classify the mutations.

Each genetic mutation is linked to a corresponding text entry via the ID field.

## Machine Learning Approach
The approach to this classification task involved the following steps:

### 1. Data Preprocessing
- **Text Processing:** Cleaned text data by removing stopwords, stemming, and tokenizing.
- **Feature Engineering:**
  - One-hot encoding for categorical variables.
  - Response coding for categorical features.
- **Handling Imbalanced Classes:** Used `class_weight='balanced'` to assign appropriate weights.

### 2. Model Training
- **K-Nearest Neighbors (KNN):** Used to capture local similarity patterns.
- **Logistic Regression:** Tuned hyperparameters using cross-validation.
- **Support Vector Machines (SVM):** Implemented with linear kernels.
- **Random Forest Classifier:** Tuned `n_estimators` and `max_depth` to optimize performance.
- **Stacking Classifier:** Combined multiple models using Logistic Regression as a meta-classifier.
- **Voting Classifier:** Implemented soft voting for ensemble learning.

### 3. Model Calibration
To improve probability estimates, models were calibrated using `CalibratedClassifierCV` with the `sigmoid` method.

### 4. Performance Metrics
- **Log Loss:** Evaluated for model performance.
- **Confusion Matrix:** Visualized model errors.
- **Feature Importance Analysis:** Analyzed significant textual and categorical features.

## Results and Findings
- The best-performing model was the Stacking Classifier with Logistic Regression as the meta-classifier.
- Text-based features played a crucial role in improving classification accuracy.
- Random Forest performed well but was outperformed by stacking models.

## Visualizations
### 1. Cross-validation Error for Alpha Tuning
![Cross Validation Error](images/cv_error_plot.png)

### 2. Feature Importance in Random Forest
![Feature Importance](images/feature_importance.png)

### 3. Confusion Matrix for Best Model
![Confusion Matrix](images/confusion_matrix.png)

## Installation & Usage
1. Clone the repository:
   ```sh
   git clone https://github.com/yourusername/genetic-mutation-classification.git
   ```
2. Install dependencies:
   ```sh
   pip install -r requirements.txt
   ```
3. Run the notebook:
   ```sh
   jupyter notebook genetic_mutation_classification.ipynb
   ```

## Conclusion
This project showcases the application of various machine learning models for classifying genetic mutations based on clinical text data. The combination of text processing, feature engineering, and advanced model stacking significantly improved classification performance. Future work can explore deep learning techniques such as LSTMs and Transformers for text analysis.

## References
- Scikit-learn Documentation: [https://scikit-learn.org/](https://scikit-learn.org/)
- Kaggle Competition Link: [https://www.kaggle.com/c/genetic-mutations](https://www.kaggle.com/c/genetic-mutations)

