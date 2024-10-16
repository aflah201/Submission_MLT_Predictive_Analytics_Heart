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

Pada berkas yang diunduh yakni heart.csv berisi 918 rows x 12 columns. Kolom-kolom tersebut berisi diantaranya 1 kolom berisi tipe data `float64`, 6 kolom berisi tipe data `int64`, dan 5 kolom berisi tipe data `object`. Untuk penjelasan mengenai variabel dapat dilihat sebagai berikut:

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
## Exploratory Data Analysis
Berikut adalah tahapan dalam melakukan exploratory data analysis:
- Membersihkan data yang terindikasi berisi nilai 0 dengan cara menghapus kolom yang dipilih.
- Menghapus kolom yang tidak diperlukan dalam analisis seperti kolom `FastingBS`.
- Mengatasi nilai outlier dengan menampilkan boxplot & membatasi nilai outlier.
  ```
  df_numeric = df.select_dtypes(include=[np.number])
  Q1 = df_numeric.quantile(0.25)
  Q3 = df_numeric.quantile(0.75)
  IQR=Q3-Q1
  df_cleaned=df[~((df_numeric<(Q1-1.5*IQR))|(df_numeric>(Q3+1.5*IQR))).any(axis=1)]
  ```
- Membagi dua bagian untuk fitur kategori untuk data `['Sex', 'ChestPainType', 'RestingECG', 'ExerciseAngina', 'ST_Slope']` dan fitur numerik untuk data `['Age', 'RestingBP', 'Cholesterol', 'MaxHR', 'Oldpeak', 'HeartDisease']`.
- Menampilkan plot kategori dan numerik.
- Mengecek rata-rata terhadap fitur kategori.
- Menampilkan hubungan fitur numerik.
- Menampilkan korelasi matriks untuk fitur numerik.

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
- Implementasi Random Search untuk mengetahui parameter terbaik dan nilai terbaik.
---
## Model Devlopment Testing
Setelah melakukan modeling pada data, langkah selanjutnya adalah *Model Devlopment Testing* terhadap data, diantaranya sebagai berikut:
1. Membuat prediksi Model MSE (Mean Squared Error)
2. Membuat prediksi Model classifier

---
## Evaluation

Setelah melakukan model developmenet testing pada data, langkah selanjutnya adalah *Evaluation* terhadap data, diantaranya sebagai berikut:
1. Menampilkan hasil komparasi dari ketiga algoritma **K-Nearest Neighbors (KNN)**, **Random Forest (RF)**, dan **Boosting**.
   


    Berdasarkan tabel komparasi di atas, berikut adalah penjelasan dari hasil evaluasi tiga algoritma, yaitu **K-Nearest Neighbors (KNN)**, **Random Forest (RF)**, dan **Boosting**:
    - **KNN (K-Nearest Neighbors)**
      Keterangan | Nilai
      **Akurasi:** | 89.21%  
      **Presisi:** | 89.86%  
      **Recall:** | 88.57%  
      **F1-Score:** | 89.21%
       
      **KNN** menunjukkan kinerja tertinggi secara keseluruhan. Akurasi dan F1-Score yang lebih tinggi menandakan bahwa KNN mampu memprediksi kelas dengan baik dan seimbang antara precision dan recall.

    - **RF (Random Forest)**
      Keterangan | Nilai
      **Akurasi:** | 88.49%  
      **Presisi:** | 87.50%  
      **Recall:** | 90.00%  
      **F1-Score:** | 88.73%

      **Random Forest** memiliki **Recall** paling tinggi (90%). Ini berarti RF lebih baik dalam mengidentifikasi kasus positif dengan benar, namun sedikit kalah dalam akurasi dan F1-Score dibandingkan KNN. Jika aplikasi memerlukan fokus pada deteksi positif yang tinggi (misalnya deteksi penyakit), RF bisa menjadi pilihan yang baik.

    - **Boosting**
      Keterangan | Nilai
      **Akurasi:** | 84.17%  
      **Presisi:** | 88.71%  
      **Recall:** | 78.57%  
      **F1-Score:** | 83.33%

      **Boosting** memiliki performa terendah dalam hal akurasi dan F1-Score. Meskipun presisinya tinggi (88.71%), **Recall** relatif rendah (78.57%). Ini menunjukkan bahwa Boosting lebih sering melewatkan kasus positif dibandingkan model lainnya.  

    **Kesimpulan:**
    - **KNN** memberikan kinerja terbaik secara keseluruhan karena memiliki keseimbangan antara akurasi, precision, dan recall.
    - **Random Forest** unggul dalam hal **Recall**, sehingga cocok jika prioritas adalah meminimalkan false negative.
    - **Boosting** meskipun memiliki presisi tinggi, kurang optimal dalam menangkap semua kasus positif (recall rendah).

