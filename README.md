# Wafer Defect Detection using Deep Learning (LSWMD)

This repository presents an end-to-end deep learning pipeline for **wafer map defect classification** using the **LSWMD (Large-Scale Wafer Map Dataset)**. The project focuses on realistic challenges such as class imbalance, visually similar defect patterns, and explainability using Grad-CAM.

---

## 📌 Project Highlights
- Dataset: **LSWMD (811,457 wafer maps)**
- Model: **EfficientNetB0 (Transfer Learning + Fine-tuning)**
- Classes used:
  - Center
  - Donut
  - Random
  - Scratch
- Explainability: **Grad-CAM visualization**
- Platform: **Google Colab (Free Tier compatible)**

---

## 🧪 Dataset
LSWMD is a large-scale industrial wafer defect dataset containing labeled wafer maps with severe class imbalance and noisy labels.

Only defect classes with sufficient samples were selected to ensure stable training.

---

## 🏗️ Model Architecture
- Backbone: EfficientNetB0 (ImageNet pretrained)
- Input size: 224 × 224
- Fine-tuned last layers with very low learning rate
- Loss: Categorical Crossentropy
- Optimizer: Adam

Total Parameters: ~4.3M  
Trainable Parameters (Fine-tuned): ~3.4M

---

## 📊 Results Summary

| Class   | Precision | Recall | F1-score |
|--------|-----------|--------|----------|
| Center | 0.95 | 0.17 | 0.27 |
| Donut  | 0.93 | 0.94 | 0.19 |
| Random | 0.94 | 0.88 | 0.91 |
| Scratch| 0.00 | 0.00 | 0.00 |

Overall Accuracy: **~90%**

> ⚠️ Accuracy is not the sole metric due to extreme class imbalance and structural similarity between defect patterns.

---

## 🔍 Explainability with Grad-CAM
Grad-CAM was used to visualize the regions contributing to model predictions.

### Key Observations:
- The model successfully focuses on wafer regions instead of background.
- Global defect patterns (Random, Center) are well learned.
- Thin, directional defects (Scratch) are poorly localized, explaining zero recall.
- Confusion between Center and Donut defects is caused by overlapping spatial patterns.

These observations align with findings reported in prior wafer defect detection literature.

---

## ⚠️ Limitations
- Scratch defects require higher spatial resolution or directional feature modeling.
- Resizing wafer maps reduces fine-grained geometric information.
- Label noise in LSWMD affects boundary-sensitive classes.

---

## 🚀 Future Work
- Directional edge-based preprocessing (Sobel / Canny)
- Multi-scale feature fusion
- Graph-based or transformer-based wafer representations
- Class-conditional attention mechanisms

---

## 📜 License
This project is released under the MIT License.

---

## 🙌 Acknowledgements
LSWMD dataset creators and the open-source deep learning community.

