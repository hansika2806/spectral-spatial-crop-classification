# 🌾 Spectral–Spatial Hyperspectral Image Classification  
## Hybrid CNN Ensemble with Attention-Based Feature Fusion  
**Dataset: Indian Pines (AVIRIS)**

---

## 📌 Overview

This project presents a **spectral–spatial deep learning framework** for agricultural land-cover classification using hyperspectral remote sensing imagery.

Unlike RGB images (3 channels), hyperspectral images contain ~200 contiguous spectral bands per pixel, enabling fine-grained material discrimination through spectral signatures. However, this high dimensionality introduces challenges such as spectral redundancy, limited labeled samples, and the curse of dimensionality.

To address these challenges, this work proposes a **multi-branch hybrid CNN architecture** integrating:

- 1D Spectral Convolutional Neural Networks  
- 2D Spatial Convolutional Neural Networks  
- 3D Spectral–Spatial Convolutional Networks  
- Attention-based feature fusion  
- Ensemble learning strategy  

The framework is evaluated on the Indian Pines dataset and benchmarked against classical and deep learning baselines.

---

## 🌍 Problem Definition

Given a hyperspectral image cube:

X ∈ ℝ^(H × W × B)

Where:
- H, W = spatial dimensions  
- B ≈ 200 spectral bands  

Each pixel:

xᵢⱼ ∈ ℝ^B

The objective is:

> Perform pixel-wise supervised classification into one of 16 agricultural land-cover classes by leveraging both spectral signatures and spatial context.

This is a high-dimensional, multi-class classification problem under limited labeled data.

---

## 🛰️ Dataset: Indian Pines

- Sensor: AVIRIS  
- Spatial Resolution: 145 × 145 pixels  
- Spectral Bands: ~200 usable bands  
- Classes: 16 agricultural categories  
- Region: Agricultural area in Indiana, USA  

### Key Challenges

- High inter-class spectral similarity  
- Class imbalance  
- Small sample problem  
- Spectral redundancy  
- Hughes phenomenon (curse of dimensionality)  

---

## 🧠 Technical Framework

### 1️⃣ Spectral Feature Learning (1D CNN)

Operates along the spectral dimension to model material-specific reflectance patterns.

f_s = CNN₁ᴰ(x_spectral)

Captures subtle absorption and reflectance characteristics unique to crop types.

---

### 2️⃣ Spatial Feature Learning (2D CNN)

Operates on local spatial patches (e.g., 5×5 neighborhood) to model texture and contextual structure.

f_p = CNN₂ᴰ(x_spatial)

Captures neighborhood dependencies and spatial continuity.

---

### 3️⃣ Joint Spectral–Spatial Learning (3D CNN)

Performs volumetric convolution across spatial and spectral dimensions simultaneously.

f_ss = CNN₃ᴰ(x_patch)

Learns integrated high-level representations.

---

## 🔥 Attention-Based Feature Fusion

Instead of naïve concatenation, extracted features are adaptively weighted:

F = [f_s ; f_p ; f_ss]  
F' = Attention(F)

This allows the network to dynamically emphasize the most informative representation for classification.

---

## 🎯 Classification Layer

Final prediction is obtained using:

- Fully connected layers  
- Softmax activation  

P(y|x) = Softmax(WF' + b)

Loss Function: Cross-Entropy Loss  
Optimizer: Adam  

---

## 📐 Handling the Curse of Dimensionality

Hyperspectral data contains high-dimensional feature spaces relative to available labeled samples. To mitigate overfitting and redundancy:

- Spectral convolution provides implicit dimensionality compression  
- Regularization techniques (dropout, weight decay) are applied  
- Optional PCA-based dimensionality reduction is evaluated  
- Patch-based learning introduces spatial priors  

The impact of dimensionality reduction is analyzed through ablation studies.

---

## 📊 Evaluation Metrics

Performance is evaluated using:

- Overall Accuracy (OA)  
- Average Accuracy (AA)  
- Kappa Coefficient (κ)  
- Per-class accuracy  
- Confusion Matrix  

### Baseline Comparisons

- Support Vector Machine (SVM)  
- 1D CNN (Spectral-only)  
- 2D CNN (Spatial-only)  
- 3D CNN (Joint baseline)  

An ablation study evaluates:
- Contribution of each branch  
- Effectiveness of attention fusion  
- Impact of dimensionality reduction  

---

## 🧮 Theoretical Foundations

This project integrates:

### Linear Algebra
- Tensor representations  
- Convolution as structured matrix multiplication  
- High-dimensional feature embeddings  

### Probability Theory
- Softmax as categorical distribution modeling  
- Cross-entropy as negative log-likelihood  
- Statistical reliability metrics  

### Optimization
- Gradient descent  
- Backpropagation  
- Regularized empirical risk minimization  

---

## 🚀 Applications

- Precision agriculture  
- Crop-type discrimination  
- Vegetation monitoring  
- Environmental change detection  
- Land-use analysis  

---

## 🛠️ Technology Stack

- Python  
- PyTorch  
- NumPy  
- SciPy  
- scikit-learn  
- Matplotlib  
- Google Colab (development)  
- GitHub (version control and reproducibility)  

---

## 📂 Repository Structure

<img width="307" height="387" alt="image" src="https://github.com/user-attachments/assets/6116443f-a137-40d9-90c1-45f22265a162" />

## 🎓 Academic Significance

This project demonstrates:

- High-dimensional data modeling  
- Spectral–spatial representation learning  
- Hybrid deep ensemble design  
- Attention-based fusion mechanisms  
- Robust evaluation under limited supervision  

It bridges remote sensing analytics with modern deep learning methodologies.

---
## Future Improvements

Transformer-based spectral modeling

Graph Convolutional Networks for spatial relations

Semi-supervised learning

Self-supervised pretraining

Domain adaptation for cross-dataset generalization

