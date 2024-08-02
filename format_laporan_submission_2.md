# Laporan Proyek Machine Learning - Kevin Chrsitian Sepoetro 

## Project Overview

Di era zaman sekarang yang semakin berkembang, banyak bidang bisnis yang menggunakan Machine Learning untuk meningkatkan bisnis mereka. Misalnya dengan sistem rekomendasi, mereka akan mendapatkan banyak keuntungan dari pembelian barang yang direkomendasikan atau bahkan meningkatkan insight toko. Hal ini juga dapat diterapkan di toko perpustakaan atau pada toko buku online agar user dapat rekomendasi buku yang tepat dan sesuai selera. Sistem rekomendasi buku juga berperan untuk meningkatkan literasi baca pada masyarakat Indoensia.

Menurut Jurnal yang ditulis oleh Moh. Irfan, Andharini Dwi C, Fika Hastarita R. buku merupakan informasi segala kebutuhan yang diperlukan, dimulai dari iptek, seni budaya, ekonomi, politik, sosial dan pertahanan keamanan dan lain-lain. Upaya membaca buku membuka wawasan dunia intelek sehingga dapat mengubah masa depan serta mencerdaskan akal, pikiran dan iman. Dengan membaca buku, selain pengetahuan akan semakin bertambah, pribadi akan semakin kaya, yang kesemuannya jelas akan menurunkan efek negatif terhadap anak-anak, yakni kenakalan. Sedangkan anak yang tidak terbina minat bacanya sejak dini akanmenghadapi peluang yang semakin kecil untuk mengembangkan pengetahuan setinggi-tingginya. Namun berdasarkan laporan Bank Dunia, Indonesia merupakan negara yang memiliki minat baca sangat rendah. Hal tersebut sungguh disayangkan, mengingat sebagai negara besar, Indonesia memiliki potensi besar untuk menjadi negara yang unggul.
  
  Format Referensi: [Sistem Rekomendasi Buku Online Dengan Metode Collaborative Filtering](https://ejournal.akprind.ac.id/index.php/technoscientia/article/view/612) 

Dari jurnal tersebut, dapat diketahui bahwa rendahnya minat baca di Indonesia, yang dapat menghambat kemajuan perkembangan bangsa. Untuk mengatasi masalah ini, salah satu solusi yang potensial adalah pengembangan dan implementasi sistem rekomendasi buku.  Sistem rekomendasi buku bukan hanya alat komersial untuk meningkatkan penjualan, tetapi juga instrumen penting dalam misi sosial untuk meningkatkan literasi dan pengetahuan di masyarakat Indonesia.

## Business Understanding

### Problem Statements

Menjelaskan pernyataan masalah:
- Rendahnya minat baca di Indoenesia yang tercemin dari kurangnya jumlah bku yang dibaca masyarakat, menghambat perkembangan intektul
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
  




**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menyajikan dua solusi rekomendasi dengan algoritma yang berbeda.
- Menjelaskan kelebihan dan kekurangan dari solusi/pendekatan yang dipilih.

## Evaluation
Pada bagian ini Anda perlu menyebutkan metrik evaluasi yang digunakan. Kemudian, jelaskan hasil proyek berdasarkan metrik evaluasi tersebut.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.
