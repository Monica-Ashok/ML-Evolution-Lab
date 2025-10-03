# Automated Diabetic Retinopathy Screening Proof-of-Concept (PoC)

# Introduction and Business Rationale

## 1. Project Overview & Business Rationale

### 1.1. Project Overview
This document outlines the objectives, methodology, and expected outcomes for a technical **proof-of-concept (PoC)** aimed at developing a deep learning model for the **automated detection and classification of Diabetic Retinopathy (DR)**. The model will analyze retinal fundus images and classify them into one of five severity grades, from "No DR" to "Proliferative DR."

### 1.2. Business Problem & Opportunity
As a Senior Business Analyst for our Medical Imaging product suite, I've identified a critical bottleneck in the ophthalmic care pathway. Diabetic Retinopathy is a leading cause of preventable blindness worldwide, and early detection through regular screening is paramount. 

However, the current screening process relies on **manual** interpretation of retinal images by highly trained ophthalmologists—a resource that is both scarce and costly. This creates significant delays in diagnosis, increases healthcare costs, and limits the accessibility of screening in underserved regions.

This PoC addresses a clear market opportunity: **to leverage Artificial Intelligence to augment the screening process**. An automated DR classification tool, integrated into our existing imaging platform, can serve as a highly efficient "first-pass" analysis. 

It would automatically flag high-risk cases for immediate review by a specialist while confidently identifying healthy cases, thereby optimizing the ophthalmologist's workflow. This would not only enhance clinical efficiency and reduce costs but also democratize access to essential diagnostic services, aligning perfectly with our mission to innovate within the healthcare technology space.

### 1.3. Project Goal
The primary goal of this PoC is to **validate the technical feasibility of using modern CNN architectures to achieve clinically relevant accuracy in DR classification**. 

This project will de-risk the technology and provide the data-driven insights necessary to build a business case for full-scale product development and integration.

## 2. Project Workflow & Methodology
This project followed a systematic, four-phase machine learning workflow, documented in a single, end-to-end Python notebook (`Diabetic_Retinopathy_PoC.py`):

* **Phase 1**: Data Curation: Verified the integrity of the raw dataset, removing corrupted and duplicate images to create a clean metadata file.
* **Phase 2**: Exploratory Data Analysis (EDA): Analyzed the clean dataset to identify key characteristics, most notably a severe class imbalance.
* **Phase 3**: Model Experimentation: Systematically prototyped, trained, and diagnosed multiple model architectures to identify a winning approach.
* **Phase 4**: Final Evaluation & Packaging: Conducted an in-depth evaluation of the best model and packaged it for a final submission.

## 3. Key Findings & The Engineering Journey
This project was a detective story. Our final, successful model was the result of a rigorous, iterative process of diagnosing problems and implementing evidence-based solutions.

### 3.1. EDA Insights: The Class Imbalance Problem
Our initial analysis proved that the dataset was severely imbalanced, with the 'No DR' class representing over 50% of the data. This insight became the guiding principle for our entire modeling strategy.

### 3.2. Model Experimentation: A Tale of Three Architectures
Our core challenge was finding an architecture and strategy that could overcome both the complexity of the medical images and the severe class imbalance.

* Experiment 1: Baseline CNN
  * Result: Failure (Underfitting). The simple, custom-built CNN achieved ~72% accuracy but was not powerful enough to learn the subtle features of the disease.
  * Conclusion: A more powerful, pre-trained architecture was necessary.

* Experiment 2: ResNet50 Fine-Tuning
  * Result: Critical Failure (Domain Mismatch). Despite applying advanced techniques like class weights and a low learning rate, the ResNet50 model failed to learn, with accuracy never rising above random chance.
  * Conclusion: This was a breakthrough insight. We proved that the features ResNet50 learned from everyday objects (ImageNet) were not transferring to our specialized medical task. The architecture itself was a poor fit.

* Experiment 3: DenseNet121 Fine-Tuning (The Winner)
  * Result: Success! The DenseNet121 architecture, combined with our full strategy (class weights, low learning rate, two-stage fine-tuning), successfully learned from the data.
  * Conclusion: DenseNet121 was declared the winning architecture. However, the model showed clear signs of overfitting, which became the final problem to solve.

## 4. Final Model Performance & Evaluation
The final, optimized DenseNet121 model represents the successful culmination of this PoC.

### 4.1. Key Performance Metrics
* **Quadratic Weighted Kappa Score: 0.75**
  * This is the primary metric for this problem. A score of 0.75 indicates a substantial level of agreement with the ground truth, proving the model is making clinically relevant predictions.
* **Accuracy**: ~70%
  * While a respectable score, this metric is misleading due to the class imbalance.

### 4.2. Analysis
The in-depth evaluation revealed a clear picture of the model's capabilities:
* **Strength**: The model is exceptionally good at identifying healthy patients (Class '0'), with precision and recall scores over 90%. This makes it a potentially valuable screening tool.
* **Weakness**: The model's primary weakness is in differentiating between the adjacent, subtle stages of the disease (e.g., telling 'Mild' from 'Moderate'). This is a classic challenge in medical imaging and the primary area for future improvement.

## 5. How to Run This Project
* **Setup**: Ensure you have Python and the necessary libraries installed (tensorflow, pandas, scikit-learn, seaborn, matplotlib, tqdm, pillow).
* **Data**: Download the data from the [Kaggle APTOS 2019 competition](https://www.kaggle.com/competitions/aptos2019-blindness-detection/data) and place the train_images/, test_images/, train.csv, and test.csv files in the same directory as the notebook.
* **Execute Notebook**: Run the [Diabetic_Retinopathy_PoC.py](01_Projects/Diabetic Retinopathy Detection/Data/Diabetic_Retinopathy_PoC.py) notebook from top to bottom. The notebook is fully automated:
  * It will first generate the clean_metadata.csv file.
  * It will then train the final DenseNet121 model, saving the best version as best_model.keras.
  * Finally, it will evaluate the saved model and generate the `submission.csv` file.

## 6. Conclusion & Roadmap for Future Work
### 6.1. Final PoC Verdict
This Proof-of-Concept is a **clear success**. We have proven the technical feasibility of using deep learning for DR classification, identified a winning architecture, and produced a prototype model with a strong performance benchmark.

### 6.2. Roadmap to a Competition-Winning Model (Future Work)
Our analysis shows that our current model, while successful for a PoC, underperforms top-tier competition models (Kappa > 0.93). The following data-driven steps would be necessary to bridge this gap in a "Phase 2" of this project:

* **Implement a Custom Loss Function**: Replace the standard loss function with one that directly optimizes for Quadratic Weighted Kappa (QWK).
* **Advanced Augmentations**: Integrate more powerful libraries like Albumentations.
* **Test-Time Augmentation (TTA)**: Average predictions over multiple augmented versions of each test image.
* **Advanced Learning Rate Schedulers**: Use dynamic schedulers like `ReduceLROnPlateau` for more nuanced fine-tuning.
* **Model Ensembling**: Train several different high-performing models and blend their predictions together.

## 7. Connect & Collaborate
This project was an incredible hands-on learning journey into the real-world challenges of medical image analysis. The process of diagnosing and systematically solving each roadblock—from class imbalance to domain mismatch—was the most valuable part of the experience.

I believe in the power of open collaboration to push the boundaries of what's possible in AI for healthcare. If you found this project insightful, have ideas for improvement, or are interested in collaborating on future challenges, I'd love to connect.

* Follow me on [GitHub](https://github.com/Monica-Ashok)
* Connect on [LinkedIn](https://www.linkedin.com/in/monica-ashokkumar/)

**Let's build the future of medical AI together.**