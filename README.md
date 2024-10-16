# Laporan Proyek Machine Learning - Moh. Aflah Azzaky

## Domain Proyek
---
Penyakit kardiovaskular (CVD) merupakan penyebab kematian nomor 1 secara global, merenggut sekitar 17,9 juta jiwa setiap tahunnya, atau menyumbang 31% dari seluruh kematian di seluruh dunia. Empat dari kematian 5CVD disebabkan oleh serangan jantung dan stroke, dan sepertiga dari kematian ini terjadi sebelum waktunya pada orang di bawah usia 70 tahun. Gagal jantung adalah kejadian umum yang disebabkan oleh penyakit kardiovaskular dan kumpulan data ini berisi 11 fitur yang dapat digunakan untuk memprediksi kemungkinan penyakit jantung.

Orang dengan penyakit kardiovaskular atau yang memiliki risiko kardiovaskular tinggi (karena adanya satu atau lebih faktor risiko seperti hipertensi, diabetes, hiperlipidemia, atau penyakit yang sudah ada) memerlukan deteksi dan manajemen dini sehingga model pembelajaran mesin dapat sangat membantu.[[1](https://www.kaggle.com/fedesoriano/heart-failure-prediction)]

Penyakit gagal jantung dapat disebabkan oleh beberapa kondisi penyakit jantung. Menurut WHO, penyakit jantung atau yang disingkat sebagai CVD (Cardiovascular disease) adalah kelompok gangguan pada jantung dan pembuluh darah yang termasuk diataranya: coronary heart disease, cerebrovascular disease, rheumatic heart disease, dan kondisi jantung lainnya. Lebih dari 4 dari 5 kematian atas CVD disebabkan oleh gagal jantung dan strokes, dan sepertiga dari angka kematian tersebut merupakan orang yang mati premature dibawah umur 70. Faktor resiko penyakit ini seringnya disebabkan oleh diet yang tidak sehat, kurang berolahraga, serta penggunaan rokok dan alkohol yang berlebih. Sifatnya yang menyerang mendadak menyebabkan dikembangkannya teknologi yang dapat memprevensi. EKG sebagai salah satu teknologi hasil yang dikembangkan berkontribusi memberikan tanda dan informasi akan aktifitas aliran listrik pada jantung.[[2](https://jurnal.unprimdn.ac.id/index.php/JUSIKOM/article/view/2445)]

## Business Understanding
---
### Problem Statements

Berdasarkan latar belakang diatas, berikut ini rumusan masalah yang dapat diselesaikan pada proyek ini:
- Bagaimana cara melakukan pra-pemrosesan pada data penyakit gagal jantung yang akan digunakan untuk membuat model yang baik?
- Bagaimana cara membuat model untuk memprediksi penyakit gagal jantung pada manusia menggunakan machine learning?

### Goals Statements

Berdasarkan rumusan masalah diatas, berikut ini tujuan yang dapat diselesaikan pada proyek ini:
- Melakukan pra-pemrosesan data dengan baik agar dapat digunakan dalam pembuatan model.
- mengetahui cara membuat model machine learning untuk memprediksi penyakit gagal jantung pada manusia berdasarkan rata-rata umur.

### Solution Statements

Berdasarkan tujuan diatas, berikut ini solusi yang dapat diselesaikan pada proyek ini:
- Untuk pra-pemrosesan data dapat dilakukan dengan beberapa teknik diantaranya:
   * Melakukan *drop* pada kolom `FastingBS` karena tidak diperlukan dalam analisis data.
   * Mengatasi masalah data yang kosong dengan cara menghapus beberapa data yang terindikasi kosong yang menyebabkan data statistik bernilai 0.
   * Melakukan Encoding terhadap kolom yang bertipe data `object`.
   * Melakukan pembagian dataset menjadi dua bagian dengan rasio 80:20, 80% untuk data latih dan 20% untuk data uji.
   * Melakukan *Standard Scaler*.

- Untuk penggunaan model dengan algoritma kami uji beberapa algoritma diantaranya Algoritma Random Forest, Algoritma K-Nearest Neighbor, dan Algoritma Boosting.

## Data Understanding
---
Data pada project ini menggunakan data yang bersumber pada sebuah situs kaggle, dimana fokus pada data tersebut menjelaskan faktor-faktor yang akan mempengaruhi sebuah penyakit gagal jantung.[[Kaggle Dataset - Heart Failure Prediction Dataset](https://www.kaggle.com/datasets/fedesoriano/heart-failure-prediction)]

Informasi dataset dapat dilihat pada tabel dibawah ini :
Jenis | Keterangan
--- | ---
Sumber | [Kaggle Dataset - Heart Failure Prediction Dataset](https://www.kaggle.com/datasets/fedesoriano/heart-failure-prediction)
Lisensi | Open Database
Kategori | Health, Health Conditions, Classification, Heart Conditions, Healthcare
Jenis dan Ukuran Berkas | CSV (35.92 kB)

Pada berkas yang diunduh yakni heart.csv berisi 918 rows x 12 columns. Kolom-kolom tersebut berisi diantaranya 1 kolom berisi tipe data `float64`, 6 kolom berisi tipe data `int64`, dan 5 kolom berisi tipe data `object`. Untuk penjelasan mengenai variabel dapat dilihat sebagai berikut:
1. **Age**: usia pasien dalam jumlah tahun dengan tipe data `int64`
2. **Sex**: jenis kelamin pasien dengan kategori M = Male/Pria dan F = Female/Perempuan dengan tipe data object
3. **ChestPainType**: jenis nyeri dada dengan kategori TA: Typical Angina, ATA: Atypical Angina, NAP: Non-Anginal Pain, ASY: Asymptomatic dengan tipe data object
   - *Typical Angina* adalah nyeri dada yang disebabkan oleh aktivitas fisik atau stres emosional, dan berkurang saat istirahat atau mengonsumsi nitrogliserin.
   - *Atypical Angina* adalah nyeri dada yang tidak memenuhi kriteria angina tipikal, tetapi sesuai dengan penyebab iskemik jantung.
   - *Non-Anginal Pain* adalah nyeri dada yang tidak disebabkan oleh penyakit jantung.
   - *Asymptomatic* adalah istilah yang menggambarkan kondisi seseorang yang menderita penyakit, tetapi tidak menunjukkan gejala klinis apa pun.
4. **RestingBP**: tekanan darah istirahat dengan tipe data `int64`.
5. **Cholesterol**: kolesterol serum dengan tipe data `int64`.
6. **FastingBS**: gula darah puasa dengan tipe data `int64`.
7. **RestingECG**: hasil elektrokardiogram istirahat dengan kategori Normal, ST = Mengalami kelainan gelombang ST-T, LVH = menunjukkan kemungkinan atau pasti hipertrofi ventrikel kiri dengan tipe data `object`.
8. **MaxHR**: detak jantung maksimum tercapai dengan tipe data `int64` yang berisi nilai numerik antara 60 dan 202.
9. **ExerciseAngina**: angina akibat olahraga dengan kategori Y = Yes/Iya & N = No/Tidak bertipe data `object`.
10. **Oldpeak**: puncak tua nilai numerik yang diukur pada depresi bertipe data `float64`.
11. **ST_Slope**: kemiringan segmen ST terhadap denyut jantung (heart rate) yang dihitung dengan linear regression dengan kategori Up: upsloping, Flat: flat, Down: downsloping bertipe data `object`.
12. **HeartDisease**: penyakit jantung dengan hasil keluaran 1 = penyakit jantung dan 0 = normal bertipe data `int64`.

## Data Loading
---
Berikut adalah tahapan dalam melakukan data loading:
- Menginstall dan import library yang diperlukan seperti:
  * *Libray* Numpy digunakan untuk memproses larik atau array.
  * *Libray* Matplotlib digunakan membuat visualisasi data dalam dua dimensi.
  * *Libray* Seaborn dibangun di ata *library* Matplotlib, digunakan untuk membuat visualisasi data.
  * *Libray* Pandas digunakan untuk menganalisis dan memanipulasi data.
- Menginstall Kaggle & unduh dataset.

## Exploratory Data Analysis
---
Berikut adalah tahapan dalam melakukan exploratory data analysis:
- Mendeskripsikan variabel dan statistika.
  * Menggunakan kode `df.info()` untuk menghasilkan deskripsi variabel, dan `df.describe()` untuk menhasilkan nilai statistik pada dataset.
- Menangani data nilai yang hilang.
  ```
  RestingBP = (df.RestingBP == 0).sum()
  Cholesterol = (df.Cholesterol == 0).sum()
  print(f'Jumlah nilai 0 pada RestingBP: {RestingBP}')
  print(f'Jumlah nilai 0 pada Cholesterol: {Cholesterol}')
  ```
  ```
  df.drop(df.loc[(df['RestingBP']==0)].index, inplace=True)
  df.drop(df.loc[(df['Cholesterol']==0)].index, inplace=True)
  df.shape
  ```
- Membatasi nilai outliers.
  * Jika ada nilai yang lebih kecil dari (Q1 - 1.5 * IQR) atau lebih besar dari (Q3 + 1.5 * IQR), maka baris tersebut dianggap sebagai outlier. Simbol ~ digunakan untuk membalik kondisi tersebut, sehingga hanya baris yang tidak memiliki outliers yang akan disimpan. Memastikan bahwa jika ada satu saja nilai yang outlier dalam sebuah baris, maka seluruh baris tersebut akan di-drop.
- Menganalisis data kategori dan numerik dengan cara menampilkan plot analisis data.
- Menampilkan hasil grafik analisis.
- Membuat korelasi untuk fitur numerik.
  ![download (1)](https://github.com/user-attachments/assets/dc08c920-2690-4f17-bea4-91c0b4aa2df7)
  Matriks korelasi ini menggambarkan seberapa kuat hubungan antara fitur-fitur numerik dalam dataset yang berkaitan dengan penyakit jantung. Mari kita lihat satu per satu dengan lebih sederhana:
  * **Umur (Age)**:
     - Ada hubungan positif dengan penyakit jantung (korelasi 0.31). Ini artinya, semakin tua seseorang, semakin besar kemungkinan dia punya penyakit jantung.
     - Ada juga hubungan negatif dengan `MaxHR` (detak jantung maksimal saat olahraga), sebesar -0.41. Ini berarti semakin tua seseorang, detak jantung maksimalnya cenderung lebih rendah.
  * **Tekanan Darah Istirahat (RestingBP)**:
     - Ada sedikit hubungan positif dengan penyakit jantung (0.17). Ini menunjukkan kalau tekanan darah istirahat yang lebih tinggi sedikit berhubungan dengan risiko penyakit jantung.
     - Tekanan darah juga ada hubungannya dengan usia (0.27), jadi semakin tua, biasanya tekanan darah istirahat bisa naik sedikit.
  * **Kolesterol**:
     - Fitur ini hampir tidak ada hubungannya dengan penyakit jantung (korelasi cuma 0.09). Jadi, kadar kolesterol di dataset ini mungkin bukan faktor utama untuk menentukan risiko penyakit jantung.
     - Hubungan dengan fitur lain juga sangat lemah, jadi kolesterol tampaknya kurang berpengaruh dalam kasus ini.
  * **Detak Jantung Maksimal (MaxHR)**:
     - Ada hubungan negatif dengan penyakit jantung (-0.39). Artinya, detak jantung maksimal yang lebih rendah cenderung dihubungkan dengan risiko penyakit jantung yang lebih tinggi.
     - Juga ada hubungan negatif dengan umur (-0.41), yang menunjukkan bahwa seiring bertambahnya usia, detak jantung maksimal kita biasanya menurun.
  * **Oldpeak (Penurunan ST setelah olahraga)**:
     - Ini fitur yang punya hubungan paling kuat dengan penyakit jantung (0.5). Jadi, semakin tinggi penurunan ST ini, makin besar peluang seseorang mengalami penyakit jantung.
     - Oldpeak juga ada hubungannya dengan `MaxHR` (-0.28), menunjukkan bahwa nilai Oldpeak cenderung lebih tinggi kalau detak jantung maksimal menurun. Secara keseluruhan, fitur yang paling berpengaruh terhadap penyakit jantung adalah `Oldpeak`, diikuti oleh `MaxHR` dan `Umur`, sementara fitur seperti `Kolesterol` kelihatannya tidak terlalu berpengaruh di sini.

## Data Preparation
---
Berikut adalah tahapan dalam melakukan data preparation:
- Membuat Encoding untuk fitur kategori yang berisi tipe data `object` agar dapat berubah menjadi numerik, setelah selesai membuat fitur encoding jangan lupa untuk menghapus kolom yang bertipe data `object` dikarenakan sudah diubah menjadi data numerik.
  ```
  df_cleaned = pd.concat([df_cleaned, pd.get_dummies(df_cleaned['Sex'], prefix='Sex', dtype='int')], axis=1)
  df_cleaned = pd.concat([df_cleaned, pd.get_dummies(df_cleaned['ChestPainType'], prefix='ChestPainType', dtype='int')], axis=1)
  df_cleaned = pd.concat([df_cleaned, pd.get_dummies(df_cleaned['RestingECG'], prefix='RestingECG', dtype='int')], axis=1)
  df_cleaned = pd.concat([df_cleaned, pd.get_dummies(df_cleaned['ExerciseAngina'], prefix='ExerciseAngina', dtype='int')], axis=1)
  df_cleaned = pd.concat([df_cleaned, pd.get_dummies(df_cleaned['ST_Slope'], prefix='ST_Slope', dtype='int')], axis=1)
  df_cleaned.drop(['Sex', 'ChestPainType', 'RestingECG', 'ExerciseAngina', 'ST_Slope'], axis=1, inplace=True)
  ```
- Membagi dataset 80% untuk data latih, 20% untuk data uji.
  ```
  X = df_cleaned.drop(["Age"],axis =1)
  y = df_cleaned["Age"]
  X_train, X_test, y_train, y_test = train_test_split(X, y, test_size = 0.2, random_state = 123)
  ```
  pada sumbu X gunakan seluruh dataset kecuali `Age`, dan pada sumbu Y kita menggunakan dataset `Age` sebagai data yang akan di analisis.
- Melakukan standarisasi, hal ini dilakukan untuk membuat semua fitur berada dalam skala data yang sama yaitu dengan range 0-1

## Modeling
---
Setelah melakukan pra-pemrosesan pada data, langkah selanjutnya adalah *Modeling* terhadap data, dengan menggunakan beberapa algoritma, diantaranya sebagai berikut:
- Membuat dataframe untuk analisis model.
- Membuat model dengan Algoritma K-Nearest Neighbor.
  - Algoritma k-Nearest Neighbor adalah algoritma supervised learning dimana hasil dari instance yang baru diklasikasikan berdasarkan mayoritas dari kategori k-tetangga terdekat. Tujuan dari algoritma ini adalah untuk mengklasikasikan obyek baru berdasarkan atribut dan sample-sample dari training data. Algoritma k-Nearest Neighbor menggunakan Neighborhood Classication sebagai nilai prediksi dari nilai instance yang baru.[[3](https://www.researchgate.net/profile/Asep-Ismail-3/publication/330840826_Cara_Kerja_Algoritma_k-Nearest_Neighbor_k-NN/links/5c56f8d9458515a4c7553b2b/Cara-Kerja-Algoritma-k-Nearest-Neighbor-k-NN.pdf)]
- Membuat model dengan Algoritma Random Forest.
  - Random Forest adalah pengembangan dari metode Decision Tree yang menggunakan beberapa Decision Tree, dimana setiap Decision Tree telah dilakukan pelatihan menggunakan sampel individu dan setiap atribut dipecah pada pohon yang dipilih antara atribut subset yang bersifat acak. Random Forest memiliki beberapa kelebihan, yaitu dapat meningkatkan hasil akurasi jika terdapat data yang hilang, dan untuk resisting outliers, serta efisien untuk penyimpanan sebuah data. Selain itu, Random Forest mempunyai proses seleksi fitur dimana mampu mengambil fitur terbaik sehingga dapat meningkatkan performa terhadap model klasifikasi. Dengan adanya seleksi fitur tentu Random Forest dapat bekerja pada big data dengan parameter yang kompleks secara efektif.[[4](https://journal.stekom.ac.id/index.php/Bisnis/article/download/247/182)]
- Membuat model dengan Algortima Boosting.
  - Adaptive boosting (adaboost) merupakan salah satu dari beberapa varian pada algoritma boosting. Adaboost merupakan ensemble learning yang sering digunakan pada algoritma boosting Boosting bisa dikombinasikan dengan classifier algoritma yang lain untuk meningkatkan performa klasifikasi. Tentunya secara intuitif, penggabungan beberapa model akan membantu jika model tersebut berbeda satu sama lain. Adaboost dan variannya telah sukses diterapkan pada beberapa bidang (domain) karena dasar teorinya yang kuat, presdiksi yang akurat, dan kesederhanaan yang besar. [[5](https://ejournal.poltekharber.ac.id/index.php/informatika/article/view/5675/2640)]

## Evaluation
---
Pada proyek ini, model dikembangan dengan kasus klasifikasi. Berikut hasil dari pengukuran model:
![download](https://github.com/user-attachments/assets/e0b581c7-4319-47bf-b7d9-b5f612067581)

Grafik di atas menunjukkan perbandingan performa tiga model prediksi: **Boosting**, **Random Forest (RF)**, dan **K-Nearest Neighbors (KNN)**. Nilai yang dibandingkan adalah **Mean Squared Error (MSE)**—semakin kecil MSE, semakin akurat prediksi model tersebut.

Berikut penjelasan untuk setiap model:

1. **Boosting**  
   - Nilai kesalahan (MSE) pada data latih (*train set*) lebih rendah daripada pada data uji (*test set*), tapi perbedaannya tidak terlalu jauh.  
   - Ini menunjukkan model cukup mampu memahami pola data dan **tidak mengalami overfitting** (yaitu kondisi di mana model terlalu baik di data latih tapi buruk di data baru).

2. **Random Forest (RF)**  
   - MSE di data latih sangat rendah, tapi di data uji jauh lebih tinggi.  
   - Ini menandakan model mengalami **overfitting**—terlalu baik di data latih tapi kesulitan menangani data baru.

3. **KNN (K-Nearest Neighbors)**  
   - MSE cukup tinggi di kedua data (latih dan uji).  
   - Ini menunjukkan model kurang cocok untuk dataset ini atau mungkin terlalu sederhana untuk menangkap pola yang ada.

Dari hasil prediksi yang paling mendekati nilai asli didapatkan oleh Algoritma Boosting dengan hasil akhir sebagai berikut.
![Screenshot 2024-10-15 214136](https://github.com/user-attachments/assets/f902514e-0851-4659-b01d-f72c4e4b6aad)

Hasil di atas menunjukkan perbandingan nilai **asli** dengan **prediksi** dari tiga model berbeda untuk satu data (baris ke-629):

1. **`y_true`**: Nilai asli adalah **57**.
2. **`prediksi_KNN`**: Model **KNN** memprediksi **50.3**.
3. **`prediksi_RF`**: Model **Random Forest** memprediksi **53.0**.
4. **`prediksi_Boosting`**: Model **Boosting** memprediksi **53.5**.

Jadi, nilai asli adalah 57, dan semua model memiliki perbedaan prediksi, tetapi model **Boosting** paling mendekati (53.5).


