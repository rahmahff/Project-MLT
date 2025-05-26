# Laporan Proyek Machine Learning - Rahmah Fauziah

## Domain Proyek

Rumah merupakan bangunan yang memiliki fungsi sebagai tempat tinggal atau hunian makhluk hidup. Dapat dikatakan bahwa rumah menjadi salah satu kebutuhan pokok bagi semua orang. Namun, seiring dengan perkembangan zaman, harga rumah semakin mengalami peningkatan setiap tahunnya. Kecenderungan akan peningkatan harga rumah sulit untuk diprediksi terutama dipengaruhi oleh beberapa faktor seperti lokasi, struktur fisik, dan faktor pendukung lainnya [1]. 
Keadaan ini dapat menjadi tantangan tersendiri terutama bagi calon pembeli dalam memperkirakan harga rumah yang sesuai dengan faktor spesifikasi yang dimiliki. Dalam hal ini, ketidaksesuaian dalam memprediksi harga rumah dapat menimbulkan kerugian. Salah satu kerugian yang dapat dialami seperti harga rumah yang cenderung lebih mahal dengan spesifikasi yang kurang mumpuni. Untuk itu, diperlukan solusi yang dapat memperkirakan harga rumah secara efektif dan efisien. Prediksi tersebut dapat didasari pada spesifikasi rumah seperti luas bangunan, jumlah kamar tidur, dan spesifikasi lainnya [2]. 
Untuk mengatasi permasalahan tersebut, proyek ini dibangun dengan memanfaatkan Machine Learning melalui algoritma Random Forest, K-Nearest Neighbor (KNN), dan algoritma Boosting. Proyek ini diharapkan dapat membantu pengguna baik penjual dan pembeli dalam menentukan keputusan terkait dengan harga rumah yang akurat.

## Business Understanding

### Problem Statements
- Fitur apa saja yang berpengaruh besar terhadap harga rumah?
- Bagaimana cara untuk melakukan prediksi harga rumah berdasarkan fitur luas bangunan, jumlah kamar tidur, dan fitur lainnya?

### Goals
- Mengetahui fitur yang mempengaruhi harga rumah.
- Membangun model Machine Learning yang dapat memprediksi harga rumah dengan akurat berdasarkan fitur yang dimiliki.

### Solution Statement
Untuk mencapai tujuan tersebut, solusi yang digunakan dalam membangun model prediksi yaitu memanfaatkan beberapa algoritma berikut ini:
- K-Nearest Neighbor : mengaplikasikan kemiripan fitur dalam memprediksi nilai pada suatu data.
- Random Forest : model machine learning termasuk ke dalam kategori ensemble atau model prediksi erdiri dari beberapa model dan bekerja secara bersama-sama.
- Algoritma Boosting : model dilatih secara berurutan atau dalam proses yang iteratif.
Selain itu, menangani proses outlier, one-hot encoding, melakukan proses scaling pada fitur numerik dengan menggunakan StandarScaler, serta melakukan proses evaluasi dengan menggunakan metrik Mean Squared Error (MSE).

