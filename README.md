# Prediksi Faktor-faktor yang Mempengaruhi Konsumsi Alkohol pada Anak Muda

## Rigkasan

Proyek ini bertujuan untuk memprediksi tingkat konsumsi alkohol pada anak muda berdasarkan berbagai faktor seperti karakteristik demografis dan kebiasaan hidup. Data yang digunakan berasal dari dataset konsumsi alkohol pada siswa di sekolah menengah pertama dan atas. Masalah utama yang ingin diselesaikan adalah menentukan sejauh mana faktor-faktor tersebut mempengaruhi konsumsi alkohol.

## Permasalahan

- Memprediksi nilai konsumsi alkohol harian (Dalc) dan mingguan (Walc) berdasarkan fitur seperti umur, pendidikan orang tua, waktu belajar, dan lain-lain.

## Model

Model awal menggunakan neural network untuk regresi guna memprediksi nilai kontinu.
Model kemudian dikembangkan menjadi model klasifikasi untuk mengelompokkan tingkat konsumsi alkohol ke dalam kategori.

## Penjelasan Dataset, EDA, dan Proses Features Dataset

- Penjelasan Dataset:
- Dataset: Student Alcohol Consumption
- Fitur Utama:
  age: Umur siswa,
  Medu: Pendidikan ibu,
  Fedu: Pendidikan ayah,
  studytime: Waktu belajar mingguan,
  failures: Jumlah kegagalan sebelumnya,
  schoolsup: Dukungan tambahan dari sekolah,
  Dalc: Konsumsi alkohol harian,
  Walc: Konsumsi alkohol mingguan

# Exploratory Data Analysis (EDA)
Langkah-langkah EDA ini bertujuan untuk memahami karakteristik dataset konsumsi alkohol pada anak muda. EDA membantu dalam mengenali pola, mendeteksi anomali, dan mendapatkan wawasan awal tentang data sebelum memulai proses modeling.