2. Menampilkan hasil evaluasi MSE

Berikut hasil dari pengukuran model:

![download](https://github.com/user-attachments/assets/e0b581c7-4319-47bf-b7d9-b5f612067581)

Gambar di atas menunjukkan hasil evaluasi dari tiga model machine learning: Random Forest (RF), K-Nearest Neighbors (KNN), dan Boosting. Grafik tersebut membandingkan performa model pada data training dan testing dalam bentuk bar horizontal. Berikut penjelasan dari setiap model:

  - **Boosting**:
    - Performa pada data training (warna biru) dan testing (warna oranye) sangat mirip dan tinggi, menunjukkan bahwa model ini memiliki kemampuan generalisasi yang baik. Tidak ada tanda overfitting atau underfitting yang signifikan.

  - **KNN**:
    - Performa pada data training dan testing hampir sama seperti Boosting. Nilai pada kedua dataset ini juga tinggi dan konsisten. Hal ini menunjukkan bahwa KNN cukup efektif dalam memprediksi data baru tanpa overfitting.

  - **Random Forest (RF)**:
    - Pada model ini, terlihat perbedaan yang cukup signifikan antara performa pada data training dan testing. Performa pada data training jauh lebih rendah dibandingkan dengan testing, yang mungkin menunjukkan bahwa model ini mengalami underfitting atau memiliki performa yang kurang optimal pada data training.

Secara keseluruhan, Boosting dan KNN menunjukkan performa yang lebih baik dan stabil dibandingkan dengan RF. Boosting dan KNN sepertinya merupakan pilihan yang lebih baik untuk dataset ini.

Hasil prediksi yang paling mendekati nilai asli didapatkan oleh algoritma KNN dengan hasil akhir sebagai berikut.



Hasil di atas menunjukkan perbandingan nilai **asli** dengan **prediksi** dari tiga model berbeda untuk satu data (baris ke-629):

  * **`HeartDisease`**: Nilai asli adalah **0**.
  * **`prediksi_KNN`**: Model **KNN** memprediksi **0.4**.
  * **`prediksi_RF`**: Model **Random Forest** memprediksi **0.8**.
  * **`prediksi_Boosting`**: Model **Boosting** memprediksi **0.5**.

Kita dapat melihat bahwa model dengan algoritma KNN memiliki hasil prediksi 0.4, algoritma Random Forest memiliki hasil prediksi 0.8, dan algoritma Boosting memiliki hasil prediksi 0.5, perlu diketahui jika probabilitas lebih dari 0.5, kelas yang diprediksi adalah 1, jika kurang dari 0.5, kelas yang diprediksi adalah 0.
Jadi, nilai asli adalah 0, dan semua model memiliki perbedaan prediksi, tetapi model **KNN** paling mendekati (0.4).

3. Menampilkan hasil evaluasi classifier



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

---
## Kesimpulan
Pengujian setiap model dengan algoritma yang berbeda menghasilkan nilai prediksi yang berbeda pula. Model dengan nilai yang mendekati nilai sebenarnya diperoleh pada prediksi dengan menggunakan algoritma KNN. Untuk prediksi menggunakan algoritma Random Forest dan Boosting, performanya masih dibawah prediksi model KNN. Sehingga dapat disimpulkan bahwa pada kasus ini, model dengan menggunakan Algoritma KNN lebih tepat untuk digunakan atau diterapkan.

---
## Penutup
Demikian hasil dari laporan proyek machine learning tentang Prediktif Analitik Penyakit Gagal Jantung. Bilamana didalam penyampaian serta penjelasan yang kurang berkenaan, saya memohon maaf. Atas waktu dan perhatiannya, saya ucapkan Terima kasih telah membaca laporan ini. Semoga dapat memberi manfaat bagi kita semuanya.
