Project 7: Transfer Learning ile İlaç Görüntüleri Sınıflandırma
🔹 Ana Fikir

Amaç:

Yeni bir sınıflandırma problemi için önceden eğitilmiş bir CNN modeli (ResNet, VGG, EfficientNet gibi) kullanmak.
Bu sayede az veri ile yüksek doğruluk elde edebilirsin.

Problem:

Elimizde ilaç (hap, kapsül vb.) görüntüleri var.
Bu görüntüleri sınıflandırmak istiyoruz: örneğin ilacın türü, rengi veya şekli.

Ana mantık:

Önceden büyük veri üzerinde eğitilmiş bir CNN modeli (ImageNet gibi) kullanılır → özellik çıkarıcı (feature extractor) olarak görev yapar.
Son katman (classifier) kendi veri setimize göre değiştirilir ve yeniden eğitilir → transfer learning.
Bu yöntem ile sıfırdan model eğitmeye gerek kalmaz, eğitim süresi kısalır ve küçük veri ile iyi performans alınır.
🔹 Kullanılan Dataset
Genellikle Image classification için özel ilaç datasetleri kullanılır:
Örnek: “Pill Image Dataset” (çeşitli renk, şekil ve boyutlarda ilaç resimleri)
Her resim bir sınıfa ait (label)
Özellikler:
Görüntü boyutu farklı olabilir (32x32, 224x224, vb.) → resize edilir
RGB renkli görüntüler
Training / Validation / Test split yapılır
🔹 Öğrenilecek Konular
Transfer Learning Mantığı → feature extractor + classifier
Pretrained model kullanımı (ResNet, EfficientNet, VGG)
Data augmentation → küçük veri ile overfitting önleme
Optimizer, Loss, Epoch gibi eğitim parametreleri
Evaluation metrics → Accuracy, Confusion Matrix

Kısaca:

“Var olan güçlü bir modeli alıyoruz, son katmanı kendi ilaç datasetimize göre değiştiriyoruz ve az veri ile yüksek performans elde ediyoruz.”

---

Kodun Detaylı Açıklaması (satır satır)
Kütüphaneler:
torch → tensor ve GPU işlemleri
torchvision → pretrained modeller, dataset, transform
matplotlib → görselleştirme
Device:
GPU varsa kullan, yoksa CPU
Data Augmentation / Transform:
Resize → ResNet bekler 224x224
RandomHorizontalFlip → veri çoğaltma
ToTensor → 0-255 → 0-1
Dummy Dataset:
Gerçek dataset yerine demo amaçlı FakeData kullanıldı
5 sınıf, RGB 224x224 görüntü
Train/Validation Split:
%80 train, %20 validation
DataLoader:
Batch halinde veri GPU’ya gider
Shuffle → eğitim sırasında karışır
Pretrained Model:
ResNet18 ImageNet ağırlıkları ile
Son katman 5 sınıfa göre değiştirildi → transfer learning
Loss & Optimizer:
CrossEntropyLoss → multi-class sınıflandırma
Adam optimizer → ağırlıkları güncelle
Eğitim Döngüsü:
Forward pass → loss → backward → optimizer.step()
Train ve validation loss/accuracy hesaplanır
Tahmin Görselleştirme:
İlk 5 validation örneği
Görüntü + predicted ve true label yan yana gösterilir.

---

# Project 7: Transfer Learning for Drug Image Classification

## 🔹 Project Overview

This project demonstrates **transfer learning** using a **pretrained CNN (ResNet18)** to classify drug images into multiple categories.  
The idea is to leverage a model trained on a large dataset (ImageNet) and **adapt it to a small custom dataset** efficiently.  

Transfer learning allows:
- High accuracy with **limited data**
- Reduced training time
- Reuse of powerful feature extractors

---

## 🔹 Dataset

- Demo uses **PyTorch FakeData** for quick testing  
- Original use case: **drug pill images**  
- Typical features:
  - RGB images, variable size (resized to 224x224)
  - Multiple classes (types/shapes/colors of pills)
  - Training / Validation / Test split

---

## 🔹 Model Architecture

- **Base model:** ResNet18 pretrained on ImageNet  
- **Transfer Learning Steps:**
  1. Load pretrained ResNet18
  2. Replace the final fully connected (FC) layer with a new layer for **5 classes** (demo)
  3. Freeze base layers if needed (optional)
- **Input size:** 224x224 RGB images

---

## 🔹 Training

- **Loss function:** CrossEntropyLoss (multi-class classification)  
- **Optimizer:** Adam  
- **Learning rate:** 0.001  
- **Batch size:** 16  
- **Epochs:** 3 (demo, quick run)  

**Workflow:**
1. Forward pass: input images → model → outputs  
2. Compute loss vs ground truth  
3. Backpropagation → update weights  
4. Compute training and validation accuracy  

---

## 🔹 Data Augmentation

- Resize images to 224x224  
- Random horizontal flip  
- Convert to tensor (0-1 range)  

**Purpose:** Helps model generalize better on small datasets

---

## 🔹 Usage

```bash
# Clone repository
git clone <repository-url>
cd project7-transfer-learning

# Install dependencies
pip install torch torchvision matplotlib

Run the Python script:

python transfer_learning_drug_demo.py
🔹 Visualization
After training, first 5 validation images are displayed:
Each image shows predicted class vs true label
Helps verify how well the model learned features
🔹 Results
Pretrained ResNet18 successfully adapts to small dataset
Model can be extended to:
Real drug image datasets
Medical image classification
Anomaly detection in pills or tablets

🔹 References
PyTorch Transfer Learning Tutorial
ResNet Paper
Pill Image Dataset Example