---

# **Tugas Kecerdasan Buatan (CNN)**

### **Nama**        : Jihan Nabilah  
### **NPM**         : 2208107010035  
### **Mata Kuliah** : Kecerdasan Buatan  

---

## **Proyek CNN Menggunakan Dataset CIFAR-10**

Proyek ini melibatkan pelatihan dan evaluasi model CNN (**Convolutional Neural Network**) menggunakan dataset CIFAR-10. Proyek terdiri dari dua file utama: **`train1.py`** untuk melatih model dan **`predict1.py`** untuk melakukan prediksi menggunakan model yang telah dilatih.

### **1. Dataset CIFAR-10**
Dataset CIFAR-10 adalah kumpulan gambar dengan ukuran 32x32 piksel yang dikelompokkan ke dalam 10 kategori: **pesawat**, **mobil**, **burung**, **kucing**, **rusa**, **anjing**, **katak**, **kuda**, **kapal**, dan **truk**. Dataset ini terdiri dari 60.000 gambar, dengan pembagian 50.000 gambar untuk pelatihan dan 10.000 gambar untuk pengujian.

- **Normalisasi Data**: Gambar dinormalisasi dengan membagi nilai piksel (0-255) menjadi rentang 0-1.
- **One-hot Encoding**: Label numerik (0–9) diubah menjadi format one-hot encoded menggunakan `to_categorical`.

### **2. Arsitektur CNN**
Model CNN dibangun dengan lapisan-lapisan berikut:
- **Convolutional Layers (`Conv2D`)**: Menangkap pola pada gambar menggunakan filter berukuran `(3, 3)`.
- **Pooling Layers (`MaxPooling2D`)**: Mengurangi dimensi data untuk mempercepat pelatihan dan mengurangi overfitting.
- **Fully Connected Layers (`Dense`)**: Menggabungkan fitur yang dipelajari untuk klasifikasi.
- **Dropout Layers**: Mencegah overfitting dengan secara acak menonaktifkan sebagian neuron selama pelatihan.
- **Activation Functions**:
  - `ReLU`: Memperkenalkan non-linearitas.
  - `Softmax`: Menghasilkan probabilitas untuk klasifikasi multi-kelas.

### **3. Melatih Model**
- Model dilatih selama **10 epoch** dengan ukuran batch **64**.
- Fungsi loss yang digunakan adalah **categorical_crossentropy**, dan optimasi dilakukan menggunakan **Adam optimizer**.
- Data pengujian digunakan sebagai **validation set** untuk memantau kinerja model selama pelatihan.

### **4. Menyimpan dan Mengevaluasi Model**
- Model yang telah dilatih disimpan dalam file **`model.h5`**.
- Skrip mengevaluasi akurasi model pada data pengujian untuk memastikan kinerjanya.

---

## **Prediksi Gambar dengan Model CIFAR-10**

File **`predict1.py`** digunakan untuk memuat model yang telah dilatih dan melakukan prediksi pada gambar yang diunggah pengguna.

### **Fungsi Utama**
- **Memuat Gambar**: Gambar diunggah melalui antarmuka grafis lokal menggunakan **Tkinter**. Gambar diubah ukurannya menjadi **32x32** piksel, dinormalisasi, dan diubah menjadi format batch.
- **Memuat Model**: Model disimpan dalam **`model.h5`** dan dimuat untuk melakukan prediksi.
- **Prediksi**: Model memberikan prediksi probabilitas untuk setiap kelas, dan kelas dengan probabilitas tertinggi dipilih sebagai hasil prediksi.

---

## **Klasifikasi Gambar Anjing dan Kucing**

Proyek ini juga mencakup pelatihan model CNN untuk klasifikasi gambar **anjing** dan **kucing** menggunakan dataset terpisah.

### **File dan Struktur Proyek**
1. **`train2.py`**: Skrip untuk melatih model CNN menggunakan dataset gambar anjing dan kucing.
2. **`predict2.py`**: Skrip untuk memprediksi gambar baru menggunakan model yang telah dilatih.
3. **`dataset/`**: Folder yang berisi dataset dengan struktur:
   ```
   dataset/
   ├── training_set/
   │   ├── cats/
   │   └── dogs/
   └── test_set/
       ├── cats/
       └── dogs/
   ```

### **Langkah-langkah Proyek**
1. **Data Augmentasi**: Dataset dilatih menggunakan augmentasi seperti rotasi, zoom, dan flipping untuk meningkatkan generalisasi model.
2. **Pelatihan Model**:
   - Model dilatih menggunakan data di folder `training_set/`.
   - Hasil pelatihan disimpan dalam file **`model.h5`**.
3. **Prediksi Gambar Baru**:
   - Gambar di folder `test_set/` diuji menggunakan file **`predict2.py`**.
   - Skrip memberikan hasil prediksi untuk gambar baru, termasuk jumlah gambar yang diprediksi sebagai **anjing** dan **kucing**.

---

## **Langkah Menjalankan Proyek**
1. **Persiapan Lingkungan**:
   Pastikan TensorFlow dan Keras terinstal:
   ```bash
   pip install tensorflow keras
   ```

2. **Dataset CIFAR-10**:
   Untuk menggunakan model CIFAR-10, jalankan:
   ```bash
   python train1.py
   python predict1.py
   ```

3. **Dataset Anjing dan Kucing**:
   Siapkan dataset dengan struktur di atas, lalu jalankan:
   ```bash
   python train2.py
   python predict2.py
   ```

4. **Hasil Prediksi**:
   Prediksi kelas akan ditampilkan di terminal, termasuk jumlah gambar untuk setiap kategori.

--- 
