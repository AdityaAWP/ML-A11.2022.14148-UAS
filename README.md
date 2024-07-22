![Distribusi konsumsi alkohol harian](https://github.com/user-attachments/assets/1f4869db-9a52-4fa1-9edd-4d5266826562)# Prediksi Faktor-faktor yang Mempengaruhi Konsumsi Alkohol pada Anak Muda

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
  age: Umur siswa
  Medu: Pendidikan ibu
  Fedu: Pendidikan ayah
  studytime: Waktu belajar mingguan
  failures: Jumlah kegagalan sebelumnya
  schoolsup: Dukungan tambahan dari sekolah
  Dalc: Konsumsi alkohol harian
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
