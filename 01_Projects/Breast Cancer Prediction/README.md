# 🩺 Breast Cancer Classification Project

This project uses the **Wisconsin Breast Cancer Dataset** to build, evaluate, and finalize machine learning models for predicting whether a tumor is **malignant** or **benign**.  

The workflow is structured into **modular steps** — preprocessing, exploratory data analysis (EDA), model experimentation, and final model training.  

---

## 📂 Project Structure

```
Breast Cancer Classification Project  
├── Assets/                       # 📊 Original dataset (untouched)  
├── 01_Preprocess.ipynb           # 🧹 Data preprocessing script  
├── 02_Exploratory_Analysis.ipynb # 🔎 Exploratory Data Analysis  
├── 03_Model_Experiment.ipynb     # 🧪 Model experimentation  
├── 04_Final_Model.ipynb          # 🏆 Final model training & saving     
└── README.md                     # 📖 Project documentation  
```


## 🎯 Project Goals  

This project is designed to guide you through a complete machine learning workflow for breast cancer classification, emphasizing clarity, reproducibility, and best practices. Each stage is modular, allowing for easy updates and experimentation.

1. **Preprocessing** ✅  
  - Imported the **Breast Cancer Wisconsin dataset** directly from scikit-learn, ensuring reproducibility and accessibility.  
  - Conducted a thorough audit of dataset structure, data types, and missing values to establish a reliable data foundation.  
  - Addressed **missing values** using median imputation, preserving statistical integrity, or removed records only when necessary.  
  - Eliminated **duplicate entries** to maintain data quality and prevent bias in downstream analysis.  
  - Standardized **feature names** for consistency (lowercase, underscores), facilitating seamless integration with analysis tools.  
  - Transformed the **target variable** into categorical labels (`malignant` = 0, `benign` = 1) for clarity and compatibility with ML algorithms.  
  - Detected and removed **extreme outliers** (e.g., `mean_radius` above the 99th percentile) to enhance model robustness.  
  - Exported a **fully cleaned dataset**, ready for advanced exploratory analysis and modeling.  

  *This meticulous preprocessing ensures the dataset is accurate, consistent, and primed for professional-grade machine learning workflows.*  


2. **EDA (Exploratory Data Analysis)** ✅  
  - Assessed **class distribution**, confirming a slight imbalance (more benign than malignant), which informs model evaluation strategies.  
  - Generated comprehensive **summary statistics**, including skewness and kurtosis, to characterize feature distributions and identify potential modeling challenges.  
  - Visualized data using **histograms, KDE plots, and violin plots**, revealing feature skewness and clear separation between malignant and benign cases.  
  - Constructed a **correlation heatmap** to uncover multicollinearity among features (notably radius, perimeter, and area), guiding feature selection and engineering.  
  - Analyzed **feature–target relationships**, highlighting concavity, compactness, and symmetry as key predictors for diagnosis.  
  - Performed rigorous **outlier detection** with boxplots and Z-scores, flagging extreme values for careful handling in subsequent modeling.  
  - Applied **Principal Component Analysis (PCA)** for dimensionality reduction, achieving clear visual separation between classes in 2D space and informing feature engineering.  
  - Compared **grouped means by class**, demonstrating that malignant tumors consistently exhibit larger cell measurements than benign ones.  

  *These EDA findings provide actionable insights, validate data quality, and strategically inform feature engineering and model development for robust, interpretable results.*  

2. **Model Experminentation** ✅ 
    - Explored a diverse set of algorithms:  
      - **Logistic Regression** for baseline interpretability  
      - **K-Nearest Neighbors (KNN)** for instance-based learning  
      - **Decision Tree** for transparent, rule-based classification  
      - **Random Forest** for robust ensemble learning  
      - **Gradient Boosting** (XGBoost & LightGBM) for advanced performance  
      - **Support Vector Machines** for margin-based classification  
    - Implemented **stratified cross-validation** to ensure fair model comparison and mitigate class imbalance effects.  
    - Systematically tuned hyperparameters using grid search and randomized search, optimizing for accuracy and generalization.  
    - Assessed models with multiple metrics: **accuracy, precision, recall, F1-score, ROC-AUC**, and confusion matrices for nuanced evaluation.  
    - Visualized **learning curves** and **validation curves** to diagnose overfitting and underfitting.  
    - Investigated **feature importances** and **SHAP values** to interpret model decisions and support transparent ML practices.  
    - Documented all experiments in `03_Model_Experiment.ipynb` for reproducibility and future reference.  

    *This rigorous experimentation phase identified XGBoost and Random Forest as the most reliable and interpretable models for breast cancer classification.*

    4. **Final Model** ✅  
    - Selected **XGBoost** as the final model based on superior validation metrics and interpretability.  
    - Performed **fine-grained hyperparameter tuning** to maximize predictive performance and minimize generalization error.  
    - Evaluated the final model on a **hold-out test set**, reporting comprehensive metrics and calibration plots.  
    - Exported the trained model using `joblib` for seamless deployment.  
      - Provided clear documentation and usage instructions for both technical and non-technical audiences in `04_Final_Model.ipynb`. 

---

## 📊 Dataset Information  

- **Name:** Wisconsin Breast Cancer Dataset  
- **Source:** `scikit-learn.datasets.load_breast_cancer`  
- **Features:**  
  - 30 real-valued features (e.g., mean radius, mean texture, mean area, etc.)  
  - Features are derived from digitized images of breast mass fine needle aspirates, capturing essential characteristics for diagnosis.  
- **Target Classes:**  
  - `0 → malignant`  
  - `1 → benign`  
- **Shape:** ~569 samples × 30 features  

*This dataset is widely used in the ML community and provides a robust foundation for classification tasks.*

---

## 🚀 Current Progress  

- ✅ Preprocessing completed: Data is clean and ready for analysis.  
- ⏳ EDA: Visualizations and insights are in development.  
- ⏳ Model experimentation: Multiple algorithms will be tested soon.  
- ⏳ Final model: Training, evaluation, and deployment are upcoming.

*Progress is tracked step-by-step, ensuring transparency and reproducibility.*

---

## 🛠️ Tech Stack  

- **Python 3.9+**  
- **Libraries:**  
  - `pandas`, `numpy` — Efficient data manipulation and analysis.  
  - `seaborn`, `matplotlib` — High-quality visualizations for EDA.  
  - `scikit-learn` — Comprehensive machine learning toolkit.

*The chosen stack is industry-standard, supporting both rapid prototyping and robust analysis.*

---

## 📌 Next Steps  

### 🆕 v2.0: Interactive Streamlit Demo (Planned)

  - A **Streamlit demo app** will be developed to enable interactive, real-time predictions, allowing users to input features and receive instant diagnostic feedback.
  - This feature will be introduced after learning deployment and web app integration topics.
  - Comprehensive documentation and usage instructions will be included for both technical and non-technical audiences.
  - The upgrade will enhance accessibility and practicality, making the project suitable for real-world diagnostic scenarios.

*This stage delivers a robust, production-ready solution, combining high accuracy with transparency and ease of use for breast cancer diagnosis.*

---

✨ Stay tuned — this project is evolving step by step, mirroring the iterative nature of real-world machine learning workflows. Each update will bring new insights and improvements, making this portfolio a valuable resource for both learning and showcasing ML skills.

