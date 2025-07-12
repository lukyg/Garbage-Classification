# Proyek Klasifikasi Gambar Sampah

Proyek ini mengembangkan model *Convolutional Neural Network* (CNN) untuk mengklasifikasikan gambar sampah ke dalam 12 kategori berbeda. Model dibangun menggunakan TensorFlow dan Keras, dilatih dengan dataset gambar sampah, dan mendukung ekspor ke format TensorFlow.js serta TensorFlow Lite.

## Penulis
- **Nama**: Ade Safarudin Madani
- **Email**: adesfdnmdn@gmail.com
- **ID Dicoding**: ade_madani

## Tujuan
Membangun model CNN yang mampu mengklasifikasikan sampah ke dalam 12 kategori:
- Battery
- Biological
- Brown-glass
- Cardboard
- Clothes
- Green-glass
- Metal
- Paper
- Plastic
- Shoes
- Trash
- White-glass

## Dataset
Dataset yang digunakan adalah **Garbage Classification** dari Kaggle:
- **Sumber**: [Kaggle - Garbage Classification](https://www.kaggle.com/datasets/mostafaabla/garbage-classification)
- **Deskripsi**: Berisi gambar sampah yang terorganisir dalam 12 folder, masing-masing mewakili satu kelas.
- **Jumlah Label**: 12

## Arsitektur Model
Model CNN dibangun dengan arsitektur berikut:
```python
model = models.Sequential()
model.add(layers.Conv2D(32, (3, 3), activation='relu', input_shape=(224, 224, 3)))
model.add(layers.MaxPooling2D((2, 2)))
model.add(layers.Conv2D(64, (3, 3), activation='relu'))
model.add(layers.MaxPooling2D((2, 2)))
model.add(layers.Conv2D(128, (3, 3), activation='relu'))
model.add(layers.Conv2D(256, (3, 3), activation='relu'))
model.add(layers.GlobalAveragePooling2D())
model.add(layers.Dense(128, activation='relu'))
model.add(layers.Dropout(0.5))
model.add(layers.Dense(12, activation='softmax'))
```

## Daftar Isi
- [Prasyarat](#prasyarat)
- [Penggunaan](#penggunaan)
- [Dependensi](#dependensi)
- [Struktur Proyek](#struktur-proyek)

## Prasyarat
- Python 3.8 atau lebih tinggi
- Google Colab
- Dataset [Garbage Classification](https://www.kaggle.com/datasets/mostafaabla/garbage-classification) yang telah diunduh dan diorganisir

## Penggunaan
1. **Siapkan dataset**:
   - Unduh dataset dari [Kaggle](https://www.kaggle.com/datasets/mostafaabla/garbage-classification).
   - Pastikan dataset diorganisir dengan struktur berikut:
     ```
     dataset/
     ├── battery/
     ├── biological/
     ├── brown-glass/
     ├── cardboard/
     ├── clothes/
     ├── green-glass/
     ├── metal/
     ├── paper/
     ├── plastic/
     ├── shoes/
     ├── trash/
     └── white-glass/
     ```
   - Perbarui jalur dataset di `Garbage_Classification_CNN.ipynb` jika diperlukan.

2. **Jalankan notebook**:
   - Unggah `Garbage_Classification_CNN.ipynb` ke Google Colab.
   - Jalankan sel-sel untuk memproses data, melatih model, dan mengevaluasi performa.
   - Model yang telah dilatih akan disimpan di direktori `saved_model`.

3. **Ekspor model** (opsional):
   - **TensorFlow.js**: Gunakan kode di notebook untuk mengonversi model ke format TensorFlow.js, disimpan di `tfjs_model/`.
   - **TensorFlow Lite**: Konversi model ke format TensorFlow Lite, disimpan di `tflite/`.

4. **Evaluasi model**:
   - Gunakan bagian evaluasi di notebook untuk menguji model pada set validasi atau gambar baru.

## Dependensi
Proyek ini bergantung pada pustaka Python berikut (lihat `requirements.txt` untuk versi pasti):
- `numpy==2.0.2`: Komputasi numerik
- `pandas==2.2.2`: Manipulasi data
- `tqdm==4.67.1`: Bilah kemajuan
- `matplotlib==3.10.0`: Visualisasi dan plotting
- `seaborn==0.13.2`: Visualisasi statistik
- `pillow==11.1.0`: Pemrosesan gambar
- `keras==3.8.0`: API jaringan saraf tingkat tinggi
- `tensorflow==2.18.0`: Kerangka kerja pembelajaran mesin
- `tensorflowjs==4.22.0`: Konversi model untuk deployment web

Instal dependensi di Google Colab dengan:
```bash
!pip install -r requirements.txt
```

## Struktur Proyek
```
proyek-sampah/
├── tfjs_model/                # File model TensorFlow.js
│   ├── group1-shard1of1.bin
│   └── model.json
├── tflite/                    # File model TensorFlow Lite
│   ├── model.tflite
│   └── label.txt
├── saved_model/               # Model TensorFlow yang disimpan
│   ├── saved_model.pb
│   └── variables/
├── Garbage_Classification_CNN.ipynb  # Notebook Jupyter dengan kode utama
├── README.md                  # Dokumentasi proyek
└── requirements.txt           # Daftar dependensi
```
