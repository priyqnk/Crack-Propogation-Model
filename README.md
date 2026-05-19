# Crack Propagation Prediction using Physics-Informed VAE

This project implements a Variational Autoencoder (VAE) to predict the crack propagation path in a glass plate under tensile loading, incorporating physics-informed loss constraints.

## Project Overview

The goal is to predict the final crack configuration of a 100mm x 40mm glass plate given an initial notch length and location. The model uses a combination of structural similarity (SSIM), KL Divergence, and custom physics losses to ensure realistic crack growth.

### Key Features
- **Variational Autoencoder (VAE)**: Architecture designed for image-to-image prediction of crack paths.
- **Physics-Informed Loss**:
  - **Growth Constraint**: Ensures the crack only grows or remains constant (no shrinkage).
  - **Direction Constraint**: Penalizes deviations from the expected propagation path using skeletonization and crack tip detection.
- **Image Preprocessing**: Automated white-border removal and cropping for simulation data.

## Installation

1. Clone the repository:
   ```bash
   git clone <your-repo-url>
   cd crack-propagation-model
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Usage

The project is contained within a Jupyter Notebook:
- `Codes.ipynb`: Contains the preprocessing pipeline, model architecture, training loop, and evaluation metrics.

## Dataset

The project uses simulation images:
- `Data/input`: Initial configuration images.
- `Data/output`: Final configuration (ground truth) images.
- `Processed Data`: Cropped and preprocessed images used for training.

## Model

The trained model weights are saved in `best_crack_vae_physics.pth`.

## Evaluation Metrics

The model is evaluated using:
- MAE (Mean Absolute Error)
- MSE (Mean Squared Error)
- SSIM (Structural Similarity Index)
- PSNR (Peak Signal-to-Noise Ratio)
- Dice Coefficient & IoU (Intersection over Union)
- LPIPS (Learned Perceptual Image Patch Similarity)
