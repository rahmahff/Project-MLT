# Laporan Proyek Machine Learning - Rahmah Fauziah

## Domain Proyek

Rumah merupakan bangunan yang memiliki fungsi sebagai tempat tinggal atau hunian makhluk hidup. Dapat dikatakan bahwa rumah menjadi salah satu kebutuhan pokok bagi semua orang. Namun, seiring dengan perkembangan zaman, harga rumah semakin mengalami peningkatan setiap tahunnya. Kecenderungan akan peningkatan harga rumah sulit untuk diprediksi terutama dipengaruhi oleh beberapa faktor seperti lokasi, struktur fisik, dan faktor pendukung lainnya [1]. 
Keadaan ini dapat menjadi tantangan tersendiri terutama bagi calon pembeli dalam memperkirakan harga rumah yang sesuai dengan faktor spesifikasi yang dimiliki. Dalam hal ini, ketidaksesuaian dalam memprediksi harga rumah dapat menimbulkan kerugian. Salah satu kerugian yang dapat dialami seperti harga rumah yang cenderung lebih mahal dengan spesifikasi yang kurang mumpuni. Untuk itu, diperlukan solusi yang dapat memperkirakan harga rumah secara efektif dan efisien. Prediksi tersebut dapat didasari pada spesifikasi rumah seperti luas bangunan, jumlah kamar mandi, jumlah kamar tidur, dan spesifikasi lainnya [2]. 
Untuk mengatasi permasalahan tersebut, proyek ini dibangun dengan memanfaatkan Machine Learning melalui algoritma Random Forest, K-Nearest Neighbor (KNN), dan algoritma Boosting. Proyek ini diharapkan dapat membantu pengguna baik penjual dan pembeli dalam menentukan keputusan terkait dengan harga rumah yang akurat.

## Business Understanding

### Problem Statements
- Fitur apa saja yang berpengaruh besar terhadap harga rumah?
- Bagaimana cara untuk melakukan prediksi harga rumah berdasarkan fitur luas bangunan, jumlah kamar mandi, jumlah kamar tidur, dan fitur lainnya?

### Goals
- Mengetahui fitur yang mempengaruhi harga rumah.
- Membangun model Machine Learning yang dapat memprediksi harga rumah dengan akurat berdasarkan fitur yang dimiliki.

### Solution Statement
Untuk mencapai tujuan tersebut, solusi yang digunakan dalam membangun model prediksi yaitu memanfaatkan beberapa algoritma yang akan diukur melalui metrik evaluasi MSE (Mean Squared Error) berikut ini:
- K-Nearest Neighbor : mengaplikasikan kemiripan fitur dalam memprediksi nilai pada suatu data.
- Random Forest : model machine learning termasuk ke dalam kategori ensemble atau model prediksi erdiri dari beberapa model dan bekerja secara bersama-sama.
- Algoritma Boosting : model dilatih secara berurutan atau dalam proses yang iteratif.

## Data Understanding
Data yang digunakan dalam proyek ini adalah [House Price Prediction Dataset](https://www.kaggle.com/datasets/zafarali27/house-price-prediction-dataset?resource=download) diperoleh dari platform Kaggle. Dataset ini memiliki jumlah 2.000 data yang berkaitan dengan rumah mewakili 9 fitur yaitu luas bangunan, kamar tidur, kamar mandi, jumlah lantai, tahun dibangun, lokasi, kondisi, garasi, dan harga.

### Variabel-variabel pada House Price Prediction Dataset adalah sebagai berikut:
- Area: merupakan luas bangunan dalam meter persegi.
- Bedrooms : merupakan jumlah kamar tidur dalam rumah.
- Bathrooms: merupakan jumlah kamar mandi dalam rumah.
- Floors: merupakan jumlah lantai dalam rumah.
- Year Built: merupakan tahun rumah dibangun.
- Location: merupakan lokasi rumah seperti pusat kota, daerah perkotaan, daerah pinggiran kota, dan pedesaan.
- Condition: merupakan kondisi rumah seperti sangat baik, baik, cukup, dan buruk.
- Garage: merupakan ketersediaan garasi dalam setiap rumah.
- Price: merupakan variabel target jual rumah dalam satuan USD.

### Visualisasi Data atau Exploratory Data Analysis

**Rubrik/Kriteria Tambahan (Opsional)**:
- Melakukan beberapa tahapan yang diperlukan untuk memahami data, contohnya teknik visualisasi data atau exploratory data analysis.

## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling
Tahapan ini membahas mengenai model machine learning yang digunakan untuk menyelesaikan permasalahan. Anda perlu menjelaskan tahapan dan parameter yang digunakan pada proses pemodelan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan kelebihan dan kekurangan dari setiap algoritma yang digunakan.
- Jika menggunakan satu algoritma pada solution statement, lakukan proses improvement terhadap model dengan hyperparameter tuning. **Jelaskan proses improvement yang dilakukan**.
- Jika menggunakan dua atau lebih algoritma pada solution statement, maka pilih model terbaik sebagai solusi. **Jelaskan mengapa memilih model tersebut sebagai model terbaik**.

## Evaluation
Pada bagian ini anda perlu menyebutkan metrik evaluasi yang digunakan. Lalu anda perlu menjelaskan hasil proyek berdasarkan metrik evaluasi yang digunakan.

Sebagai contoh, Anda memiih kasus klasifikasi dan menggunakan metrik **akurasi, precision, recall, dan F1 score**. Jelaskan mengenai beberapa hal berikut:
- Penjelasan mengenai metrik yang digunakan
- Menjelaskan hasil proyek berdasarkan metrik evaluasi

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.

**Referensi:**

[1]	Warjiyono, A. Nur Rais, I. Alfarobi, S. Wira Hadi, and W. Kurniawan, “Analisa Prediksi Harga Jual Rumah Menggunakan Algoritma Random Forest Machine Learning,” _JURSISTEKNI (Jurnal Sist. Inf. dan Teknol. Informasi)_, vol. 6, no. 2, pp. 416–423, 2024.
[2]	M. L. Mu’tashim, T. Muhayat, S. A. Damayanti, H. N. Zaki, and R. Wirawan, “Analisis Prediksi Harga Rumah Sesuai Spesifikasi Menggunakan Multiple Linear Regression,” _Inform.  J. Ilmu Komput._, vol. 17, no. 3, p. 238, 2021, doi: 10.52958/iftk.v17i3.3635.
