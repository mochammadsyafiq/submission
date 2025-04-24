# 🧠 Intel Image Classification (6 Classes)

Proyek ini merupakan implementasi deep learning untuk klasifikasi gambar ke dalam 6 kelas lingkungan menggunakan **Convolutional Neural Network (CNN)** yang dibangun dari awal tanpa pretrained model.

## 📁 Dataset
Dataset yang digunakan adalah [Intel Image Classification](https://www.kaggle.com/datasets/puneet6060/intel-image-classification), yang terdiri dari gambar pemandangan outdoor dengan 6 kelas berbeda:

- **Buildings**
- **Forest**
- **Glacier**
- **Mountain**
- **Sea**
- **Street**

### Karakteristik Dataset:
- Total: ~25.000+ gambar
- Resolusi gambar bervariasi
- Dataset dibagi menjadi folder `train`, `test`, dan `val`

📌 **Preprocessing**:
- Resize gambar ke ukuran tetap (misal: 150x150)
- Normalisasi pixel (rescaling)
- Augmentasi data (rotation, flip, zoom, shift, dll)

## 🛠️ Arsitektur Model

Model CNN dibangun menggunakan Keras Sequential API. Arsitektur terdiri dari:

- 4 blok Conv2D + MaxPooling2D
- Dropout untuk mengurangi overfitting
- Dense layer berukuran 128 dan 256 neuron
- Output layer dengan Softmax (6 kelas)

### Ringkasan Model:

Conv2D → MaxPooling2D → Conv2D → MaxPooling2D → Conv2D → MaxPooling2D → Conv2D → MaxPooling2D
→ Flatten → Dense(128) → Dropout → Dense(256) → Dropout → Dense(6) → Softmax

## ⚙️ Konfigurasi Training
- **Loss Function**: Categorical Crossentropy
- **Optimizer**: Adam (learning_rate=0.001)
- **Metrics**: Accuracy
- **Callbacks**:
  - EarlyStopping (monitor val_loss, patience=5)
  - ReduceLROnPlateau
  - ModelCheckpoint (save best model)
  - Custom Callback: StopTrainingAtAccuracy (jika diperlukan)

## 📊 Hasil Evaluasi
| Dataset       | Akurasi     | Loss     |
|---------------|-------------|----------|
| Training      | **86.28%**  | -        |
| Testing       | **85.16%**  | -        |

Model menunjukkan generalisasi yang cukup baik dengan selisih kecil antara akurasi training dan testing.

## 🧠 Inference
Model diekspor dalam 3 format:
- `SavedModel`
- `TensorFlow Lite (.tflite)`
- `TensorFlow.js`

## 📁 Struktur Folder
```
submission/
├──—notebook.ipynb
├──—README.md
├──—requirements.txt
├──—predict.png
├──—training_plot.png
├──—saved_model/
│   ├── saved_model.pb
│   └── variables/
├──—tflite/
│   ├── model.tflite
│   └── label.txt
└──—tfjs_model/
    ├── model.json
    └── group1-shard1of1.bin
```




