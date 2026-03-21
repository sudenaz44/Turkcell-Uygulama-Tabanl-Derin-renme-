5️⃣ Transformers ile Duygu Analizi (Text) yapılacaklar: 
Ana Fikir
Amaç: Verilen bir metnin (örneğin bir film yorumu, tweet veya yorum) olumlu mu yoksa olumsuz mu olduğunu otomatik olarak sınıflandırmak.
Kullanacağımız yöntem: Transformers tabanlı önceden eğitilmiş modeller (BERT gibi).
Transformers → modern NLP modelleri, dikkat (attention) mekanizması ile kelimeler arası ilişkileri yakalar.
Önceden eğitilmiş modeller → büyük metin veri setleriyle eğitilmiş, sonradan bizim küçük veri setimize göre fine-tuning yapılabilir.
Dataset
IMDb Movie Reviews (yaygın kullanılır)
Film yorumlarını içerir.
Etiketler: 0 → olumsuz, 1 → olumlu
Eğitim ve test seti vardır.
Her yorum genellikle 50–500 kelime arasıdır.
Özellikleri:
Çeşitli uzunluklarda metinler
Duygusal ifade yoğunluğu değişir
İngilizce
Kullanım amacı: Model, bir metindeki duyguyu öğrenir ve sınıflandırma yapar.
Öğreneceklerin
Transformers mimarisi mantığı ve BERT’in text classification’daki kullanımı.
Tokenization ve embedding süreci (kelimeleri modelin anlayacağı sayısal forma çevirme).
Model eğitimi, fine-tuning ve test.
Performans ölçümü (accuracy, confusion matrix gibi).
Kısaca Yol Haritası
Gerekli kütüphaneleri yükle ve hazırla
Dataset’i yükle
Tokenizer ile metinleri sayısala çevir
Modeli oluştur ve fine-tuning yap
Modeli eğit, test et ve sonuçları görselleştir
Tahmin örnekleri yap.

----başlayalım:

# 🎬 Sentiment Analysis with BERT (Transformers)

## 📌 Project Overview

This project performs sentiment analysis on movie reviews using a pre-trained BERT model. The goal is to classify reviews as **positive** or **negative**.

---

## 🚀 Technologies Used

* Python
* PyTorch
* Hugging Face Transformers
* Datasets (IMDb)
* Scikit-learn
* Matplotlib

---

## 📂 Dataset

We used the IMDb Movie Reviews dataset:

* 50,000 reviews
* 25,000 for training
* 25,000 for testing
* Labels:

  * 0 → Negative
  * 1 → Positive

---

## 🧠 Model

* Pre-trained: `bert-base-uncased`
* Fine-tuned for sequence classification
* Output classes: 2 (Positive / Negative)

---

## ⚙️ Process

1. Load dataset using Hugging Face
2. Tokenize text data
3. Apply padding and truncation
4. Load pre-trained BERT model
5. Fine-tune on IMDb dataset
6. Evaluate model performance

---

## 📊 Results

* Accuracy: ~85–90%
* Loss: Low and stable

---

## 📈 Evaluation Metrics

* Accuracy
* Confusion Matrix

---

## 🔥 Key Learnings

* Understanding Transformer architecture
* Using pre-trained models (BERT)
* Tokenization and text preprocessing
* Model fine-tuning
* Evaluation and visualization

---

## 🧪 Example Prediction

Input:

> "This movie was amazing!"

Output:

> Positive ✅

---

## 📌 Future Improvements

* Add more metrics (F1-score, precision, recall)
* Hyperparameter tuning
* Deploy as a web app (Streamlit)

---

## 👨‍💻 Author

Sudenaz KILIÇ

