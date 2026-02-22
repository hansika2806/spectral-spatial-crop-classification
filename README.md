🌾 Spectral–Spatial Hyperspectral Image Classification
Hybrid CNN Ensemble with Attention-Based Feature Fusion

Dataset: Indian Pines (AVIRIS)

📌 Overview

This repository implements a spectral–spatial deep learning framework for hyperspectral image (HSI) classification in agricultural remote sensing.

Unlike RGB imagery, hyperspectral images contain hundreds of contiguous spectral bands per pixel, enabling fine-grained material discrimination. However, this high dimensionality introduces challenges such as:

Spectral redundancy

Limited labeled samples

High inter-class similarity

Curse of dimensionality (Hughes phenomenon)

To address these challenges, this project proposes a multi-branch hybrid CNN architecture that integrates spectral, spatial, and joint representations using attention-based feature fusion.

🛰️ Dataset — Indian Pines

Sensor: AVIRIS

Spatial Size: 145 × 145 pixels

Spectral Bands: ~200 usable bands

Classes: 16 agricultural land-cover categories

Region: Agricultural area, Indiana, USA

Key Challenges

High spectral similarity between crop types

Class imbalance

Small sample size

High dimensional feature space

🧠 Proposed Architecture

The model consists of three complementary branches:

1️⃣ Spectral Feature Learning (1D CNN)

Operates along the spectral dimension

Learns material-specific reflectance signatures

Captures fine-grained absorption patterns

2️⃣ Spatial Feature Learning (2D CNN)

Operates on local spatial patches (e.g., 5×5 neighborhood)

Learns texture and contextual dependencies

3️⃣ Joint Spectral–Spatial Learning (3D CNN)

Applies volumetric convolution across spatial and spectral dimensions

Learns integrated representations

🔥 Attention-Based Feature Fusion

Instead of simple concatenation, extracted features from all branches are adaptively weighted using an attention mechanism.

This allows the model to:

Emphasize the most informative feature representation

Suppress redundant information

Improve discriminative performance

🎯 Classification Head

Fully connected layers

Softmax activation

Cross-Entropy Loss

Adam optimizer

The final output is a pixel-wise prediction over 16 land-cover classes.

📐 Handling the Curse of Dimensionality

Hyperspectral data has a large number of spectral bands relative to labeled samples. This project mitigates dimensionality issues using:

Spectral convolution as implicit feature compression

Regularization (dropout, weight decay)

Patch-based spatial priors

Optional PCA-based dimensionality reduction (evaluated via ablation study)

The effect of dimensionality reduction is systematically analyzed.

📊 Evaluation Metrics

Performance is evaluated using:

Overall Accuracy (OA)

Average Accuracy (AA)

Kappa Coefficient (κ)

Per-class Accuracy

Confusion Matrix

Baselines Compared

Support Vector Machine (SVM)

1D CNN (spectral-only)

2D CNN (spatial-only)

3D CNN (joint baseline)

Ablation Study

Contribution of each CNN branch

Effectiveness of attention fusion

Impact of dimensionality reduction

🚀 Applications

Precision agriculture

Crop-type classification

Vegetation monitoring

Land-use mapping

Environmental change detection

🛠️ Technology Stack

Python

PyTorch

NumPy

SciPy

scikit-learn

Matplotlib

Google Colab (development)

GitHub (version control & reproducibility)

📂 Repository Structure
Hyperspectral-Classification/
│
├── data/
├── models/
├── utils/
├── train.py
├── evaluate.py
└── README.md
🎓 Research Contribution

This project demonstrates:

High-dimensional data modeling

Spectral–spatial representation learning

Hybrid deep learning architecture design

Attention-based feature fusion

Robust evaluation under limited supervision

It bridges remote sensing analytics with modern deep learning methodologies.
