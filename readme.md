# Laporan Proyek Machine Learning - Muh. Wira

Ini adalah proyek sistem rekomendasi yang digunakan untuk memenuhi proyek akhir di kelas [Dicoding](https://www.dicoding.com/academies/319). Proyek ini menggunakan dua pendekatan, yaitu Content-Based Filtering dan Collaborative Filtering.

## Project Overview

Dalam era digital saat ini, jumlah konten multimedia yang tersedia secara online terus meningkat dengan pesat. Salah satu bentuk konten yang sangat populer adalah anime. Dengan ribuan judul anime yang tersedia, pengguna sering kali merasa kesulitan untuk menemukan anime yang sesuai dengan selera mereka. Di sinilah pentingnya sistem rekomendasi.

Sistem rekomendasi adalah alat yang sangat berguna untuk membantu pengguna menemukan konten yang relevan dan menarik berdasarkan preferensi mereka sebelumnya. Sistem ini memanfaatkan data historis pengguna, seperti rating dan riwayat tontonan, untuk memprediksi dan merekomendasikan anime yang mungkin disukai oleh pengguna.

Proyek ini bertujuan untuk mengembangkan sistem rekomendasi yang efektif dan akurat. Dengan menggunakan teknik machine learning, saya mengembangkan dua sistem rekomendasi yang berbeda. Pertama, sistem rekomendasi berbasis genre yang menggunakan informasi genre dari anime untuk memberikan rekomendasi. Jika seorang pengguna menyukai anime dengan genre tertentu, sistem ini akan merekomendasikan anime lain dengan genre yang sama atau serupa. Kedua, sistem rekomendasi berbasis rating yang menganalisis data rating dari pengguna untuk anime yang telah mereka tonton dan memprediksi anime lain yang mungkin disukai oleh pengguna. Dengan kedua pendekatan ini, proyek ini diharapkan dapat memberikan rekomendasi yang lebih komprehensif dan sesuai dengan preferensi pengguna.

Dengan menyelesaikan proyek ini, kita tidak hanya meningkatkan pengalaman dan kepuasan pengguna tetapi juga memberikan solusi yang efektif dalam membantu pengguna menemukan anime yang mereka sukai, yang pada gilirannya akan meningkatkan keterlibatan dan loyalitas pengguna terhadap platform.

## Business Understanding

### Problem Statements

- Pengguna kesulitan menemukan anime yang sesuai dengan preferensi pribadi mereka di antara ribuan judul yang tersedia.
- Sistem rekomendasi yang ada seringkali tidak memberikan rekomendasi yang relevan atau akurat, sehingga pengguna merasa tidak puas.
- Pengguna sering kali menghabiskan lebih banyak waktu untuk mencari anime yang menarik daripada waktu yang mereka habiskan untuk menontonnya.

### Goals

- Mengembangkan sistem rekomendasi berbasis rating yang menganalisis data rating pengguna untuk anime yang telah mereka tonton, sehingga dapat memberikan rekomendasi yang personal dan sesuai dengan preferensi pengguna.
- Mengembangkan sistem rekomendasi berbasis genre yang menggunakan informasi genre dari anime untuk memberikan rekomendasi yang relevan berdasarkan minat umum pengguna.
- Menggabungkan kedua pendekatan rekomendasi (berbasis rating dan berbasis genre) untuk memberikan rekomendasi yang lebih komprehensif, efisien, dan memuaskan, sehingga mengurangi waktu yang dihabiskan pengguna untuk mencari anime yang menarik.

### Solution statements

Untuk mencapai tujuan yang telah ditetapkan, ada dua pendekatan solusi yang dapat digunakan dalam pengembangan sistem rekomendasi ini:

#### Solution Approach 1: Content-Based Filtering:

- **Deskripsi**: Pendekatan ini menggunakan informasi genre dari anime untuk memberikan rekomendasi. Jika seorang pengguna menyukai anime dengan genre tertentu, sistem akan merekomendasikan anime lain dengan genre yang sama atau serupa.
- **Kelebihan**: Tidak memerlukan data pengguna yang banyak dan dapat memberikan rekomendasi yang relevan berdasarkan informasi konten.
- **Kekurangan**: Kurang personal dibandingkan collaborative filtering dan mungkin tidak menangkap preferensi pengguna yang lebih kompleks.

#### Solution Approach 2: Collaborative Filtering:

- **Deskripsi**: Pendekatan ini menggunakan data rating dari pengguna untuk memprediksi anime yang mungkin disukai oleh pengguna lain dengan preferensi serupa.
- **Kelebihan**: Memberikan rekomendasi yang sangat personal dan akurat berdasarkan preferensi pengguna sebelumnya.
- **Kekurangan**: Membutuhkan jumlah data yang besar dan dapat mengalami masalah "cold start" ketika data pengguna baru atau anime baru belum tersedia.

## Data Understanding

Proyek ini menggunakan tiga dataset utama yang berhubungan dengan anime dan pengguna platform anime. Dataset ini mencakup berbagai informasi yang dapat digunakan untuk menganalisis karakteristik anime, perilaku pengguna, dan preferensi mereka. Dataset ini dapat diunduh dari [Kaggle](https://www.kaggle.com/datasets/dbdmobile/myanimelist-dataset).

### Dataset Descriptions

#### 1. Anime Dataset ("anime-dataset-2023.csv")

Dataset ini memiliki 24.901 baris dan 24 kolom, yang berisi informasi detail tentang berbagai anime, termasuk rating, genre, dan popularitas. Berikut adalah deskripsi dari variabel-variabel yang ada:

- **anime_id**: ID unik untuk setiap anime.
- **Name**: Nama anime dalam bahasa aslinya.
- **English name**: Nama anime dalam bahasa Inggris.
- **Other name**: Nama atau judul lain dari anime (dalam bahasa Jepang, Cina, atau Korea).
- **Score**: Skor atau rating yang diberikan kepada anime.
- **Genres**: Genre dari anime, dipisahkan dengan koma.
- **Synopsis**: Deskripsi singkat atau ringkasan plot dari anime.
- **Type**: Jenis anime (misalnya, TV series, movie, OVA, dll.).
- **Episodes**: Jumlah episode dalam anime.
- **Aired**: Tanggal ketika anime ditayangkan.
- **Premiered**: Musim dan tahun ketika anime pertama kali ditayangkan.
- **Status**: Status anime (misalnya, Finished Airing, Currently Airing, dll.).
- **Producers**: Perusahaan produksi atau produser dari anime.
- **Licensors**: Pemberi lisensi dari anime (misalnya, platform streaming).
- **Studios**: Studio animasi yang mengerjakan anime.
- **Source**: Sumber materi dari anime (misalnya, manga, light novel, original).
- **Duration**: Durasi setiap episode.
- **Rating**: Rating usia dari anime.
- **Rank**: Peringkat anime berdasarkan popularitas atau kriteria lain.
- **Popularity**: Peringkat popularitas anime.
- **Favorites**: Jumlah kali anime ditandai sebagai favorit oleh pengguna.
- **Scored By**: Jumlah pengguna yang memberi skor pada anime.
- **Members**: Jumlah anggota yang menambahkan anime ke daftar mereka di platform.
- **Image URL**: URL gambar atau poster anime.

**Kondisi Data**:

- Semua kolom dalam dataset ini memiliki nilai yang tidak kosong (non-null), yang berarti tidak ada nilai yang hilang.
- Beberapa kolom yang seharusnya berisi informasi numerik, seperti Score, Episodes, dan Rank, bertipe data object. Ini menunjukkan bahwa data tersebut perlu diubah menjadi tipe data yang sesuai.
- Sebagian besar kolom dalam dataset ini adalah tipe data object, yang biasanya digunakan untuk teks.
- Beberapa kolom menunjukkan distribusi yang sangat lebar, terutama `Favorites` dan `Members`, dengan nilai maksimum yang sangat tinggi dibandingkan dengan nilai median dan kuartil bawah.
- Kolom `Favorites` memiliki banyak nilai nol, yang menunjukkan bahwa banyak anime tidak memiliki favorit yang tercatat.
- Kolom `Members` menunjukkan variasi yang sangat besar, yang mengindikasikan adanya anime yang sangat populer dan banyak yang kurang populer.
- Dataset ini tidak memiliki baris atau nilai yang duplikat.

#### 2. User Details Dataset ("users-details-2023.csv")

Dataset ini memiliki 731.290 baris dan 16 kolom, yang berisi informasi detail tentang pengguna platform anime, termasuk perilaku menonton dan preferensi mereka. Berikut adalah deskripsi dari variabel-variabel yang ada:

- **Mal ID**: ID unik untuk setiap pengguna.
- **Username**: Nama pengguna.
- **Gender**: Jenis kelamin pengguna.
- **Birthday**: Tanggal lahir pengguna (dalam format ISO).
- **Location**: Lokasi atau negara pengguna.
- **Joined**: Tanggal ketika pengguna bergabung dengan platform (dalam format ISO).
- **Days Watched**: Total jumlah hari yang dihabiskan pengguna untuk menonton anime.
- **Mean Score**: Skor rata-rata yang diberikan oleh pengguna kepada anime yang telah mereka tonton.
- **Watching**: Jumlah anime yang saat ini sedang ditonton oleh pengguna.
- **Completed**: Jumlah anime yang telah diselesaikan oleh pengguna.
- **On Hold**: Jumlah anime yang ditunda oleh pengguna.
- **Dropped**: Jumlah anime yang dihentikan oleh pengguna.
- **Plan to Watch**: Jumlah anime yang direncanakan untuk ditonton oleh pengguna di masa depan.
- **Total Entries**: Total jumlah entri anime dalam daftar pengguna.
- **Rewatched**: Jumlah anime yang ditonton ulang oleh pengguna.
- **Episodes Watched**: Total jumlah episode yang ditonton oleh pengguna.

**Kondisi Data**:

- Kolom `Mal ID`, `Joined`, dan sebagian besar kolom numerik (`Days Watched`, `Mean Score`, dll.) memiliki nilai yang lengkap.
- Kolom `Gender`, `Birthday`, dan `Location` memiliki banyak nilai kosong. Ini menunjukkan bahwa informasi ini tidak selalu tersedia untuk setiap penggun. Maka dari itu diperlukan penanganan terhadap nilai-nilai kosong tersebut sesuai dengan kebutuhan analisis.
- Dataset ini memiliki tipe data yang beragam, termasuk integer, float, dan object. Kolom yang seharusnya berisi informasi numerik sudah menggunakan tipe data float64 yang sesuai.
- Kolom seperti `Days Watched`, `Mean Score`, `Watching`, `Completed`, `On Hold`, `Dropped`, `Plan to Watch`, `Rewatche`d memiliki banyak nilai nol, yang menunjukkan bahwa banyak pengguna tidak memiliki aktivitas di kategori tersebut.
- Kolom `Episodes Watched` menunjukkan variasi yang sangat besar, yang mengindikasikan adanya pengguna yang sangat aktif dan banyak yang kurang aktif.
- Dataset ini tidak memiliki baris atau nilai yang duplikat.

#### 3. User Score Dataset ("users-score-2023.csv")

Dataset ini memiliki 24.325.191 baris dan 5 kolom, yang berisi informasi tentang rating yang diberikan oleh pengguna kepada berbagai anime. Berikut adalah deskripsi dari variabel-variabel yang ada:

- **user_id**: ID unik untuk setiap pengguna.
- **Username**: Nama pengguna.
- **anime_id**: ID unik untuk setiap anime.
- **Anime Title**: Judul anime.
- **rating**: Rating yang diberikan oleh pengguna kepada anime.

**Kondisi Data**:

- Dataset ini memiliki lebih dari 24 juta baris, yang menunjukkan bahwa ini adalah dataset yang sangat besar dan mungkin memerlukan sumber daya komputasi yang signifikan untuk diproses.
- Kolom-kolom yang seharusnya berisi informasi numerik (`user_id`, `anime_id`, dan `rating`) sudah menggunakan tipe data `int64`, yang sesuai. Kolom teks (`Username` dan `Anime Title`) menggunakan tipe data `object`, yang juga sesuai.
- Rating yang diberikan oleh pengguna berkisar antara 1 hingga 10, dengan rata-rata 7.62. Sebagian besar rating berada di atas 7, yang menunjukkan kecenderungan pengguna untuk memberikan rating yang cukup tinggi.
- ID user dan anime memiliki rentang yang luas, dengan ID user berkisar dari 1 hingga lebih dari 1.291.097 dan ID anime dari 1 hingga 56.085. Ini menunjukkan bahwa dataset mencakup sejumlah besar user dan anime.
- Terdapat beberapa nilai kosong pada kolom `Username` yang perlu penangan lebih lanjut.
- Dataset ini tidak memiliki baris atau nilai yang duplikat.

## Data Preparation

Pada tahap ini dilakukan beberapa langakah yang bertujuan untuk membersihkan serta menyesuaikan tipe data agar sesuai dengan kebutuhan analisis dan modeling.

### Menyesuaikan Tipe Data

#### **Mengubah Tipe Data Kolom 'Score', 'Episodes', dan 'Rank' Menjadi Numerik**:

- **Proses**: Menggunakan fungsi `pd.to_numeric()` pada kolom-kolom tersebut. Fungsi ini akan mencoba mengonversi semua nilai dalam kolom menjadi tipe data numerik. Parameter `errors='coerce'` juga digunakan untuk memastikan bahwa nilai yang tidak dapat dikonversi menjadi angka akan diubah menjadi NaN, sehingga menghindari kesalahan dalam proses konversi.
- **Alasan**: Kolom-kolom ini perlu dikonversi ke tipe data numerik agar bisa digunakan dalam analisis statistik dan modeling. Penggunaan metode yang tepat memastikan bahwa nilai yang tidak dapat dikonversi menjadi angka akan diubah menjadi NaN, sehingga menghindari kesalahan dalam proses konversi.

### Menangani Nilai NaN

#### **Mengisi Nilai NaN dengan 0**:

- **Proses**: Menggunakan fungsi `fillna(0)` pada kolom yang memiliki nilai NaN. Fungsi ini akan menggantikan semua nilai NaN dengan 0.
- **Alasan**: Mengisi nilai NaN dengan 0 untuk menghindari masalah dalam analisis dan modeling yang membutuhkan nilai numerik. Ini juga memungkinkan kita untuk mengkonversi kolom 'Episodes' dan 'Rank' menjadi tipe data integer.

#### **Mengonversi Kolom 'Episodes' dan 'Rank' Menjadi Integer**:

- **Proses**: Menggunakan fungsi `astype(int)` pada kolom 'Episodes' dan 'Rank' setelah nilai NaN diisi dengan 0. Fungsi ini akan mengonversi tipe data kolom menjadi integer.
- **Alasan**: Kolom 'Episodes' dan 'Rank' seharusnya berupa bilangan bulat, sehingga konversi ini diperlukan setelah nilai NaN diisi.

### Menangani Nilai Null pada Dataframe `users_details_df`

#### **Mengisi Nilai Null dengan Nilai Tertentu**:

- **Proses**: Menggunakan fungsi `fillna()` dengan nilai tertentu pada kolom yang memiliki nilai null. Misalnya, `fillna('Unknown')` untuk kolom 'Gender' dan 'Location', serta `fillna('1900-01-01')` untuk kolom 'Birthday'.
- **Alasan**: Mengganti nilai null dengan nilai tertentu untuk menghindari masalah dalam analisis dan modeling. Nilai default dipilih untuk menjaga konsistensi data dan memberikan informasi yang dapat diterima dalam konteks analisis.

### Menangani Nilai Null pada Dataframe `users_score_df`

#### **Menghapus Baris yang Memiliki Nilai Null**:

- **Proses**: Menggunakan fungsi `dropna(subset=['Username'])` untuk menghapus baris yang memiliki nilai null pada kolom 'Username'.
- **Alasan**: Karena jumlah nilai null yang ada terhitung sedikit, kita bisa langsung menghapus baris yang memiliki nilai null untuk menjaga kualitas data.

### Menyiapkan Data untuk Modeling

- **Proses**: Memulai dengan ngambil kolom `anime_id`, `Name`, dan `Genres` dari DataFrame `anime_df` dan menyimpannya ke dalam list. Setelah itu, kami membuat DataFrame baru `anime_new` yang berisi kolom `id`, `name`, dan `genre`. Selain itu, baris yang memiliki nilai `genre` sebagai 'UNKNOWN' dihapus untuk memastikan kualitas data.

- **Alasan**: Langkah ini penting untuk memisahkan dan menyusun ulang data sehingga lebih terstruktur dan siap digunakan dalam proses selanjutnya. Menghapus data dengan genre 'UNKNOWN' memastikan bahwa data yang digunakan memiliki informa

### TF-IDF Vectorizer

- **Proses**: Menginisialisasi `TfidfVectorizer` dan melakukan perhitungan idf pada data genre. Selanjutnya, melakukan fit dan transformasi data genre ke dalam bentuk matriks tf-idf, dan mengubah vektor tf-idf ke dalam bentuk matriks menggunakan fungsi `todense()`.

- **Alasan**: Menggunakan `TfidfVectorizer` memungkinkan untuk mengubah teks genre menjadi representasi numerik, yang memudahkan perhitungan kesamaan antar anime. Representasi numerik ini penting untuk memfasilitasi analisis lebih lanjut dan pembuatan model sistem rekomendasi.

### Cosine Similarity

- **Proses**: Menghitung cosine similarity dari DataFrame `tfidf_matrix` yang telah diperoleh. Hasilnya adalah sebuah matriks kesamaan yang menunjukkan seberapa mirip setiap anime dengan anime lainnya berdasarkan genre. Selain itu, juga dibuat DataFrame dari variabel `cosine_sim` dengan baris dan kolom berupa nama anime untuk memudahkan visualisasi.

- **Alasan**: Cosine similarity digunakan untuk mengukur kesamaan antar anime berdasarkan genre. Matriks kesamaan ini sangat berguna dalam sistem rekomendasi karena memungkinkan kita untuk menemukan anime yang mirip berdasarkan genre, sehingga rekomendasi yang diberikan lebih relevan dan sesuai dengan preferensi pengguna.

Dengan langkah-langkah di atas, data telah dipersiapkan dengan baik untuk tahap modeling, memastikan bahwa tipe data sesuai dan tidak ada nilai null yang dapat mengganggu analisis selanjutnya.

## Modeling

Tahap modeling menggunakan dua pendekatan berbeda untuk memberikan rekomendasi: Content-Based Filtering dan Collaborative Filtering.

### Content-Based Filtering

Pendekatan pertama yang digunakan adalah **Content-Based Filtering**. Algoritma yang digunakan pada pendekatan ini adalah `Cosine Similarity`.

#### Cara Kerja

- `Cosine similarity` adalah metode untuk mengukur kemiripan antara dua vektor dalam ruang multidimensi. Dalam konteks sistem rekomendasi, vektor ini biasanya merepresentasikan item (anime) berdasarkan fitur tertentu, seperti genre. Cosine similarity dihitung sebagai dot product dari dua vektor dibagi dengan magnitudo dari masing-masing vektor.
- Sistem rekomendasi dibuat menggunakna fungsi `anime_recommendations` yang menerima parameter `anime_name`, `similarity_data`, `items`, dan `k` (jumlah rekomendasi yang diinginkan).
- Fungsi ini mengidentifikasi `k` anime yang paling mirip berdasarkan skor cosine similarity.
- Menghasilkan dataframe yang berisi nama-nama anime yang direkomendasikan beserta genre mereka.

#### Parameter yang Digunakan

- **TF-IDF Vectorizer**: Mengubah teks genre menjadi vektor numerik.
- **Cosine Similarity**: Menghitung skor kemiripan antara pasangan anime berdasarkan vektor TF-IDF mereka.

#### Contoh Output

![output](https://i.ibb.co.com/C1h2Wf7/image.png)

- Untuk anime `Seishun Buta Yarou wa Bunny Girl Senpai no Yume wo Minai` dengan genre Drama, Romanca, dan Supranatural, dapat diperoleh rekomendasi 5 anime yang memiliki genre yang sama atau mirip.

#### Kelebihan dan Kekurangan

**Kelebihan**:

- Rekomendasi yang dihasilkan sangat relevan karena didasarkan pada fitur spesifik dari item, dalam hal ini fitur genre.
- Tidak memerlukan data dari pengguna lain, sehingga lebih privasi.

**Kekurangan**:

- Terbatas pada fitur yang digunakan; jika fitur tidak representatif, rekomendasi bisa kurang akurat.
- Tidak dapat merekomendasikan item yang berbeda dari preferensi sebelumnya.

### Collaborative Filtering

Pendekatan kedua yang kita gunakan adalah Collaborative Filtering dengan menggunakan model Neural Network. Algoritma yang digunakan adalah `RecommenderNer` dari Keras.

#### Cara Kerja

- `RecommenderNet` adalah model neural network yang dirancang untuk sistem rekomendasi. Model ini mempelajari embedding dari pengguna dan item (anime) untuk memprediksi rating yang akan diberikan oleh pengguna terhadap item yang belum dirating.
- Embedding adalah representasi vektor dari pengguna dan item dalam ruang laten yang lebih rendah.
- Rekomendasi dilakukan dengan mengambil sample pengguna, memprediksi rating untuk item yang belum dirating oleh pengguna tersebut, dan memberikan rekomendasi berdasarkan prediksi rating tertinggi.

#### Parameter yang Digunakan

- **Embedding Dimension**: Ukuran vektor embedding untuk pengguna dan item.
- **User and Item Embedding Layers**: Layer embedding untuk pengguna dan item.
- **Bias Terms**: Layer bias untuk menangkap preferensi spesifik pengguna dan item.
- **Optimizer**: Algoritma optimisasi seperti Adam untuk memperbarui bobot model selama training.
- **Loss Function**: Fungsi loss seperti Mean Squared Error untuk mengukur kesalahan prediksi.

#### Contoh Output

![alt text](https://i.ibb.co.com/P5Sm9ZT/image.png)

- Output tersebut menampilkan anime yang telah diberi rating oleh pengguna. Dalam contoh ini, pengguna 11142 memberikan rating tinggi pada anime `Ijiranaide, Nagatoro-san` dengan genre `Comedy`. Kemudian sistem menampilkan 10 rekomendasi anime berdasarkan prediksi rating tertinggi yang dihasilkan oleh model.

#### Kelebihan dan Kekurangan

**Kelebihan**:

- Dapat menemukan item baru yang mungkin tidak akan ditemukan dengan content-based filtering.
- Menggunakan data dari banyak pengguna untuk meningkatkan akurasi rekomendasi.
- Neural Network memberikan fleksibilitas dalam mendefinisikan arsitektur model yang kompleks

**Kekurangan**:

- Membutuhkan data yang cukup banyak dari banyak pengguna.
- Masalah cold start untuk pengguna atau item baru yang belum memiliki cukup data interaksi.

Dengan menggunakan dua pendekatan ini, sistem rekomendasi dapat memberikan rekomendasi yang lebih komprehensif dan relevan bagi pengguna.

## Evaluation

### Model Content-Based Filtering

- Pada model content-based filtering, kita melakukan evaluasi dengan menggunakan metrik precision, recall, dan F1 score untuk mengukur kinerja sistem rekomendasi.
- Precision mengukur persentase rekomendasi yang relevan dari total rekomendasi yang diberikan oleh sistem.
- Recall mengukur persentase item relevan yang berhasil ditemukan oleh sistem dari total item relevan yang ada.
- F1 score adalah rata-rata harmonis dari precision dan recall, memberikan gambaran keseimbangan antara kedua metrik tersebut.
- Dengan menggunakan metrik ini, kita dapat secara kuantitatif menilai seberapa baik sistem rekomendasi dalam memberikan rekomendasi yang relevan dan menemukan semua item yang relevan.

**Hasil Evaluasi**:

- Evaluasi dilakukan pada 5000 sampel data acak dari dataset.
- Precision dari sistem rekomendasi adalah 0.9502, yang menunjukkan bahwa sekitar 95.02% dari rekomendasi yang diberikan oleh sistem adalah relevan.
- Recall dari sistem rekomendasi adalah 1.0000, yang berarti bahwa sistem berhasil menemukan semua item yang relevan dalam dataset yang diuji.
- F1 Score dari sistem rekomendasi adalah 0.9745, yang menunjukkan keseimbangan yang sangat baik antara precision dan recall.
- Dari hasil evaluasi tersebut, dapat disimpulkan bahwa genre dari anime yang direkomendasikan sudah sangat sesuai dengan genre dari anime yang diminta. Sistem rekomendasi tidak hanya akurat dalam memberikan rekomendasi yang relevan tetapi juga sangat efektif dalam menemukan semua item yang relevan, memberikan gambaran tentang relevansi dan kinerja tinggi dari model cosine similarity yang digunakan.

### Model Collaborative Filtering

- Pada model content-based filtering kita melakukan evaluasi hasil rekomendasi menggunakan metrik `Root Mean Squared Error (RMSE)`.
- RMSE mengukur rata-rata kesalahan kuadrat antara nilai sebenarnya ($y_i$) dan nilai prediksi ($\hat{y}_i$). Semakin kecil nilai RMSE, semakin baik performa model. RMSE sangat sensitif terhadap kesalahan besar, sehingga memberikan penalti yang lebih besar pada prediksi yang jauh dari nilai sebenarnya.

**Hasil Evaluasi**

![alt text](https://i.ibb.co.com/R3pc7bm/image.png)

- Grafik di atas menunjukkan metrik RMSE selama proses pelatihan model. Sumbu X merepresentasikan jumlah epoch, yaitu iterasi pelatihan model, sedangkan sumbu Y merepresentasikan nilai RMSE. Grafik ini memplot nilai RMSE untuk data pelatihan (train) dan data validasi (test) terhadap jumlah epoch.
- Dimana hasil akhir niali RMSE untuk data pelatihan adalah 0.0658, sementara untuk data validasi adalah 0.2519.
- Berdasarkan hasil evaluasi, model Collaborative Filtering dengan Neural Network menunjukkan peningkatan performa yang signifikan selama pelatihan, sebagaimana ditunjukkan oleh penurunan nilai RMSE. Namun, adanya perbedaan antara nilai RMSE pada data pelatihan dan data validasi mengindikasikan bahwa model mungkin mengalami overfitting. Untuk mengatasi hal ini, beberapa langkah yang dapat diambil meliputi: regularisasi, dropout, ataupun cross-validation.

### Kesimpulan

Berdasarkan hasil dan evaluasi yang dilakukan, dapat disimpulkan bahwa:

- Model yang dibangun telah menjawab problem statement dengan memberikan rekomendasi anime yang relevan berdasarkan preferensi pengguna. Evaluasi dengan RMSE menunjukkan bahwa model dapat memprediksi rating dengan tingkat kesalahan yang dapat diterima.
- Model juga telah berhasil mencapai goals yang diharapkan, yaitu memberikan rekomendasi yang relevan dan akurat kepada pengguna. Hal ini dibuktikan dengan hasil evaluasi yang menunjukkan bahwa genre dari anime yang direkomendasikan sudah sesuai dengan genre dari anime yang diminta.
- Solusi yang direncanakan, yaitu menggunakan model Collaborative Filtering dengan Neural Network, berdampak positif terhadap sistem rekomendasi. Model ini dapat memberikan rekomendasi yang lebih komprehensif dan relevan bagi pengguna, dibandingkan dengan model content-based filtering. Selain itu, penggunaan Neural Network memungkinkan fleksibilitas dalam mendefinisikan arsitektur model yang kompleks, sehingga dapat meningkatkan akurasi rekomendasi.

Dengan demikian, model ini tidak hanya memberikan rekomendasi yang sesuai dengan preferensi pengguna tetapi juga berpotensi meningkatkan kepuasan pengguna dan engagement dalam platform, yang pada akhirnya dapat berdampak positif terhadap tujuan bisnis.
