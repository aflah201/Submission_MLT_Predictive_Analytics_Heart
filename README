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
- Bagaimana cara melakukan pra-pemrosesan pada data penyakit gagal jantung?
- Bagaimana cara membuat model untuk memprediksi penyakit gagal jantung menggunakan machine learning?

### Goals Statements

Berdasarkan rumusan masalah diatas, berikut ini tujuan yang dapat diselesaikan pada proyek ini:
- Melakukan pra-pemrosesan data dengan baik agar dapat digunakan dalam pembuatan model.
- mengetahui cara membuat model machine learning untuk memprediksi penyakit gagal jantung.

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

## Data Preparation
---
Berikut adalah tahapan dalam melakukan pra-pemrosesan data:
- Menginstall & mengimport library yang diperlukan.
- Mengunduh dataset yang akan digunakan dalam analisis data.
- Mendeskripsikan variabel dan statistika.
- Menangani data nilai yang hilang serta membatasi nilai outliers.
- Menganalisis data kategori dan numerik.
- Menampilkan hasil grafik analisis.
- Membuat korelasi untuk fitur numerik.
- Membuat Encoding untuk fitur kategori yang berisi tipe data `object` agar dapat berubah menjadi numerik.
- Membagi dataset 80% untuk data latih, 20% untuk data uji.
- Melakukan standarisasi.

## Modeling
---
Setelah melakukan pra-pemrosesan pada data, langkah selanjutnya adalah *Modeling* terhadap data, dengan menggunakan beberapa algoritma, diantaranya sebagai berikut:
- Membuat dataframe untuk analisis model.
- Membuat model dengan Algoritma K-Nearest Neighbor.
- Membuat model dengan Algoritma Random Forest.
- Membuat model dengan Algortima Boosting.

## Evaluation
---
Pada proyek ini, model dikembangan dengan kasus klasifikasi. Berikut hasil dari pengukuran model:

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

Dari hasil prediksi yang paling mendekati nilai asli didapatkan oleh Algoritma Boosting.

