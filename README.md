# Phishing URL Detection using Machine Learning

## Description

This project implements a machine learning-based system for detecting phishing URLs. It is an academic project for the Machine Learning Sessional course at MIST (Military Institute of Science and Technology).

The project involves data preprocessing, exploratory data analysis (EDA), feature selection using mutual information, handling class imbalance using different techniques, model training with various algorithms including Logistic Regression, XGBoost, Random Forest, AdaBoost, and Decision Tree, and comprehensive evaluation using cross-validation, confusion matrices, ROC curves, and feature importance analysis.

This implementation is based on a research paper on phishing URL detection using machine learning techniques.

## Main Files

- **FINAL_code.ipynb**: The original Jupyter notebook containing the ML pipeline, but with a data leakage issue (feature selection performed before train-test split).
- **FINAL_code_with_class_imbalance_fix.ipynb**: The improved Jupyter notebook that fixes the ML pipeline by performing train-test split before mutual information feature selection to prevent data leakage, and handles class imbalance using SMOTE, ADASYN, or SMOTE Tomek (selecting the best based on performance).
- **final_dataset.csv**: The dataset used for training and testing the models.
- **A_Machine_Learning_Algorithms_for_Detecting_Phishing.pdf**: The research paper on phishing URL detection.

## Requirements

- Python 3.x
- Libraries: pandas, numpy, matplotlib, seaborn, scikit-learn, xgboost, ydata-profiling, imbalanced-learn

## Installation

1. Ensure Python 3.x is installed.
2. Install the required libraries using pip:
   ```
   pip install pandas numpy matplotlib seaborn scikit-learn xgboost ydata-profiling imbalanced-learn
   ```

## Usage

1. For the original pipeline: Open `FINAL_code.ipynb` in Jupyter Notebook or Jupyter Lab and run the cells.
2. For the improved pipeline: Open `FINAL_code_with_class_imbalance_fix.ipynb` in Jupyter Notebook or Jupyter Lab and run the cells. This version includes imbalance handling and prevents data leakage.

## Results

Both notebooks evaluate multiple models (Logistic Regression, Decision Tree, Random Forest, AdaBoost, XGBoost) and provide visualizations of performance metrics, including accuracy, confusion matrices, ROC curves, and feature importances.

### FINAL_code.ipynb (Original)
- **Cross-Validation Accuracy Distribution**: The boxplot illustrates the distribution of 5-fold cross-validation accuracies for each model. Random Forest achieves the highest median accuracy, followed closely by XGBoost, indicating strong predictive performance. However, the results exhibit relatively high accuracy across all models due to data leakage, as feature selection was performed on the entire dataset before splitting. This leads to overly optimistic estimates of model performance and reduced reliability. Additionally, models like Decision Tree show higher variance, suggesting instability across folds, while Logistic Regression and AdaBoost demonstrate more consistent but comparatively lower performance. Overall, although Random Forest appears to be the best model in this setup, the evaluation is biased and may not reflect true generalization ability.

### FINAL_code_with_class_imbalance_fix.ipynb (Improved)
- **Key Improvements**: Prevents data leakage by splitting data first, selects top 24 features via mutual information on training data, and applies the best class imbalance technique (SMOTE Tomek) based on test accuracy comparison.
- **Cross-Validation Accuracy Distribution**: The boxplot on the resampled training data provides a more realistic and unbiased estimate of model performance. Compared to the original setup, the accuracy scores are slightly lower but more consistent, indicating better generalization. Random Forest achieves the highest median accuracy with a tight distribution, demonstrating both strong performance and stability across folds. XGBoost follows closely as the second-best model, while Decision Tree shows comparatively higher variance, suggesting less stable performance. Logistic Regression and AdaBoost remain consistent but underperform relative to ensemble methods.

Overall, the improved notebook yields more reliable and generalizable results, with Random Forest as the top-performing model in both files.

## Academic Information

This is a project submitted for the Machine Learning Sessional course at MIST University.

## License

This project is for academic purposes.