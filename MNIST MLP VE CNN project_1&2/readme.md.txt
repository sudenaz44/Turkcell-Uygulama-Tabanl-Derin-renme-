# 🧠 Handwritten Digit Classification with Deep Learning (MLP & CNN)

## 📌 Proje Açıklaması

Bu projede, MNIST veri seti kullanılarak el yazısı rakamların sınıflandırılması gerçekleştirilmiştir.
İki farklı model yaklaşımı karşılaştırılmıştır:

* **MLP (Multi-Layer Perceptron)** → Temel yapay sinir ağı
* **CNN (Convolutional Neural Network)** → Görüntü işleme için gelişmiş model

Amaç: Aynı veri seti üzerinde farklı mimarilerin performansını gözlemlemek ve derin öğrenme mantığını anlamak.

---

## 📊 Veri Seti

**MNIST Dataset**

* 70.000 adet görüntü
* 28x28 gri tonlu (grayscale)
* 10 sınıf (0–9 rakamları)
* 60.000 eğitim / 10.000 test

---

## 🧠 Kullanılan Modeller

### 🔹 1. MLP (Multi-Layer Perceptron)

* Flatten edilmiş giriş (784 boyut)
* 2 hidden layer:

  * 128 nöron (ReLU)
  * 64 nöron (ReLU)
* Output: 10 sınıf (Softmax)

👉 Özellik:

* Görüntüyü **düz veri (vektör)** olarak işler
* Uzamsal bilgiyi kaybeder

---

### 🔹 2. CNN (Convolutional Neural Network)

* Conv2D + MaxPooling katmanları
* Feature extraction (kenar, şekil öğrenme)
* Dropout ile overfitting önleme

👉 Özellik:

* Görüntüyü **uzamsal olarak analiz eder**
* MLP’ye göre daha yüksek performans sağlar

---

## ⚙️ Kullanılan Teknolojiler

* Python
* TensorFlow / Keras
* NumPy
* Matplotlib
* Google Colab

---

## 📈 Model Eğitimi

| Model | Epoch | Batch Size | Optimizer |
| ----- | ----- | ---------- | --------- |
| MLP   | 5     | 32         | Adam      |
| CNN   | 5     | 32         | Adam      |

---

## 📊 Sonuçlar

| Model | Test Accuracy |
| ----- | ------------- |
| MLP   | ~97%          |
| CNN   | ~98-99%       |

👉 CNN modelinin, görüntü verisinde daha başarılı olduğu gözlemlenmiştir.

---

## 🧠 Öğrenilenler

* Görüntü verisi nasıl işlenir (normalization, reshape)
* MLP vs CNN farkı
* Feature extraction mantığı
* Model eğitimi ve performans değerlendirme
* Overfitting ve Dropout kullanımı
* Data Augmentation ile model iyileştirme

---

## 🚀 Nasıl Çalıştırılır?

1. Google Colab aç
2. Notebook kodlarını yapıştır
3. Hücreleri sırayla çalıştır
4. Sonuçları gözlemle

---

## 📁 Proje Yapısı

```
📦 digit-classification
 ┣ 📜 mlp_model.ipynb
 ┣ 📜 cnn_model.ipynb
 ┣ 📜 README.md
```

---

## 🎯 Gelecek Geliştirmeler

* Daha derin CNN mimarileri (ResNet, VGG)
* Hyperparameter tuning
* Farklı veri setleri ile test
* Model deployment (Streamlit / Flask)

---

## 👩‍💻 Geliştirici

Bu proje, derin öğrenme alanında pratik yapmak ve portföy geliştirmek amacıyla hazırlanmıştır.

---


