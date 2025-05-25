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

### Exploratory Data Analysis
1. Exploratory Data Analysis - Deskripsi Variabel
   - Tipe data numerik meliputi: Id, Area, Bedrooms, Bathrooms, Floors, YearBuilt, dan Price.
   - Tipe data kategorikal meliputi: Location, Condition, dan Garage.
     
     ![image](https://github.com/user-attachments/assets/f3e7f1ab-a5c2-4bb9-a2b4-33054b9dfaa8)

   - Adapun deskripsi pada data numerik meliputi count, mean, std, min, 25%, 50%, 75%, dan max berikut ini.

      ![image](https://github.com/user-attachments/assets/bbdaf2d4-b6ff-4b4e-baca-5a9ca4d3c88a)

2. Exploratory Data Analysis - Menangani Missing Value dan Outliers
   - Pada data ini tidak ada nilai yang kosong dan tidak ada outlier. Adapun visualisasi untuk mengetahui ada outlier atau tidak berikut.

     ![image](https://github.com/user-attachments/assets/20c63f2a-0c40-4ba9-9590-689feef6b733)

3. Exploratory Data Analysis - Univariate Analysis
   Pada tahap ini melakukan analisis data terhadap fitur yang ada, untuk fitur kategorikal salah satunya:
   
   ![image](https://github.com/user-attachments/assets/6c202695-d8a3-484f-8b8c-c2b1cdf40a21)

   - Gambar diatas menunjukkan data kategorikal pada fitur lokasi. Terdapat 4 kategori pada fitur lokasi yaitu Downtown, Urban, Suburban, dan Rural. Dalam persentase ditunjukkan bahwa lebih dari 50% lokasi rumah yang banyak diminati pada lokasi Downtown dan Urban.
   Adapun pada fitur numerik di bawah ini:

  ![image](https://github.com/user-attachments/assets/5ef12031-4ca2-4d96-9e96-b54402b072d4)

  ![image](https://github.com/user-attachments/assets/38422f6d-358f-40fc-ac5e-784be66b30e2)

  ![image](https://github.com/user-attachments/assets/172c2b76-0b35-4c7d-95aa-46782df171d8)

   - Gambar diatas menunjukkan visualisasi distribusi pada data numerik. Dapat diketahui bahwa sebagian besar harga rumah berada dalam kisaran yang lebih rendah. Rentang harga rumah yang cukup tinggi sekitar 1.000.000 USD. Untuk fitur Bedrooms, Bathrooms, dan Floors rentang nilai antar satu kategori dengan kategori lainnya tidak jauh berbeda.
     
4. Exploratory Data Analysis - Multivariate Analysis
   Pada tahap ini menunjukkan hubungan antara dua variabel. Adapun untuk fitur kategorikal:

   ![image](https://github.com/user-attachments/assets/9490337d-d314-4423-b0c5-b40f72b2f5de)

   ![image](https://github.com/user-attachments/assets/f003cc5d-6811-4a03-ad56-5000c94fa0ad)

   ![image](https://github.com/user-attachments/assets/6923b081-e16d-44a3-ba47-2f898a9fea0c)

   - Gambar diatas menunjukkan visualisasi rata-rata Price terhadap fitur Location, Condition, dan Garage pada data kategorikal. Pada fitur Location, rentang harga setiap kategori hampir mirip yaitu kisaran 500.000 - 600.000 USD. Adapun kategori yang memiliki harga yang rendah yaitu Location Urban. Sama halnya dengan fitur Location, pada fitur Condition memiliki rentang harga yang sama yaitu pada 500.000 - 600.000 USD. Kategori yang memiliki harga tertinggi berada pada Condition Fair. Untuk fitur Garage, masing-masing kategori memiliki harga yang sama sekitar 500.000 USD.

   Adapun untuk fitur numerik pada proses multivariate analysis:

   ![image](https://github.com/user-attachments/assets/1f1b8cff-0d63-4603-9d9f-92dcca397aad)

   - Pada gambar tersebut menunjukkan korelasi antara fitur numerik dengan fitur target (Price). Dapat dilihat pada fitur Area yang di mana sebarannya membentuk pola yang dapat dikatakan bahwa luas bangunan itu mempengaruhi harga. Begitu pun dengan fitur Bedrooms, Bathrooms, Floors, dan YearBuilt yang membentuk pola tertentu sehingga bisa dikatakan bahwa setiap fitur sama-sama mempengaruhi harga rumah.
   Untuk korelasi matriks:

     
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
