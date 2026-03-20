MNIST GAN (Generative Adversarial Network)
Proje Hakkında

Bu proje, Generative Adversarial Network (GAN) kullanarak MNIST el yazısı rakamlarını üretmeyi amaçlamaktadır.
GAN, iki modelden oluşur:

Generator (Üretici): Rastgele gürültüden (noise) sahte resim üretir.

Discriminator (Ayırt Edici): Resmin gerçek mi sahte mi olduğunu belirler.

Proje, TensorFlow/Keras kullanılarak sıfırdan geliştirilmiştir.

Özellikler

MNIST veri seti ile eğitim

100 boyutlu rastgele gürültü ile sahte 28x28 resim üretimi

Discriminator ve Generator modellerinin ayrı ayrı eğitimi

Eğitim ilerlemesini kayıp (loss) ve doğruluk (accuracy) ile takip

Üretilen sahte görüntülerin görselleştirilmesi

Gereksinimler

Python 3.8+

TensorFlow 2.x

NumPy

Matplotlib

Kurulum örneği:

pip install tensorflow numpy matplotlib
Dosya Açıklamaları

mnist_gan.py → GAN modeli ve eğitim döngüsü

generate_images.py → Eğitim sonrası sahte resim üretimi ve görselleştirme

README.md → Proje hakkında bilgi

Kullanım
1️⃣ MNIST veri setini yükle ve normalize et
from tensorflow.keras.datasets import mnist
(x_train, _), (_, _) = mnist.load_data()
x_train = x_train.astype('float32') / 255.0
x_train = x_train.reshape(-1, 28*28)
2️⃣ Generator modeli
from tensorflow.keras import models, layers

def build_generator():
    model = models.Sequential()
    model.add(layers.Dense(128, activation='relu', input_dim=100))
    model.add(layers.Dense(784, activation='sigmoid'))
    return model
3️⃣ Discriminator modeli
def build_discriminator():
    model = models.Sequential()
    model.add(layers.Dense(128, activation='relu', input_dim=784))
    model.add(layers.Dense(1, activation='sigmoid'))
    model.compile(optimizer='adam', loss='binary_crossentropy', metrics=['accuracy'])
    return model
4️⃣ GAN modeli
discriminator = build_discriminator()
discriminator.trainable = False

generator = build_generator()
gan_input = layers.Input(shape=(100,))
gan_output = discriminator(generator(gan_input))
gan = models.Model(gan_input, gan_output)
gan.compile(optimizer='adam', loss='binary_crossentropy')
5️⃣ Eğitim döngüsü
import numpy as np

batch_size = 128
epochs = 1000

for epoch in range(epochs):
    # Gerçek verilerden batch seç
    idx = np.random.randint(0, x_train.shape[0], batch_size)
    real_imgs = x_train[idx]

    # Sahte görüntü üret
    noise = np.random.normal(0, 1, (batch_size, 100))
    fake_imgs = generator.predict(noise, verbose=0)

    # Etiketler
    real_labels = np.ones((batch_size, 1))
    fake_labels = np.zeros((batch_size, 1))

    # Discriminator'u eğit
    d_loss_real = discriminator.train_on_batch(real_imgs, real_labels)
    d_loss_fake = discriminator.train_on_batch(fake_imgs, fake_labels)
    d_loss = 0.5 * np.add(d_loss_real, d_loss_fake)

    # Generator'u eğit
    noise = np.random.normal(0, 1, (batch_size, 100))
    g_loss = gan.train_on_batch(noise, np.ones((batch_size, 1)))

    if epoch % 100 == 0:
        print(f"{epoch} [D loss: {d_loss[0]:.4f}, acc: {100*d_loss[1]:.2f}%] [G loss: {g_loss:.4f}]")
6️⃣ Üretilen görüntüleri görselleştirme
import matplotlib.pyplot as plt

noise = np.random.normal(0, 1, (10, 100))
gen_imgs = generator.predict(noise)

for i in range(10):
    plt.subplot(2, 5, i+1)
    plt.imshow(gen_imgs[i].reshape(28,28), cmap='gray')
    plt.axis('off')
plt.show()
Önemli Notlar

discriminator.trainable = False → GAN eğitilirken discriminator sabit kalır.

Girdi ve çıktı boyutları:

Generator input: (batch_size, 100)

Generator output: (batch_size, 784)

Discriminator input: (batch_size, 784)

Discriminator output: (batch_size, 1)

Kaynaklar

TensorFlow GAN Guide

MNIST Dataset