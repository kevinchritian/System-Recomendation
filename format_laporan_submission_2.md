# Laporan Proyek Machine Learning - Kevin Chrsitian Sepoetro 

## Project Overview

Di era zaman sekarang yang semakin berkembang, banyak bidang bisnis yang menggunakan Machine Learning untuk meningkatkan bisnis mereka. Misalnya dengan sistem rekomendasi, mereka akan mendapatkan banyak keuntungan dari pembelian barang yang direkomendasikan atau bahkan meningkatkan insight toko. Hal ini juga dapat diterapkan di toko perpustakaan atau pada toko buku online agar user dapat rekomendasi buku yang tepat dan sesuai selera. Sistem rekomendasi buku juga berperan untuk meningkatkan literasi baca pada masyarakat Indoensia.

Menurut Jurnal yang ditulis oleh Moh. Irfan, Andharini Dwi C, Fika Hastarita R. buku merupakan informasi segala kebutuhan yang diperlukan, dimulai dari iptek, seni budaya, ekonomi, politik, sosial dan pertahanan keamanan dan lain-lain. Upaya membaca buku membuka wawasan dunia intelek sehingga dapat mengubah masa depan serta mencerdaskan akal, pikiran dan iman. Dengan membaca buku, selain pengetahuan akan semakin bertambah, pribadi akan semakin kaya, yang kesemuannya jelas akan menurunkan efek negatif terhadap anak-anak, yakni kenakalan. Sedangkan anak yang tidak terbina minat bacanya sejak dini akanmenghadapi peluang yang semakin kecil untuk mengembangkan pengetahuan setinggi-tingginya. Namun berdasarkan laporan Bank Dunia, Indonesia merupakan negara yang memiliki minat baca sangat rendah. Hal tersebut sungguh disayangkan, mengingat sebagai negara besar, Indonesia memiliki potensi besar untuk menjadi negara yang unggul.
  
  Format Referensi: [Sistem Rekomendasi Buku Online Dengan Metode Collaborative Filtering](https://ejournal.akprind.ac.id/index.php/technoscientia/article/view/612) 

Dari jurnal tersebut, dapat diketahui bahwa rendahnya minat baca di Indonesia, yang dapat menghambat kemajuan perkembangan bangsa. Untuk mengatasi masalah ini, salah satu solusi yang potensial adalah pengembangan dan implementasi sistem rekomendasi buku.  Sistem rekomendasi buku bukan hanya alat komersial untuk meningkatkan penjualan, tetapi juga instrumen penting dalam misi sosial untuk meningkatkan literasi dan pengetahuan di masyarakat Indonesia.

## Business Understanding

### Problem Statements

Menjelaskan pernyataan masalah:
- Rendahnya minat baca di Indoenesia yang tercemin dari kurangnya jumlah buku yang dibaca masyarakat, menghambat perkembangan intektul
- Kurangnya akses dan keterkaitan terhadap buku yang relevan, bisa membuat masyarakat sulit menemukan bahan bacaan yang sesuai minat.
- Pemanfaaran teknologi yang kurang optimal dalam mengatasi litrasi, dimana sistem rekomendasi buku yang ada belum maksimal dalam memberikan rekomendasi yang personal dan relevan

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
- Book.csv memiliki 271.360 data unik berdasarkan ISBN
- Ratings.csv memiliki 105.283 data unik berdasarkan User-ID
- Users.csv memiliki 278.858 data unik berdasarkan User-ID

![image](https://github.com/user-attachments/assets/9dc4291b-93d3-44d6-94f3-3e632035e53e)

**Univariate Exploratory Data Analysis**
- Book
  
Untuk mengetahui informasi Book.csv seperti tentang struktur DataFrame, termasuk jumlah total baris dan kolom, tipe data dari setiap kolom, dan serta jumlah nilai non-null menggunakan pandas dengan perintah book.info()

![image](https://github.com/user-attachments/assets/485801a2-d383-421f-90a4-423babe57464)

dapat dilihat bahwa type semua feature adalah object dan terdiri dari 271.360 baris serta tidak ada yang kosong (non-null). Lalu untuk mengetahui apakah ada nilai yang NaN atau hilang dapat menggunakan book.sinull().sum()

![image](https://github.com/user-attachments/assets/6cf6f0bf-a3ac-4a86-a45a-8ee1a13e6e5e)


Dapat dilihat ada sedikit sekali yang missing value. Selanjutnya menghitung jumlah data unik pada setiap feature.

![image](https://github.com/user-attachments/assets/09e212b4-aea8-4052-9dcf-ecdb67ea0670)


Dapat dilihat bahwa total ISBN memiliki jumlah data unik 271.360, jumlah unik data book berdasarkan Book-Title adalah 242.135, Jumlah unik data book berdasarkan Author adalah 102.023, dan jumlah unik book berdasarkan publisher adalah 16.808.


- Rating
Untuk mengetahui informasi Ratings.csv seperti tentang struktur DataFrame, termasuk jumlah total baris dan kolom, tipe data dari setiap kolom, dan serta jumlah nilai non-null menggunakan pandas dengan perintah rating.info()

![image](https://github.com/user-attachments/assets/873c53bb-6914-44c8-95c3-546d919a85d6)

dapat dilihat bahwa type feature User ID adalah int64, ISBN adalah object, Book-Rating int64 dan semua terdiri dari 1.149.780 baris serta tidak ada yang kosong (non-null). Lalu untuk mengetahui apakah ada nilai yang NaN atau hilang dapat menggunakan book.sinull().sum()

![image](https://github.com/user-attachments/assets/4842d7cd-7a26-4d96-be9c-8ebd97aa30c4)


Ternyata tidak ada yang missing value. Selanjutnya melihat jumlah nilai unik rating berdasarkan User-ID dan ISBN

![image](https://github.com/user-attachments/assets/a3c61c24-6154-4efb-83d4-f56b70ef22a3)


Lalu untuk melihat deskripsi rating dapat menggunakan rating.describe()

![image](https://github.com/user-attachments/assets/cf8953fd-b841-47f7-b0cf-727bec0aea7f)


Dapat diketahui bahwa max rating adalah 10 dan minimal rating adalah 0.


- User
Berikut adalah jumlah data unik pada User-ID.

![image](https://github.com/user-attachments/assets/264dbd96-12e9-4687-9d05-c17c2b4c3eec)

Dapat dilihat bahwa terdapat 278.858 data unik pada Users.csv berdasarkan User-ID. Lalu selanjutnya apakah ada missing value dengan perintah user.isnull().sum().

![image](https://github.com/user-attachments/assets/c0045063-046a-464f-81e5-88f8a369f77f)


Teranyata tidak ada yang missing value.


**Data Preprocesing**
Pada tahap ini, melihat jumlah Rating pada buku. Caranya dengan menggabungkan rating dengan book berdasarkan ISBN. berikut code nya :

![image](https://github.com/user-attachments/assets/4b3ec40b-df45-404e-bc1e-03107dd9332a)


Outputnya : 

![image](https://github.com/user-attachments/assets/333d402c-665f-4389-94fb-2b79282b8383)

Terdapat 1.149.780 row dan 10 kolom. Lalu cek apakah ada missing value dengan perintah buku.isnull().sum(). 

![image](https://github.com/user-attachments/assets/dbea8d57-1576-427c-974e-b07d5ccecf0e)

ternyata ada banyak missing value. selanjutnya hitung jumlah rating berdasarkan ISBN.

![image](https://github.com/user-attachments/assets/d8e5dab1-4d9e-4c6b-b630-719fd049588f)


Selanjutnya menggabungkan Data dengan Fitur Nama Buku sebelum dilakukan Data Prepration.

![image](https://github.com/user-attachments/assets/87268adc-8d71-47b9-81b1-38272d10d6fb)

Dapat dilihat jumlah data sekarang adalah 1.149.780. dan terdiri dari 6 columns



## Data Preparation
Berikut adalah tahapan Data Preparation :
- **Mengatasi Missing Value**
Untuk mengatasi missing value dengan perintah .isnull.sum().
  
![image](https://github.com/user-attachments/assets/e5b427b6-f196-4a60-a4d1-daf656f312c7)

Dapat dilihat terdapat banyak sekali missing Value. Hal ini bisa mengganggu model dalam kinerja model. Oelh karena itu dihapus yang missing Value menggunakan .dropna().

![image](https://github.com/user-attachments/assets/7900d9df-0d2d-434d-9389-99c16b7e9135)

Dari hasil .dropna() dapat dilihat bahwa data masih banyak yaitu 1.031.132. Selanjutnya hapus data yang memiliki Duplikat data, hal ini bisa mempengaruhi hasil Rekomendasi jika tidak dihapus misalnya seperti di rekomendasi muncul data yang direkomendasikan sama persis seperti ISBN dan judul buku. Untuk perintah menghapus data dengan .drop_duplicates() berdasarkan ISBN.

![image](https://github.com/user-attachments/assets/df32ee4c-9a02-4865-8f5d-a6f590d7f1e8)


Dapat dilihat setelah di drop duplikat data menjadi 270.147. Cukup banyak data yang Terduplikat. Selanjutnya pada kasus ini menggunakan Data 40.000. Alasan menjadi 40.000 data karena pada Tools Colab RAM untuk memproses Data sebanyak 270.147 tidak men support (dalam melakukan Cosine Similarity). Sehingga pada kasus ini menggunakan 40.000 data. 

![image](https://github.com/user-attachments/assets/8741a128-ef5f-4462-b6d9-83df17f00b5c)


Selanjutnya sebelum membuat Model perlu melakukan konversi menjadi list dengan menggunakan perintah .tolist().

![image](https://github.com/user-attachments/assets/767630b4-44fe-40dd-b5fb-21ae17835a79)


Tahap berikutnya, membuat dictionary untuk menentukan pasangan key-value pada data ISBN_id, book_name, dan Author yang telah disiapkan sebelumnya.

![image](https://github.com/user-attachments/assets/53387da4-3030-4990-9fb9-6c64ba39efa6)



## Modeling
Pada Modeling Data terdapat dua Pendekatan yaitu Content Based dan Colaborative Filtering.
- **Content Based Filtering**
Sebelumnya, mari cek lagi data yang  dimiliki dan assign dataframe dari tahap sebelumnya ke dalam variabel data, sebagai berikut:

![image](https://github.com/user-attachments/assets/a521b20c-aab9-40b3-83f8-696d04a04b9b)


**TF IDF Vectorizer**
Pada tahp ini mengubah teks menjadi numerik menggunakan TF IDF Vectorizer pada Author. Untuk perintah mengubah ke Tf IDF menggunakan library yang disediakan Sklearn yaitu tfidfvectorizer().

![image](https://github.com/user-attachments/assets/86096ffd-eaed-4868-8544-475c44c9b928)


Selanjutnya elakukan melakukan fit dan transform ke dalam matrix dengan fit.transform() dan hasil nya sebagai berikut :

![image](https://github.com/user-attachments/assets/e5c08cb9-a877-4842-9250-e13299dba0b0)


terdapat 40.000 jumlah ukuran data dan  13.842 jumlah Author dalam matrix. Selanjutnya untuk menghasilkan vektor tf-idf dalam bentuk matriks, menggunakan fungsi todense().

![image](https://github.com/user-attachments/assets/5420bce2-de4f-4895-9116-7a333e12f1cc)


Selanjutnya, melihat matriks tf-idf untuk beberapa buku (book_name) dan Author. 

![image](https://github.com/user-attachments/assets/048782c1-2aaf-4d7b-8e30-6761a16e9e32)


![image](https://github.com/user-attachments/assets/f0ed8f94-2bc8-4095-97be-1b86d9977e79)


![image](https://github.com/user-attachments/assets/0ba66332-90dc-4e35-9841-70e014b5176f)



Pada Ouput Matrix diatas hanya menampilkan beberapa saja, tidak bisa semua outputnya karena data terlalu besar. Dari matriks kolerasi antara book name dan author dapat dilihat bahwa jika 0 maka tidak ada keterkaitan dan jika 1 ada keterkaitan antara Author dan book_name. 

Kemudian menghitung derajat kesamaan (similarity degree) antar buku dengan teknik cosine similarity. Di sini, menggunakan fungsi cosine_similarity dari library sklearn. 


![image](https://github.com/user-attachments/assets/54cf1871-9296-40d7-9168-f3553e711e09)


Pada tahapan ini, menghitung cosine similarity dataframe tfidf_matrix yang diperoleh pada tahapan sebelumnya. Dengan satu baris kode untuk memanggil fungsi cosine similarity dari library sklearn, telah berhasil menghitung kesamaan (similarity) antar buku. 

Selanjutnya,  melihat matriks kesamaan setiap buku dengan menampilkan nama buku dalam 5 sampel kolom (axis = 1) dan 10 sampel baris (axis=0).

![image](https://github.com/user-attachments/assets/1f65bbb1-7a54-4b7f-b197-8b54a0eaa8f6)


Dengan cosine similarity pada output diatas, berhasil mengidentifikasi kesamaan antara satu buku dengan buku lainnya. Shape (40000, 40000) merupakan ukuran matriks similarity data. Berdasarkan data yang ada, matriks di atas sebenarnya berukuran 40000 restoran x 40000 nama buku. Akan tetapi tentu ouputnya tidak bisa menampilkan semuanya. Oleh karena itu, hanya memilih 10 buku pada baris vertikal dan 5 buku.

Sama seperti antar Auhtor dengan Buku_name jika atau mendaekati 1 maka memiliki similarity atau kesamaan, jika 0 sebaliknya.

Selanjutnya untuk mendapatkan rekomendasi Buku berdasarkan Author maka ada beberapa yang perlu diperhatikan. Dimana sistem ini user melihat lihat buku misalnya buku "JOSHUA" karya Joshep Girzone. Kemudian user ingin berencana membaca buku lain, Sistem akan merekomendasikan buku seperti Joshua In Holy Land. Rekomendasi kedua buku ini berdasarkan kesamaan yang dihitung dengan cosine similarity pada tahap sebelumnya. 

Dalam code membuat fungsi book_recommendations dengan beberapa parameter sebagai berikut:
- Nama_buku : Nama buku 
- Similarity_data : Dataframe mengenai similarity yang telah di definisikan sebelumnya.
- Items : Nama buku dan Author yang digunakan untuk mendefinisikan kemiripan.
- k : Banyak rekomendasi yang ingin diberikan

![image](https://github.com/user-attachments/assets/a5e9b081-329f-4d61-9e4c-344abef54425)


argpartition, adalah mengambil sejumlah nilai k tertinggi dari similarity data. Kemudian, mengambil data dari bobot (tingkat kesamaan) tertinggi ke terendah. Data ini dimasukkan ke dalam variabel closest. Lalu menghapus nama_buku yang yang dicari agar tidak muncul dalam daftar rekomendasi. Dalam kasus ini, nanti kita akan mencari resto yang mirip dengan Joshua, sehingga kita perlu drop nama_buku Joshua agar tidak muncul dalam daftar rekomendasi yang diberikan nanti.  

Selanjutnya untuk test panggil dengan code seperti berikut :

![image](https://github.com/user-attachments/assets/4f21671e-20f3-402e-b078-ceb1eb32008c)


Pada Sistem rekomendasi berharap bahwa nanti yang muncul sama Author nya dengan buku yang dicari. Misalnya pada kasus ini Author adalah Joseph Girzone maka Author nanti rekomendasi data adalah Joseph Girzone.

Lalu untuk memunculkan rekomnedasi dengan panggil fungsi book_recommendations.

![image](https://github.com/user-attachments/assets/2991c0e0-ca7f-409f-a9d1-335c33d7bd88)


Dan dapat dilihat bahwa sistem berhasil merekomendasikan Authoryang sama dengan Author Joshua.



- **Colaborative Filtering**
Untuk melakukan pendekatan Collaborative Filtering import dahulu library yang dibutuhkan.

![image](https://github.com/user-attachments/assets/245febeb-9883-477e-bd3f-2af149cf4dd9)


kemudian definiskan variable df sebagai rating (Ratings.csv). Lalu kenapa hanya 60.000 data, Karena data Ratings.csv terlalu banyak jutaan data. Sehingga nanti saat proses train akan memakan waktu sangat lama. oleh karena itu pada kasus ini menggunakan data 60.000.

![image](https://github.com/user-attachments/assets/cb300fd7-2c3f-415b-b045-a5e2aae010b1)


Tahapan selanjutnya melakukan encode / mengubah ke dictionary pada UserID dan pada ISBN ke dalam index integer.

![image](https://github.com/user-attachments/assets/a6fc072e-e85f-407d-8544-c1e94da901af)


![image](https://github.com/user-attachments/assets/2c091e43-70d8-4c65-aa48-d825a70fca27)


![image](https://github.com/user-attachments/assets/81af72c3-a937-4860-887f-25cc6e701273)


Selanjutnya melakukan mapping ke dataframe User-ID dan ISBN


![image](https://github.com/user-attachments/assets/b9c51a0d-f281-4309-86ca-d3e0f9a9fe84)


Selanjutnya mencetak jumlah user, buku, max rating, minimal rating dan mengubah rating ke dalam float.

![image](https://github.com/user-attachments/assets/dcb276e3-3a51-4eb6-9138-94f7f2bb0ec0)


Langkah selanjutnya membagi data train dan test. Sebelum itu melakukan random data agar distribusi nya acak.


![image](https://github.com/user-attachments/assets/77874139-b0ca-4b0a-adc2-e643844c6a11)


Setelah itu melakukan pembagian train dan test dimana data train adalah 90% dan test 10%.


![image](https://github.com/user-attachments/assets/c8618962-7204-44ce-80ea-f6d584275f6c)


Pada code diatas perlu memetakan (mapping) data user dan book menjadi satu value terlebih dahulu. Lalu, rating dalam skala 0 sampai 1 agar mudah dalam melakukan proses training. 

Pada tahap selanjutnya, model menghitung skor kecocokan antara pengguna dan buku dengan teknik embedding. Pertama, melakukan proses embedding terhadap data user dan buku. Selanjutnya, lakukan operasi perkalian dot product antara embedding user dan buku. Selain itu, dapat menambahkan bias untuk setiap user dan buku. Skor kecocokan ditetapkan dalam skala [0,1] dengan fungsi aktivasi sigmoid. Dimana jika 1 maka sangat cocok jika 0 tidak cocok sama sekali.

Lalu membuat class RecommenderNet dengan keras Model class. 

![image](https://github.com/user-attachments/assets/f83909d2-102e-4d00-bf35-16173ad7a210)


Selanjutnya melakukan proses compile data dengan parameter :
 - loss function : Binary Crossentropy  
 - Optimizer : Adam (Adaptive Moment Estimation)
 - Evaluation : root mean squared error (RMSE)
 - Epochs : 100

![image](https://github.com/user-attachments/assets/2bba99b1-b0dc-4b53-a7eb-df8bd57c7653)


![image](https://github.com/user-attachments/assets/8f799b4d-462e-44c8-8977-aa5d5118b421)


Output :
![image](https://github.com/user-attachments/assets/15bb1578-f7b5-4c90-ba91-c29acb94f36a)

Pada grafik diatas dapat dilihat bahwa grafik overfitting, Dimana overfitting saat train bagus akurasi tetapi saat akurasi validasi jelek.

Untuk membuat rekomendasi buku, langkah pertama adalah mengambil sampel pengguna secara acak dan menentukan variabel book_not_visited, yang berisi daftar buku yang belum pernah dilihat oleh pengguna. Daftar book_not_visited ini nantinya akan menjadi kumpulan buku yang dapat direkomendasikan.

Pengguna sebelumnya telah memberikan penilaian (rating) pada beberapa buku yang telah mereka baca. Rating ini akan digunakan untuk membuat rekomendasi buku yang mungkin akan disukai oleh pengguna tersebut. Karena rekomendasi yang kita buat adalah untuk buku-buku yang belum pernah dikunjungi oleh pengguna, kita perlu menyusun variabel book_not_visited untuk menyimpan daftar buku yang bisa direkomendasikan.

Variabel book_not_visited dapat diperoleh dengan menggunakan operator bitwise (~) pada variabel book_visited_by_user. Operator ini akan menghasilkan daftar buku yang tidak ada dalam daftar book_visited_by_user, yang artinya belum pernah dilihat oleh pengguna dan layak untuk direkomendasikan.


![image](https://github.com/user-attachments/assets/a9c81911-4c26-4863-8689-7bb3c6dd25a9)


Selanjutnya, untuk memperoleh rekomendasi buku, gunakan fungsi model.predict() dari library Keras.

![image](https://github.com/user-attachments/assets/b1d6a65f-805b-4bed-bd2c-cfa433631c90)


Ouput :


![image](https://github.com/user-attachments/assets/3e64ff42-56c4-496d-971d-29cc642e06a1)


dapat dilihat bahwa Sistem Rekomendasi bisa memberikan Rekomendasi tapi tidak akurat. Dimana Rekomendasi buku harusnya sama dengan pengarang atau Author tapi disini merekomendasikan yang lain. Tidak ada kesamaan. Hal ini disebabkan Overfitting.

**Kelibahan dan Kelemahan Content Based Filtering dan Collaborative Filtering**

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

## Evaluation
Pada hasil Evaluasi Content Based Filtering merekomendasikan buku JOSHUA 

![image](https://github.com/user-attachments/assets/86bb17e3-93dc-419f-b7a9-8ad7352e4152)


Hasil dari Top-N 5 dari sistem merekomendasikan sebagai berikut :

![image](https://github.com/user-attachments/assets/c6ff1179-b163-4a46-be19-698cc4b62203)


Dari  hasil Rekomendasi, dapat diketahui bahwa 5 item yang direkomendasikan, 3 item memiliki Author yang sma yaitu Joseph Girzone. Artinya, Precision sistem sebesar 3/5 yaitu 60%. Untuk rumuas sebagai berikut :

![image](https://github.com/user-attachments/assets/8440cab1-d4fc-45c8-820e-359ae3c83651)


Untuk hasil Evaluasi Collaborative Filtering. Metrik kinerja model diukur dengan RMSE (Root Mean Squared Error.
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

Pada hasil hasil history RMSE train dan val dapat dilihat bahwa overfitting dan tidak memiliki kesamaaan dalam merekomendasi antar data.

![image](https://github.com/user-attachments/assets/6a6073fe-67ca-460b-8743-c7dda6b377e6)


Kenapa hal ini bisa terjadi ? 
- kemungkinan pertama bahwa data varian kurang banyak. karena data mungkin terlalu kecil pada kasus ini untuk Deep Learning
- Data pelatihan berisi banyak informasi yang tidak relevan.
- Model sangat kompleks sehingga model mempelajari data tidak berarti dalam data pelatihan.

Cara mengatasi dengan memberikan Regularisasi L1 dan L2, menambah data saat melakukan train.


**Kesimpulan**

Rendahnya Minat Baca di Indonesia:
- Evaluasi: Content-Based Filtering dapat membantu dengan memberikan rekomendasi yang lebih relevan berdasarkan minat pengguna. Namun, untuk benar-benar mengatasi rendahnya minat baca secara menyeluruh, perlu juga adanya kolaborasi upaya lain seperti promosi budaya baca.

Kurangnya Akses dan Keterkaitan terhadap Buku yang Relevan:
- Evaluasi: Sistem ini berhasil dalam memperbaiki akses ke buku yang relevan dengan memberikan rekomendasi berdasarkan kesamaan fitur. Meskipun demikian, akses yang lebih luas dan distribusi buku juga penting untuk menyelesaikan masalah ini secara komprehensif.

Pemanfaatan Teknologi yang Kurang Optimal dalam Literasi:
- Evaluasi: Dengan menggunakan Content-Based Filtering, teknologi rekomendasi buku menjadi lebih efisien dan relevan.

Secara keseluruhan, Content-Based Filtering telah memecahkan sebagian besar permasalahan yang diidentifikasi dengan memberikan rekomendasi yang lebih personal dan relevan. Namun, beberapa masalah lebih kompleks dan memerlukan pendekatan tambahan serta upaya lain di luar sistem rekomendasi untuk penyelesaian yang lebih menyeluruh.






