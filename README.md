# Crack Propagation Model

A **physics-informed Variational Autoencoder (VAE)** that predicts crack growth paths in a glass plate under tensile loading. Combines reconstruction loss, KL divergence, and custom physics constraints so predicted cracks grow realistically from an initial notch.

## Overview

Given an initial notch configuration on a **100 mm × 40 mm** glass plate, the model predicts the final crack pattern. Training uses paired simulation images (initial → final state) with losses designed to respect physical propagation behavior.

## Features

- **Variational Autoencoder** — Image-to-image prediction of crack morphology
- **Physics-informed loss**
  - **Growth constraint** — Crack length does not decrease between input and prediction
  - **Direction constraint** — Penalizes deviation from expected propagation using skeletonization and tip detection
- **Preprocessing pipeline** — Automated border removal and cropping for simulation frames
- **Rich evaluation** — MAE, MSE, SSIM, PSNR, Dice, IoU, and LPIPS

## Tech Stack

| Component | Technology |
|-----------|------------|
| Language | Python 3.x |
| Deep learning | PyTorch, torchvision |
| Vision / metrics | OpenCV, scikit-image, LPIPS |
| Environment | Jupyter Notebook |

## Project Structure

```
Crack-Propogation-Model/
├── Codes.ipynb                  # Preprocessing, training, evaluation
├── requirements.txt
├── best_crack_vae_physics.pth   # Saved model weights
├── Data/
│   ├── input/                   # Initial crack configurations
│   └── output/                  # Ground-truth final states
├── Processed Data/              # Cropped training images
└── README.md
```

## Getting Started

### Prerequisites

- Python 3.8+
- CUDA-capable GPU recommended for training (CPU works for inference at smaller scale)

### Installation

```bash
git clone https://github.com/priyqnk/Crack-Propogation-Model.git
cd Crack-Propogation-Model

pip install -r requirements.txt
```

### Usage

Open and run `Codes.ipynb` in Jupyter Notebook or JupyterLab. The notebook covers:

1. Image preprocessing and dataset loading
2. VAE architecture and physics-informed loss
3. Training loop and checkpointing (`best_crack_vae_physics.pth`)
4. Quantitative evaluation on the test set

## Dataset

| Directory | Contents |
|-----------|----------|
| `Data/input` | Initial notch / crack configuration images |
| `Data/output` | Simulated final crack states (labels) |
| `Processed Data` | Normalized, cropped images used during training |

## Evaluation Metrics

| Metric | Measures |
|--------|----------|
| MAE / MSE | Pixel-level error |
| SSIM / PSNR | Structural and signal fidelity |
| Dice / IoU | Overlap with ground truth |
| LPIPS | Perceptual similarity |
