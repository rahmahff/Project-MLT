# Laporan Proyek Machine Learning - Rahmah Fauziah

![image](https://github.com/user-attachments/assets/fe0df260-3ab4-49b8-bcec-4635b714aee7)
# Movie Recommendation System

## Project Overview

Di era perkembangan teknologi digital saat ini membuat industri perfilman saling bersaing satu sama lain dalam memproduksi film yang menarik banyak penonton. Berbagai macam film dengan alur hingga tema cerita yang berbeda maupun serupa masif diproduksi dan mudah diakses dalam berbagai platform digital. Kegiatan menonton film telah menjadi salah satu bentuk hiburan yang dapat mengatasi kejenuhan akan suatu hal. Di lain sisi, semakin banyaknya film yang tersedia menyebabkan permasalahan yaitu penonton sulit untuk menentukan film mana yang akan ditonton. Dalam menentukan pilihannya, penonton biasanya bergantung pada hasil review pengguna lain. Namun mengingat jumlah review banyak semakin mempersulit dalam mencari film yang sesuai dengan keinginan sehingga memakan banyak waktu [1]. Untuk itu, diperlukan sistem rekomendasi film dalam memberikan saran yang sesuai dengan keinginan pengguna. Sistem rekomendasi digunakan untuk merekomendasikan suatu item pada pengguna dengan memperkirakan nilai item tersebut, di mana apabila memiliki nilai prediksi tinggi akan ditampilkan sebagai rekomendasi utama [2]. Adapun pendekatan pada sistem rekomendasi meliputi dua macam yaitu _Content-Based Filtering_ dan C_ollaborative Filtering_. _Content-Based Filtering_ adalah pendekatan rekomendasi yang mengacu pada fitur dari konten film seperti genre film [3]. _Collaborative Filtering_ adalah memperkirakan relevansi item berdasarkan penilaian dari pengguna, di mana akan merekomendasikan item yang sudah dipilih oleh pengguna dengan pola kesamaan dari pengguna saat ini [4]. 

## Business Understanding

### Problem Statements
- Bagaimana cara untuk membangun sistem rekomendasi film yang dapat membantu pengguna dalam menentukan film sesuai dengan keinginan?
- Bagaimana sistem rekomendasi dapat memberikan saran film yang serupa berdasarkan genre film yang sudah ditonton sebelumnya? 

### Goals
- Mengembangkan sistem rekomendasi film yang dapat membantu pengguna menemukan film yang sesuai dengan teknik pendekatan _content-based filtering_.
- Menghasilkan sistem rekomendasi yang dapat memuaskan pengguna dalam memilih film berdasarkan keakuratan dan relevansi.

### Solution statements
Untuk mencapai tujuan tersebut, solusi yang digunakan dalam membangun sistem rekomendasi film yaitu memanfaatkan pendekatan berikut ini:
- _Content-Based Filtering_: rekomendasi berdasarkan item yang mirip dengan item yang disukai pengguna dengan teknik TF-IDF Vectorizer dan Cosine Similarity.

## Data Understanding
Data yang digunakan dalam proyek ini adalah [Movie Recommendation System](https://www.kaggle.com/datasets/parasharmanas/movie-recommendation-system) diperoleh dari platform Kaggle. Dataset ini memiliki 2 file csv yaitu `movies.csv` dan `ratings.csv`. Untuk data movies.csv memiliki 3 kolom yaitu movieId, title, dan genres. Adapun data untuk ratings.csv memiliki 4 kolom yaitu userId, movieId, rating, dan timestamp. 

Variabel-variabel pada Movie Recommendation System adalah sebagai berikut:
- `movieId` : Id unik terkait film.
- `title` : Judul film beserta dengan tahun perilisan.
- `genres` : kategori film yang terdiri lebih dari satu genre.
- `userId` : Id unik pengguna.
- `rating` : Nilai rating yang diberikan pengguna.
- `timestamp` : Waktu pemberian rating oleh pengguna. 

### Exploratory Data Analysis 
Tahap ini dilakukan untuk mengetahui investigasi awal untuk melakukan analisis karakteristik dari dataset.
#### Univariate Analysis
Tahapan ini untuk melakukan analisis dan eksplorasi setiap variabel pada data. Adapun variabel nya meliputi 2 macam yaitu movies dan ratings.
- `movies` : merupakan data yang berisikan informasi terkait film yang meliputi kolom movieId, title, dan genres.
- `ratings` : merupakan data rating dari film berisikan kolom userId, movieId, rating, dan timestamp.
  
#### 1. Eksplorasi Variabel
Proses ini dilakukan melalui pengecekan informasi pada data movies dan ratings dengan fungsi `info()`.
- Data `movies.csv`
Dapat diketahui bahwa jumlah data movies.csv sebanyak 62423 entri dan 3 kolom. Terdapat 3 kolom untuk data movies meliputi:
    - `movieId` merupakan Id film yang bertipe data int64.
    - `title` merupakan judul film yang memiliki tipe data object.
    - `genres` merupakan genre pada film yang memiliki tipe data object.
Bentuk tampilan baris pada data movies.csv melalui fungsi `head()` dengan menampilkan lima baris pertama berikut ini.

  | movieId | Title                              | Genres                                          |
  |---------|------------------------------------|-------------------------------------------------|
  | 1       | Toy Story (1995)                   | Adventure, Animation, Children, Comedy, Fantasy |
  | 2       | Jumanji (1995)                     | Adventure, Children, Fantasy                    |
  | 3       | Grumpier Old Men (1995)            | Comedy, Romance                                 |
  | 4       | Waiting to Exhale (1995)           | Comedy, Drama, Romance                          |
  | 5       | Father of the Bride Part II (1995) | Comedy                                          |
Tabel tersebut menampilkan tiga kolom yaitu movieId, title, dan genres yang berisikan data setiap kolom. Untuk movieId berisikan data nilai unik setiap film, title berisikan judul film dilengkapi dengan tahun perilisannya, dan genres berisikan macam-macam genre dari film dengan dipisahkan oleh tanda (|).

- Data `ratings.csv`
Dapat diketahui bahwa jumlah data ratings.csv sebanyak 25000095 baris dan 4 kolom. Terdapat 4 kolom untuk data ratings meliputi:
    - `userId` merupakan Id pengguna yang bertipe data int64.
    - `movieId` merupakan Id film bertipe data int64.
    - `rating` merupakan nilai rating film yang bertipe data float64.
    - `timestamp` merupakan waktu pemberian rating yang bertipe data int64.
Bentuk tampilan baris pada data ratings.csv melalui fungsi `head()` dengan menampilkan lima baris pertama berikut ini.

  | userId | movieId | rating | timestamp   |
  |--------|---------|--------|-------------|
  | 1      | 296     | 5.0    | 1147880044  |
  | 1      | 306     | 3.5    | 1147868817  |
  | 1      | 307     | 5.0    | 1147868828  |
  | 1      | 665     | 5.0    | 1147878820  |
  | 1      | 899     | 3.5    | 1147868510  |
Tabel tersebut menampilkan empat kolom yaitu userId, movieId, rating, dan timestamp yang berisikan data setiap kolom. Untuk userId berisikan data nilai unik pengguna, movieId berisikan data nilai unik setiap film, rating berisikan nilai rating yang diberikan pengguna, dan timestamp berisikan waktu pemberian rating.

Pada data ratings.csv dilakukan pengecekan deskripsi statistik data ratings dengan fitur `describe()`. Fungsi describe() memberikan informasi statistik pada masing-masing kolom, antara lain:
- Count adalah jumlah sampel pada data.
- Mean adalah nilai rata-rata.
- Std adalah standar deviasi.
- Min yaitu nilai minimum setiap kolom.
- 25% adalah kuartil pertama. Kuartil adalah nilai yang menandai batas interval dalam empat bagian sebaran yang sama.
- 50% adalah kuartil kedua, atau biasa juga disebut median (nilai tengah).
- 75% adalah kuartil ketiga.
Diketahui bahwa nilai maksimum rating adalah 5 dan nilai minimum adalah 0,5. Untuk rata-rata pemberian rating oleh pengguna berada di kisaran 3,5. Hal ini menunjukkan bahwa pengguna memberikan rating yang cukup tinggi untuk film nya. Jumlah pengguna dan film memiliki nilai maksimum 1.625410e+05 dan dan 2.091710e+05 dan nilai minimum adalah 1.000000e+00.

  |           | userId       | movieId      | rating       | timestamp    |
  |-----------|--------------|--------------|--------------|--------------|
  | count     | 2.500010e+07 | 2.500010e+07 | 2.500010e+07 | 2.500010e+07 |
  | mean      | 8.118928e+04 | 2.138798e+04 | 3.533854e+00 | 1.215601e+09 |
  | std       | 4.679172e+04 | 3.919886e+04 | 1.060744e+00 | 2.268758e+08 |
  | min       | 1.000000e+00 | 1.000000e+00 | 5.000000e-01 | 7.896520e+08 |
  | 25%       | 4.051000e+04 | 1.196000e+03 | 3.000000e+00 | 1.011747e+09 |
  | 50%       | 8.091400e+04 | 2.947000e+03 | 3.500000e+00 | 1.198868e+09 |
  | 75%       | 1.215570e+05 | 8.623000e+03 | 4.000000e+00 | 1.447205e+09 |
  | max       | 1.625410e+05 | 2.091710e+05 | 5.000000e+00 | 1.574328e+09 |

Pada data ratings melakukan peninjauan terhadap banyaknya pengguna yang memberikan rating dan banyaknya jumlah rating. Dapat diketahui bahwa jumlah pengguna yang memberikan rating berdasarkan kolom unik yaitu userId sebanyak 162541 sedangkan untuk jumlah rating sebanyak 25000095. Proses ini dilakukan menggunakan kode:
```
print('Jumlah userId: ', len(ratings['userId'].unique()))
print('Jumlah data rating: ', len(ratings))
```
**Output:** 
  ```
  Jumlah userId:  162541
  Jumlah data rating:  25000095
  ```

#### 2. Pengecekan nilai missing value
Pada tahap ini melakukan pengecekan terhadap kolom data movies dan ratings apakah memiliki nilai missing values dengan menggunakan fungsi `isnull().sum()`. Pada data ini tidak ada nilai yang kosong sehingga keluaran berupa 0.

#### 3. Pengecekan duplikasi data
Tahap ini untuk melakukan identifikasi pada data movies dan ratings apakah terdapat baris yang memiliki duplikasi menggunakan fungsi `duplicated()`. Diketahui bahwa tidak ada baris yang memiliki duplikasi ditunjukkan dengan keluaran `Baris duplikat: Empty DataFrame`.

## Data Preparation
Tahapan ini adalah tahapan untuk mempersiapkan data sebelum tahap modelling. Pada tahap ini diawali dengan melakukan perubahan tipe data timestamp menjadi datetime melalui fungsi `pd.to_datetime`, sehingga menampilkan hasil perubahan data pada kolom timestamp menjadi bentuk datetime.

  | userId | movieId | rating | timestamp           |
  |--------|---------|--------|---------------------|
  | 1      | 296     | 5.0    | 2006-05-17 15:34:04 |
  | 1      | 306     | 3.5    | 2006-05-17 12:26:57 |
  | 1      | 307     | 5.0    | 2006-05-17 12:27:08 |
  | 1      | 665     | 5.0    | 2006-05-17 15:13:40 |
  | 1      | 899     | 3.5    | 2006-05-17 12:21:50 |

Pada tahap ini pula melakukan penggabungan data ratings dengan movies berdasarkan nilai movieId menggunakan fungsi `merge()`. Hal tersebut menghasilkan penggabungan data ratings dengan movies yang di mana kolom title dan genres pada data movies ditambahkan ke sebelah kiri pada kolom data ratings, sehingga menghasilkan 6 kolom dan 25000095 baris, seperti:

![image](https://github.com/user-attachments/assets/bea3c9b1-a9e9-45e9-90ba-6f8f8d231cb7)

Kemudian, dilanjutkan dengan melakukan proses pengurutan movies_info berdasarkan movieId kemudian memasukkannya ke dalam variabel fix_movies. Proses ini dengan menggunakan fungsi `sort_values()` melalui teknik Ascending atau mengurutkan nilai dari yang terkecil ke terbesar, di mana memiliki jumlah baris 25000095 dan 6 kolom. Hal ini dilakukan agar data terlihat rapi dan berurutan.

![image](https://github.com/user-attachments/assets/75e5c62d-1f16-4e21-9ace-cb73452c53e3)

Tahap selanjutnya melakukan pengecekan jumlah dari fix_movies berdasarkan movieId yang bernilai unik menggunakan kode di bawah ini. Hasil menunjukkan bahwa jumlah data dari fix_movies adalah 59047.
``` len(fix_movies.movieId.unique()) ```
Selain itu, dilakukan pengecekan untuk kategori genres yang unik yang di mana menghasilkan berbagai macam genre dengan adanya kombinasi genre pada film. Proses ini dilakukan melalui kode berikut.
``` fix_movies.genres.unique() ```
Tahap selanjutnya melakukan pembuatan variabel preparation yang berisi dataframe fix_movies kemudian mengurutkan berdasarkan movieId yang menghasilkan keluaran:

![image](https://github.com/user-attachments/assets/15360f96-8220-401c-92d7-5e4cf530cf1e)

Setelah membuat variabel preparation, tahap lainnya yaitu menghapus data duplikasi pada variabel preparation menggunakan fungsi `drop_duplicates` berdasarkan kolom movieId. Pada awalnya jumlah baris sebanyak 25000095 seperti gambar diatas. Namun, terjadi perubahan ketika sudah menghapus data duplikasi menjadi 59047 baris dan 6 kolom.

![image](https://github.com/user-attachments/assets/5e9dba61-443b-490a-be92-f6a9fc2c139e)

Kemudian, melakukan proses konversi data series menjadi bentuk list menggunakan fungsi `tolist()`. Untuk data yang di konversi adalah data kolom movieId, title, dan genres, menghasilkan keluaran jumlah data sebesar 59047 pada masing-masing kolom:

![image](https://github.com/user-attachments/assets/69bdb226-ea3c-4adc-be44-7c8ba5c5dddf)

Sebelum masuk tahap modeling, tahap selanjutnya melakukan pembuatan dictionary untuk menentukan pasangan key-value pada data movies_id, movies_title, dan movies_genres. Proses ini berisikan tiga kolom yaitu id yang berisikan movies_id, movies_title berisikan data movies_title, dan genres berisikan data movies_genres. Untuk jumlah baris datanya adalah 59047.

![image](https://github.com/user-attachments/assets/d424c3a4-3ca5-43d5-8e10-ee1892014bf3)

## Modeling
Tahap ini dilakukan melalui pendekatan _Content Based Filtering_.
### 1. _Content Based Filtering_
Tahapan ini adalah melakukan pembangunan model sistem rekomendasi menggunakan pendekatan Content Based Filtering. Pendekatan ini dilakukan untuk mengetahui rekomendasi item yang mirip dengan item yang disukai pengguna yaitu film didasari pada kategori genre. Proses ini diawali dengan TF-IDF Vectorizer untuk melakukan perhitungan idf pada data genres dan mapping array fitur index integer ke fitur nama, melalui fungsi `tfidfvectorizer()` dari library sklearn. Kemudian, melakukan fit dan mentransformasikan dalam bentuk matriks yang menghasilkan keluaran (59047, 20). Hal tersebut menunjukkan bahwa 59047 adalah ukuran data dan 20 merupakan matriks kategori genre. Setelah itu, dilanjutkan dengan mengubah vektor tf-idf dalam bentuk matriks dengan menggunakan fungsi `todense()` dan melakukan pembatasan data hanya 1000 data saja. Dilanjutkan dengan membuat dataframe yang berisikan genre (kolom) dan judul film (baris). Hasil menunjukkan bahwa terdapat korelasi antara judul film dengan genre ditunjukkan adanya output 1.0 seperti:

![image](https://github.com/user-attachments/assets/7881058c-a1a8-4ee0-befc-8fc2557220a2)

Dalam hal ini, terdapat kelebihan dan kekurangan pada pendekatan ini yaitu:
- Kelebihan: dapat memberikan rekomendasi yang personal mengingat tidak bergantung pada pengguna lain.
- Kekurangan: kurang efektif digunakan untuk rekomendasi item yang berbeda dari yang sudah disukai pengguna.

Dari proses tersebut, dilakukan proses rekomendasi melalui fungsi `def movies_recommendations`, terdiri dari beberapa parameter sebagai berikut:
- Judul_film: judul_film (index kemiripan dataframe).
- Similarity_data : Dataframe mengenai similarity yang telah kita definisikan sebelumnya yaitu cosine_sim_df.
- Items : judul dan genre yang digunakan untuk mendefinisikan kemiripan, dalam hal ini adalah movies_title dan genres.
- k : Banyak rekomendasi yang ingin diberikan yaitu berjumlah 5.

Rekomendasi di uji coba pada film dengan judul Toy Story (1995), didapatkan 5 data teratas yaitu:


| No | Judul Film                         | Genre                                           |
|----|------------------------------------|-------------------------------------------------|
| 0  | Space Jam (1996)                   | Adventure, Animation, Children, Comedy, Fantasy |
| 1  | Pagemaster, The (1994)             | Action, Adventure, Animation, Children, Fantasy |
| 2  | Kids of the Round Table (1995)     | Adventure, Children, Comedy, Fantasy            |
| 3  | NeverEnding Story III, The (1994)  | Adventure, Children, Fantasy                    |
| 4  | Jumanji (1995)                     | Adventure, Children, Fantasy                    |


## Evaluation
Tahap ini dilakukan untuk mengetahui hasil evaluasi dari sistem rekomendasi film. Metrik evaluasi yang digunakan yaitu Cosine Similarity yang melakukan pengukuran derajat berdasarkan kesamaan atau seberapa mirip sebuah data. Adapun formula dari metrik evaluasi Cosine Similarity yaitu:

$$
\cos(\theta) = \frac{A \cdot B}{\|A\| \|B\|}
$$

Keterangan:
- A dan B adalah vektor yang akan dibandingkan kesamaannya.
- A . B adalah dot product antara kedua vektor A dan B.
- |A| dan |B| adalah panjang dari vektor A dan B.
- |A||B| adalah cross product antara |A| dan |B|

Proses cosine similarity dilakukan dengan menggunakan kode di bawah ini.
```
# Membuat dataframe dari variabel cosine_sim dengan baris dan kolom berupa nama movie
cosine_sim_df = pd.DataFrame(cosine_sim, index=data['movies_title'][:1000], columns=data['movies_title'][:1000])
print('Shape:', cosine_sim_df.shape)

# Melihat similarity matrix pada setiap movie
cosine_sim_df.sample(5, axis=1).sample(10, axis=0)
```
Tahapannya dilakukan dengan mengidentifikasi kesamaan antara film yang satu dengan yang lainnya, ditunjukkan dengan memiliki angka 1.0 mengindikasikan bahwa film pada kolom X (horizontal) memiliki kesamaan dengan film pada baris Y (vertikal). Shape yang digunakan berukuran (1000, 1000) seperti:

![image](https://github.com/user-attachments/assets/e95634fa-7ca0-495f-b044-41795eee713f)

## Referensi
[1]	M. Fajriansyah, P. P. Adikara, and A. W. Widodo, “Sistem Rekomendasi Film Menggunakan Content Based Filtering,” _J. Pengemb. Teknol. Inf. dan Ilmu Komput._, vol. 5, no. 6, pp. 2188–2199, 2021.

[2]	K. R. Sari, W. Suharso, and Y. Azhar, “Pembuatan Sistem Rekomendasi Film dengan Menggunakan Metode Item Based Collaborative Filtering pada Apache Mahout,” _J. Repos._, vol. 2, no. 6, p. 767, 2020, doi: 10.22219/repositor.v2i6.936.

[3]	S. Lestari and M. M. Ramdhani, “Sistem Rekomendasi Film Menggunakan Metode Content-Based Filtering Studi Kasus Materi Data Mining Di Smk Idn Boarding School,” _J. Indones.  Manaj. Inform. dan Komun._, vol. 4, no. 3, pp. 1581–1587, 2023, doi: 10.35870/jimik.v4i3.381.

[4]	E. R. Agustian, Munir, and E. P. Nugroho, “Sistem Rekomendasi Film Menggunakan Metode Collaborative Filtering dan K-Nearest Neighbors,” J_ATIKOM J. Apl. dan Teor. Ilmu Komput._, vol. 3, no. 1, pp. 18–21, 2020, [Online]. Available: https://ejournal.upi.edu/index.php/JATIKOM
