# Project 6: Autoencoder for Fashion-MNIST

## 🔹 Project Overview

This project implements an **Autoencoder** using **PyTorch** to reconstruct images from the **Fashion-MNIST dataset**. The goal is to compress the image into a **latent representation** and then reconstruct it back to its original form.  

Autoencoders are widely used for:
- **Data compression**
- **Noise reduction / denoising**
- **Anomaly detection**
- **Feature extraction** for other tasks  

---

## 🔹 Dataset

**Fashion-MNIST**:
- 28x28 grayscale images of fashion items  
- 10 classes:
  | Label | Item |
  |-------|------|
  | 0 | T-shirt/Top |
  | 1 | Trouser |
  | 2 | Pullover |
  | 3 | Dress |
  | 4 | Coat |
  | 5 | Sandal |
  | 6 | Shirt |
  | 7 | Sneaker |
  | 8 | Bag |
  | 9 | Boot |
- Training set: 60,000 images  
- Test set: 10,000 images  

---

## 🔹 Model Architecture

The Autoencoder consists of two main parts:

### Encoder
- **Flatten**: 28x28 → 784 vector  
- **Linear Layers**: 784 → 128 → 64 → 32  
- **Activation**: ReLU (non-linearities)  

### Decoder
- **Linear Layers**: 32 → 64 → 128 → 784  
- **Activation**: ReLU + Sigmoid (0-1 output)  
- **Unflatten**: vector → 28x28 image  

**Latent space size:** 32 (compressed representation of each image)

---

## 🔹 Training

- **Loss function**: Mean Squared Error (MSE)  
- **Optimizer**: Adam  
- **Learning rate**: 0.001  
- **Epochs**: 5 (demo)  
- **Batch size**: 128  

Training involves passing images through the encoder, reconstructing them via the decoder, and minimizing the MSE between original and reconstructed images.

---

## 🔹 Usage

```bash
# Clone repository
git clone <repository-url>
cd project6-autoencoder

# Install dependencies
pip install torch torchvision matplotlib

Then, run the Python script:

python autoencoder_fashion_mnist.py
🔹 Visualization

After training, the model reconstructs images. The first 5 original images and their reconstructions are displayed side by side:

Top row: Original images
Bottom row: Reconstructed images by the autoencoder

This helps evaluate the model visually and understand how well it learned the underlying patterns.

🔹 Results
The Autoencoder successfully compresses and reconstructs images.
It captures the main features of each clothing item.
Can be extended to:
Denoising images
Detecting anomalies in datasets
Feature extraction for downstream tasks
🔹 Folder Structure
project6-autoencoder/
│
├── autoencoder_fashion_mnist.py    # main script with model and training
├── data/                           # Fashion-MNIST dataset downloaded
├── results/                        # optional: save reconstructed images or checkpoints
└── README.md
🔹 References
Fashion-MNIST Dataset
PyTorch Autoencoder Tutorial

