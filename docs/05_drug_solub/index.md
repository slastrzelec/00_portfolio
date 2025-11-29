# 💊 Drug Solubility Prediction using Machine Learning

## Overview

The **Drug Solubility Prediction Tool** is a comprehensive machine learning application built with Streamlit that predicts aqueous solubility of pharmaceutical compounds. This project combines **cheminformatics** knowledge with modern **machine learning** techniques to solve a real problem in drug development.

Given a drug's chemical structure (SMILES notation), the model predicts how well it will dissolve in water, which is crucial for determining drug bioavailability and efficacy. The model uses Morgan fingerprints (2,048 molecular descriptors) and a Random Forest regressor trained on 1,144 pharmaceutical compounds.

It streamlines the entire workflow from molecular structure input to solubility prediction, eliminating the need for expensive computational chemistry software.

📋 **Some key results from the project:**

## 🎯 Model Performance

| Metric | Value |
|--------|-------|
| **Best Algorithm** | Random Forest |
| **Test R² Score** | 0.6985 (70% variance explained) |
| **Test RMSE** | 1.1459 log(mol/L) |
| **Test MAE** | 0.8599 log(mol/L) |
| **Dataset Size** | 1,144 compounds |
| **Features** | 2,048 Morgan fingerprints |

## 🔬 Feature Engineering

**Morgan Fingerprints** - Circular molecular descriptors that encode:
- Molecular connectivity patterns
- Atomic neighborhoods at different radii
- Specific chemical substructures
- Hydrogen bonding potential

Key insight: Only **6.2% of features (128 out of 2,048)** are needed to explain 80% of model predictions, indicating strong interpretability.

## 📊 Model Comparison

Five different algorithms were tested:

```
Linear Regression      ❌  R² = -0.1372
Ridge Regression       ⚠️  R² =  0.3362
Random Forest          ✅  R² =  0.6985  ← BEST
Gradient Boosting      🟡  R² =  0.6235
SVR                    🟡  R² =  0.6283
```

Random Forest outperforms others by capturing **non-linear relationships** between molecular structure and solubility.

## 💡 Key Features and Workflow

### Data Pipeline
1. **Input**: Drug structure as SMILES notation
2. **Feature Generation**: Convert to Morgan fingerprints (2,048 bits)
3. **Normalization**: StandardScaler for feature consistency
4. **Prediction**: Random Forest model inference
5. **Output**: Solubility value with classification (High/Medium/Low)

### Hyperparameter Optimization
- **Method**: GridSearchCV with 5-fold cross-validation
- **Combinations Tested**: 270 different hyperparameter sets
- **Total Model Fits**: 1,350 (270 × 5 CV folds)
- **Optimization Time**: ~115 seconds
- **Result**: Identified optimal configuration with R² = 0.6985

### Feature Importance Analysis

**Top 10 Most Important Features:**
```
fp_1380: 11.60% ← Most critical molecular fragment
fp_1143:  6.04%
fp_1683:  4.24%
fp_561:   3.24%
fp_1087:  2.84%
fp_352:   2.82%
fp_875:   2.13%
fp_807:   1.96%
fp_519:   1.65%
fp_650:   1.62%
```

These fragments represent specific molecular substructures crucial for water solubility prediction.

## 🧪 Example Predictions

| Drug | log(Solubility) | Category | Solubility (mol/L) |
|------|-----------------|----------|-------------------|
| Aspirin | -2.55 | 🟡 Medium | 2.82e-3 |
| Paracetamol | -1.21 | 🟢 High | 6.17e-2 |
| Caffeine | -1.47 | 🟢 High | 3.39e-2 |
| Ibuprofen | -3.15 | 🔴 Low | 7.08e-4 |

**Solubility Categories:**
- 🟢 **High** (> -1): Very soluble, good bioavailability
- 🟡 **Medium** (-1 to -3): Moderately soluble, may need formulation
- 🔴 **Low** (< -3): Poorly soluble, requires alternatives

## 🛠️ Technical Stack

**Core Libraries:**
- **RDKit** - Molecular structure parsing and fingerprint generation
- **scikit-learn** - Random Forest and ML pipeline
- **pandas/numpy** - Data manipulation and numerical computing
- **Streamlit** - Interactive web application
- **Matplotlib/Seaborn** - Data visualization

**Skills Demonstrated:**
- ✅ Cheminformatics (SMILES, molecular descriptors)
- ✅ Machine Learning (model selection, hyperparameter tuning)
- ✅ Feature Engineering (fingerprint generation, importance analysis)
- ✅ Cross-validation and model evaluation
- ✅ Web application development
- ✅ Data visualization and reporting

## 🌟 Contributions and Impact

**Research Applications:**
- High-throughput drug candidate screening
- Solubility-driven medicinal chemistry optimization
- Virtual compound library filtering
- Machine learning methodology validation

**Educational Value:**
- Integration of chemistry with data science
- Real-world cheminformatics problem solving
- Practical ML model development and deployment
- Interpretable AI in pharmaceutical domain

**Project Outcomes:**
- Successfully trained production-ready model (R² = 0.70)
- Identified key molecular fragments predicting solubility
- Created interactive web application for end-users
- Demonstrated controlled overfitting (24% train-test gap acceptable)
- Validated predictions against known pharmaceutical compounds

## 🔗 Project Links

- **📂 GitHub Repository** - <a href="https://github.com/slastrzelec/05_Drug-Solubility-Prediction-using-Machine-Learning-" target="_blank">View on GitHub</a>
- **🚀 Web App** - <a href="https://drug-solubility-prediction.streamlit.app/" target="_blank">Streamlit App</a>
- **📊 Full Analysis** - See methodology and results sections


---

**Project Status**: ✅ Complete | **Last Updated**: November 2025