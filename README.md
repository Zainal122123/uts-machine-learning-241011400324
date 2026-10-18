# Tugas UTS Machine Learning

Repositori ini berisi implementasi algoritma **Linear Regression** dan **Logistic Regression** yang dibangun secara manual menggunakan NumPy (tanpa *library* Scikit-Learn untuk algoritma utamanya), sebagai bagian dari Ujian Tengah Semester mata kuliah Machine Learning.

## 👤 Identitas Mahasiswa
- **Nama**  : Muhamad Zaenal
- **NIM**   : 241011400324
- **Kelas** : [Isi Kelas Anda, contoh: 06TIDE001]

---

## 📊 Ringkasan Hasil Evaluasi Model

### Bagian A – Linear Regression (Prediksi Penjualan dari Biaya Iklan)
Model dilatih menggunakan metode *Normal Equation* dan *Gradient Descent*. Parameter terbaik (konvergen) ditemukan pada proses *Gradient Descent* dengan *Learning Rate* = 0.02.
- **Nilai $R^2$ (R-Squared)** : [Isi nilai R2 dari tabel Soal A4, contoh: 0.85]
- **RMSE (Data Testing)**     : [Isi nilai RMSE dari tabel Soal A4, contoh: 2.34]
- **MAE (Data Testing)**      : [Isi nilai MAE dari tabel Soal A4, contoh: 1.95]

**Kesimpulan Bagian A:**
Model menunjukkan bahwa variabel Biaya Iklan memiliki korelasi positif terhadap Penjualan. Namun, melakukan prediksi ekstrapolasi (misal: Biaya Iklan 12 juta yang berada di luar rentang data) berisiko tidak akurat karena adanya faktor saturasi pasar.

### Bagian B – Logistic Regression (Klasifikasi Email Spam)
Model dilatih menggunakan metode *Gradient Descent* untuk memprediksi apakah suatu email adalah Spam (1) atau Bukan Spam (0) berdasarkan *Jumlah Link* dan *Kata Promo*.
- **Akurasi**   : [Isi nilai Akurasi dari Soal B3, contoh: 0.92]
- **Precision** : [Isi nilai Precision dari Soal B3, contoh: 0.95]
- **Recall**    : [Isi nilai Recall dari Soal B3, contoh: 0.88]
- **F1-Score**  : [Isi nilai F1-Score dari Soal B3, contoh: 0.91]

**Kesimpulan Bagian B:**
Dalam penyaringan filter Spam, kesalahan *False Positive* (email penting masuk spam) lebih merugikan daripada *False Negative*. Oleh karena itu, *Threshold* yang lebih tinggi (0.7) dipilih untuk memaksimalkan nilai *Precision* dan menekan angka *False Positive*.

### Bagian Bonus – Perbandingan dengan Scikit-Learn
- **Linear Regression**: Hasil perhitungan intersep dan koefisien manual (*Normal Equation*) identik 100% dengan hasil `scikit-learn`.
- **Logistic Regression**: Terdapat sedikit perbedaan koefisien. Hal ini dikarenakan algoritma manual murni menggunakan *Gradient Descent* biasa, sedangkan default dari `scikit-learn` menerapkan regulariasi penalti L2 (Ridge) untuk mencegah *overfitting*.

---

## 📁 Struktur Repositori
- `README.md` : Dokumentasi informasi identitas dan ringkasan hasil evaluasi.
- `tugas_UTS.ipynb` : *Jupyter Notebook* berisi seluruh kode sumber (pemrosesan data, pembuatan model manual, evaluasi, hingga visualisasi) yang sudah dijalankan lengkap dengan *output*-nya.
- `Ads_Data.csv` : Dataset untuk analisis regresi linier.
- `Email_Data.csv` : Dataset untuk analisis regresi logistik (klasifikasi).
