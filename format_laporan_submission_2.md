# Laporan Proyek Machine Learning - Kevin Chrsitian Sepoetro 

## Project Overview

Di era zaman sekarang yang semakin berkembang, banyak bidang bisnis yang menggunakan Machine Learning untuk meningkatkan bisnis mereka. Misalnya dengan sistem rekomendasi, mereka akan mendapatkan banyak keuntungan dari pembelian barang yang direkomendasikan atau bahkan meningkatkan insight toko. Hal ini juga dapat diterapkan di toko perpustakaan atau pada toko buku online agar user dapat rekomendasi buku yang tepat dan sesuai selera. Sistem rekomendasi buku juga berperan untuk meningkatkan literasi baca pada masyarakat Indoensia.

Menurut Jurnal yang ditulis oleh Moh. Irfan, Andharini Dwi C, Fika Hastarita R. buku merupakan informasi segala kebutuhan yang diperlukan, dimulai dari iptek, seni budaya, ekonomi, politik, sosial dan pertahanan keamanan dan lain-lain. Upaya membaca buku membuka wawasan dunia intelek sehingga dapat mengubah masa depan serta mencerdaskan akal, pikiran dan iman. Dengan membaca buku, selain pengetahuan akan semakin bertambah, pribadi akan semakin kaya, yang kesemuannya jelas akan menurunkan efek negatif terhadap anak-anak, yakni kenakalan. Sedangkan anak yang tidak terbina minat bacanya sejak dini akanmenghadapi peluang yang semakin kecil untuk mengembangkan pengetahuan setinggi-tingginya. Namun berdasarkan laporan Bank Dunia, Indonesia merupakan negara yang memiliki minat baca sangat rendah. Hal tersebut sungguh disayangkan, mengingat sebagai negara besar, Indonesia memiliki potensi besar untuk menjadi negara yang unggul.
  
  Format Referensi: [Sistem Rekomendasi Buku Online Dengan Metode Collaborative Filtering](https://ejournal.akprind.ac.id/index.php/technoscientia/article/view/612) 

Dari jurnal tersebut, dapat diketahui bahwa rendahnya minat baca di Indonesia, yang dapat menghambat kemajuan perkembangan bangsa. Untuk mengatasi masalah ini, salah satu solusi yang potensial adalah pengembangan dan implementasi sistem rekomendasi buku.  Sistem rekomendasi buku bukan hanya alat komersial untuk meningkatkan penjualan, tetapi juga instrumen penting dalam misi sosial untuk meningkatkan literasi dan pengetahuan di masyarakat Indonesia.

Sistem rekomendasi buku dapat mengatasi masalah rendahnya minat baca di Indonesia dengan memberikan rekomendasi yang personal dan relevan berdasarkan data interaksi pengguna, seperti riwayat pembelian dan preferensi bacaan. Dengan memperkenalkan pengguna pada buku-buku yang sesuai dengan minat mereka dan genre baru yang mungkin belum dikenal, sistem ini mempermudah akses dan pemilihan buku yang tepat, sehingga meningkatkan minat dan keterlibatan dalam membaca. Selain itu, platform online yang didukung oleh sistem rekomendasi ini juga mempermudah akses buku dari berbagai lokasi, yang secara keseluruhan mendukung peningkatan literasi dan pendidikan di masyarakat.
***

## Business Understanding

### Problem Statements

Menjelaskan pernyataan masalah:
- Bagaimana cara meningkatkan minat baca di Indonesia yang saat ini masih rendah, sehingga dapat mendorong perkembangan intelektual masyarakat?
- Bagaimana cara mempermudah akses masyarakat terhadap buku-buku yang relevan dan sesuai minat mereka, sehingga mereka dapat menemukan bahan bacaan yang menarik?
- Bagaimana teknologi dapat dimanfaatkan secara optimal untuk mengembangkan sistem rekomendasi buku yang lebih personal dan relevan, sehingga dapat meningkatkan literasi di masyarakat?

### Goals

Menjelaskan tujuan proyek yang menjawab pernyataan masalah:
- Meningkatkan minat baca masyarakat Indonesia dengan memperkenalkan sistem rekomendasi buku yang mempermudahkan pengguna menemukan buku yang relevan.
-  Meningkatkan akses ke buku buku yang sesuai dengan kebutuhan user melalui rekomendasi yang dipersonalisasi, sehingga meningkatkan kepuasan user.
- Mengembangkan Rekomendasi Sitem dengan Machine Learning yang efektif dan efesien, yang mampu memberikan rekomendasi buku yang berkualitas.

    ### Solution statements
    - Collaborative Filtering
      Metode ini akan menghasilkan rekomendasi sejumlah buku yang sesuai dengan preferensi pengguna berdasarkan rating yang telah diberikan user sebelumnya. Dari data rating pengguna dapat digunakan untuk mengidentifikasi buku-buku yang mirip dan belum pernah diberi rating oleh pengguna untuk direkomendasikan.
    - Content Based Filtering
      Algoritma ini merekomendasikan buku berdasarkan karakteristik konten buku dan preferensi pengguna yang telah ada. Dengan menganalisis seperti deskripsi, genre, penulis, dan kata kunci dari buku-buku yang disukai pengguna sebelumnya, sistem dapat merekomendasikan buku-buku lain yang memiliki karakteristik serupa.
***

## Data Understanding
Dataset yang digunakan pada proyek ini diambil dari website kaggle yaitu Book Recommendation Dataset. Dataset ini memiliki 3 file csv yaitu Ratings.csv, Book.csv, dan Users.csv. 
Dataset : [Book Recommendation Dataset](https://www.kaggle.com/datasets/arashnic/book-recommendation-dataset?select=Users.csv).

Variabel-variabel pada Book Recomendation dataset adalah sebagai berikut:
- Books.csv terdiri dari 271.360 rows. Berikut adalah  feature feature yang ada pada Books.csv :
  - `ISBN` : berisi kode ISBN dari buku  
  - `Book-Title` : berisi judul buku
  - `Book-Author` : berisi penulis buku
  - `Year-Of-Publication` : tahun terbit buku  
  - `Publisher` : penerbit buku  
  - `Image-URL-S` : URL menuju gambar buku berukuran kecil
  - `Image-URL-M` : URL menuju gambar buku berukuran sedang
  - `Image-URL-L` : URL menuju gambar buku berukuran besar
    
- Ratings.csv terdiri dari 1.149.780 rows. Berikut adalah feature feature dari Ratings.csv :
  - `User-ID` : berisi ID user
  - `ISBN` : berisi kode ISBN buku yang diberi rating oleh pengguna
  - `Book-Rating` : rating buku (1 -10)

- Users.csv terdiri dari 278.858 rows. Berikut adalah feature feature dari Users.csv :
  - `User-ID` : berisi ID unik pengguna
  - `Location` : berisi data lokasi pengguna
  - `Age` : berisi data usia pengguna

Pada jumlah dari setiap file memiliki jumlah nilai yang unik, dimana data yang sama muncul beberapa kali dihitung sekali, sehingga total data sebagai berikut :



| Nama File                  | Jumlah Data                                                                                                        |
| ---------------------- | ----------------------------------------------------------------------------------------------------- |
| Book.csv                 | 271.360               |
| Ratings.csv                | 105.283 |
| Users.csv              | 278.858


<br>

#### **Univariate Exploratory Data Analysis**

- **Book Variable** 
Untuk mengetahui informasi Book.csv seperti tentang struktur DataFrame, termasuk jumlah total baris dan kolom, tipe data dari setiap kolom, dan serta jumlah nilai non-null menggunakan pandas dengan perintah book.info()<br>
![image](https://github.com/user-attachments/assets/485801a2-d383-421f-90a4-423babe57464)<br>
Data pada Book.csv memiliki :
- 8 Feature
- Semua Feature berjumlah 271360
- Data semua feature non-null
- Semua Feature bertipe Object
Lalu untuk mengetahui apakah ada nilai yang NaN atau hilang dapat menggunakan book.isnull().sum() <br>
![image](https://github.com/user-attachments/assets/6cf6f0bf-a3ac-4a86-a45a-8ee1a13e6e5e) 
Dari Ouput book.isnull().sum() ada sedikit yang missing value. Selanjutnya menghitung jumlah data unik pada setiap feature. 
![image](https://github.com/user-attachments/assets/09e212b4-aea8-4052-9dcf-ecdb67ea0670)
<br>

- **Rating Variable**
Untuk mengetahui informasi Ratings.csv seperti tentang struktur DataFrame, termasuk jumlah total baris dan kolom, tipe data dari setiap kolom, dan serta jumlah nilai non-null menggunakan pandas dengan perintah rating.info()<br>
![image](https://github.com/user-attachments/assets/873c53bb-6914-44c8-95c3-546d919a85d6)<br>
Dari Ouput rating.info() bisa disimpulkan :
- Semua Feature berjumlah 1.149.780 data
- Terdapat 2 type data yaitu int64 (User-ID dan Book-Rating) dan object (ISBN)
- Data semua Feature Non-Null <br>
 Mengetahui apakah ada nilai yang NaN atau hilang dapat menggunakan book.isnull().sum()<br>
![image](https://github.com/user-attachments/assets/4842d7cd-7a26-4d96-be9c-8ebd97aa30c4)<br>
Ternyata tidak ada yang missing value. Selanjutnya melihat jumlah nilai unik rating berdasarkan User-ID dan ISBN.<br>
![image](https://github.com/user-attachments/assets/a3c61c24-6154-4efb-83d4-f56b70ef22a3) <br>
Melihat deskripsi rating dapat menggunakan rating.describe()<br>
![image](https://github.com/user-attachments/assets/cf8953fd-b841-47f7-b0cf-727bec0aea7f)
Dapat disimpulkan bahawa max Rating 10 dan Min Rating 0 <br>
Selanjutnya melihat Jumlah rating. Melihat Jumlah pada Rating dengan cara menggabungkan data rating dengan data book berdasarkan ISBN. Dari Ouput yang dihasilkan terdapat jumlah data yaitu 1.149.780. Selanjutnya melihat apakah ada missing value atau tidak dengan syntax isnull().sum(). <br>
![image](https://github.com/user-attachments/assets/2fc8a0a8-c3f3-44b2-a454-c968f083f3f5)<br>
Ternyata terdapat banyak missing Value. 
<br>

- **User Variable**
Jumlah data unik pada User-ID. <br>
![image](https://github.com/user-attachments/assets/264dbd96-12e9-4687-9d05-c17c2b4c3eec)
Selanjutnya periksa ada missing value dengan syntax user.isnull().sum().<br>
![image](https://github.com/user-attachments/assets/c0045063-046a-464f-81e5-88f8a369f77f)<br>
Dapat Disimpulkan bahwa terdapat missing Value pada feature Age

***

## Data Preparation

### Content Based Filtering
Pada tahap ini dilakukan :
- Menyimpan data Book pada variable all_buku_name
- Mengatasi Missing Value
- Mengatasi data Duplikat
- Proses Sampling
- Konversi data ke List
- Membuat Dictionary 
- TF IDF Vectorizer
- Melihat hubungan Book dengan Author
<br>

1. **Menyimpan data Book pada variable all_buku_name**
Pada Tahapan ini melakukan pengecekan lagi dan membuat variable all_buku_name untuk menyimpan data Book.csv. Jumlah data sebanyak 271.360 
<br>

2. **Mengatasi Missing Value**
Sebelum Mengatasi Missing Value, periksa terlebih dahulu apakah ada missing value. Dapat menggunakan syntax isnull().sum() <br>
![image](https://github.com/user-attachments/assets/7adb6573-ec10-4579-861e-08f1497fafe9) <br>
Pada Ouput terdapat sedikit missing Value. Meskipun sedikit tetapi hal ini bisa mengganggu model dalam kinerja model. Oleh karena salah satu cara mengatasi yaitu hapus yang missing Value menggunakan .dropna(). <br>
![image](https://github.com/user-attachments/assets/2b94e67e-90c0-4c73-b8d8-fdad6e3d450a) <br>
Setelah dilakukan Drop data maka tidak ada lagi missing value.
<br>

3. **Mengatasi Data Duplikat**
Tahapan selanjutnya yaitu menghapus Duplikat pada data. Tujuan menghapus data Duplikat agar menghindari bias dan dapat mencegah terjadinya overfitting. Untuk menghapus duplikat menggunakan syntax .drop.duplicates().<br>
![image](https://github.com/user-attachments/assets/32d50fda-dcea-4af2-935b-b432827bd723)
![image](https://github.com/user-attachments/assets/cf91a9ce-4556-4d39-9083-6a58a41e390b)<br>
Terdapat 271.353 Data setelah terduplikat.

<br>

4. **Proses Sampling**
Pada tahapan ini sebelum konversi data ke list, melakukan pengambilan data yang akan dipakai yaitu 40.000 data dari 271.353. Hal ini dikarenakan jika menggunakan 271.353 data RAM pada Google Colab tidak cukup saat melakukan conversi ke TF-IDF. 
<br>

5. **Konversi Data ke List**
Selanjutnya mengubah data ke list. Hal ini bertujuan agar saat pengolahan data lebih mudah. Untuk konversi ke list dapat menggunakan syntax .tolist().
<br>


6. **Membuat Dictionary**
Tahapan ini membuat dictionary untuk menetukan pasangan key-value pada data ISBN_id, book_name, dan Author yang telah disiapkan sebelumnya. <br>
![image](https://github.com/user-attachments/assets/7fd258ff-e5c8-4dce-a210-ebba612c7b0d)

<br>

7. **TF IDF Vectorizer**
Pada tahap ini mengubah teks menjadi numerik menggunakan TF IDF Vectorizer pada Author. Untuk perintah mengubah ke TF IDF menggunakan library yang disediakan Sklearn yaitu tfidfvectorizer(). Selanjutnya melakukan fit dan transform ke dalam matrix dengan `fit.transform()`. Untuk mengecek data nya bisa menggunakan syntax `.shape`. 
![image](https://github.com/user-attachments/assets/2a6b6001-9a44-476d-bdd4-4f23cb170292) <br> Ouput yang dihasilkan terdapat 40.000 jumlah ukuran data dan  13.842 jumlah Author dalam matrix. 
<br>

8. **Melihat hubungan Book dengan Author**
Selanjutnya untuk menghasilkan vektor tf-idf dalam bentuk matriks, menggunakan syntax todense(). Kemudian, melihat matriks tf-idf untuk beberapa buku (book_name) dan Author. <br>
![image](https://github.com/user-attachments/assets/50a63f7f-cc67-4969-b559-0325cc497845) <br>
Pada Ouput Matrix diatas hanya menampilkan beberapa saja, tidak bisa semua outputnya karena data terlalu besar. Dari matriks kolerasi antara book name dan author dapat dilihat bahwa jika 0 maka tidak ada keterkaitan dan jika 1 ada keterkaitan antara Author dan book_name. 

<br>

### Collaborative Filltering
Pada Tahapan ini dilakukan beberapa hal :
- Memahami data rating 
- Menyandikan (encode) fitur ‘user’ dan ‘ISBN’ ke dalam indeks integer. 
- Memetakan ‘USER-ID’ dan ‘ISBN’ ke dataframe yang berkaitan.
- Mengecek beberapa hal dalam data seperti jumlah user, jumlah buku, kemudian mengubah nilai rating menjadi float.

1. **Memahami Data Rating**
Pada tahapan ini menggunakan data pada rating 60.000 data. Karena jika menggunakan data 1.149.780, akan sangat memakan waktu lama untuk proses training. Untuk memudahkan supaya tidak tertukar dengan fitur ‘rating’ pada data, nama variabel rating diubah menjadi df.
<br>

2. **Melakukan Encode Pada fitur User dan ISBN**
Pada Tahapan ini dilakukan Encode kedalam Index integer. Hal ini seperti mengubah fitur User-ID dan ISBN kedalam dictionary. 
<br>

3. **Memetakan User-ID dan ISBN ke dataframe yang berkaitan**
Setelah dilakukan encode, selanjutnya melakukan mapping kedalam datframe yang berkaitan. Contohnya User dilakukan mapping pada fitur User-ID, dan Mapping ISBN ke dataframe book.
<br>

4. **Mengecek jumlah user, buku, dan mengubah rating menjadi float**
Pada tahapan ini mengecek jumlah User-ID, Buku, dan jumlah max rating dan Min Rating pada dataframe. Sebelum menghitung max dan min rating, dilakukan konversi data rating ke Float.

| Variable                  | Jumlah Data                                               |
| ---------------------- | ----------------------------------------------------------------------------------------------------- |
| User                 | 5.153            |
| Buku                | 43.266|
| Max Rating              | 10.0|
| Min Rating|  0.0|

***

## Modeling
Pada Modeling Data terdapat dua Pendekatan yaitu, Content Based dan Colaborative Filtering.

### **Content Based Filtering**

- **Cosine Similarity**
Kemudian menghitung derajat kesamaan (similarity degree) antar buku dengan teknik cosine similarity. Di sini, menggunakan fungsi cosine_similarity dari library sklearn.  <br> Pada tahapan ini, menghitung cosine similarity dataframe tfidf_matrix yang diperoleh pada tahapan sebelumnya. 
<br>Selanjutnya,  Ouput kesamaan matirx pada setiap buku dapat dengan cara menampilkan nama buku dalam 5 sampel kolom (axis = 1) dan 10 sampel baris (axis=0). <br>
![image](https://github.com/user-attachments/assets/195eaf82-ab8d-4805-80d6-dfed10fd8fdf) <br>
Dengan cosine similarity pada output diatas, berhasil mengidentifikasi kesamaan antara satu buku dengan buku lainnya. Berdasarkan data yang ada, matriks di atas sebenarnya berukuran 40000 Author x 40000 nama buku. Akan tetapi tentu ouputnya tidak bisa menampilkan semuanya. Oleh karena itu, hanya memilih 10 buku pada baris vertikal dan 5 buku. Sama seperti antar Auhtor dengan Buku_name jika atau mendaekati 1 maka memiliki similarity atau kesamaan, jika 0 sebaliknya.
<br>

- **Mendapatkan Rekomendasi Buku**
Selanjutnya untuk mendapatkan rekomendasi Buku berdasarkan Author maka ada beberapa yang perlu diperhatikan. Dimana sistem ini user melihat lihat buku misalnya buku "JOSHUA" karya Joshep Girzone. Kemudian user ingin berencana membaca buku lain, Sistem akan merekomendasikan buku seperti Joshua In Holy Land. Rekomendasi kedua buku ini berdasarkan kesamaan yang dihitung dengan cosine similarity pada tahap sebelumnya. <br>
Dalam code membuat fungsi book_recommendations dengan beberapa parameter sebagai berikut:
- Nama_buku : Nama buku 
- Similarity_data : Dataframe mengenai similarity yang telah di definisikan sebelumnya.
- Items : Nama buku dan Author yang digunakan untuk mendefinisikan kemiripan.
- k : Banyak rekomendasi yang ingin diberikan (Top-5)

Selain itu pada mendapatkan rekomendasi menggunakan argpartition. Dalam sistem rekomendasi ini, argpartition digunakan untuk menemukan 5 item teratas yang paling mirip dengan item yang dicari. Prosesnya adalah:
- Menghitung Similarity: Sistem menghitung tingkat kesamaan antara item yang dicari dengan semua item lainnya.
- Memilih 5 Teratas: Menggunakan argpartition untuk memilih 5 item dengan tingkat kesamaan tertinggi.
- Mengurutkan: Item-item ini kemudian diurutkan berdasarkan kesamaan tertinggi hingga terendah.
- Menghapus Item Asli: Item asli (contoh: nama restoran yang dicari) dihapus dari daftar rekomendasi.
- Hasil Akhir: Menampilkan 5 item yang paling mirip, tanpa menyertakan item asli yang dicari.

<br>

- **Result**
Cara penggunaan nya dengam memanggil function book_recommendations dan memasukan judul buku. Contohnya `JOSHUA`.<br>
![image](https://github.com/user-attachments/assets/d79359bc-24e4-4a51-96c0-a3cfabec742c)<br>
Dan dapat dilihat **top-5** hasil sitem rekomendasi, bahwa sistem berhasil merekomendasikan Author yang sama dengan Author yaitu Joshua.

<br>

### **Colaborative Filtering**
1.  **Import Libary**
Untuk melakukan pendekatan Collaborative Filtering import dahulu library yang dibutuhkan seperti import tensorflow, keras, dan lain lain.
<br>


2.  **Membagi data Training dan Testing**
Langkah selanjutnya membagi data train dan test. Sebelum itu melakukan random data agar distribusi nya acak.Setelah itu melakukan pembagian train dan test dimana data train adalah 90% dan test 10%. Saat membagi dataset perlu memetakan (mapping) data user dan book menjadi satu value terlebih dahulu. Lalu, rating dalam skala 0 sampai 1 agar mudah dalam melakukan proses training. 
<br>

3.  **Proses Training**<br>
Pada tahap training, membuat class RecommenderNet dengan keras Model class. Berikut cara kerjanya :
- Embedding: Data pengguna dan buku dikonversi menjadi representasi vektor numerik (embedding).
- Dot Product: Vektor embedding pengguna dan buku dikalikan (dot product) untuk mengukur kecocokan.
- Bias: Ditambahkan bias spesifik untuk setiap pengguna dan buku untuk mengakomodasi preferensi individual.
- Fungsi Aktivasi Sigmoid: Hasil dari dot product dan bias kemudian diterapkan fungsi sigmoid untuk mengubah skor kecocokan ke dalam rentang [0,1].
Skor Kecocokan: Skor ini menunjukkan seberapa cocok pengguna dengan buku tertentu, di mana 1 berarti sangat cocok dan 0 berarti tidak cocok sama sekali.
Lalu membuat class RecommenderNet dengan keras Model class. <br>
Selanjutnya melakukan proses compile data dengan parameter :
 - loss function : Binary Crossentropy  
 - Optimizer : Adam (Adaptive Moment Estimation)
 - Evaluation : root mean squared error (RMSE)
 - Learning Rate : 0.001
 - Epochs : 100  <br>
Fungsi Loss (Binary Crossentropy):
Digunakan untuk mengukur perbedaan antara distribusi probabilitas prediksi model dan distribusi sebenarnya. Binary Crossentropy cocok untuk klasifikasi biner, di mana output model adalah probabilitas dari dua kelas yaitu 1 dan 0. <br>
Optimizer (Adam):
Adam dipilih karena kemampuannya untuk menyesuaikan laju pembelajaran selama pelatihan, membuat proses konvergensi lebih cepat dan stabil. Ini membantu mengoptimalkan fungsi loss dengan menyesuaikan bobot model.
 <br>

Output :
![image](https://github.com/user-attachments/assets/d698ad1e-3554-413f-9fec-af769e42ede8)<br>
Pada grafik diatas dapat dilihat bahwa grafik overfitting, Dimana overfitting saat train bagus akurasi tetapi saat akurasi validasi jelek.

4. **Result**
Untuk membuat Sistem rekomendasi berikut adalah langkah langkahnya :
- Ambil Sampel Pengguna: Pilih pengguna secara acak.
- Identifikasi Buku yang Belum Dibaca: Tentukan daftar buku (book_not_visited) yang belum pernah dilihat oleh pengguna tersebut.
- Gunakan Penilaian Pengguna: Gunakan rating yang diberikan pengguna pada buku-buku yang telah mereka baca untuk membuat rekomendasi buku.
- Gunakan Operator Bitwise (~): Gunakan operator bitwise ~ pada variabel book_visited_by_user untuk mendapatkan daftar book_not_visited. Ini akan menghasilkan daftar buku yang tidak ada dalam daftar book_visited_by_user, artinya buku-buku yang belum pernah dibaca oleh pengguna dan layak direkomendasikan. <br>
Selanjutnya, untuk memperoleh rekomendasi buku, gunakan fungsi model.predict() dari library Keras. Pada Rekomendasi berbasis Collaborative Filtering ini merekomendasikan **top 10**. <br>
![image](https://github.com/user-attachments/assets/61cc4660-39ff-42e8-93ed-73c11e7d10f4) <br>
Dapat dilihat bahwa Sistem Rekomendasi bisa memberikan Rekomendasi **top 10**, tetapi tidak akurat. Dimana Rekomendasi buku harusnya sama dengan pengarang atau Author tetapi disini merekomendasikan yang lain. Tidak ada kesamaan antar kolerasi. Hal ini mungkin disebabkan model Overfitting.<br>

### **Kelibahan dan Kelemahan Content Based Filtering dan Collaborative Filtering**

Kelebihan Content-Based Filtering
-  Personalized Recommendations:
Rekomendasi sangat disesuaikan dengan preferensi individu pengguna, berdasarkan fitur dari item yang telah mereka sukai sebelumnya.
- Tidak Membutuhkan Data Pengguna Lain:
Metode ini tidak bergantung pada data dari pengguna lain, sehingga tidak terpengaruh oleh masalah sparsity atau cold start dari item.
- Menghindari Cold Start untuk Item:
Item baru dengan deskripsi atau fitur yang baik dapat direkomendasikan tanpa perlu menunggu rating dari pengguna lain.

Kekurangan Content-Based Filtering
- Keterbatasan Fitur Konten:
Sangat tergantung pada kualitas dan kelengkapan fitur yang tersedia untuk setiap item. Jika fitur yang relevan tidak ada atau kurang akurat, kualitas rekomendasi dapat menurun.
- Kurang Diversifikasi Rekomendasi:
Cenderung merekomendasikan item yang mirip dengan yang sudah disukai pengguna, sehingga kurang mampu memperkenalkan variasi atau mengeksplorasi item baru yang berbeda dari preferensi yang sudah diketahui.
- Kesulitan dalam Ekstraksi Fitur Otomatis:
Proses penentuan fitur yang relevan secara otomatis bisa menjadi tantangan, terutama jika deskripsi atau atribut item tidak terstruktur atau sulit dikuantifikasi.


Kelebihan Collaborative Filtering
- Tidak Membutuhkan Fitur Konten:
Metode ini hanya membutuhkan informasi interaksi pengguna-item (seperti rating atau perilaku), sehingga dapat diaplikasikan pada berbagai jenis item tanpa memerlukan pengetahuan tentang fitur spesifik dari item tersebut.
- Kemampuan Menangkap Preferensi Kompleks:
Collaborative Filtering dapat menangkap pola preferensi kompleks yang mungkin tidak terlihat melalui analisis fitur konten, dengan mengandalkan kesamaan perilaku di antara pengguna.
- Rekomendasi Berbasis Komunitas:
Metode ini dapat merekomendasikan item yang mungkin tidak akan ditemukan oleh pengguna sendiri, karena didasarkan pada preferensi pengguna lain yang serupa. Ini membantu dalam mengeksplorasi item-item baru dan tidak terbatas pada apa yang sudah diketahui pengguna.

Kekurangan Collaborative Filtering
- Masalah Cold Start:
Sulit memberikan rekomendasi kepada pengguna baru (tanpa riwayat interaksi) atau untuk item baru (tanpa rating atau ulasan dari pengguna).
- Masalah Sparsity:
Dalam dataset besar, hanya sedikit pengguna yang mungkin memberi rating pada item-item yang ada, menyebabkan data menjadi sparse dan mengurangi efektivitas rekomendasi.
- Skalabilitas:
Menghitung kesamaan antara pengguna atau item bisa menjadi sangat mahal secara komputasi, terutama jika jumlah pengguna atau item sangat besar.

***
## Evaluation
Pada hasil Evaluasi Content Based Filtering merekomendasikan dengan contoh buku JOSHUA, hasil dari **Top-5** dari sistem berhasil merekomendasikan item buku.
Dari  hasil Rekomendasi, dapat diketahui bahwa 5 item yang direkomendasikan, 3 item memiliki Author yang sama yaitu Joseph Girzone. Artinya, Precision sistem sebesar 3/5 yaitu 60%. Untuk rumuas sebagai berikut :

![image](https://github.com/user-attachments/assets/8440cab1-d4fc-45c8-820e-359ae3c83651)


Sedangkan hasil Evaluasi Collaborative Filtering. Metrik kinerja model diukur dengan RMSE (Root Mean Squared Error).
- RMSE adalah metode pengukuran dengan mengukur perbedaan nilai dari prediksi sebuah model sebagai estimasi atas nilai yang diobservasi. Root Mean Square Error adalah hasil dari akar kuadrat Mean Square Error. Keakuratan metode estimasi kesalahan pengukuran ditandai dengan adanya nilai RMSE yang kecil. Metode estimasi yang mempunyai Root Mean Square Error (RMSE) lebih kecil dikatakan lebih akurat daripada metode estimasi yang mempunyai Root Mean Square Error (RMSE) lebih besar

Kelebihan dan kekurang matriks ini adalah :
- kelebihan : menghukum kesalahan besar lebih sehingga bisa lebih tepat dalam beberapa kasus.
- Kekurangan : memberikan bobot yang relatif tinggi untuk kesalahan besar. Ini berarti RMSE harus lebih berguna ketika kesalahan besar sangat tidak diinginkan

Rumus :

![image](https://github.com/user-attachments/assets/ecf90f36-0813-494d-86a5-b3542e9496fd)


Keterangan :
- At = Nilai data Aktual
- FT = Nilai hasil peramalan
- N = Banyak data
- ∑ = Summation (Jumlahkan keseluruhan  nilai)


Interpretasi Hasil Evaluasi
- Training Set
Pada akhir epochs ke 100, loss training adalah 0.3005 dengan RMSE 0.1691. Ini menandakan bahwa mode mampu belajar dari pola data training dengan baik, menghasilkan kesalahan prediksi yang rendah pada data yang telah dilihat
- Validation Set
Pada epoch yang sama, loss validation adalah 0.6856 dengan RMSE 0.3914. Nilai loss dan RMSE yang lebih tinggi dibandingkan dengan data training menunjukkan bahwa model tidak dapat generalisasi dengan baik pada data yang tidak terlihat sebelumnya.

Overfitting:
Hasil ini menunjukkan adanya overfitting, di mana model performa baik pada data training namun buruk pada data validation. Ini terlihat dari perbedaan signifikan antara loss dan RMSE pada data training dan validation. Overfitting terjadi karena model terlalu fit pada data training atau kurangnya data latih.

![image](https://github.com/user-attachments/assets/6a6073fe-67ca-460b-8743-c7dda6b377e6)


**Kesimpulan**

Rendahnya Minat Baca di Indonesia:
- Evaluasi: Content-Based Filtering dapat membantu dengan memberikan rekomendasi yang lebih relevan berdasarkan minat pengguna. Namun, untuk benar-benar mengatasi rendahnya minat baca secara menyeluruh, perlu juga adanya kolaborasi upaya lain seperti promosi budaya baca.

Kurangnya Akses dan Keterkaitan terhadap Buku yang Relevan:
- Evaluasi: Sistem ini berhasil dalam memperbaiki akses ke buku yang relevan dengan memberikan rekomendasi berdasarkan kesamaan fitur. Meskipun demikian, akses yang lebih luas dan distribusi buku juga penting untuk menyelesaikan masalah ini secara komprehensif.

Pemanfaatan Teknologi yang Kurang Optimal dalam Literasi:
- Evaluasi: Dengan menggunakan Content-Based Filtering, teknologi rekomendasi buku menjadi lebih efisien dan relevan.

Secara keseluruhan, Content-Based Filtering telah memecahkan sebagian besar permasalahan yang diidentifikasi dengan memberikan rekomendasi yang lebih personal dan relevan. Namun, beberapa masalah lebih kompleks dan memerlukan pendekatan tambahan serta upaya lain di luar sistem rekomendasi untuk penyelesaian yang lebih menyeluruh.
***
