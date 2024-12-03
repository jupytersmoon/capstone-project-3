# capstone-project-3
## Project Introduction
Project ini akan menerapkan machine learning untuk klasifikasi data Travel Insurance. Data diklasifikasikan ke dalam 2 kelas:
* Tidak klaim (No)
* Klaim (Yes)

Ada 8 fitur yang akan digunakan:
* Agency type (kategorikal)
* Distribution channel (kategorikal)
* Product name (kategorikal)
* Duration (numerik)
* Destination (kategorikal)
* Net sales (numerik)
* Commision (value) (numerik)
* Age (numerik)

Ada 1 target:
* Claim: Yes/No

### Data Preprocessing
* Fitur dengan kategori yang banyak dipangkas dengan menggabungkan kategori bervalue rendah ke dalam 1 kategori yaitu "others"
* Menghapus data janggal dan extreme outlier dari data numerik
* Melakukan robust scaling ke fitur numerik karena memiliki banyak outlier
* Mengubah string data kategorikal ke lowercase
* One hot encoding data kategorikal
* Mengubah target kelas menjadi 0 untuk "No" dan 1 untuk "Yes"

### Modelling: Classification
* Cek Logit dan VIF dari fitur
* EDA, perbedaan banyak anggota kedua kelas sangat besar("No"=98.5%. "Yes"=1.5%)
* Data splitting: train dan validation
* Imbalance classification: SMOTE, random under sampling, random over sampling, near miss, cross-validation+balancing, hyperparameter (didapatkan metode SMOTE sebagai metode yang memberikan hasil paling baik)
* Logistic Regression: default, weighted (penalized)
* KNN: n = 1,2,3,4,5 (dipilih 4 karena paling bagus)
* Decision Tree: max_depth = 1,2,3,4,5,6 (dipilih 5 karena paling bagus)

### Model Evaluation
* Karena banyak anggota kelas yang tidak seimbang, maka metrik yang paling baik digunakan adalah Recall, termasuk ROC-AUC
* Confusion matrix
* 3 model yang diuji: (KNN tidak dipakai karena eksekusi terlalu lama)
  1. SMOTE + Logistic Regression default
  2. SMOTE + Weighted Logistic Regression
  3. Weighted Logistic Regression (without SMOTE)
* Model yang diambil adalah yang memiliki Recall kelas 0 + Recall kelas 1 terbesar (Model 2)

### Pickle
* Menggunakan library dill untuk pickle python function
* Function yang di-pickle adalah function yang akan preprocess data mentah/input dan memodelkan sesuai dengan model pilihan kemudian memberikan output prediksi kelas (0 atau 1)

# PENTING: Pickle
Pastikan format data input sesuai dengan format data Travel Insurance
