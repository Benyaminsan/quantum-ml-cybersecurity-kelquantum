# Quantum Machine Learning for Cybersecurity

## Anggota Kelompok

| Nama | NRP |
| --- | --- |
| Benjamin | 502723 |
| Abhinaya | 502723 |
| Ricko | 502723 |
| Rizqi | 502723 |
| Gandhi | 502723 |

Repositori pembelajaran dan eksperimen **Quantum Machine Learning (QML)** untuk keamanan siber. Materi di dalamnya membangun pemahaman secara bertahap: mulai dari konsep dasar QML dan machine learning klasik, encoding data ke sirkuit kuantum, quantum kernel methods, hingga Variational Quantum Classifiers (VQC) dan Quantum Neural Networks (QNN).

> Proyek ini bersifat eksperimental dan edukasional. Quantum computing saat ini masih memiliki keterbatasan pada jumlah qubit, noise, kedalaman sirkuit, dan waktu eksekusi. Hasil notebook tidak dimaksudkan sebagai bukti keunggulan quantum ML atas model klasik secara umum.

## Tujuan

- Mempelajari hubungan antara machine learning klasik dan quantum machine learning.
- Membandingkan beberapa strategi encoding data ke state atau sirkuit kuantum.
- Memahami cara membangun dan menggunakan quantum kernel untuk klasifikasi.
- Mencoba VQC/QNN pada dataset sederhana.
- Mengeksplorasi peluang penggunaan QML pada problem cybersecurity, khususnya network intrusion detection.

## Isi repository

### Notebook pembelajaran

| Notebook | Deskripsi |
| --- | --- |
| [`introduction.ipynb`](./introduction.ipynb) | Pengantar QML, supervised dan unsupervised learning, feature map, serta batasan klaim quantum advantage. |
| [`classical-ml-review.ipynb`](./classical-ml-review.ipynb) | Ringkasan supervised learning, kernel methods, SVM, dan neural networks sebagai dasar untuk QML. |
| [`data-encoding.ipynb`](./data-encoding.ipynb) | Eksperimen basis, amplitude, angle, phase, dense, dan strategi encoding lainnya. |
| [`quantum-kernel-methods.ipynb`](./quantum-kernel-methods.ipynb) | Pembuatan kernel matrix dengan feature map kuantum dan penggunaannya pada model klasik seperti SVM. |
| [`qvc-qnn.ipynb`](./qvc-qnn.ipynb) | Implementasi variational quantum circuits untuk klasifikasi pola serta pengantar QVC/QNN. |

### Dataset dan materi pendukung

- [`dataset_graph7.csv`](./dataset_graph7.csv) — dataset CSV yang dapat digunakan untuk eksplorasi data dan eksperimen awal.
- [`A Hybrid Quantum-Classical Network Intrusion Detec/`](./A%20Hybrid%20Quantum-Classical%20Network%20Intrusion%20Detec/) — materi dan dataset tambahan untuk eksperimen network intrusion detection hybrid.
- [`Bab_1`–`Bab_5`](.) dan [`Presentasi_Bab_6_Dataset_HQC_2026_untuk_QML_ITS.pdf`](./Presentasi_Bab_6_Dataset_HQC_2026_untuk_QML_ITS.pdf) — bahan bacaan dan presentasi pendukung.

## Alur belajar yang disarankan

Jalankan notebook dalam urutan berikut:

```text
introduction.ipynb
        ↓
classical-ml-review.ipynb
        ↓
data-encoding.ipynb
        ↓
quantum-kernel-methods.ipynb
        ↓
qvc-qnn.ipynb
```

Notebook dapat dibaca secara mandiri, tetapi pemahaman tentang encoding data dan preprocessing klasik akan membantu sebelum menjalankan quantum kernel atau QVC/QNN.

## Persiapan environment

Gunakan Python 3.10 atau versi yang lebih baru. Buat virtual environment dari root repository:

```bash
python -m venv .venv
```

Aktifkan environment:

```bash
# Windows PowerShell
.\.venv\Scripts\Activate.ps1

# macOS/Linux
source .venv/bin/activate
```

Install paket dasar yang digunakan notebook:

```bash
pip install jupyterlab notebook numpy pandas matplotlib scikit-learn qiskit qiskit-aer
```

Kemudian buka JupyterLab:

```bash
jupyter lab
```

Pilih kernel `.venv` dan buka notebook yang ingin dijalankan.

> Dependensi dapat berbeda antar-notebook dan versi Qiskit dapat memengaruhi API. Jika hanya ingin mempelajari satu notebook, install paket sesuai import dan cell yang digunakan di notebook tersebut.

## Menjalankan dengan IBM Quantum

Sebagian eksperimen quantum kernel dapat dijalankan menggunakan simulator, sedangkan eksekusi pada perangkat IBM Quantum membutuhkan akun dan kredensial IBM Quantum.

Untuk eksperimen pada hardware nyata:

1. Buat akun pada [IBM Quantum](https://quantum.ibm.com/).
2. Konfigurasi kredensial sesuai dokumentasi Qiskit/IBM Quantum.
3. Jalankan cell terkait secara hati-hati karena hardware nyata memiliki antrean, noise, dan batas penggunaan.

Untuk pembelajaran awal, simulator lokal seperti Aer lebih mudah direproduksi dan tidak memerlukan akun cloud.

## Catatan tentang dataset cybersecurity

Dataset intrusion detection umumnya berukuran besar dan memiliki banyak fitur. Sebelum memasukkannya ke sirkuit kuantum, lakukan preprocessing seperti:

- membersihkan missing value dan data duplikat;
- mengubah fitur kategorikal menjadi representasi numerik;
- melakukan scaling/normalisasi fitur;
- memilih atau mereduksi fitur agar sesuai dengan jumlah qubit;
- membagi data menjadi training dan testing secara konsisten.

Jumlah fitur tidak otomatis sama dengan jumlah qubit untuk semua metode encoding. Pilihan encoding, kedalaman sirkuit, dan karakteristik dataset harus dievaluasi bersama.

## Reproducibility

Untuk mendapatkan hasil yang lebih konsisten:

- gunakan seed pada generator bilangan acak;
- catat versi Python dan paket yang digunakan;
- simpan konfigurasi simulator, jumlah shots, feature map, dan optimizer;
- bedakan hasil simulator ideal, simulator noisy, dan hardware nyata;
- bandingkan selalu dengan baseline classical ML yang sesuai.

## Roadmap

- Menambahkan pipeline preprocessing dataset cybersecurity yang terdokumentasi.
- Membuat baseline classical ML dan metrik evaluasi intrusion detection.
- Membandingkan model klasik, quantum kernel, dan model hybrid pada subset fitur yang sama.
- Menambahkan konfigurasi environment yang reproducible.
- Mendokumentasikan hasil eksperimen, keterbatasan, dan analisis biaya komputasi.

## Lisensi dan atribusi

Periksa lisensi setiap dataset, notebook, gambar, dan materi pembelajaran pihak ketiga sebelum mendistribusikan ulang repositori. Tambahkan file `LICENSE` apabila proyek ini akan dipublikasikan dengan lisensi tertentu.
