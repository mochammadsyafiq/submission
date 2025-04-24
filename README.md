# 🧠 Animal Image Classification (4 Classes)

Proyek ini merupakan implementasi deep learning untuk klasifikasi gambar hewan ke dalam 4 kelas: **Horse**, **Chicken**, **Cat**, dan **Spider**, menggunakan model **Convolutional Neural Network (CNN)** dari awal (tanpa pretrained model).

## 📁 Dataset
Dataset yang digunakan adalah subset dari [Animals-10](https://www.kaggle.com/datasets/alessiocorrado99/animals10), dengan total 4 kelas:
- Horse (`cavallo`)
- Chicken (`gallina`)
- Cat (`gatto`)
- Spider (`ragno`)

Dataset ini memiliki gambar dengan resolusi tidak seragam, sehingga dilakukan preprocessing termasuk resize, augmentasi, dan normalisasi.

### Distribusi Data (Setelah Filter)
- Horse: `2623` gambar
- Chicken: `3098` gambar
- Cat: `1668` gambar
- Spider: `4821` gambar


Total: `12201` gambar

## 🛠️ Model Arsitektur
Model CNN dibangun menggunakan Keras Sequential API dengan arsitektur sebagai berikut:

- 4 buah blok Conv2D + MaxPooling2D
- Dropout untuk mencegah overfitting
- Dense layer 256 & 512 neuron + softmax output (4 kelas)

### Ringkasan Model
```
Conv2D → MaxPooling2D → Conv2D → MaxPooling2D → Conv2D → MaxPooling2D → Conv2D → MaxPooling2D  
→ Flatten → Dense(128)→ Dropout → Dense(512) → Dropout → Dense(4) Softmax
```

## 🧪 Evaluasi
- **Loss Function**: Categorical Crossentropy
- **Optimizer**: Adam(learning_rate=0.001),
- **Metrics**: Accuracy
- **Callbacks**:
  - EarlyStopping
  - ReduceLROnPlateau
  - ModelCheckpoint
  - StopTrainingAtAccuracy(Callback)

### Hasil Terbaik:
- ✅ **Training Accuracy**: ~93.2%
- ✅ **Validation Accuracy**: ~92.0%
- ✅ **Validation Loss**: ~0.26

## 📊 Visualisasi Training
![Training Plot](training_plot.png)

## 🧠 Inference
Model diekspor dalam 3 format:
- `SavedModel`
- `TensorFlow Lite (.tflite)`
- `TensorFlow.js`

Contoh prediksi:
```python
predict_image("/content/drive/MyDrive/dataset_split/test/chicken/4.jpeg")
# Output: 'chicken' (confidence: 100%)
![predict](predict.png)
```

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




