# Laporan Tugas SML A
## Anggota
**Nama:** Narendra A, Nicholas B, Aldi M 
**NRP:** 014, 011, 130

## Employee Attrition Prediction
**Dataset file:** `train.csv`, `test.csv`, dan `submission_stacking_Last3.csv`

## Tujuan
**Memprediksi kemungkinan karyawan akan keluar (attrition)** dari perusahaan berdasarkan data profil dan perilaku kerja mereka.  
Dengan model machine learning dapat mengidentifikasi faktor yang berkontribusi terhadap keputusan karyawan untuk resign.

---

## Dataset
Dataset berisi informasi personal dan profesional dari setiap karyawan.

| Jenis Kolom        | Contoh Variabel                                           | Keterangan                              |
|--------------------|-----------------------------------------------------------|-----------------------------------------|
| Identitas          | `id`, `EmployeeNumber`                                    | Penanda unik tiap karyawan              |
| Demografi          | `Age`, `Gender`, `MaritalStatus`, `Education`             | Informasi pribadi                       |
| Jabatan            | `Department`, `JobRole`, `JobLevel`                       | Posisi dan tanggung jawab               |
| Kinerja & Kepuasan | `PerformanceRating`, `JobSatisfaction`, `WorkLifeBalance` | Penilaian subjektif dan objektif        |
| Kompensasi         | `MonthlyIncome`, `PercentSalaryHike`, `StockOptionLevel`  | Gaji dan tunjangan                      |
| Aktivitas Kerja    | `OverTime`, `DistanceFromHome`, `YearsAtCompany`          | Pola kerja dan pengalaman               |
| Target             | `Attrition`                                               | 1 = Karyawan keluar, 0 = Tetap bekerja  |

Jumlah data pada file `train.csv`: **1176 baris × 36 kolom**  
File `test.csv` memiliki kolom yang sama **tanpa kolom `Attrition`**.

---

## Langkah Analisis
Analisis dilakukan menggunakan **Python (Kaggle Notebook)** dengan tahapan berikut:

1. **Exploratory Data Analysis (EDA)**  
   - Mengecek tipe data, missing values, dan distribusi target  
   - Visualisasi hubungan antara fitur dan `Attrition`  
   - Contoh visualisasi: usia vs attrition, lembur vs attrition, jabatan vs attrition

2. **Data Preprocessing**  
   - Encoding kolom kategorikal (`LabelEncoder` / `OneHotEncoder`)  
   - Normalisasi data numerik (`StandardScaler`)  
   - Split dataset menjadi data latih (train) dan validasi (validation)

3. **Modeling**  
   - Model yang digunakan:
     - Logistic Regression
     - Random Forest Classifier
     - (opsional) XGBoost / LightGBM
   - Setiap model dievaluasi dengan **ROC-AUC**.

4. **Evaluasi Model**  
   - Metrik utama: **ROC-AUC**  
   - ROC-AUC mengukur kemampuan model membedakan antara karyawan yang keluar vs tetap  
   - Model terbaik dipilih berdasarkan nilai ROC-AUC tertinggi

5. **Feature Importance**  
   - Mengetahui fitur yang paling mempengaruhi attrition  
   - Biasanya: `OverTime`, `MonthlyIncome`, `YearsAtCompany`, `JobSatisfaction`

6. **Submission**  
   - Menggunakan model terbaik untuk memprediksi data `test.csv`  
   - Menyimpan hasil ke file `submission_stacking_Last3.csv`

---

## Hasil
Faktor berpengaruh terhadap keputusan karyawan untuk keluar:
- OverTime (Lembur)
- MonthlyIncome (Pendapatan Bulanan)
- YearsAtCompany (Lama Bekerja)
- JobSatisfaction (Kepuasan Kerja)

---

## Kesimpulan
Model machine learning berhasil mengidentifikasi pola attrition dengan tingkat pemisahan yang cukup tinggi (ROC-AUC > 0.9).  
Hasil ini dapat membantu tim HR untuk:
- Mengurangi turnover karyawan dengan fokus pada faktor risiko tinggi (lembur, gaji, kepuasan kerja)
- Membuat kebijakan retensi yang lebih efisien

---
