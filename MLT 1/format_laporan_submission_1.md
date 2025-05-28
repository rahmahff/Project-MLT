# Laporan Proyek Machine Learning - Rahmah Fauziah

![image](https://github.com/user-attachments/assets/aa574687-658c-47a9-9ab3-3d10f410587e)
# House Price Prediction Dataset

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
Data yang digunakan dalam proyek ini adalah [House Price Prediction Dataset](https://www.kaggle.com/datasets/jacksondivakarr/house-price-prediction-dataset) diperoleh dari platform Kaggle. Dataset ini memiliki jumlah sekitar 29.135 data yang berkaitan dengan rumah mewakili 6 fitur yaitu Unnamed: 0, City, Price, Area, Location, dan No. of Bedrooms.

### Variabel-variabel pada House Price Prediction Dataset adalah sebagai berikut:
- `Unnamed: 0` : dapat dikatakan sebagai kolom index baris asli dari dataset yang tidak memuat informasi penting.
- `City` : merupakan kota dari rumah tersebut berada seperti Mumbai, Kolkata, Bangalore, Chennai, Delhi, dan Hyderabad.
- `Price` : merupakan harga rumah yang dijadikan sebagai variabel target jual rumah.
- `Area` : merupakan luas bangunan dari rumah.
- `Location` : merupakan lokasi spesifik rumah seperti New Town, Kharghar, Thane West, Mira Road East, Rajarhat, Uttam Nagar, Noida, Tangra, Ulwe, Dwarka Mor, dan lokasi lainnya.
- `No. of Bedrooms` : merupakan jumlah kamar tidur dalam rumah.

### Exploratory Data Analysis
Tahapan Exploratory Data Analysis (EDA) dilakukan untuk mengetahui investigasi awal untuk melakukan analisis karakteristik dari dataset sebelum dilakukan pemodelan. Proses ini mencakup deskripsi variabel, menangani missing value dan outlier, univariate analysis, dan multivariate analysis.

#### 1. Exploratory Data Analysis - Deskripsi Variabel
Proses ini dilakukan melalui pengecekan informasi pada dataset dengan fungsi `info()`. Berdasarkan fungsi tersebut, diketahui bahwa:
- Terdapat 2 kolom kategorikal dengan tipe data object yaitu kolom City dan Location.
- Terdapat 4 kolom numerik dengan tipe data int64 yaitu Unnamed: 0, Price, Area, dan No. of Bedrooms.
- Kolom target pada dataset ini yaitu Price.
     
![image](https://github.com/user-attachments/assets/45a5d817-f140-4a44-a528-1caab6d332f8)

- Adapun tahapan untuk mengecek deskripsi statistik data dengan fitur `describe()`. Fungsi describe() memberikan informasi statistik pada masing-masing kolom, antara lain:
- Count  adalah jumlah sampel pada data.
- Mean adalah nilai rata-rata.
- Std adalah standar deviasi.
- Min yaitu nilai minimum setiap kolom.
- 25% adalah kuartil pertama. Kuartil adalah nilai yang menandai batas interval dalam empat bagian sebaran yang sama.
- 50% adalah kuartil kedua, atau biasa juga disebut median (nilai tengah).
- 75% adalah kuartil ketiga.
Diketahui bahwa Unnamed: 0 memiliki nilai rata-rata sebesar 3058.808238, nilai min nya itu 0, dan max itu 7718. Pada fitur Price memiliki nilai rata-rata sebesar 1.195267e+07, min 2.000000e+06, dan max 8.546000e+08. Untuk fitur Area memiliki nilai rata-rata sebesar 1301.816475, nilai min 200, dan max 16000. Untuk No. of Bedrooms memiliki nilai mean 2.421074, dengan nilai minimal dan maksimal masing-masing berjumlah 1 dan 9.

![image](https://github.com/user-attachments/assets/38a62547-7873-48a9-af89-04c82601d88f)

#### 2. Exploratory Data Analysis - Menangani Missing Value dan Outliers
Tahapan ini dilakukan untuk mengetahui kolom yang memiliki missing value, baris yang duplikasi, dan outlier. Pada data ini tidak ada nilai yang kosong dan duplikasi. Dapat ditinjau bahwa pada gambar dibawah ini yang menunjukkan tidak adanya missing value:

![image](https://github.com/user-attachments/assets/15f820f1-dac7-4670-9caf-c2a8a2554331)

Adapun untuk mengetahui apakah baris setiap kolom memiliki nilai yang duplikat:

![image](https://github.com/user-attachments/assets/c9bba7f3-da61-4500-a99a-5561e6de1d43)

Adapun melakukan pengecekan outlier pada data numerik yaitu salah satunya pada fitur No. of Bedrooms. 

![image](https://github.com/user-attachments/assets/ebfc480f-ba37-4527-beb8-9dec65fc7f24)

#### 3. Exploratory Data Analysis - Univariate Analysis
Pada tahap ini melakukan analisis data terhadap fitur yang ada, di mana untuk data kategorikal meliputi fitur City dan Location. Terdapat 6 kategori pada fitur city yaitu Mumbai, Kolkata, Bangalore, Chennai, Delhi, dan Hyderabad. Dalam persentase ditunjukkan bahwa lebih dari 40% kota untuk rumah yang banyak diminati terdapat di kota Mumbai dan Kolkata.
   
![image](https://github.com/user-attachments/assets/c6ae8a2a-7d60-4794-afde-f9eebd1f3a5d)

Adapun untuk fitur Location yang diambil 10 kategori dengan jumlah paling banyak secara berurutan yaitu: New Town, Kharghar, Thane West, Mira Road East, Rajarhat, Uttam Nagar, Noida, Tangra, Ulwe, dan Dwarka Mor. Dari data persentase dapat kita simpulkan bahwa lokasi rumah terbanyak berada di New Town sebesar 2.5% dari total 645 sampel, dan sisanya tersebar di berbagai lokasi lainnya.

![image](https://github.com/user-attachments/assets/f4a57782-c3be-45b8-ba83-fda898688c1e)

Adapun pada fitur numerik di bawah ini, di mana menunjukkan visualisasi distribusi pada data numerik. Dapat diketahui bahwa sebagian besar harga rumah mengalami penurunan. Salah satunya pada fitur Price yang merupakan target dalam proyek ini menunjukkan grafik mengalami penurunan seiring dengan semakin banyaknya jumlah sampel. Hal ini dapat dikatakan bahwa distribusi harga miring ke kanan atau right-skewed. Rentang harga rumah dapat dikatakan cukup luas dengan sebagian besar rumah berada di bawah kisaran 10 juta.

![image](https://github.com/user-attachments/assets/8efb0d5f-d994-4097-b4f3-656c1d9e3401)

![image](https://github.com/user-attachments/assets/b2ed47aa-df68-414d-9c15-2f2415293f8d)
     
#### 4. Exploratory Data Analysis - Multivariate Analysis
Pada tahap ini menunjukkan hubungan antara dua atau lebih variabel. Gambar dibawah ini menunjukkan visualisasi rata-rata Price terhadap fitur City dan Location. Pada fitur City, rumah yang memiliki harga tinggi berada pada kota Mumbai sekitar 9,8 juta sedangkan untuk harga terendah berada di kota Kolkata sebesar 5,9 juta. Untuk fitur Location, perbedaan harga antar lokasi cukup signifikan mengingat lokasinya sangat bervariasi, sehingga hanya diambil 10 lokasi saja untuk direpresentasikan. Lokasi yang memiliki harga tertinggi yaitu Thane West sekitar 10 juta, diikuti dengan Kharghar 9 jutaan, dan Mira Road East 8 jutaan. Untuk lokasi dengan rata-rata harga terendah yaitu berada dalam rentang harga 3-4 jutaan yaitu pada lokasi Noida, Uttam Nagar, dan Dwarka Mor. Dapat dikatakan bahwa fitur City dan Location memiliki pengaruh terhadap rata-rata harga rumah.

![image](https://github.com/user-attachments/assets/4e2e65ac-4b42-4d3a-bea5-0a459168c71e)

![image](https://github.com/user-attachments/assets/62c40aec-a0a6-42c1-8ed2-965b9433e7b6)

Adapun untuk fitur numerik, dilakukan observasi hubungan antara fitur numerik dengan fitur target menggunakan fungsi `pairplot()`. Gambar dibawah ini menunjukkan korelasi antara fitur numerik dengan fitur target (Price). Diketahui bahwa relasi fitur Area terhadap fitur Price, di mana titik-titik tersebar cukup merata memenuhi seluruh area plot. Dapat dikatakan bahwa terdapat korelasi antara Area dengan Price namun tidak terlalu kuat. Untuk fitur No. of Bedrooms menunjukkan titik-titik yang vertikal terhadap jumlah kamar, di mana banyaknya kamar tidur dapat mempengaruhi harga rumah, sehingga Price dengan No. of Bedrooms memiliki korelasi yang lemah.

![image](https://github.com/user-attachments/assets/a24c0a32-897f-42fa-a592-eb3ecdb610bb)

Untuk melihat hubungan korelasi matrix antar fitur numerik menggunakan fungsi `heatmap()`. Dapat dilihat bahwa fitur Area memiliki korelasi yang kuat terhadap Price sebesar 0,3. Dapat dikatakan bahwa fitur Area atau luas bangunan memiliki pengaruh terhadap harga rumah. Sementara untuk fitur No. of Bedrooms memiliki nilai korelasi rendah terhadap Price yaitu sebesar 0,15. Terdapat pula korelasi yang cukup kuat pada fitur Area terhadap fitur No. of Bedrooms sebesar 0,74 yang dapat dikatakan bahwa banyaknya jumlah kamar tidur mempengaruhi luas bangunan rumah.
   
![image](https://github.com/user-attachments/assets/d40d8f2d-a0d0-49b8-a34c-12c9009ac8a9)
     
## Data Preparation
Tahapan ini adalah tahapan untuk melakukan proses transformasi pada data sehingga menjadi bentuk yang cocok untuk proses pemodelan. Tahapan preparation meliputi penanganan outlier, encoding fitur kategori, pembagian dataset, dan proses standarisasi.
#### 1. Penanganan Outlier
Penanganan outlier dilakukan pada fitur numerik yaitu Area, Price, dan No. of Bedrooms menggunakan metode IQR (Inter Quartile Range). Proses ini dilakukan untuk mengidentifikasi outlier yang berada di luar Q1 dan Q3. Nilai apa pun yang berada di luar batas ini dianggap sebagai outlier. Adapun bentuk persamaan:

$$
\text{Batas bawah} = Q1 - 1.5 \times IQR
$$

$$
\text{Batas atas} = Q3 + 1.5 \times IQR
$$

Persamaan tersebut diimplementasikan pada kode berikut ini:

```
# Ambil hanya kolom numerikal
numeric_cols = house.select_dtypes(include='number').columns
# Hitung Q1, Q3, dan IQR hanya untuk kolom numerikal
Q1 = house[numeric_cols].quantile(0.25)
Q3 = house[numeric_cols].quantile(0.75)
IQR = Q3 - Q1
# Buat filter untuk menghapus baris yang mengandung outlier di kolom numerikal
filter_outliers = ~((house[numeric_cols] < (Q1 - 1.5 * IQR)) |
                    (house[numeric_cols] > (Q3 + 1.5 * IQR))).any(axis=1)
# Terapkan filter ke dataset asli (termasuk kolom non-numerikal)
house = house[filter_outliers]
# Cek ukuran dataset setelah outlier dihapus
house.shape
```
**Output:** `(25532, 6)`

Hasil pada kode tersebut yaitu `(25532, 6)`. Diketahui bahwa terjadi perubahan pada jumlah sampel, di mana jumlah sampel pertama kali ketika load dataset yaitu sebesar 29.135. Namun, ketika outlier sudah ditangani dengan cara dihapus menggunakan metode IQR hasilnya menjadi 25.532 sampel data.

#### 2. Proses Encoding Fitur Kategorikal
Tahapan ini dilakukan untuk mengubah nilai kategori yaitu City dan Location menjadi bentuk biner menggunakan teknik OneHotEncoding. Implementasi kode pada tahapan ini:
```
# Encoding Fitur Kategori
house = pd.concat([house, pd.get_dummies(house['City'], prefix='City')],axis=1)
house = pd.concat([house, pd.get_dummies(house['Location'], prefix='Location')],axis=1)
house.drop(['City','Location'], axis=1, inplace=True)
house = house.astype('int64')
house.head()
```
Diketahui bahwa hasil dari kode tersebut menunjukkan perubahan yang terjadi pada fitur City dan Location di mana nilainya sudah berubah menjadi variabel numerik atau biner.

![image](https://github.com/user-attachments/assets/70f18061-6a7d-4b01-93cf-ff1f8d625b38)

#### 3. Split Dataset
Tahapan ini digunakan untuk membagi dataset menjadi data latih (train) dan data uji (test) sebelum membuat model. Untuk proporsi pembagian sebesar 80:20 dengan fungsi `train_test_split` dari sklearn.

```X_train, X_test, y_train, y_test = train_test_split(X, y, test_size = 0.2, random_state = 42)```

Diketahui bahwa jumlah sampel setelah dilakukan split dataset untuk data train sebesar 20.425 dan untuk data test sebesar 5.107, sedangkan untuk total keseluruhan dataset yaitu sebesar 25.532 sampel data.

![image](https://github.com/user-attachments/assets/8b16eda2-5479-4ca3-9043-e25b498b4ca2)

#### 4. Standarisasi
Tahapan standarisasi digunakan pada fitur numerik yaitu Area dan No. of Bedrooms dengan menggunakan teknik `StandardScaler` dari library Scikitlearn. Teknik ini bekerja dengan melakukan proses standarisasi fitur dengan mengurangkan mean (nilai rata-rata) kemudian membaginya dengan standar deviasi untuk menggeser distribusi. StandardScaler menghasilkan distribusi dengan standar deviasi sama dengan 1 dan mean sama dengan 0. Adapun untuk implementasi kode berikut ini:

```
# standarisasi - standarscaler
numerical_features = ['Area', 'No. of Bedrooms']
scaler = StandardScaler()
scaler.fit(X_train[numerical_features])
X_train[numerical_features] = scaler.transform(X_train[numerical_features])
X_test[numerical_features] = scaler.transform(X_test[numerical_features])
```

## Modeling
Tahapan ini adalah tahapan Model Development di mana menggunakan algoritma machine learning untuk menjawab problem statement dari tahap business understanding. Pada tahap ini pengembangan model Machine Learning menggunakan 3 algoritma yaitu K-Nearest Neighbor, Random Forest, dan Algoritma Boosting.
#### 1. K-Nearest Neighbor
KNN adalah algoritma yang menggunakan kesamaan fitur untuk memprediksi nilai dari setiap data yang baru. Setiap data baru diberi nilai berdasarkan seberapa mirip titik tersebut dalam set pelatihan. Cara kerja dari KNN dengan menentukan nilai k yang menunjukkan jumlah tetangga terdekat dalam membuat sebuah prediksi. Penentuan nilai k yang terlalu kecil dapat membuat model overfitting sedangkan apabila nilai k terlalu besar dapat menyebabkan model underfitting. Selanjutnya, melakukan perhitungan ukuran jarak. Metrik pengukuran jarak secara default yaitu Minkowski distance, lalu metrik lain yang dapat digunakan seperti Euclidean distance dan Manhattan distance. Selain itu, dapat menemukan tetangga terdekat serta mengambil rata-rata untuk prediksi regresi. Dapat dikatakan bahwa KNN bekerja dengan membandingkan jarak satu sampel ke sampel pelatihan lain dengan memilih sejumlah k tetangga terdekat (dengan k adalah sebuah angka positif). Adapun parameter dalam algoritma yaitu ```n_neighbors=10``` di mana menggunakan k = 10 tetangga, ditunjukkan pada kode di bawah ini yang diawali import `KNeighborsRegressor` dan `mean_squared_error`  dari library sklearn.neighbors dan sklearn.metrics:
```
# Model Development - KNN
from sklearn.neighbors import KNeighborsRegressor
from sklearn.metrics import mean_squared_error

knn = KNeighborsRegressor(n_neighbors=10)
knn.fit(X_train, y_train)

models.loc['train_mse','knn'] = mean_squared_error(y_pred = knn.predict(X_train), y_true=y_train)
```
Terdapat pula kelebihan dan kekurangan pada algoritma ini yaitu:
- Kelebihan: mudah untuk digunakan dan dipahami.
- Kekurangan: kurang efektif digunakan pada dataset yang besar serta prediksi akan memakan waktu cukup lama apabila dataset besar.
     
#### 2. Random Forest
Random forest juga merupakan algoritma yang sering digunakan karena cukup sederhana tetapi memiliki stabilitas yang mumpuni. Random forest merupakan salah satu model machine learning yang termasuk ke dalam kategori ensemble (group) learning, di mana model prediksi yang terdiri dari beberapa model dan bekerja secara bersama-sama. Cara kerja dari Random Forest dapat melalui pendekatan bagging. Bagging atau teknik yang melatih model dengan sampel random. Dalam teknik bagging, sejumlah model dilatih dengan teknik sampling with replacement (proses sampling dengan penggantian). Kemudian memilih sejumlah fitur dan sejumlah sampel secara acak dari dataset yang terdiri dari n fitur dan m sampel. Dilanjutkan dengan membangun model secara independen untuk membuat prediksi. Kemudian, prediksi dari setiap model ensemble ini digabungkan untuk membuat prediksi akhir. Adapun parameter pada algoritma ini:
- n_estimator: jumlah trees (pohon) di forest. 
- max_depth: kedalaman atau panjang pohon. 
- random_state: digunakan untuk mengontrol random number generator yang digunakan.
- n_jobs: jumlah job yang digunakan secara paralel.
Parameter tersebut diimplementasikan pada kode diawali dengan import `RandomForestRegressor` dari library scikit-learn:
```
# Model Development - Random Forest
from sklearn.ensemble import RandomForestRegressor

# buat model prediksi
RF = RandomForestRegressor(n_estimators=50, max_depth=16, random_state=55, n_jobs=-1)
RF.fit(X_train, y_train)

models.loc['train_mse','RandomForest'] = mean_squared_error(y_pred=RF.predict(X_train), y_true=y_train)
```
Untuk kelebihan dan kekurangan meliputi: 
- Kelebihan: dapat menangani hubungan non-linear.
- Kekurangan: sulit untuk menginterpretasikan secara langsung output yang dihasilkan.

#### 3. Algoritma Boosting
Algoritma yang menggunakan teknik boosting bekerja dengan membangun model dari data latih. Kemudian ia membuat model kedua yang bertugas memperbaiki kesalahan dari model pertama. Model ditambahkan sampai data latih terprediksi dengan baik atau telah mencapai jumlah maksimum model untuk ditambahkan. Cara kerja dari algoritma ini yaitu menggabungkan beberapa model sederhana dan dianggap lemah (weak learners) sehingga membentuk suatu model yang kuat (strong ensemble learner). Kemudian melakukan proses identifikasi kesalahan melalui bobot yang lebih tinggi kemudian diberikan pada model yang salah sehingga akan dimasukkan ke dalam tahapan selanjutnya yaitu proses iteratif pada model untuk mencapai akurasi yang diinginkan. Parameter yang digunakan pada algoritma ini:
- learning_rate: bobot yang diterapkan pada setiap regressor di masing-masing proses iterasi boosting.
- random_state: digunakan untuk mengontrol random number generator yang digunakan.
Parameter di atas diimplementasikan pada kode berikut dengan diawali import `AdaBoostRegressor` dari library sklearn.ensemble.
```
# Model Development - Algoritma Boosting
from sklearn.ensemble import AdaBoostRegressor

boosting = AdaBoostRegressor(learning_rate=0.05, random_state=55)
boosting.fit(X_train, y_train)
models.loc['train_mse','Boosting'] = mean_squared_error(y_pred=boosting.predict(X_train), y_true=y_train)
```
Kelebihan dan kekurangan algoritma Boosting:
- Kelebihan: dapat menghasilkan model yang akurat.
- Kekurangan: sensitif terhadap noise dan outlier.

## Evaluation
Tahap ini dilakukan untuk mengetahui performa model yang dilatih. Metrik evaluasi yang digunakan yaitu `Mean Squared Error (MSE)` yang menghitung jumlah selisih kuadrat rata-rata nilai sebenarnya dengan nilai prediksi. Adapun formula dari metrik evaluasi MSE yaitu:

![image](https://github.com/user-attachments/assets/200df7fd-1a3d-4d49-8587-53a2f6c32d61)

Pada formula MSE tersebut, di mana N menunjukkan jumlah dataset. Untuk `yi` sebagai nilai sebenarnya dan `y_pred` adalah nilai prediksi. Selain itu, dapat ditinjau bahwa gambar dibawah ini merupakan hasil proyek berdasarkan metrik evaluasi pada data latih dan data test berdasarkan algoritma yang digunakan yaitu KNN, Random Forest, dan Boosting. Nilai MSE tidak dilakukan penskalaan sehingga masih dalam format satuan asli. Berikut hasil evaluasi model berdasarkan nilai MSE menggunakan algoritma KNN, Random Forest, dan Boosting pada data latih dan data uji pada masing-masing algoritma:

|           | Train MSE             | Test MSE              |
|-----------|-----------------------|-----------------------|
| KNN       | 16840339303812.019531 | 26224980016413.128906 |
| RF        | 9613303955776.796875  | 30023670100653.316406 |
| Boosting  | 18904264506932.152344 | 25418562295376.261719 |

Adapun untuk plot metriknya yang menginterpretasikan hasil evaluasi ketiga model algoritma melalui plot metrik menggunakan bar chart. Pada model Random Forest (RF) menunjukkan nilai error terkecil pada data train, menunjukkan bahwa model dapat mempelajari pola data latih dengan baik. Untuk data test, model Boosting memiliki error paling rendah, sehingga menunjukkan bahwa model ini memiliki kemampuan generalisasi yang lebih baik. Pada model KNN menunjukkan error yang cukup tinggi pada data train maupun test. Model terbaik yang dipilih untuk membantu memprediksi harga rumah yaitu model algoritma Boosting.

![image](https://github.com/user-attachments/assets/1b4b8bb5-1030-4fb5-a4ff-0be1bf832606)

Tahapan di bawah untuk membuat prediksi menggunakan beberapa harga dari data test menggunakan kode:
```
# membuat prediksi menggunakan beberapa harga dari data test
prediksi = X_test.iloc[:1].copy()
pred_dict = {'y_true':y_test[:1]}
for name, model in model_dict.items():
    pred_dict['prediksi_'+name] = model.predict(prediksi).round(1)

pd.DataFrame(pred_dict)
```
Berdasarkan kode diatas menghasilkan keluaran berupa tabel hasil prediksi dengan nama kolom y_true, prediksi_KNN, prediksi_RF, dan prediksi_Boosting. Proses prediksi dilakukan terhadap satu sampel dari data uji untuk mengamati nilai prediksi secara langsung. Hasil menunjukkan bahwa prediksi untuk model dengan algoritma Boosting yang nilainya cukup mendekati dengan nilai y_true dibandingkan dengan dua model lainnya yaitu K-Nearest Neighbor dan Random Forest.

**Tabel Hasil Prediksi:**

|      | y_true  | prediksi_KNN | prediksi_RF | prediksi_Boosting |
|------|---------|--------------|-------------|-------------------|
| 7814 | 2763000 | 6718600.0    | 6854925.0   | 6165064.1         |

**Referensi:**

[1]	Warjiyono, A. Nur Rais, I. Alfarobi, S. Wira Hadi, and W. Kurniawan, “Analisa Prediksi Harga Jual Rumah Menggunakan Algoritma Random Forest Machine Learning,” _JURSISTEKNI (Jurnal Sist. Inf. dan Teknol. Informasi)_, vol. 6, no. 2, pp. 416–423, 2024.

[2]	M. L. Mu’tashim, T. Muhayat, S. A. Damayanti, H. N. Zaki, and R. Wirawan, “Analisis Prediksi Harga Rumah Sesuai Spesifikasi Menggunakan Multiple Linear Regression,” _Inform.  J. Ilmu Komput._, vol. 17, no. 3, p. 238, 2021, doi: 10.52958/iftk.v17i3.3635.
