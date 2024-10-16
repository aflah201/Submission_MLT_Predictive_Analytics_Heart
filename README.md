# Laporan Proyek Machine Learning - Moh. Aflah Azzaky

---
## Domain Proyek
Penyakit kardiovaskular (CVD) merupakan penyebab kematian nomor 1 secara global, merenggut sekitar 17,9 juta jiwa setiap tahunnya, atau menyumbang 31% dari seluruh kematian di seluruh dunia. Empat dari kematian 5CVD disebabkan oleh serangan jantung dan stroke, dan sepertiga dari kematian ini terjadi sebelum waktunya pada orang di bawah usia 70 tahun. Gagal jantung adalah kejadian umum yang disebabkan oleh penyakit kardiovaskular dan kumpulan data ini berisi 11 fitur yang dapat digunakan untuk memprediksi kemungkinan penyakit jantung.

Orang dengan penyakit kardiovaskular atau yang memiliki risiko kardiovaskular tinggi (karena adanya satu atau lebih faktor risiko seperti hipertensi, diabetes, hiperlipidemia, atau penyakit yang sudah ada) memerlukan deteksi dan manajemen dini sehingga model pembelajaran mesin dapat sangat membantu.[[1](https://www.kaggle.com/fedesoriano/heart-failure-prediction)]

Penyakit gagal jantung dapat disebabkan oleh beberapa kondisi penyakit jantung. Menurut WHO, penyakit jantung atau yang disingkat sebagai CVD (Cardiovascular disease) adalah kelompok gangguan pada jantung dan pembuluh darah yang termasuk diataranya: coronary heart disease, cerebrovascular disease, rheumatic heart disease, dan kondisi jantung lainnya. Lebih dari 4 dari 5 kematian atas CVD disebabkan oleh gagal jantung dan strokes, dan sepertiga dari angka kematian tersebut merupakan orang yang mati premature dibawah umur 70. Faktor resiko penyakit ini seringnya disebabkan oleh diet yang tidak sehat, kurang berolahraga, serta penggunaan rokok dan alkohol yang berlebih. Sifatnya yang menyerang mendadak menyebabkan dikembangkannya teknologi yang dapat memprevensi. EKG sebagai salah satu teknologi hasil yang dikembangkan berkontribusi memberikan tanda dan informasi akan aktifitas aliran listrik pada jantung.[[2](https://jurnal.unprimdn.ac.id/index.php/JUSIKOM/article/view/2445)]

Penerapan **machine learning (ML)** dalam manajemen penyakit kardiovaskular dan gagal jantung menawarkan solusi strategis untuk meningkatkan efektivitas layanan kesehatan. Model ML mampu memprediksi risiko gagal jantung secara akurat berdasarkan data klinis dan gaya hidup pasien, memungkinkan intervensi dini dan pencegahan komplikasi lebih lanjut. Selain itu, teknologi ini dapat mempersonalisasi perawatan sesuai kebutuhan spesifik pasien, memastikan terapi yang lebih tepat sasaran. Dalam ekosistem yang terhubung seperti perangkat IoT (misalnya EKG atau smartwatch), model ML memungkinkan pemantauan kondisi secara real-time dan memberikan peringatan otomatis kepada tenaga medis saat ditemukan anomali. ML juga dapat mengidentifikasi faktor risiko tersembunyi melalui analisis pola kompleks, mendukung keputusan klinis berbasis data yang lebih baik. Dari sisi operasional, otomatisasi analisis data mempercepat proses diagnosis dan mengurangi beban administrasi, meningkatkan efisiensi layanan rumah sakit. Selain itu, model prediktif membantu memprioritaskan pasien berisiko tinggi terhadap kematian atau kekambuhan, memastikan alokasi sumber daya yang optimal. Dengan adopsi machine learning, institusi kesehatan dapat menghadirkan layanan yang lebih responsif, proaktif, dan efisien, sekaligus berkontribusi signifikan dalam menurunkan angka kematian akibat penyakit kardiovaskular.

---
## Business Understanding
### Problem Statements

Berdasarkan latar belakang diatas, berikut ini rumusan masalah yang dapat diselesaikan pada proyek ini:
1. Bagaimana cara melakukan pra-pemrosesan pada data penyakit gagal jantung yang akan digunakan untuk membuat model yang baik?
2. Bagaimana memprediksi resiko gagal jantung melalui faktor resiko Usia, Tekanan Darah Istirahat, Kolesterol, Detak Jantung Maksimum, dan Puncak Tua?

### Goals Statements

Berdasarkan rumusan masalah diatas, berikut ini tujuan yang dapat diselesaikan pada proyek ini:
1. **Melakukan pra-pemrosesan pada data penyakit gagal jantung** untuk memastikan data yang digunakan dalam pengembangan model memiliki kualitas yang baik dan sesuai dengan standar, sehingga model yang dihasilkan memiliki akurasi yang optimal.
2. **Mengembangkan model prediksi risiko gagal jantung** berdasarkan faktor risiko seperti Usia, Tekanan Darah Istirahat, Kolesterol, Detak Jantung Maksimum, dan Puncak Tua, dengan tujuan untuk membantu dalam mengidentifikasi individu yang memiliki risiko tinggi secara lebih akurat.

### Solution Statements

Berdasarkan tujuan diatas, berikut ini solusi yang dapat diselesaikan pada proyek ini:
1. **Solusi untuk Melakukan Pra-Pemrosesan Data Penyakit Gagal Jantung**:
    - Lakukan **pembersihan data** untuk mengatasi data yang hilang, duplikat, atau data yang tidak valid. Ini bisa dilakukan dengan teknik imputasi atau penghapusan baris/kolom yang tidak relevan.
    - **Normalisasi atau standarisasi** fitur numerik seperti Usia, Tekanan Darah, Kolesterol, dan Detak Jantung untuk memastikan bahwa skala variabel tidak mempengaruhi model.
    - Lakukan **pemeriksaan dan penanganan outlier** pada variabel-variabel numerik untuk menghindari pengaruh negatif terhadap performa model.
    - Gunakan **teknik encoding** untuk mengubah variabel kategorikal menjadi numerik sehingga bisa diproses oleh algoritma machine learning.
    - Pisahkan data menjadi **set training dan set testing** untuk melatih dan menguji model
    - Melakukan **Standard Scaler**

2. **Solusi untuk Mengembangkan Model Prediksi Risiko Gagal Jantung**:
    - Pilih algoritma machine learning yang cocok, misalnya **K-Nearest_Neighbor**, **Random Forest**, atau **Boosting**, untuk membangun model prediksi berdasarkan faktor risiko yang telah ditentukan.
    - **Latih model** menggunakan set data yang telah diproses, dan lakukan optimasi hyperparameter menggunakan teknik seperti **Random Search** untuk mendapatkan konfigurasi terbaik.
    - Evaluasi model menggunakan **metrik evaluasi** seperti akurasi, precision, recall, F1-score untuk menentukan performa model dalam memprediksi risiko gagal jantung.

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

Pada berkas yang diunduh yakni heart.csv berisi 918 baris x 12 kolom. Kolom-kolom tersebut berisi diantaranya 1 kolom berisi tipe data `float64`, 6 kolom berisi tipe data `int64`, dan 5 kolom berisi tipe data `object`. Untuk penjelasan mengenai variabel dapat dilihat sebagai berikut:

Variable | Keterangan | Tipe Data
--- | --- | ---
**Age** | Usia pasien dalam jumlah tahun | `int64`
**Sex** | Jenis kelamin pasien dengan kategori M = Male/Pria dan F = Female/Perempuan | `object`
**ChestPainType** | Jenis nyeri dada dengan kategori TA: Typical Angina ***Typical Angina*** adalah nyeri dada yang disebabkan oleh aktivitas fisik atau stres emosional, dan berkurang saat istirahat atau mengonsumsi nitrogliserin, ATA: Atypical Angina ***Atypical Angina*** adalah nyeri dada yang tidak memenuhi kriteria angina tipikal, tetapi sesuai dengan penyebab iskemik jantung, NAP: Non-Anginal Pain ***Non-Anginal Pain*** adalah nyeri dada yang tidak disebabkan oleh penyakit jantung, ASY: Asymptomatic ***Asymptomatic*** adalah istilah yang menggambarkan kondisi seseorang yang menderita penyakit, tetapi tidak menunjukkan gejala klinis apa pun. | `object`
**RestingBP** | Tekanan darah istirahat | `int64`
**Cholesterol** | Kolesterol serum | `int64`
**FastingBS** | Gula darah puasa | `int64`
**RestingECG** | Hasil elektrokardiogram istirahat dengan kategori Normal, ST = Mengalami kelainan gelombang ST-T, LVH = menunjukkan kemungkinan atau pasti hipertrofi ventrikel kiri | `object`
**MaxHR** | Detak jantung maksimum tercapai yang berisi nilai numerik antara 60 dan 202 | `int64`
**ExerciseAngina** | Angina akibat olahraga dengan kategori Y = Yes/Iya & N = No/Tidak | `object`
**Oldpeak** | Puncak tua nilai numerik yang diukur pada depresi | `float64`
**ST_Slope** | Kemiringan segmen ST terhadap denyut jantung (heart rate) yang dihitung dengan linear regression dengan kategori Up: upsloping, Flat: flat, Down: downsloping | `object`
**HeartDisease** | Penyakit jantung dengan hasil keluaran 1 = penyakit jantung dan 0 = normal | `int64`

Berikut informasi mengenai jumlah data, tipe data, data statisika, dan informasi data hilang (missing value) yang terdapat pada dataset ini:

![Screenshot 2024-10-17 135043](https://github.com/user-attachments/assets/52347397-4ec8-4ac3-b88d-14d93321a65f) 
![Screenshot 2024-10-17 135111](https://github.com/user-attachments/assets/0c1e93f1-9098-4563-82f4-2953861e67ea)

Dalam memudahkan proses analisis diperlukan beberapa visualisasi data, seperti:
- ***sns.bloxpot***, untuk mendeteksi adanya nilai outliers.

    ![NilaiOutlier 3baris](https://github.com/user-attachments/assets/25288b57-0b57-4dcb-ab66-464a33bcb167)

- ***count.plot***, untuk menganalisa fitur kategori diantaranya `Sex, ChestPainType, RestingECG, ExerciseAngina, ST_Slope`.

    ![PlotKategori 5 kotak](https://github.com/user-attachments/assets/0cec36e2-ed25-48f7-bf02-337371241dcf)
    
  Dengan penjelasan sebagai berikut:
  - **Sex**: Kategori M memiliki jumlah sampel yang lebih tinggi dibandingkan kategori F.
  - **ChestPainType**: Kategori ASY memiliki frekuensi tertinggi, diikuti oleh kategori NAP dan ATA, sedangkan kategori TA memiliki frekuensi paling rendah. Ini menunjukkan distribusi tipe nyeri dada yang dialami oleh pasien dalam dataset.
  - **RestingECG**: Kategori Normal memiliki frekuensi tertinggi, diikuti oleh kategori LVH dan ST. Ini menunjukkan hasil pemeriksaan EKG saat istirahat, di mana kategori tertentu lebih dominan dibandingkan lainnya.
  - **ExerciseAngina**: Kategori N lebih tinggi daripada kategori Y, yang menunjukkan bahwa lebih banyak sampel yang tidak mengalami angina saat latihan dibandingkan yang mengalaminya.
  - **ST_Slope**: Kategori Flat dan Down memiliki jumlah sampel yang hampir sama dan dominan, sementara kategori Up memiliki jumlah sampel yang jauh lebih sedikit. Ini menggambarkan pola kemiringan segmen ST setelah latihan.
- ***sns.catplot***, untuk mempertimbangkan fitur HeartDisease dengan kategori.

    ![sns1](https://github.com/user-attachments/assets/303ca59a-ed1a-4a8a-ad62-7a3cdd1faceb)
    ![sns2](https://github.com/user-attachments/assets/93eb59f9-b66e-4d4f-a775-eff43b26a16c)
    ![sns3](https://github.com/user-attachments/assets/87c62b74-3b7b-42eb-bf61-24d7a007fb83)
    ![sns4](https://github.com/user-attachments/assets/6c25fe41-28ff-4600-a9cb-9366e253f1c6)
    ![sns5](https://github.com/user-attachments/assets/37364de8-2cc9-4fa2-a14c-29c2f8241228)

  Beberapa hal yang dapat kita peroleh dari visualisai informasi tersebut adalah :
    - Rata-rata jenis kelamin pria yang terkena penyakit jantung lebih banyak, daripada jenis kelamin perempuan.
    - Rata-rata yang terkena penyakit jantung, menggambarkan kondisi seseorang yang menderita penyakit, tetapi tidak menunjukkan gejala klinis apa pun.
    - Rata-rata penyakit jantung, mengalami kelainan gelombang atau hipertrofi vertikal kiri.
    - Rata-rata penyakit jantung, terkena angina akibat olahraga.
    - Rata-rata penyakit jantung, akibat Kemiringan segmen ST terhadap denyut jantung yang dihitung dengan linear regression.
- ***sns.pairplot***, untuk menunjukkan semua grafik fitur numerik.

    ![pairplot](https://github.com/user-attachments/assets/cf18dea4-2a56-4d01-9d46-cb5256f40305)

  Pairplot menunjukkan bahwa terdapat beberapa perbedaan pola distribusi dan hubungan antar variabel antara individu yang memiliki dan tidak memiliki penyakit jantung. Misalnya, variabel seperti Age, MaxHR, dan Oldpeak memperlihatkan kecenderungan yang berbeda untuk kedua kelompok. Hal ini mengindikasikan bahwa variabel-variabel tersebut bisa menjadi indikator penting dalam memprediksi risiko penyakit jantung.
- ***sns.heatmap***, untuk menunjukkan metrik korelasi fitur numerik.

    ![korelasi](https://github.com/user-attachments/assets/a597af4e-d55f-4137-8971-a7a49436deea)

  Matriks korelasi menunjukkan bahwa **Oldpeak**, **MaxHR**, dan **Umur** adalah fitur yang paling berpengaruh terhadap penyakit jantung. **Oldpeak** memiliki korelasi positif terkuat (0.5), menunjukkan bahwa penurunan ST setelah olahraga sangat terkait dengan risiko penyakit jantung. **MaxHR** memiliki korelasi negatif (-0.39), menunjukkan bahwa detak jantung maksimal yang lebih rendah cenderung terkait dengan risiko lebih tinggi. **Umur** juga berhubungan positif (0.31), artinya semakin tua, semakin besar risiko penyakit jantung. Fitur lain seperti **Kolesterol** dan **RestingBP** menunjukkan hubungan yang lemah, sehingga kurang signifikan dalam menentukan risiko penyakit jantung dalam dataset ini.
---
## Data Preparation
Berikut adalah tahapan dalam melakukan data preparation:
- Pada dataset ditemukan nilai kosong pada tabel `RestingBP` berjumlah 1 data, dan pada tabel `Cholesterol` berjumlah 172 data, untuk mengatasi nilai yang kosong dengan cara menghitung kolom yang kosong, lalu menghapusnya.
  ```
  RestingBP = (df.RestingBP == 0).sum()
  Cholesterol = (df.Cholesterol == 0).sum()

  df.loc[(df['RestingBP']==0)]
  df.loc[(df['Cholesterol']==0)]

  df.drop(df.loc[(df['RestingBP']==0)].index, inplace=True)
  df.drop(df.loc[(df['Cholesterol']==0)].index, inplace=True)
  ```
- Menghapus kolom yang tidak diperlukan dalam analisis data, dalam kasus ini terdapat kolom `FastingBS`.
  ```
  df.drop(['FastingBS'], axis=1, inplace=True)
  ```
- Mengatasi nilai outlier dengan menampilkan boxplot & membatasi nilai outlier menggunakan metode IQR.
- Menampilkan plot kategori untuk data yang bertipe `object`.
- Menampilkan plot numerik untuk data yang bertipe `int64` dan `float64`.
  ![plot numerik](https://github.com/user-attachments/assets/25c3486b-9348-4294-ad51-a8ea24398a90)

- Menampilkan plot untuk mempertimbangkan Fitur Numerik dengan Fitur Kategori.
- Menampilkan plot untuk mengetahui hubungan fitur numerik.
- Menampilkan Korelasi Metrik untuk fitur numerik menggunakan **sns.heatmap**
- Membuat Encoding untuk fitur kategori yang berisi tipe data `object` agar dapat berubah menjadi numerik, setelah selesai membuat fitur encoding jangan lupa untuk menghapus kolom yang bertipe data `object` dikarenakan sudah diubah menjadi data numerik.
- Membagi dataset 80% untuk data latih, 20% untuk data uji.
  ```
  X = df_cleaned.drop(["HeartDisease"],axis =1)
  y = df_cleaned["HeartDisease"]
  X_train, X_test, y_train, y_test = train_test_split(X, y, test_size = 0.2, random_state = 123)
  ```
  pada sumbu X gunakan seluruh dataset kecuali `HeartDisease`, dan pada sumbu Y kita menggunakan dataset `HeartDisease` sebagai data yang akan di analisis.
- Melakukan standarisasi menggunakan ***StandardScaler***, hal ini dilakukan untuk membuat semua fitur berada dalam skala data yang sama yaitu dengan range 0-1. Proses standarisasi ini dilakukan dengan menghilangkan nilai rata-rata (mean) dari setiap fitur, sehingga distribusi data memiliki rata-rata 0, dan Menskalakan ke unit varians, sehingga setiap fitur memiliki standar deviasi 1.

---
## Model Development
Setelah melakukan pra-pemrosesan pada data, langkah selanjutnya adalah *Model Development* terhadap data, dengan menggunakan beberapa algoritma, diantaranya sebagai berikut:
- Membuat dataframe untuk analisis model.
  ```
  models = pd.DataFrame(index=['train_mse', 'test_mse'],
                        columns=['KNN', 'RandomForest', 'Boosting'])
  ```
- Membuat Model MSE Classifier
  - ***Membuat model dengan Algoritma K-Nearest Neighbor.***
    - Algoritma k-Nearest Neighbor adalah algoritma supervised learning dimana hasil dari instance yang baru diklasikasikan berdasarkan mayoritas dari kategori k-tetangga terdekat. Tujuan dari algoritma ini adalah untuk mengklasikasikan obyek baru berdasarkan atribut dan sample-sample dari training data. Algoritma k-Nearest Neighbor menggunakan Neighborhood Classication sebagai nilai prediksi dari nilai instance yang baru. Cara kerja dari Algoritma ini bekerja dengan mencari sejumlah tetangga terdekat (n_neighbors) dari data yang ingin diprediksi. Untuk regresi, nilai prediksi dihitung sebagai rata-rata dari nilai target (output) tetangga-tetangga terdekat. [[3](https://www.researchgate.net/profile/Asep-Ismail-3/publication/330840826_Cara_Kerja_Algoritma_k-Nearest_Neighbor_k-NN/links/5c56f8d9458515a4c7553b2b/Cara-Kerja-Algoritma-k-Nearest-Neighbor-k-NN.pdf)]
  - ***Membuat model dengan Algoritma Random Forest.***
    - Random Forest adalah pengembangan dari metode Decision Tree yang menggunakan beberapa Decision Tree, dimana setiap Decision Tree telah dilakukan pelatihan menggunakan sampel individu dan setiap atribut dipecah pada pohon yang dipilih antara atribut subset yang bersifat acak. Random Forest memiliki beberapa kelebihan, yaitu dapat meningkatkan hasil akurasi jika terdapat data yang hilang, dan untuk resisting outliers, serta efisien untuk penyimpanan sebuah data. Selain itu, Random Forest mempunyai proses seleksi fitur dimana mampu mengambil fitur terbaik sehingga dapat meningkatkan performa terhadap model klasifikasi. Dengan adanya seleksi fitur tentu Random Forest dapat bekerja pada big data dengan parameter yang kompleks secara efektif. Cara kerja dari Algoritma Random Forest adalah kumpulan (ensemble) dari pohon keputusan. Setiap pohon dilatih pada subset acak dari data, dan hasil akhirnya adalah rata-rata dari prediksi semua pohon. Algoritma ini mengurangi overfitting dengan menggabungkan hasil dari banyak pohon yang berbeda.[[4](https://journal.stekom.ac.id/index.php/Bisnis/article/download/247/182)]
  - ***Membuat model dengan Algortima Boosting.***
    - Adaptive boosting (adaboost) merupakan salah satu dari beberapa varian pada algoritma boosting. Adaboost merupakan ensemble learning yang sering digunakan pada algoritma boosting Boosting bisa dikombinasikan dengan classifier algoritma yang lain untuk meningkatkan performa klasifikasi. Tentunya secara intuitif, penggabungan beberapa model akan membantu jika model tersebut berbeda satu sama lain. Adaboost dan variannya telah sukses diterapkan pada beberapa bidang (domain) karena dasar teorinya yang kuat, presdiksi yang akurat, dan kesederhanaan yang besar. Cara kerja Algoritma ini meningkatkan akurasi prediksi dengan membangun model secara berurutan. Setiap model baru berfokus pada kesalahan yang dibuat oleh model sebelumnya. Boosting menggabungkan prediksi dari beberapa model yang lebih lemah (weak learners) menjadi satu model yang lebih kuat.[[5](https://ejournal.poltekharber.ac.id/index.php/informatika/article/view/5675/2640)]
- Implementasi Random Search untuk mengetahui parameter terbaik dan nilai terbaik, dengan menggunakan metode *RandomizedSearchCV*.
  RandomizedSearchCV adalah teknik yang lebih efisien daripada GridSearchCV karena hanya menguji kombinasi hyperparameter secara acak berdasarkan jumlah iterasi yang ditentukan (n_iter), bukan menguji semua kemungkinan kombinasi. Teknik ini lebih cepat dan sering kali cukup efektif, terutama ketika jumlah kombinasi hyperparameter sangat besar.

  Pada Implementasi RandomizedSearchCV telah menerapkan hyperparameter tuning untuk mencari kombinasi hyperparameter yang optimal bagi setiap classifier, berikut ini penjelasan singkat:
  - ***KNN Classifier:*** Parameter yang diuji: n_neighbors, weights, dan metric. RandomizedSearchCV melakukan pencarian kombinasi terbaik dari parameter tersebut dengan melakukan cross-validation sebanyak 5 kali (cv=5) dan iterasi sebanyak 10 (n_iter=10).
  - ***Random Forest Classifier:*** Parameter yang diuji: n_estimators, max_depth, min_samples_split, min_samples_leaf, dan bootstrap. RandomizedSearchCV mencari kombinasi terbaik dari parameter tersebut dengan skema yang sama (5-fold cross-validation dan 10 iterasi).
  - ***Boosting:*** Parameter yang diuji: n_estimators dan learning_rate. RandomizedSearchCV juga mencari kombinasi terbaik dengan skema yang sama.

  Untuk proses dan hyperparameter yang didapatkan dari tuning RandomizedSearchCV sebagai berikut:
  - ***KNN Classifier:*** Parameter yang diuji meliputi jumlah tetangga (n_neighbors), jenis pembobotan (weights), dan metrik pengukuran jarak (metric).
  - ***Random Forest Classifier:*** Parameter yang diuji meliputi jumlah pohon keputusan (n_estimators), kedalaman maksimum pohon (max_depth), jumlah sampel minimum untuk split (min_samples_split), jumlah sampel minimum untuk daun (min_samples_leaf), dan penggunaan bootstrap (bootstrap).
  - ***Boosting Classifier:*** Parameter yang diuji adalah jumlah estimator (n_estimators) dan laju pembelajaran (learning_rate).
---
## Model Devlopment Testing
Setelah melakukan modeling pada data, langkah selanjutnya adalah *Model Devlopment Testing* terhadap data, yaitu Mengetes hasil prediksi Model Classifier.

---
## Evaluation

Setelah melakukan model developmenet testing pada data, langkah selanjutnya adalah *Evaluation* terhadap data, diantaranya sebagai berikut:
1. Menampilkan hasil komparasi dari ketiga algoritma **K-Nearest Neighbors (KNN)**, **Random Forest (RF)**, dan **Boosting**.

   ![Screenshot 2024-10-17 031509](https://github.com/user-attachments/assets/c16559b4-131c-4419-94c2-08304c90c093)

   Berdasarkan tabel komparasi di atas, berikut adalah penjelasan dari hasil evaluasi tiga algoritma, yaitu **K-Nearest Neighbors (KNN)**, **Random Forest (RF)**, dan **Boosting**:
    - **KNN (K-Nearest Neighbors)**
      
      Keterangan | Nilai
      ---|---
      **Akurasi** | 89.21%  
      **Presisi** | 89.86%  
      **Recall** | 88.57%  
      **F1-Score** | 89.21%
       
      **KNN** menunjukkan kinerja tertinggi secara keseluruhan. Akurasi dan F1-Score yang lebih tinggi menandakan bahwa KNN mampu memprediksi kelas dengan baik dan seimbang antara precision dan recall.

    - **RF (Random Forest)**
      
      Keterangan | Nilai
      ---|---
      **Akurasi** | 88.49%  
      **Presisi** | 87.50%  
      **Recall** | 90.00%  
      **F1-Score** | 88.73%

      **Random Forest** memiliki **Recall** paling tinggi (90%). Ini berarti RF lebih baik dalam mengidentifikasi kasus positif dengan benar, namun sedikit kalah dalam akurasi dan F1-Score dibandingkan KNN. Jika aplikasi memerlukan fokus pada deteksi positif yang tinggi (misalnya deteksi penyakit), RF bisa menjadi pilihan yang baik.

    - **Boosting**
      
      Keterangan | Nilai
      ---|---
      **Akurasi** | 84.17%  
      **Presisi** | 88.71%  
      **Recall** | 78.57%  
      **F1-Score** | 83.33%

      **Boosting** memiliki performa terendah dalam hal akurasi dan F1-Score. Meskipun presisinya tinggi (88.71%), **Recall** relatif rendah (78.57%). Ini menunjukkan bahwa Boosting lebih sering melewatkan kasus positif dibandingkan model lainnya.  

    **Kesimpulan:**
    - **KNN** memberikan kinerja terbaik secara keseluruhan karena memiliki keseimbangan antara akurasi, precision, dan recall.
    - **Random Forest** unggul dalam hal **Recall**, sehingga cocok jika prioritas adalah meminimalkan false negative.
    - **Boosting** meskipun memiliki presisi tinggi, kurang optimal dalam menangkap semua kasus positif (recall rendah).

2. Menampilkan hasil evaluasi classifier

    ![hasil heatmap](https://github.com/user-attachments/assets/f185a178-565e-4214-a6c1-4d016c8e348c)

    Hasil plot di atas menunjukkan matriks kebingungan (confusion matrix) dari tiga model klasifikasi yang berbeda: KNN, Random Forest, dan Boosting. Setiap matriks menggambarkan seberapa baik masing-masing model memprediksi kelas data berdasarkan data aktual. Berikut penjelasan dari setiap plot:
    
      - **KNN Confusion Matrix (Merah)**:
        - Matriks ini menunjukkan bahwa model KNN memprediksi dengan benar sebanyak **65** kasus untuk kelas 0 dan **10** kasus untuk kelas 1.
        - Namun, model ini juga salah memprediksi sebanyak **4** kasus dari kelas 0 menjadi kelas 1 dan **60** kasus dari kelas 1 menjadi kelas 0.
        - Ini menunjukkan bahwa model KNN memiliki performa yang tidak terlalu baik, terutama dalam memprediksi kelas 1, karena banyak prediksi salah pada kelas tersebut.
    
      - **Random Forest Confusion Matrix (Hijau)**:
        - Matriks ini menunjukkan bahwa model Random Forest memprediksi dengan benar sebanyak **59** kasus untuk kelas 0 dan **41** kasus untuk kelas 1.
        - Kesalahan terjadi pada **10** kasus dari kelas 0 yang diprediksi menjadi kelas 1 dan **29** kasus dari kelas 1 yang diprediksi menjadi kelas 0.
        - Model ini memiliki akurasi yang lebih baik dibandingkan KNN, terutama karena lebih sedikit kesalahan dalam memprediksi kelas 1.
    
      - **Boosting Confusion Matrix (Biru)**:
        - Pada model Boosting, sebanyak **59** kasus dari kelas 0 dan **58** kasus dari kelas 1 diprediksi dengan benar.
        - Kesalahan terjadi pada **10** kasus dari kelas 0 yang diprediksi menjadi kelas 1 dan **12** kasus dari kelas 1 yang diprediksi menjadi kelas 0.
        - Ini adalah model yang paling akurat di antara ketiga model tersebut, dengan distribusi kesalahan yang lebih sedikit, terutama dalam memprediksi kelas 1.
    
    **Kesimpulan**: Dari ketiga model di atas, **Boosting** memiliki performa terbaik dengan jumlah prediksi benar yang paling tinggi dan jumlah kesalahan yang paling rendah. Model **Random Forest** berada di posisi kedua, sementara **KNN** memiliki performa yang paling rendah, terutama dalam memprediksi kelas 1.

3. Hubungan hasil metrik dari ketiga algoritma **K-Nearest Neighbors (KNN)**, **Random Forest (RF)**, dan **Boosting** untuk kebutuhan bisnis.
    - ***Pra-pemrosesan Data untuk Kualitas dan Akurasi Optimal***
      Hasil menunjukkan bahwa pemrosesan data berkualitas baik sudah dilakukan dengan cukup optimal, mengingat model bisa mencapai akurasi dan metrik yang cukup tinggi. Namun, jika tujuan bisnis adalah meminimalkan risiko terlewatnya pasien berisiko tinggi, maka perlu fokus pada model seperti Random Forest yang memiliki recall lebih tinggi, bahkan jika sedikit mengorbankan akurasi. Ini penting karena dalam konteks kesehatan, kesalahan mengabaikan pasien berisiko bisa berdampak fatal.
    - ***Mengembangkan Model Prediksi Risiko Gagal Jantung untuk Identifikasi Risiko Tinggi***
      **Random Forest** adalah pilihan terbaik untuk mengembangkan model prediksi risiko gagal jantung. Dengan recall tinggi, model ini bisa meminimalkan risiko gagal mendeteksi pasien berisiko tinggi. Ini sangat penting dalam bisnis kesehatan untuk mengurangi kejadian buruk yang bisa terjadi jika pasien dengan risiko tinggi tidak terdiagnosis tepat waktu. **K-Nearest Neighbors** bisa menjadi pilihan alternatif jika bisnis membutuhkan model yang seimbang dalam presisi dan recall, misalnya untuk mencegah over-treatment (terlalu banyak pasien dianggap berisiko). **Boosting** kurang cocok jika tujuannya adalah memastikan semua pasien berisiko terdeteksi. Ini bisa meningkatkan risiko terlewatnya pasien yang sebenarnya membutuhkan intervensi medis.

4. Implementasi dalam bisnis.
    - Kustomisasi Model untuk Rumah Sakit atau Asuransi:
      - Random Forest bisa digunakan oleh rumah sakit atau klinik untuk mendeteksi pasien dengan risiko tinggi, sehingga mereka dapat diberikan perhatian dan pemeriksaan lebih intensif.
      - Asuransi kesehatan bisa menggunakan model ini untuk mendeteksi risiko lebih dini dan memberikan program pencegahan atau premi yang disesuaikan dengan kondisi kesehatan pelanggan.
    - Pemberian Rekomendasi Tindakan Lanjutan:
      - Pasien dengan skor risiko tinggi bisa diarahkan untuk melakukan pemeriksaan lanjutan seperti ekokardiogram atau uji stres.
      - Penggunaan fitur seperti usia, tekanan darah, dan detak jantung maksimum dalam model juga memudahkan dokter untuk memberikan rekomendasi spesifik berdasarkan profil pasien.

---
## Kesimpulan
Pengujian setiap model dengan algoritma yang berbeda menghasilkan nilai prediksi yang berbeda pula. Model dengan hasil prediksi yang paling mendekati nilai sebenarnya diperoleh melalui algoritma K-Nearest Neighbors. Sementara itu, performa model dengan algoritma Random Forest dan Boosting masih berada di bawah performa model K-Nearest Neighbors. Oleh karena itu, dapat disimpulkan bahwa, dalam kasus ini, model dengan algoritma K-Nearest Neighbors lebih tepat untuk digunakan atau diterapkan.

Dalam konteks bisnis, penggunaan algoritma K-Nearest Neighbors tidak berfokus pada deteksi risiko, karena memerlukan keseimbangan antara prediksi positif dan negatif. Namun, jika tujuan bisnis adalah untuk menangkap seluruh hasil positif, algoritma Random Forest lebih tepat digunakan karena memiliki nilai recall yang tinggi. Sebaliknya, algoritma Boosting kurang cocok digunakan karena berisiko melewatkan beberapa pasien yang seharusnya teridentifikasi.   

---
## Penutup
Demikian hasil dari laporan proyek machine learning tentang Prediktif Analitik Penyakit Gagal Jantung. Bilamana didalam penyampaian serta penjelasan yang kurang berkenaan, saya memohon maaf. Atas waktu dan perhatiannya, saya ucapkan Terima kasih telah membaca laporan ini. Semoga dapat memberi manfaat bagi kita semuanya.
