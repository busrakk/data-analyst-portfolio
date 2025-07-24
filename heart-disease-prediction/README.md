# Heart Disease Prediction Project

This project aims to predict the presence of heart disease using patient health metrics. The dataset used includes attributes such as age, sex, chest pain type, cholesterol level, and maximum heart rate. The goal is to build and evaluate multiple classification models and select the best-performing one based on validation and test performance.

## 📌 Dataset

- Source: [Kaggle - Heart Disease UCI Dataset](https://www.kaggle.com/datasets/johnsmith88/heart-disease-dataset)
- Target variable: `target` (1 = has heart disease, 0 = does not)

## 🔍 Project Steps

1. **Data Loading and Exploration**: Understand the structure, types, and balance of the dataset.
2. **Preprocessing**:
   - Handled categorical variables using One-Hot Encoding.
   - Checked for and visualized outliers (especially in cholesterol).
3. **Train/Validation/Test Split**: 
   - Used stratified splitting to maintain class balance.
   - 70% train / 15% validation / 15% test.
4. **Model Training**:
   - Tried Logistic Regression, Random Forest, and SVM.
   - Evaluated models using **Accuracy** and **ROC-AUC**.
5. **Model Evaluation**:
   - Best performance achieved by **Random Forest**.
   - Final model tested on the unseen test set.
6. **Model Interpretation**:
   - Plotted feature importance.
   - Generated ROC Curve for the selected model.

## 📊 Results

- **Best Model**: Random Forest Classifier
- **Validation Accuracy**: ~0.88
- **Test Accuracy**: ~0.98
- **ROC-AUC Score**: >0.98
- **Top Features**: `cp_2`, `thalach`, `oldpeak`, `exang_1`, `age`

## 📈 Visuals Included

- Boxplot for outlier detection
- Feature importance bar plot
- ROC Curve of the final model

## 📦 Libraries Used

- `pandas`, `numpy`, `seaborn`, `matplotlib`
- `scikit-learn`

## 🚀 To Run the Project

```bash
git clone https://github.com/yourusername/heart-disease-prediction.git
cd heart-disease-prediction
