# Adversarial Attack-Resistant Steganography for Securing Medical Images

**Author**: Anand B

This project develops an **adversarial attack-resistant steganography system** to secure sensitive medical data within images, preserving diagnostic integrity and confidentiality. Leveraging **Generative Adversarial Networks (GANs)** and **self-generated supervision**, this framework ensures imperceptibility and robust resistance to advanced adversarial attacks and steganalysis techniques.

The core workflows, including testing and reconstruction processes, are implemented and demonstrated using the `testing.ipynb` notebook for reproducibility.

---

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Dataset Preparation](#dataset-preparation)
- [Installation](#installation)
- [Usage](#usage)
- [Workflow (testing.ipynb)](#workflow-testingipynb)
  - [Medical Images](#medical-images)
- [Performance](#performance)
- [Project Applications](#project-applications)
- [Future Enhancements](#future-enhancements)

---

## Introduction

Medical imaging plays a critical role in diagnosis and treatment. Protecting sensitive patient data within these images is paramount, especially in light of growing security threats. Traditional methods like encryption often degrade image quality or fail to withstand advanced detection. This project introduces a novel GAN-based steganographic framework that embeds medical data securely into images, ensuring both robustness and high fidelity.

---

## Features

- **Adversarial Robustness**: Ensures resistance to attacks using adversarial training.
- **Preserved Image Fidelity**: Maintains diagnostic-quality images, critical for healthcare analysis.
- **Notebook-based Workflow**: Simplifies usage and demonstrations with the `testing.ipynb`.
- **Versatile Dataset Handling**: Designed for real-world medical datasets.
- **Efficient Reconstruction**: Accurately retrieves embedded medical data with minimal distortion.

---

## Dataset Preparation

### Medical MRI Dataset

This project uses the **Brain Tumor MRI Dataset** as secret images, which can be downloaded from [Kaggle](https://www.kaggle.com/datasets/masoudnickparvar/brain-tumor-mri-dataset). Organize the dataset as follows:

```bash
datasets/
├── medical_mri
│   ├── train_cover/  # Cover images for training
│   ├── train_message/  # Secret images for training
│   ├── test_cover/  # Cover images for testing
│   ├── test_message/  # Secret images for testing
```

For additional preprocessing, use the provided script:

```
python prepare_data.py --dataset-path ./datasets/medical_mri
```

## Installation

### Environment Setup

1.  Install [Anaconda3](https://www.anaconda.com/products/distribution).
2.  Create a virtual environment and activate it:

```bash
conda create -n stegano-env python=3.8
conda activate stegano-env
```

3.  Install required packages:

```
pip install -r requirements.txt
```

## Usage

The complete workflow for testing and reconstruction is implemented in `testing.ipynb`. Run this notebook to process the medical image dataset and validate the results.

## Workflow (`testing.ipynb`)

The `testing.ipynb` notebook provides a step-by-step workflow for testing and reconstruction, including configurations for medical images.

### Medical Images

1. **Steganographic Image Generation**: Creates a stego image with embedded data.
   ```bash
   !python main.py --phase test --dataset_dir medical_mri --checkpoint_dir ./check/medical --test_dir ./check/medical/test --gpu 0
   ```
2. **Secret Image Reconstruction**: Reconstructs hidden medical data from the stego images.
   `bash
    !python main.py --phase recon --stegano_dir ./check/medical/test/stego --recon_dir ./check/medical/recon --gpu 0 --checkpoint_dir ./check/medical
    `
   Use the notebook to execute workflows interactively and visualize the results.

## Performance

Key metrics evaluated include:

- **Peak Signal-to-Noise Ratio (PSNR)**: Measures quality retention of stego images.
- **Structural Similarity Index (SSIM)**: Assesses visual and structural similarity.
- **Adversarial Robustness**: Analyzes performance against statistical and adversarial attacks.

## Project Applications

- **Healthcare Security**: Protects sensitive patient information in medical imaging.
- **Data Privacy**: Ensures secure data transfer and storage.
- **Robustness**: Resists adversarial attacks and steganalysis.

## Future Enhancements

- Integration with **blockchain** for secure traceability.
- Improved scalability for large datasets.
- Exploration of lightweight models for real-time clinical applications.