## Data Understanding
Data yang digunakan dalam proyek ini adalah [House Price Prediction Dataset](https://www.kaggle.com/datasets/jacksondivakarr/house-price-prediction-dataset) diperoleh dari platform Kaggle. Dataset ini memiliki jumlah sekitar 29.135 data yang berkaitan dengan rumah mewakili 5 fitur yaitu luas bangunan, kamar tidur, kota, lokasi, dan harga.

### Variabel-variabel pada House Price Prediction Dataset adalah sebagai berikut:
- `City` : merupakan kota dari rumah tersebut.
- `Price` : merupakan variabel target jual rumah.
- `Area` : merupakan luas bangunan dari rumah.
- `Location` : merupakan lokasi rumah.
- `No. of Bedrooms` : merupakan jumlah kamar tidur dalam rumah.

### Exploratory Data Analysis
1. Exploratory Data Analysis - Deskripsi Variabel
   - Tipe data numerik meliputi: Unnamed: 0, Price, Area, dan No. of Bedrooms.
   - Tipe data kategorikal meliputi: City dan Location.
     
     ![image](https://github.com/user-attachments/assets/45a5d817-f140-4a44-a528-1caab6d332f8)

   - Adapun deskripsi pada data numerik meliputi count, mean, std, min, 25%, 50%, 75%, dan max berikut ini.

      ![image](https://github.com/user-attachments/assets/38a62547-7873-48a9-af89-04c82601d88f)

2. Exploratory Data Analysis - Menangani Missing Value dan Outliers
   - Pada data ini tidak ada nilai yang kosong dan duplikasi. Dapat ditinjau bahwa pada gambar dibawah ini tidak terdapat nilai kosong dan duplikasi pada data.
     ```
     missing_values = house.isnull().sum()
     missing_values[missing_values > 0]
     ```
     Dengan hasil output:
     
     ![image](https://github.com/user-attachments/assets/a649f592-a169-4882-adf6-d7a2c9c1b8a0)
     
     ```
     duplicates = house.duplicated()
     print("Baris duplikat:")
     print(house[duplicates])
     ```
     Output pada kode tersebut:
     
     ![image](https://github.com/user-attachments/assets/c9bba7f3-da61-4500-a99a-5561e6de1d43)

   - Adapun melakukan pengecekan outlier pada data numerik yaitu salah satunya pada fitur No. of Bedrooms. Diketahui bahwa terdapat outlier pada fitur tersebut sehingga membuat filter untuk dapat menghapus baris yang mengandung outlier.
     
     ![image](https://github.com/user-attachments/assets/12df8374-eec5-4b3a-9787-73792bd0f133)

3. Exploratory Data Analysis - Univariate Analysis
   
   Pada tahap ini melakukan analisis data terhadap fitur yang ada, untuk data kategorikal pada fitur lokasi. Terdapat 6 kategori pada fitur city yaitu Mumbai, Kolkata, Bangalore, Chennai, Delhi, dan Hyderabad. Dalam persentase ditunjukkan bahwa lebih dari 40% kota untuk rumah yang banyak diminati pada kota Mumbai dan Kolkata.
   
   ![image](https://github.com/user-attachments/assets/c6ae8a2a-7d60-4794-afde-f9eebd1f3a5d)

   Adapun pada fitur numerik di bawah ini, di mana menunjukkan visualisasi distribusi pada data numerik. Dapat diketahui bahwa sebagian besar harga rumah mengalami penurunan seiring dengan semakin banyaknya jumlah sampel pada sumbu y. Begitu pun pada fitur area yang mengalami penurunan dan peningkatan pada sampelnya.

  ![image](https://github.com/user-attachments/assets/8efb0d5f-d994-4097-b4f3-656c1d9e3401)

  ![image](https://github.com/user-attachments/assets/b2ed47aa-df68-414d-9c15-2f2415293f8d)
     
4. Exploratory Data Analysis - Multivariate Analysis
   
   Pada tahap ini menunjukkan hubungan antara dua variabel. Gambar dibawah ini menunjukkan visualisasi rata-rata Price terhadap fitur City dan Location. Pada fitur City, rumah yang memiliki harga tinggi berada pada kota Mumbai dan Delhi. Pada fitur Location diambil 10 data lokasi yang di mana harga meningkat berdasarkan lokasi dari rumah.

   ![image](https://github.com/user-attachments/assets/4e2e65ac-4b42-4d3a-bea5-0a459168c71e)

   ![image](https://github.com/user-attachments/assets/62c40aec-a0a6-42c1-8ed2-965b9433e7b6)

   Adapun untuk fitur numerik pada proses multivariate analysis. Gambar dibawah ini menunjukkan korelasi antara fitur numerik dengan fitur target (Price). Terlihat sebaran data membentuk pada fitur Area terhadap Price. Pada No. of Bedrooms terlihat memiliki korelasi, namun tidak terlalu kuat. 

   ![image](https://github.com/user-attachments/assets/a24c0a32-897f-42fa-a592-eb3ecdb610bb)

   Untuk korelasi matriks terdapat pada gambar dibawah ini. Dapat dilihat bahwa fitur Area memiliki korelasi yang kuat terhadap Price sebesar 0,3. Dapat dikatakan bahwa fitur Area atau luas bangunan memiliki pengaruh terhadap harga rumah. Sementara untuk fitur No. of Bedrooms memiliki nilai korelasi rendah terhadap Price yaitu sebesar 0,15. Terdapat pula korelasi yang cukup kuat pada fitur Area terhadap fitur No. of Bedrooms sebesar 0,74 yang dapat dikatakan bahwa banyaknya jumlah kamar tidur mempengaruhi luas bangunan rumah.
   
   ![image](https://github.com/user-attachments/assets/d40d8f2d-a0d0-49b8-a34c-12c9009ac8a9)

     
## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.
Teknik yang digunakan pada tahapan data preparation meliputi proses:
- Encoding fitur kategori yaitu pada fitur City dan fitur Location dengan memanfaarkan one-hot encoding menggunakan kode:
  ```
  pd.get_dummies
  ```
  Hal ini dilakukan untuk mengubah data kategorikal menjadi numerik, untuk memudahkan dalam pemrosesan data karena pada dasarnya algoritma Machine Learning hanya dapat memproses data numerik.
- Pemisahan data melalui proses split data yaitu train dan test, di mana dengan rasio 80:20. Sebanyak 80% data untuk data latih dan 20% untuk data uji. Adapun kode yang digunakan pada tahapan ini yaitu:
  ```
  X_train, X_test, y_train, y_test = train_test_split(X, y, test_size = 0.2, random_state = 42)
  ```
- Standarisasi untuk fitur numerik dengan menggunakan one hot encoding. Fitur numerik yang di standarisasi yaitu fitur Area dan No. of Bedrooms. Hal ini dilakukan untuk menyamakan skala fitur numerik serta dapat membuat fitur data menjadi bentuk yang lebih mudah diolah oleh algoritma. , di mana untuk kodenya berikut ini:
  ```
  scaler = StandardScaler()
  scaler.fit(X_train[numerical_features])
  X_train[numerical_features] = scaler.transform(X_train[numerical_features])
  X_test[numerical_features] = scaler.transform(X_test[numerical_features])
  ```

## Modeling
Pada tahapan ini digunakan beberapa model algoritma untuk dapat membantu dalam memprediksi harga rumah berdasarkan fitur yang sudah ada. Berikut algoritma yang digunakan:
1. K-Nearest Neighbor
   - Parameter pada algoritma ini: ```n_neighbors=10``` di mana menggunakan k = 10 tetangga. 
   - Kelebihan: mudah untuk digunakan dan dipahami.
   - Kekurangan: kurang efektif digunakan pada dataset yang besar.
2. Random Forest
   - Parameter pada algoritma ini: ```n_estimators=50``` untuk menentukan jumlah pohon dalam hutan, ```max_depth=16``` menentukan kedalaman atau panjang pohon, dan ```random_state=55``` untuk mengontrol random number generator yang digunakan, serta ```n_jobs=-1``` jumlah pekerjaan yang digunakan secara paralel. 
   - Kelebihan: dapat menangani hubungan non-linear.
   - Kekurangan: sulit untuk menginterpretasikan secara langsung output yang dihasilkan.
4. Algoritma Boosting
   - Parameter pada algoritma ini: ```learning_rate=0.05``` yaitu bobot yang diterapkan pada setiap regressor di masing-masing proses iterasi boosting, serta ```random_state=55``` untuk mengontrol random number generator yang digunakan. 
   - Kelebihan: dapat menghasilkan model yang akurat.
   - Kekurangan: sensitif terhadap noise dan outlier.

## Evaluation
Metrik evaluasi yang digunakan yaitu Mean Squared Error (MSE) yang menghitung jumlah selisih kuadrat rata-rata nilai sebenarnya dengan nilai prediksi. Adapun formula dari metrik evaluasi MSE yaitu:

![image](https://github.com/user-attachments/assets/200df7fd-1a3d-4d49-8587-53a2f6c32d61)

Pada formula MSE tersebut, di mana N menunjukkan jumlah dataset. Untuk yi sebagai nilai sebenarnya dan y_pred adalah nilai prediksi. Selain itu, dapat ditinjau bahwa gambar dibawah ini merupakan hasil proyek berdasarkan metrik evaluasi pada data latih dan data test berdasarkan algoritma yang digunakan yaitu KNN, Random Forest, dan Boosting.

![image](https://github.com/user-attachments/assets/c998c607-b73c-491a-b643-adfeeee2da33)

**Referensi:**

[1]	Warjiyono, A. Nur Rais, I. Alfarobi, S. Wira Hadi, and W. Kurniawan, “Analisa Prediksi Harga Jual Rumah Menggunakan Algoritma Random Forest Machine Learning,” _JURSISTEKNI (Jurnal Sist. Inf. dan Teknol. Informasi)_, vol. 6, no. 2, pp. 416–423, 2024.

[2]	M. L. Mu’tashim, T. Muhayat, S. A. Damayanti, H. N. Zaki, and R. Wirawan, “Analisis Prediksi Harga Rumah Sesuai Spesifikasi Menggunakan Multiple Linear Regression,” _Inform.  J. Ilmu Komput._, vol. 17, no. 3, p. 238, 2021, doi: 10.52958/iftk.v17i3.3635.
