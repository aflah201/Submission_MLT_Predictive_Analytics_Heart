# Laporan Proyek Machine Learning - Moh. Aflah Azzaky

---
## Domain Proyek
Penyakit kardiovaskular (CVD) merupakan penyebab kematian nomor 1 secara global, merenggut sekitar 17,9 juta jiwa setiap tahunnya, atau menyumbang 31% dari seluruh kematian di seluruh dunia. Empat dari kematian 5CVD disebabkan oleh serangan jantung dan stroke, dan sepertiga dari kematian ini terjadi sebelum waktunya pada orang di bawah usia 70 tahun. Gagal jantung adalah kejadian umum yang disebabkan oleh penyakit kardiovaskular dan kumpulan data ini berisi 11 fitur yang dapat digunakan untuk memprediksi kemungkinan penyakit jantung.

Orang dengan penyakit kardiovaskular atau yang memiliki risiko kardiovaskular tinggi (karena adanya satu atau lebih faktor risiko seperti hipertensi, diabetes, hiperlipidemia, atau penyakit yang sudah ada) memerlukan deteksi dan manajemen dini sehingga model pembelajaran mesin dapat sangat membantu.[[1](https://www.kaggle.com/fedesoriano/heart-failure-prediction)]

Penyakit gagal jantung dapat disebabkan oleh beberapa kondisi penyakit jantung. Menurut WHO, penyakit jantung atau yang disingkat sebagai CVD (Cardiovascular disease) adalah kelompok gangguan pada jantung dan pembuluh darah yang termasuk diataranya: coronary heart disease, cerebrovascular disease, rheumatic heart disease, dan kondisi jantung lainnya. Lebih dari 4 dari 5 kematian atas CVD disebabkan oleh gagal jantung dan strokes, dan sepertiga dari angka kematian tersebut merupakan orang yang mati premature dibawah umur 70. Faktor resiko penyakit ini seringnya disebabkan oleh diet yang tidak sehat, kurang berolahraga, serta penggunaan rokok dan alkohol yang berlebih. Sifatnya yang menyerang mendadak menyebabkan dikembangkannya teknologi yang dapat memprevensi. EKG sebagai salah satu teknologi hasil yang dikembangkan berkontribusi memberikan tanda dan informasi akan aktifitas aliran listrik pada jantung.[[2](https://jurnal.unprimdn.ac.id/index.php/JUSIKOM/article/view/2445)]

---
## Business Understanding
### Problem Statements

Berdasarkan latar belakang diatas, berikut ini rumusan masalah yang dapat diselesaikan pada proyek ini:
- Bagaimana cara melakukan pra-pemrosesan pada data penyakit gagal jantung yang akan digunakan untuk membuat model yang baik?
- Bagaimana memprediksi resiko gagal jantung melalui faktor resiko Usia?

### Goals Statements

Berdasarkan rumusan masalah diatas, berikut ini tujuan yang dapat diselesaikan pada proyek ini:
- Melakukan pra-pemrosesan data dengan baik agar dapat digunakan dalam pembuatan model.
- mengetahui cara membuat model machine learning untuk memprediksi penyakit gagal jantung pada manusia berdasarkan faktor usia.

### Solution Statements

Berdasarkan tujuan diatas, berikut ini solusi yang dapat diselesaikan pada proyek ini:
- Untuk pra-pemrosesan data dapat dilakukan dengan beberapa teknik diantaranya:
   * Melakukan *drop* pada kolom `FastingBS` karena tidak diperlukan dalam analisis data.
   * Mengatasi masalah data yang kosong dengan cara menghapus beberapa data yang terindikasi kosong yang menyebabkan data statistik bernilai 0.
   * Melakukan Encoding terhadap kolom yang bertipe data `object`.
   * Melakukan pembagian dataset menjadi dua bagian dengan rasio 80:20, 80% untuk data latih dan 20% untuk data uji.
   * Melakukan *Standard Scaler*.

- Untuk penggunaan model dengan algoritma kami uji beberapa algoritma diantaranya Algoritma Random Forest, Algoritma K-Nearest Neighbor, dan Algoritma Boosting.

---
## Data Understanding
Data pada project ini menggunakan data yang bersumber pada sebuah situs kaggle, dimana fokus pada data tersebut menjelaskan faktor-faktor yang akan mempengaruhi sebuah penyakit gagal jantung.[[Kaggle Dataset - Heart Failure Prediction Dataset](https://www.kaggle.com/datasets/fedesoriano/heart-failure-prediction)]

Informasi dataset dapat dilihat pada tabel dibawah ini :
Jenis | Keterangan
--- | ---
Sumber | [Kaggle Dataset - Heart Failure Prediction Dataset](https://www.kaggle.com/datasets/fedesoriano/heart-failure-prediction)
Lisensi | Open Database
Kategori | Health, Health Conditions, Classification, Heart Conditions, Healthcare
Jenis dan Ukuran Berkas | CSV (35.92 kB)

Pada berkas yang diunduh yakni heart.csv berisi 918 rows x 12 columns. Kolom-kolom tersebut berisi diantaranya 1 kolom berisi tipe data `float64`, 6 kolom berisi tipe data `int64`, dan 5 kolom berisi tipe data `object`. Untuk penjelasan mengenai variabel dapat dilihat sebagai berikut:

Variable | Keterangan | Tipe Data
--- | --- | ---
**Age** | Usia pasien dalam jumlah tahun | `int64`
**Sex** | Jenis kelamin pasien dengan kategori M = Male/Pria dan F = Female/Perempuan | `object`
**ChestPainType** | Jenis nyeri dada dengan kategori TA: Typical Angina *Typical Angina* adalah nyeri dada yang disebabkan oleh aktivitas fisik atau stres emosional, dan berkurang saat istirahat atau mengonsumsi nitrogliserin, ATA: Atypical Angina *Atypical Angina* adalah nyeri dada yang tidak memenuhi kriteria angina tipikal, tetapi sesuai dengan penyebab iskemik jantung, NAP: Non-Anginal Pain *Non-Anginal Pain* adalah nyeri dada yang tidak disebabkan oleh penyakit jantung, ASY: Asymptomatic *Asymptomatic* adalah istilah yang menggambarkan kondisi seseorang yang menderita penyakit, tetapi tidak menunjukkan gejala klinis apa pun. | `object`
**RestingBP** | Tekanan darah istirahat | `int64`
**Cholesterol** | Kolesterol serum | `int64`
**FastingBS** | Gula darah puasa | `int64`
**RestingECG** | Hasil elektrokardiogram istirahat dengan kategori Normal, ST = Mengalami kelainan gelombang ST-T, LVH = menunjukkan kemungkinan atau pasti hipertrofi ventrikel kiri | `object`.
**MaxHR** | Detak jantung maksimum tercapai yang berisi nilai numerik antara 60 dan 202 | `int64`
**ExerciseAngina** | Angina akibat olahraga dengan kategori Y = Yes/Iya & N = No/Tidak | `object`
**Oldpeak** | Puncak tua nilai numerik yang diukur pada depresi | `float64`
**ST_Slope** | Kemiringan segmen ST terhadap denyut jantung (heart rate) yang dihitung dengan linear regression dengan kategori Up: upsloping, Flat: flat, Down: downsloping | `object`
**HeartDisease** | Penyakit jantung dengan hasil keluaran 1 = penyakit jantung dan 0 = normal | `int64`

---
## Data Loading
Berikut adalah tahapan dalam melakukan data loading:
- Menginstall dan import library yang diperlukan seperti:
  * *Libray* Numpy digunakan untuk memproses larik atau array.
  * *Libray* Matplotlib digunakan membuat visualisasi data dalam dua dimensi.
  * *Libray* Seaborn dibangun di ata *library* Matplotlib, digunakan untuk membuat visualisasi data.
  * *Libray* Pandas digunakan untuk menganalisis dan memanipulasi data.
- Menginstall Kaggle & unduh dataset.

---
## Data Preparation
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

---
## Modeling
Setelah melakukan pra-pemrosesan pada data, langkah selanjutnya adalah *Modeling* terhadap data, dengan menggunakan beberapa algoritma, diantaranya sebagai berikut:
- Membuat dataframe untuk analisis model.
- Membuat model dengan Algoritma K-Nearest Neighbor.
  - Algoritma k-Nearest Neighbor adalah algoritma supervised learning dimana hasil dari instance yang baru diklasikasikan berdasarkan mayoritas dari kategori k-tetangga terdekat. Tujuan dari algoritma ini adalah untuk mengklasikasikan obyek baru berdasarkan atribut dan sample-sample dari training data. Algoritma k-Nearest Neighbor menggunakan Neighborhood Classication sebagai nilai prediksi dari nilai instance yang baru.[[3](https://www.researchgate.net/profile/Asep-Ismail-3/publication/330840826_Cara_Kerja_Algoritma_k-Nearest_Neighbor_k-NN/links/5c56f8d9458515a4c7553b2b/Cara-Kerja-Algoritma-k-Nearest-Neighbor-k-NN.pdf)]
- Membuat model dengan Algoritma Random Forest.
  - Random Forest adalah pengembangan dari metode Decision Tree yang menggunakan beberapa Decision Tree, dimana setiap Decision Tree telah dilakukan pelatihan menggunakan sampel individu dan setiap atribut dipecah pada pohon yang dipilih antara atribut subset yang bersifat acak. Random Forest memiliki beberapa kelebihan, yaitu dapat meningkatkan hasil akurasi jika terdapat data yang hilang, dan untuk resisting outliers, serta efisien untuk penyimpanan sebuah data. Selain itu, Random Forest mempunyai proses seleksi fitur dimana mampu mengambil fitur terbaik sehingga dapat meningkatkan performa terhadap model klasifikasi. Dengan adanya seleksi fitur tentu Random Forest dapat bekerja pada big data dengan parameter yang kompleks secara efektif.[[4](https://journal.stekom.ac.id/index.php/Bisnis/article/download/247/182)]
- Membuat model dengan Algortima Boosting.
  - Adaptive boosting (adaboost) merupakan salah satu dari beberapa varian pada algoritma boosting. Adaboost merupakan ensemble learning yang sering digunakan pada algoritma boosting Boosting bisa dikombinasikan dengan classifier algoritma yang lain untuk meningkatkan performa klasifikasi. Tentunya secara intuitif, penggabungan beberapa model akan membantu jika model tersebut berbeda satu sama lain. Adaboost dan variannya telah sukses diterapkan pada beberapa bidang (domain) karena dasar teorinya yang kuat, presdiksi yang akurat, dan kesederhanaan yang besar. [[5](https://ejournal.poltekharber.ac.id/index.php/informatika/article/view/5675/2640)]

---
## Evaluation
Pada proyek ini, model dikembangan dengan kasus Regresi. Berikut hasil dari pengukuran model:

![download](https://github.com/user-attachments/assets/edc5d843-ef28-4976-9e04-321b8557ec9b)

Gambar di atas menunjukkan hasil evaluasi dari tiga model machine learning: Random Forest (RF), K-Nearest Neighbors (KNN), dan Boosting. Grafik tersebut membandingkan performa model pada data training dan testing dalam bentuk bar horizontal. Berikut penjelasan dari setiap model:

1. **Boosting**:
   - Performa pada data training (warna biru) dan testing (warna oranye) sangat mirip dan tinggi, menunjukkan bahwa model ini memiliki kemampuan generalisasi yang baik. Tidak ada tanda overfitting atau underfitting yang signifikan.

2. **KNN**:
   - Performa pada data training dan testing hampir sama seperti Boosting. Nilai pada kedua dataset ini juga tinggi dan konsisten. Hal ini menunjukkan bahwa KNN cukup efektif dalam memprediksi data baru tanpa overfitting.

3. **Random Forest (RF)**:
   - Pada model ini, terlihat perbedaan yang cukup signifikan antara performa pada data training dan testing. Performa pada data training jauh lebih rendah dibandingkan dengan testing, yang mungkin menunjukkan bahwa model ini mengalami underfitting atau memiliki performa yang kurang optimal pada data training.

Secara keseluruhan, Boosting dan KNN menunjukkan performa yang lebih baik dan stabil dibandingkan dengan RF. Boosting dan KNN sepertinya merupakan pilihan yang lebih baik untuk dataset ini.

Dari hasil prediksi yang paling mendekati nilai asli didapatkan oleh Algoritma KNN & Boosting dengan hasil akhir sebagai berikut.

![{483E3751-D453-4416-BB0A-882209A151FE}](https://github.com/user-attachments/assets/9a2da6cd-0f68-473c-af16-43bf03730a92)

Hasil di atas menunjukkan perbandingan nilai **asli** dengan **prediksi** dari tiga model berbeda untuk satu data (baris ke-629):

1. **`HeartDisease`**: Nilai asli adalah **0**.
2. **`prediksi_KNN`**: Model **KNN** memprediksi **0.4**.
3. **`prediksi_RF`**: Model **Random Forest** memprediksi **0.8**.
4. **`prediksi_Boosting`**: Model **Boosting** memprediksi **0.5**.

Kita dapat melihat bahwa model dengan algoritma KNN memiliki hasil prediksi 0.4, algoritma Random Forest memiliki hasil prediksi 0.8, dan algoritma Boosting memiliki hasil prediksi 0.5, perlu diketahui jika probabilitas lebih dari 0.5, kelas yang diprediksi adalah 1, jika kurang dari 0.5, kelas yang diprediksi adalah 0.
Jadi, nilai asli adalah 0, dan semua model memiliki perbedaan prediksi, tetapi model **KNN** paling mendekati (0.4).

---
## Kesimpulan
Pengujian setiap model dengan algoritma yang berbeda menghasilkan nilai prediksi yang berbeda pula. Model dengan nilai yang mendekati nilai sebenarnya diperoleh pada prediksi dengan menggunakan algoritma KNN. Untuk prediksi menggunakan algoritma Random Forest dan Boosting, performanya masih dibawah prediksi model KNN. Sehingga dapat disimpulkan bahwa pada kasus ini, model dengan menggunakan Algoritma KNN lebih tepat untuk digunakan atau diterapkan.

---
## Penutup
Demikian hasil dari laporan proyek machine learning tentang Prediktif Analitik Penyakit Gagal Jantung. Bilamana didalam penyampaian serta penjelasan yang kurang berkenaan, saya memohon maaf. Atas waktu dan perhatiannya, saya ucapkan Terima kasih telah membaca laporan ini. Semoga dapat memberi manfaat bagi kita semuanya.
