# Proyek Klasifikasi Gambar: Drone vs Bird

## Dataset
Dataset berisi 2 kelas gambar:
- **drone/**
- **bird/**

Struktur Direktori:

![Screenshot 2025-04-28 192449](https://github.com/user-attachments/assets/d45efb70-0c74-4e44-bf62-05bf88bb8af2)


## Alur Kerja

1. **Persiapan Dataset**  
   - Dataset dipisah menjadi folder `train/`, `validation/`, dan `test/`.
   - Setiap folder memiliki subfolder `drone/` dan `bird/` untuk masing-masing kelas.

2. **Preprocessing Data**  
   - Menggunakan `ImageDataGenerator` untuk augmentasi gambar pada data training.
   - Resize gambar ke ukuran **150x150** piksel.
   - Batch size: **32**.
   - Class mode: **categorical**.

3. **Training Model**  
   - Model CNN berbasis `Sequential` dengan arsitektur:
     - Conv2D(32) + MaxPooling2D
     - Conv2D(64) + MaxPooling2D
     - Conv2D(128) + MaxPooling2D
     - Flatten
     - Dense(512) + Dropout(0.5)
     - Dense(2) + Softmax
   - Optimizer: **Adam** (learning rate = 0.0001)
   - Loss Function: **Categorical Crossentropy**
   - Metrics: **Accuracy**
   - Menggunakan **EarlyStopping** pada `val_loss` dengan patience 7.

4. **Evaluasi dan Visualisasi**  
   - Menampilkan grafik **akurasi** dan **loss** pada data training dan validation.

5. **Inference**  
   - Mengunggah gambar baru untuk prediksi klasifikasi antara **drone** atau **bird**.
   - Menampilkan label hasil klasifikasi dan confidence score.

## Model

- **Arsitektur**:
  - 3 lapisan Conv2D + MaxPooling2D
  - Flatten → Dense(512) → Dropout → Dense(2) dengan Softmax
- **Optimizer**: Adam (lr=0.0001)
- **Loss Function**: Categorical Crossentropy
- **EarlyStopping**: berdasarkan val_loss (patience=7)

## Hasil

- **Akurasi Training**: 94.32%
- **Akurasi Validation**: 93.18%

## Format Model

Model disimpan dalam format:
- **SavedModel** (TensorFlow SavedModel format)
- **TensorFlow Lite** (.tflite) untuk penggunaan di mobile
- **TensorFlow.js** (TFJS) untuk deployment di web

---

