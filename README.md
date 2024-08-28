# Wasserstein Generative Adversarial Imputation Network (WGAIN)

## Overview

Image inpainting, or image completion, is a crucial computer vision task aimed at restoring missing pixels in an image. This project introduces a novel inpainting model based on the Wasserstein Generative Adversarial Imputation Network (WGAIN). The model is designed to handle various missingness scenarios, including random noise, multiple squares, and a central square, through its generator and critic networks.

## Model Architecture

- **Generator Network:** Utilizes convolutional layers with different dilation rates and skip connections to capture high-resolution features and enhance output quality.
- **Discriminator Network (Critic):** Computes the Wasserstein Distance to evaluate the difference between real and generated image distributions, improving the loss calculation and training process.

## Original Model Training

The model was trained on three distinct missing scenarios:

1. Random noise from a uniform distribution
2. Randomly located multiple squares
3. A large square placed in the center of the image

## Evaluation

Performance is assessed using:

- **Peak Signal-to-Noise Ratio (PSNR)**
- **Structural Similarity Index (SSIM)**

Datasets used for evaluation:

- CelebA Faces

## Practical Experiments for WGAIN Enhancement

### 3.1 Experiment 1: Irregular Mask Evaluation

To test the claim that WGAIN is a universal imputation model, we evaluate the impact of irregular missing masks compared to the geometric shapes used during training.

- **Custom Mask Creation:** A custom binary mask was generated for a cat image to represent 25% missingness. This mask was applied to a batch of images to assess the model's performance with irregular missing regions.
- **Objective:** Compare inpainting results between geometric masks (large center square and multiple squares) and irregular masks.

### 3.2 Irregular Shape Mask for Training -> Dataset Augmentation

Given that irregular masks created artifacts and the multiple square scenario had inefficiencies, we propose using a new approach for training.

- **Revised Mask Construction:** For the CelebA dataset, multiple squares are replaced with four circles and four ellipses. The shapes are constrained to a specific region within the image to create ensure better reconstruction. The overlapping of these circles and ellipses of different shapes and orientations creates bigger irregular shapes and blobs, making it more challenging for the model to reconstruct the image.
- **Objective:** Evaluate if continuous missing regions with irregular shapes improve the model’s handling of both regular and irregular missingness.

For a more detailed explanation and further elaboration, please refer to the [`Jupyter Notebook`](/dlvc_Bidaralli_AbhijithSrinivas.ipynb/)provided with this repository.
