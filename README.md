# 3D Swin-UNETR for Brain Tumor Segmentation (BraTS 2020)

This project implements a **3D Swin-UNETR–style network** for **brain tumor segmentation** on the **BraTS 2020** dataset, built end-to-end in a single Jupyter/Colab notebook.

It covers:

- Automated **dataset download** from Kaggle  
- **3D data loading & preprocessing** (NIfTI volumes)  
- A custom **Swin-UNETR 3D architecture** (windowed self-attention + UNet-like decoder)  
- **Training** with combined Cross-Entropy + Dice loss  
- **Sliding-window inference** over full 3D volumes  
- **Interactive visualization** of input, ground truth, and predictions

---

## 1. Dataset

- **Dataset**: BraTS 2020 Training Set  
- **Source**: Kaggle dataset `awsaf49/brats20-dataset-training-validation`  
- **Format**: 3D NIfTI volumes (`.nii` / `.nii.gz`) with 4 MRI modalities per case:
  - FLAIR, T1, T1ce, T2
- **Labels**: Tumor segmentation masks with labels `{0, 1, 2, 4}` (later remapped to `{0, 1, 2, 3}` for training).

The notebook:

1. Uses `kaggle.json` (Kaggle API token) uploaded in Colab.
2. Configures `/root/.kaggle/kaggle.json`.
3. Downloads and unzips the dataset into:

   ```text
   /content/brats20/BraTS2020_TrainingData/MICCAI_BraTS2020_TrainingData
