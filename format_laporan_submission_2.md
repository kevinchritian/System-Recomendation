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
Unutk mengetahui informasi seperti tentang struktur DataFrame, termasuk jumlah total baris dan kolom, tipe data dari setiap kolom, dan serta jumlah nilai non-null menggunakan padas dengan perintah book.info()
![image](https://github.com/user-attachments/assets/485801a2-d383-421f-90a4-423babe57464)

dapat dilihat bahwa type semua feature adalah object dan terdiri dari 271.360 baris serta tidak ada yang kosong (non-null)

-


## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling
Tahapan ini membahas mengenai model sisten rekomendasi yang Anda buat untuk menyelesaikan permasalahan. Sajikan top-N recommendation sebagai output.

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