> Distribusi Konsumsi Alkohol Harian
![Distribusi konsumsi alkohol harian](https://github.com/user-attachments/assets/7855dda3-682d-4a32-baac-c2cf207e0257)

> Distribusi Konsumsi Alkohol Mingguan
![Distribusi konsumsi alkohol mingguan](https://github.com/user-attachments/assets/0e83bbb8-499a-4c1e-b111-666f52dd7bd9)

> Korelasi antara Fitur
Menghitung dan memvisualisasikan korelasi antara fitur numerik untuk memahami hubungan antar fitur.
![heatmap](https://github.com/user-attachments/assets/5aa674f1-4705-4213-8d4c-63a8085df030)

> Visualisasi Distribusi Umur
Memvisualisasikan distribusi umur siswa untuk memahami komposisi umur dalam dataset.
![visualisasi distribusi umur](https://github.com/user-attachments/assets/5a784f0d-7aab-46de-b9a7-876e6c86b2dc)

>  Analisis Hubungan antara Konsumsi Alkohol dan Absensi
![korelasi antara konsumsi alkohol dan absensi](https://github.com/user-attachments/assets/ce754e9a-7547-4a9f-ba36-a6c9f99e0ec2)

# Proses Features Dataset
- Feature Selection: Memilih fitur yang relevan untuk model, termasuk umur, pendidikan orang tua, waktu belajar, dll.
- Feature Engineering: Ekstraksi informasi tambahan dari fitur yang ada untuk meningkatkan kualitas prediksi.

# Proses Modeling
#### Persiapan Data
Langkah pertama dalam proses modeling adalah menyiapkan data. Ini meliputi pemilihan fitur (X) dan label (y), serta pembersihan data dengan menghapus baris yang memiliki nilai NaN pada target. 

### Pembagian Dataset
Membagi dataset menjadi set pelatihan (training set) dan set pengujian (test set) dengan perbandingan 70:30
```
X_train, X_test, y_train, y_test = train_test_split(X_preprocessed, y, test_size=0.3, random_state=42)
```

### Inisialisasi dan Pelatihan Model
Menggunkan dua model yakni Logistic Regression dan Random Forest

#### Logistic Regression
Menggunakan Grid Search untuk menentukan nilai optimal dari parameter regularisasi (C)
```
# Inisialisasi model
log_reg = LogisticRegression(max_iter=1000)

# Grid search untuk hyperparameter tuning
param_grid_log_reg = {'C': [0.01, 0.1, 1, 10, 100]}
grid_log_reg = GridSearchCV(log_reg, param_grid_log_reg, cv=5)
grid_log_reg.fit(X_train, y_train)
```
#### Random Forest
Menggunakan Grid Search untuk menentukan jumlah tree forest (n_estimators) dan kedalaman maksimum tree (max_depth).
```
# Inisialisasi model
rf_clf = RandomForestClassifier()

# Grid search untuk hyperparameter tuning
param_grid_rf = {'n_estimators': [100, 200, 300], 'max_depth': [None, 10, 20, 30]}
grid_rf = GridSearchCV(rf_clf, param_grid_rf, cv=5)
grid_rf.fit(X_train, y_train)
```

### Evaluasi Model
Evaluasi menggunakan ROC AUC, Accuracy, Precision, Recall, F1 Score dan Confusion Matrix, 

#### ROC Logistic Forest
![ROC Logistic Forest](https://github.com/user-attachments/assets/2e48c5a0-e744-424c-9a6c-a761e15032dc)

#### ROC Random Forest
![ROC Random Forest](https://github.com/user-attachments/assets/26736e59-f800-41d9-b3ea-f56a41fce6ee)

#### Presicion, Recall, F1 Score 
```
Logistic Regression - Accuracy: 0.6974789915966386
Logistic Regression - Precision: 0.6019534027203115
Logistic Regression - Recall: 0.6974789915966386
Logistic Regression - F1 Score: 0.6456495112823037
Random Forest - Accuracy: 0.7226890756302521
Random Forest - Precision: 0.5822981366459627
Random Forest - Recall: 0.7226890756302521
Random Forest - F1 Score: 0.6328876378137461
```

#### Confusion Matrix
![Confusion Matrix Logistic Regression](https://github.com/user-attachments/assets/f9d4a4dc-29a3-4998-8830-5b776be05cef)
![Confusion Matrix Random Forest](https://github.com/user-attachments/assets/554a8c5f-b2e9-47e8-a09b-73a717bcdcde)

#### Analisis Feature Importance
Untuk model Random Forest, ada feature importance untuk mengidentifikasi fitur-fitur yang paling berpengaruh dalam prediksi.
![feature importance](https://github.com/user-attachments/assets/86c8726b-66fd-4434-9da9-4bddc746f39c)


### Perfroma Model
Berikut adalah hasil dari performa modelnya

#### Logistic Regression
```
Accuracy: 0.6974789915966386
Precision: 0.6019534027203115
Recall: 0.6974789915966386
F1 Score: 0.6456495112823037
ROC AUC: Model menunjukkan area di bawah kurva ROC yang baik untuk setiap kelas.
Confusion Matrix: Memperlihatkan distribusi prediksi benar dan salah.
```
#### Random Forest
```
Accuracy: 0.7226890756302521
Precision: 0.5822981366459627
Recall: 0.7226890756302521
F1 Score: 0.6328876378137461
ROC AUC: Model menunjukkan area di bawah kurva ROC yang sangat baik untuk setiap kelas.
Confusion Matrix: Memperlihatkan distribusi prediksi benar dan salah.
Feature Importance: Mengidentifikasi fitur paling berpengaruh dalam prediksi.
```
### Diskusi Hasil dan Kesimpulan
#### Model Regresi
- Memberikan prediksi nilai kontinu yang sesuai dengan tren data historis.
- Namun, interpretasi kurang intuitif dibandingkan dengan kategori kualitas.

#### Model Klasifikasi
- Memberikan hasil yang lebih mudah diinterpretasikan dalam bentuk kategori konsumsi alkohol.
- Evaluasi menunjukkan bahwa model dapat membedakan antara kategori konsumsi dengan akurasi yang memadai.

#### Kesimpulan
Kesimpulannya menurut hasil dari features importance untuk model random forest didapati bahwa pengaruh tertinggi adalah absences atau ketidak hadiran dalam masa pembeljaran, dan juga g1 dan g2 yakni nilai ujian pertama (g1) dan nilai ujian kedua(g2) menunjukan bahwa sebakin banyak absen semakin tinggi faktor dalam mengkonsumsi alkohol begitupun dalam nilai jika nilai lebih rendah kemungkinan besar untuk mengkonsumsi alkohol.
Regresi: Model regresi memberikan analisis mendalam tetapi kurang informatif untuk kategori kualitas alkohol.
Klasifikasi: Model klasifikasi lebih bermanfaat untuk pengambilan keputusan terkait tingkat konsumsi alkohol pada anak muda.
