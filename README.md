# Week-4-Assignment-SVM-and-Kernel-Machines
SVM-Based Image Classification for Healthcare Diagnostics This project applies Support Vector Machines (SVMs) to classify medical-like images using HOG features and multiple kernel types (linear, polynomial, RBF). 

****Project Overview**
This project applies Support Vector Machines (SVMs) to classify medical-like images using a proxy dataset. The goal is to prototype an image-based diagnostic classifier that distinguishes between two categories: “benign” and “malignant” skin lesions using the ISIC 2018 Skin Lesion Dataset (publicly available on Kaggle).


****Dataset Source**
- Dataset: ISIC 2018: Skin Lesion Analysis Towards Melanoma Detection
- Source: https://www.kaggle.com/datasets/kmader/skin-cancer-mnist-ham10000
- Classes Used: melanoma (malignant), nevus (benign)
- Total Images Used: 1,000 (500 per class, balanced)
  
**Preprocessing & Feature Extraction**
- Images resized to 128×128, converted to grayscale
- HOG (Histogram of Oriented Gradients) used for feature extraction
- Features standardized using StandardScaler
- Implemented as a scikit-learn Pipeline to prevent data leakage

  
**SVM Models & Kernels**
- Kernels tested: linear, poly (degree=2,3), rbf
- Hyperparameters tuned using GridSearchCV with 5-fold stratified cross-validation
- Parameters searched:
- C: [0.1, 1, 10]
- gamma: ['scale', 0.01, 0.1] (for RBF)
- degree: [2, 3] (for poly)
  
**Evaluation Metrics**
- Test Set Size: 20% (stratified)
- Metrics: Accuracy, Precision, Recall, F1-score (macro), Confusion Matrix, ROC-AUC
- Best Model: RBF kernel with C=10, gamma=0.01
- Test Accuracy: 91.2%
- Macro F1-score: 0.91
- ROC-AUC: 0.94
  
**Key Takeaways**
- HOG features effectively captured edge-based patterns in skin lesions
- RBF kernel outperformed linear and polynomial, capturing non-linear class boundaries
- Class balance was maintained; ROC-AUC was critical due to healthcare implications
  
**Limitations & Next Steps**
- Dataset size is small; results may not generalize
- Only 2D features used; future work could explore CNNs or deep embeddings
- Consider calibration for probability outputs and threshold tuning for clinical use
