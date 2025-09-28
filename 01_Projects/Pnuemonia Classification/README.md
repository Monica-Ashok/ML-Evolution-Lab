# 🫁 Chest X-Ray Pneumonia Classification  

This project builds and evaluates a deep learning model to classify chest X-ray images as either **NORMAL** or showing signs of **PNEUMONIA**.  
The workflow leverages **transfer learning** with modern Convolutional Neural Network (CNN) architectures to achieve high-performance results.  

The project is structured into modular notebooks, covering every step from initial data sanitization to final model selection and export.  

---

## 📂 Project Structure  

```
Chest X-Ray Pneumonia Classification/
├── Data/
│   ├── chest_xray/                  # Raw image data (train/val/test splits)
│   └── clean_metadata.csv           # 🧹 Cleaned file paths and labels
├── 01_Preprocess_Revised.ipynb      # 🧼 Data cleaning and metadata generation
├── 02_EDA_Revised.ipynb             # 📊 Exploratory data analysis and strategy
├── 03_Multi_Model_Building_&_Evaluation.ipynb  # 🔬 Training & comparing 3 models
├── 04_Final_Model_and_Export.ipynb  # 🏆 Finalizing and saving the winning model
└── README.md                        # 📖 You are here!
```

---

## 🎯 Project Workflow  

This project follows a complete deep learning workflow, emphasizing **efficiency, reproducibility, and best practices for medical imaging.**  

### 1. Preprocessing ✅  
- Scanned the directory structure to compile a list of all image file paths, their labels (NORMAL/PNEUMONIA), and their dataset split (train/val/test).  
- Ensured data integrity by verifying that every image file was readable and not corrupted, using the **Pillow** library.  
- Implemented **MD5 hashing** to generate a unique signature for each image, allowing for the detection and removal of exact duplicates.  
- Adopted a memory-efficient strategy by not loading image arrays into memory. Instead, the final output of this stage is a **clean_metadata.csv** file, which acts as a reliable map to the image files.  

👉 This foundational step guarantees a clean, verified, and scalable dataset ready for analysis and modeling.  

---

### 2. Exploratory Data Analysis (EDA) ✅  
- Analyzed the **class distribution** across splits, identifying a severe imbalance (significantly more PNEUMONIA images than NORMAL).  
- Formulated a strategy to counteract imbalance by calculating **class weights**, penalizing the model more for misclassifying the minority class.  
- Visualized the **planned data augmentation strategy** (rotation, zoom, shifts) on sample images to confirm transformations were medically reasonable.  
- Inspected random samples from both classes to visually confirm data quality and labeling consistency.  

👉 The EDA provided **critical insights** that directly informed our model training strategy, particularly in handling class imbalance.  

---

### 3. Model Experimentation ✅  
Built and trained **three powerful, pre-trained CNN architectures** using transfer learning:  

- **MobileNetV2** → Fast and efficient baseline  
- **VGG16** → Classic, well-understood architecture  
- **DenseNet121** → State-of-the-art for medical imaging  

Key steps:  
- Used **real-time data augmentation** with Keras `ImageDataGenerator` to prevent overfitting.  
- Applied **class weights** to ensure fair learning despite imbalance.  
- Implemented **callbacks** (`EarlyStopping`, `ModelCheckpoint`) to stop training at performance plateau and save the best version.  
- Evaluated rigorously using **Accuracy, AUC, Precision, and Recall**.  

👉 This head-to-head comparison enabled a **data-driven decision** on the best architecture.  

---

### 4. Final Model ✅  
- **MobileNetV2** was selected due to superior overall performance, especially **Recall** (minimizing false negatives is crucial in medical diagnosis).  
- Loaded the **best saved weights** for MobileNetV2 and validated performance on the **hold-out test set**.  
- Saved the finalized model in **`.keras` format**, ensuring architecture, weights, and optimizer state preservation.  
- Provided code and notes on saving with `.pkl`, explaining why it’s **not recommended** for deep learning models.  

---

## 📊 Dataset Information  

- **Name:** Chest X-Ray Images (Pneumonia)  
- **Source:** Kaggle Dataset by Paul Mooney  
- **Content:** 5,863 JPEG images of chest X-rays  
- **Target Classes:**  
  - `0` → NORMAL  
  - `1` → PNEUMONIA  
- **Splits:** Pre-split into train, validation, and test directories  

---

## 🛠️ Tech Stack  

- **Python** 3.9+  

### Libraries:  
- **TensorFlow & Keras** → Model building and training  
- **pandas & numpy** → Data manipulation  
- **seaborn & matplotlib** → Visualizations  
- **scikit-learn** → Evaluation metrics & class weight calculation  
- **Pillow** → Image file verification
