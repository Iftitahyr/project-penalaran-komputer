# 📚 Sistem Prediksi Amar Putusan Berbasis Case-Based Reasoning (CBR)

Repositori ini berisi kode, data, dan notebook Jupyter untuk membangun **sistem pendukung keputusan hukum** yang memprediksi *amar putusan* tindak pidana (contoh: pembunuhan) menggunakan pendekatan **Case-Based Reasoning (CBR)**.  

Pendekatan yang digunakan:
- **Klasik:** TF-IDF + SVM
- **Modern:** IndoBERT (transformer-based embedding)

---

## 📂 Struktur Repository

/data/ # Data mentah & hasil olahan (CSV, JSON, hasil prediksi)
/notebooks/ # Notebook Jupyter untuk preprocessing, training, evaluasi
README.md # Petunjuk instalasi & eksekusi

yaml
Copy
Edit

---

## ⚙️ Dependensi / Requirements

Untuk menjalankan pipeline ini, instal paket Python berikut:

pip install pandas numpy scikit-learn matplotlib seaborn transformers datasets tqdm

yaml
Copy
Edit

✅ Minimum Python versi 3.8.  
✅ Bisa dijalankan di local Jupyter Notebook atau Google Colab.

---

## 🚀 Cara Menjalankan Pipeline *End-to-End*

1️⃣ **Clone repository**

git clone https://github.com/username/nama-repo.git
cd nama-repo

markdown
Copy
Edit

2️⃣ **Install dependensi**

pip install pandas numpy scikit-learn matplotlib seaborn transformers datasets tqdm

markdown
Copy
Edit

3️⃣ **Jalankan notebook Jupyter secara berurutan**

Buka di Jupyter Notebook atau Google Colab.  
Urutan direkomendasikan:

- `01_Preprocessing.ipynb` – Membersihkan & menyiapkan data
- `02_Training_SVM_TFIDF.ipynb` – Training SVM dengan fitur TF-IDF
- `03_Training_IndoBERT.ipynb` – Fine-tuning IndoBERT
- `04_Evaluation.ipynb` – Evaluasi semua model

4️⃣ **Alternatif: Jalankan lokal**

jupyter notebook

yaml
Copy
Edit

atau upload langsung ke Google Colab.

---

## 🗂️ Contoh Struktur Data

Folder `/data/` diisi dengan:

| File                       | Deskripsi                                        |
|----------------------------|-------------------------------------------------|
| `cases_labeled.csv`        | Data kasus dengan label putusan                 |
| `predictions.csv`          | Hasil prediksi retrieval & majority voting      |
| `retrieval_metrics.csv`    | Akurasi metode retrieval                        |
| `prediction_metrics.csv`   | Akurasi model klasifikasi supervised            |
| `queries.json`             | Query uji untuk evaluasi retrieval              |

---

## 📈 Contoh Hasil Evaluasi

| Model                          | Accuracy | Precision | Recall | F1-Score |
|--------------------------------|----------|-----------|--------|----------|
| TF-IDF + Majority Vote         | 80%      | 0.64      | 0.80   | 0.71     |
| TF-IDF + Weighted Similarity   | 80%      | 0.64      | 0.80   | 0.71     |
| SVM Classifier                 | 94%      | 0.93      | 0.94   | 0.93     |
| IndoBERT + Majority Vote       | 80%      | 0.64      | 0.80   | 0.71     |

✅ *Catatan:* Kelemahan pada kelas minoritas (hukuman_mati, seumur_hidup) disebabkan data imbalance.

---

## 📊 Contoh Grafik

Grafik akurasi antar model:

- `notebooks/accuracy_barplot.png`
- Confusion Matrix di setiap notebook evaluasi

---

## 💻 Contoh Perintah

Jika di local, misal untuk menjalankan:

jupyter notebook

yaml
Copy
Edit

atau di Google Colab:

- Upload setiap notebook.
- Pastikan runtime mendukung GPU untuk fine-tuning IndoBERT.

---

## ✅ Ringkasan Hasil Penelitian

Penelitian ini berhasil mengembangkan sistem pendukung keputusan berbasis CBR untuk memprediksi amar putusan dalam kasus pidana dengan dua pendekatan: TF-IDF + SVM (klasik) dan IndoBERT (transformer).  

Hasil evaluasi menunjukkan:
- **SVM** (TF-IDF): Akurasi 94%, F1-score 0.93
- **IndoBERT Majority Vote**: Akurasi 80%, F1-score 0.71

➡️ Model SVM lebih andal untuk data kecil dan terstruktur.  
➡️ IndoBERT memiliki potensi lebih baik untuk menangani konteks semantik jika dilatih lebih lanjut dengan korpus hukum lebih besar.  
➡️ Pendekatan CBR mendukung transparansi rekomendasi berbasis preseden hukum.

---

## ⚠️ Keterbatasan Sistem

- Dataset relatif kecil & imbalance pada kelas tertentu.
- IndoBERT belum di-fine-tune secara mendalam untuk domain hukum Indonesia.
- Model retrieval cenderung bias ke kelas mayoritas.

---

## 💡 Rekomendasi Pengembangan Lanjutan

✅ Lakukan augmentasi data untuk kelas minoritas.  
✅ Fine-tuning IndoBERT pada korpus hukum lebih luas.  
✅ Terapkan *weighted loss* atau *oversampling* untuk menangani imbalance.

---

## 📜 Lisensi

Untuk keperluan akademik. Bebas digunakan dan dimodifikasi dengan mencantumkan kredit.

---

## 🙏 Kontributor