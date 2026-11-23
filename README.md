# Prediksi Harga Rumah di Bekasi Menggunakan XGBoost Regressor

Proyek akhir mata kuliah **Pengantar Data Science (PDS)** untuk memprediksi harga properti residensial di wilayah Bekasi menggunakan algoritma **XGBoost Regressor** serta membandingkannya dengan beberapa model regresi lainnya[cite: 1].

---

## 👥 Anggota Kelompok 6 (Kelas B)

**Program Studi D3 Sistem Informasi**  
**Fakultas Ilmu Komputer — UPN "Veteran" Jakarta (2026)**

| Nama Lengkap | NIM |
| :--- | :---: |
| **Nafizza Azzahra** | 2510501061 |
| **Muhammad Syauqi Rabbani** | 2510501065 |
| **Malva Nurul Fitria** | 2510501041 |
| **Adilah Azzahra** | 2510501045 |

---

## 📊 Deskripsi Dataset

* **Sumber File:** `Dataset 500 Rumah Jabodetabek - Dataset UAS PDS.csv`
* **Ukuran Data:** 500 baris data properti di kota **Bekasi** dengan 27 atribut awal
* **Pembagian Data:** 80% Data Latih (400 sampel) dan 20% Data Uji (100 sampel)
* **Distribusi Wilayah Teratas:** Harapan Indah (74), Jati Asih (42), Bekasi (34), Summarecon Bekasi (30), Jatisampurna (25), Bekasi Utara (25)

---

## 🛠️ Tahapan Pemrosesan & Pemodelan

1. **Data Cleaning & Feature Engineering**
   * Ekstraksi nilai numerik daya listrik ke dalam satuan watt (`electricity_watt`).
   * Perhitungan jumlah fasilitas dari daftar fasilitas (`facility_count`).
   * Penjumlahan total kamar tidur (`total_bedrooms`) dan kamar mandi (`total_bathrooms`).
   * Standardisasi nilai dan penanganan *missing value* pada fitur kategorikal (`property_condition`, `certificate`, `furnishing`).
2. **Exploratory Data Analysis (EDA)**
   * Analisis distribusi harga properti (dalam Miliar Rupiah), hubungan luas bangunan terhadap harga, variasi harga berdasarkan kondisi bangunan, serta matriks korelasi antarfitur numerik.
3. **Preprocessing Pipeline**
   * **Fitur Numerik:** Imputasi median (`SimpleImputer`) dan penskalaan (`StandardScaler`).
   * **Fitur Kategorikal:** Imputasi nilai konstan dan pengkodean (`OneHotEncoder`).
4. **Pelatihan & Evaluasi Model**
   * Membandingkan **Multiple Linear Regression**, **Ridge Regression**, **Random Forest Regressor**, **Gradient Boosting Regressor**, dan **XGBoost Regressor**.

---

## 📈 Hasil Evaluasi Model

### Perbandingan Model (Baseline)

| Model | R² Train | R² Test | MAE (Rp) | RMSE (Rp) | MAPE (%) |
| :--- | :---: | :---: | :---: | :---: | :---: |
| Multiple Linear Regression | 0.760 | 0.541 | Rp 368.647.750 | Rp 753.967.496 | 32.09% |
| Ridge Regression | 0.760 | 0.541 | Rp 367.009.317 | Rp 753.347.209 | 31.80% |
| Random Forest Regressor | 0.964 | 0.551 | Rp 315.296.264 | Rp 745.260.044 | 21.55% |
| Gradient Boosting Regressor | 0.959 | 0.565 | Rp 311.461.815 | Rp 733.828.066 | 23.39% |
| XGBoost Regressor (Default) | 0.925 | 0.551 | Rp 326.076.907 | Rp 745.199.664 | 26.23% |

### Performa XGBoost Regressor (Tuned)
Dengan konfigurasi `n_estimators=100`, `max_depth=4`, `learning_rate=0.08`, `subsample=0.8`, dan `colsample_bytree=0.8`:
* **R² Score (Data Latih):** `0.971`
* **R² Score (Data Uji):** `0.571`
* **MAE:** `Rp 306.269.612`
* **RMSE:** `Rp 728.738.036`
* **MAPE:** `23.76%`

---

## 💻 Struktur Repositori

```text
├── Prediksi_Harga_Rumah_Bekasi.ipynb   # Notebook utama analisis, pemodelan, dan visualisasi
└── README.md                           # Dokumentasi proyek

## 🚀 Cara Menjalankan

1. Klik tombol **Open in Colab** di bagian atas file `Prediksi_Harga_Rumah_Bekasi.ipynb`.
2. Unggah file dataset `Dataset 500 Rumah Jabodetabek - Dataset UAS PDS.csv` ke direktori `/content/` di Google Colab.
3. Jalankan seluruh sel kode secara berurutan (**Runtime > Run all**).
