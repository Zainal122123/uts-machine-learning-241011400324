# Tugas UTS Machine Learning

Repositori ini berisi implementasi algoritma **Linear Regression** dan **Logistic Regression** yang dibangun secara manual menggunakan NumPy (tanpa *library* Scikit-Learn untuk algoritma utamanya), sebagai bagian dari Ujian Tengah Semester mata kuliah Machine Learning.

## 👤 Identitas Mahasiswa
- **Nama**  : Muhamad Zaenal
- **NIM**   : 241011400324
- **Kelas** : 05TPLE005

---

##  Ringkasan Hasil Evaluasi Model

## Ringkasan Hasil Pengerjaan (Soal A1 – Bonus)

### Bagian A – Linear Regression (Prediksi Penjualan)
Model dilatih untuk memprediksi angka `Penjualan` berdasarkan `Biaya Iklan` menggunakan metode analitik (*Normal Equation*) dan iteratif (*Gradient Descent*).
- **Hasil Pelatihan Terbaik**: Melalui *Gradient Descent* dengan *Learning Rate* = 0.02, model berhasil konvergen secara optimal dan menghasilkan bobot yang sama dengan hitungan *Normal Equation*, yaitu **Intercept ($b$) = 28.1439** dan **Koefisien ($m$) = 9.1356**.
- **Evaluasi Model**: 
  - $R^2$: 0.932561 (Data Training), 0.979957 (Data Testing)
  - RMSE : 6.451991	 (Data Training), 3.695744`(Data Testing)
- **Analisis Prediksi**: Terdapat korelasi linear positif antara biaya iklan dan penjualan. Namun, prediksi *ekstrapolasi* (misal: menebak target penjualan untuk biaya iklan 12 juta yang jauh di luar data latih) terbukti tidak ideal karena di dunia nyata terdapat titik jenuh pasar (*diminishing returns*).

### Bagian B – Logistic Regression (Filter Email Spam)
Model klasifikasi biner dilatih menggunakan *Gradient Descent* untuk mendeteksi email `Spam` atau `Bukan Spam` berdasarkan fitur `JumlahLink` dan `KataPromo`.
- **Pelatihan**: Kurva *Log Loss* berhasil menurun drastis dan stabil pada *Learning Rate* = 0.1 setelah ribuan iterasi.
- **Evaluasi Threshold (Batas Probabilitas)**:
  - Default (0.5): `[Isi dengan angka Akurasi/Precision dari tabel B5]`
  - Pilihan Optimal (0.7): Dalam konteks filter email, kesalahan *False Positive* (email penting salah tebak masuk spam) sangat merugikan. Menaikkan *threshold* ke **0.7** terbukti meningkatkan nilai **Precision** dan menekan *False Positive* serendah mungkin.
- **Decision Boundary**: Visualisasi menunjukkan titik-titik kesalahan tebak (*error*) mayoritas berada di area abu-abu atau *outlier* yang sulit dipisahkan hanya dengan garis linear tegak lurus.

### Bagian C – Pemahaman Konsep
Bagian ini menguraikan analisis teoretis mencakup:
- Alasan *Logistic Regression* tergolong klasifikasi (dibantu oleh peran fungsi *Sigmoid* mengubah garis linear menjadi probabilitas 0-1).
- Keunggulan komputasi *Gradient Descent* untuk data besar dibanding memori raksasa yang dibutuhkan oleh invers matriks pada *Normal Equation*.
- Pentingnya evaluasi pada *data testing* murni untuk mencegah kebohongan akurasi akibat *overfitting*.
- Pemilihan *Log Loss* untuk klasifikasi agar ruang pencarian *error* tetap berbentuk *convex* (mangkuk mulus), berbeda dengan kontur *MSE* yang bisa bergelombang jika digunakan pada probabilitas.

### 🌟 Bonus – Perbandingan dengan Scikit-Learn
Pengujian ulang menggunakan fungsi bawaan `sklearn.linear_model` menghasilkan komparasi berikut:
- **Linear Regression**: Bobot manual dan bawaan *library* **identik 100%** ($b$ = 28.1439, $m$ = 9.1356) karena keduanya berbasis *Ordinary Least Squares* tanpa regulariasi.
- **Logistic Regression**: Terdapat selisih bobot antara manual ($b$ = -11.4233, $m_1$ = 1.0424, $m_2$ = 0.8993) dengan default Scikit-Learn ($b$ = -10.6331, $m_1$ = 0.9605, $m_2$ = 0.8379). Perbedaan ini terjadi karena `LogisticRegression` pada Scikit-Learn secara *default* mengaktifkan fitur penalti/regulariasi L2 (Ridge) untuk menyusutkan nilai bobot agar tidak *overfitting*.

## 📁 Struktur Repositori
- `README.md` : Dokumentasi informasi identitas dan ringkasan hasil evaluasi.
- `tugas_UTS.ipynb` : *Jupyter Notebook* berisi seluruh kode sumber (pemrosesan data, pembuatan model manual, evaluasi, hingga visualisasi) yang sudah dijalankan lengkap dengan *output*-nya.
- `Ads_Data.csv` : Dataset untuk analisis regresi linier.
- `Email_Data.csv` : Dataset untuk analisis regresi logistik (klasifikasi).
