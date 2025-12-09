# Material Stream Identification System ♻️

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)

## 📌 Project Overview
This project implements an **Automated Material Stream Identification (MSI) System** designed to classify post-consumer waste into specific material categories. The system emphasizes the mastery of the entire ML pipeline: Data Preprocessing, Feature Extraction, Classifier Training, and Performance Evaluation.

The solution includes a comparative analysis between **Support Vector Machines (SVM)** and **k-Nearest Neighbors (k-NN)**, and features a deployment module for real-time classification using a live camera feed.

## 🎯 Objectives
* **Data Augmentation:** Increase the training dataset size by a minimum of 30% using geometric and color transformations.
* **Feature Extraction:** Convert raw images into 1D numerical feature vectors using distinct descriptors (e.g., HOG, Color Histograms).
* **Robust Classification:** Classify items into 7 categories with a target validation accuracy of **0.85**.
* **Out-of-Distribution Detection:** Implement a rejection mechanism to classify low-confidence or blurred inputs as "Unknown".

## 🗂️ Dataset & Classes
The model classifies input images into the following 7 classes:

| ID | Class | Description |
| :--- | :--- | :--- |
| **0** | **Glass** | Bottles, jars, amorphous solid materials. |
| **1** | **Paper** | Newspapers, office paper, pressed cellulose. |
| **2** | **Cardboard** | Heavy-duty structured material. |
| **3** | **Plastic** | Water bottles, films, organic compounds. |
| **4** | **Metal** | Cans, steel scrap, metallic substances. |
| **5** | **Trash** | Non-recyclable or contaminated waste. |
| **6** | **Unknown** | Out-of-distribution items, blurred inputs, or low-confidence predictions. |

## 🏗️ Project Structure
The project follows a modular **Strategy Pattern** design to allow easy swapping of feature extractors and classifiers.

```text
Materials-Identification-Project/
├── data/
│   ├── raw/                   # Original images (0-Glass, 1-Paper, etc.)
│   └── processed/             # Augmented images  and extracted features
│
├── models/                    # Saved model weights (.pkl/.joblib) 
│   ├── svm_best_model.pkl
│   └── knn_best_model.pkl
│
├── notebooks/                 # Jupyter notebooks for experiments & plotting
│   ├── 01_augmentation_demo.ipynb
│   ├── 02_feature_extraction_comparison.ipynb
│   └── 03_model_evaluation.ipynb
│
├── src/                       # Core Source Code (The Library)
│   ├── __init__.py
│   ├── augmentation.py        # Code to increase dataset size by 30% 
│   ├── features/              # Feature Extraction Strategies 
│   │   ├── __init__.py
│   │   ├── base.py            # Abstract Base Class (Interface)
│   │   ├── hog.py             # Concrete Strategy A
│   │   └── color_hist.py      # Concrete Strategy B
│   ├── classifiers/           # Classification Strategies [cite: 23]
│   │   ├── __init__.py
│   │   ├── base.py            # Abstract Base Class (Interface)
│   │   ├── svm_wrapper.py     # SVM Implementation [cite: 49]
│   │   └── knn_wrapper.py     # k-NN Implementation [cite: 51]
│   └── utils.py               # Helper functions (file loading, resizing)
│
├── deploy.py                  # The real-time camera application 
├── train.py                   # Script to run the full training pipeline
├── requirements.txt           # List of libraries (opencv, sklearn, numpy)
├── README.md                  # Documentation for the Git repo 
└── .gitignore                 # Important: Ignore /data and /models
```

## ⚙️ Installation & Usage
1. Clone the repository:
```bash
git clone [https://github.com/](https://github.com/)[YourUsername]/Material-Stream-Identification.git
cd Material-Stream-Identification
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```
3. Train the models:
```bash
python train.py --model svm --features hog
```

4. Run Real-Time Deployment: To start the live camera classification:
```bash
python deploy.py
```

## 👥 Team Members
[Ziad Ismael]

[Omar Sameh]

[Mohamed Khamis]

[Mohannad ElBendary]

## 📝 Acknowledgment
This project is part of the Machine Learning Course at the Faculty of Computing and Artificial Intelligence, Cairo University (FCAI-CU).