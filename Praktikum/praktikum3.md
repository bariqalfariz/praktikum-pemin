# :ledger: Praktikum Integrasi MongoDB dan Express
Praktikum ini dilakukan pada 20 September 2023. Pada repository ini berisikan source code dan screenshot penerapan dari praktikum modul 3 mengenai Integrasi MongoDB dan Express

## Dasar Teori
### Express
<p align= "justify">
Express.js adalah framework web app untuk Node.js yang ditulis dengan bahasa pemrograman JavaScript. Framework open source ini dibuat oleh TJ Holowaychuk pada tahun 2010 lalu. 

Express.js adalah framework back end. Artinya, ia bertanggung jawab untuk mengatur fungsionalitas website, seperti pengelolaan routing dan session permintaan HTTP, penanganan error, serta pertukaran data di server.
</p>

### Mongoose
<p align= "justify">
Mongoose adalah pustaka berbasis Node.js yang digunakan untuk pemodelan data pada MongoDB. Mongoose menyediakan feature diantaranya, model data application berbasis Schema. Dan juga termasuk built-in type casting, validation, query building, business logic hooks dan masih banyak lagi yang menjadi ke andalan mongoose.
</p>

### Async Await
<p align= "justify">
Async sendiri merupakan sebuah fungsi yang mengembalikan sebuah Promise. Await sendiri merupakan fungsi yang hanya berjalan di dalam Async. Await bertujuan untuk menunda jalannya Async hingga proses dari Await tersebut berhasil dieksekusi.
</p>

### Model
<p align= "justify">
Model merupakan bagian yang bertugas untuk menyiapkan, mengatur, memanipulasi, dan mengorganisasikan data yang ada di database.
</p>

### Controller
<p align= "justify">
Controller merupakan bagian yang menjadi tempat berkumpulnya logika pemrograman yang digunakan untuk memisahkan organisasi data pada database. Dalam beberapa kasus, controller menjadi penghubung antara model dan view pada arsitektur MVC
</p>

### Route
<p align= "justify">
Router mengatur pintu masuk yang berupa request pada aplikasi, mereka memilah dan mengolah request url untuk kemudian diproses sesuai dengan tujuan akhir url tersebut. Bisa jadi url tersebut berfungsi untuk mengambil data kemudian menampilkannya, menghapus data, menampilkan form, sampai mengolah session.
</p>

## Langkah Percobaan 
### Instalasi NodeJS
1. Setelah instalasi selesai jalankan command   `node -v`   untuk memeriksa apakah NodeJS sudah terinstall
![Screenshot node -v](../Screenshot/praktikum3/1.png)


### Inisiasi project Express dan pemasangan package
1. Buat folder dengan nama express-mongodb lalu masuk ke dalamnya

2. Melakukan generate file package.json dengan menggunakan command  `npm init -y`
![Screenshot npm init -y](../Screenshot/praktikum3/2.png)

3. Instalasi express, mongoose dan dotend dengan menggunakan command `npm i express mongoose dotenv`
![Screenshot npm i](../Screenshot/praktikum3/3.png)
    

### Koneksi Express ke MongoDB
1. Buat file **index.js** pada root folder dan masukkan kode :
![Screenshot buat file index.js](../Screenshot/praktikum3/4.png)

2. Pembuatan file **.env** dan masukkan baris berikut :
![Screenshot buat file .env](../Screenshot/praktikum3/6.png)

    Setelah itu ubah kode pada listening port menjadi seperti berikut dan dicoba jalankan kembali
![Screenshot ubah kode pada listening](../Screenshot/praktikum3/7.png)

3. Copy connection string yang terdapat pada compass atau atlas dan paste pada **.env** 
![Screenshot mongo uri](../Screenshot/praktikum3/8.png)

4. Tambahkan baris kode pada file **index.js**
![Screenshot tambahan kode pada index.js](../Screenshot/praktikum3/9.png)

### Pembuatan Routing
1. Pembuatan direktori routes di tingkat yang sama dengan index.js
2. Buat file book.route.js di dalamnya
3. Tambahkan bari kode untuk getAllBooks
![Screenshot fungsi getAllBooks](../Screenshot/praktikum3/11.png)

4. Lakukan hal yang sama untuk getOneBook, createBook, updateBook, dan deleteBook
![Screenshot crud book](../Screenshot/praktikum3/12.png)

5. Lakukan import book.route.js pada file index.js dan tambhkan baris kode berikut
![Screenshot import book.route.js](../Screenshot/praktikum3/13.png)

6. Uji coba salah satu endpoint dengan Postman
![Screenshot uji coba postman](../Screenshot/praktikum3/14.png)


### Pembuatan Controller
1. Melakukan pembuatan direktori controllers di tingkat yang sama dengan index.js
2. Buat file book.controller.js di dalamnya
3. Masukkan baris kode dari routes untuk fungsi getAllBooks
![Screenshot kode fungsi getAllBooks](../Screenshot/praktikum3/15.png)

4. Melakukan hal yang sama untuk getOneBook, createBook, updateBook, dan deleteBook
![Screenshot controller crud onebook](../Screenshot/praktikum3/16.png)

5. Melakukan import book.controller.js pada file book.route.js
6. Melakukan perubahan pada fungsi agar dapat memanggil fungsi dari book.controller.js
![Screenshot import book.controller.js](../Screenshot/praktikum3/17.png)

7. Melakukan pengujian kembali dan pastikan response tetap sama
![Screenshot perubahan fungsi book.controller.js](../Screenshot/praktikum3/18.png)


### Pembuatan Model
1. Melakukan pembuatan direktori models di tingkat yang sama dengan index.js
2. Membuat file book.model.js di dalamnya
3. Menambahkan baris kode seperti berikut
![Screenshot model](../Screenshot/praktikum3/19.png)


### Operasi CRUD
1. Hapus semua data pada collection books 
![Screenshot hapus data](../Screenshot/praktikum3/20.png)

2. Melakukan import book.model.js pada file book.controller.js
3. Melakukan perubahan pada fungsi createBook
![Screenshot import book.model.js](../Screenshot/praktikum3/21.png)

4. Membuat dua buah buku dengan data di bawah ini menggunakan Postman
![Screenshot menambah buku](../Screenshot/praktikum3/22.png)

    Menambahkan buku kedua 
![Screenshot menambah buku kedua](../Screenshot/praktikum3/23.png)

5. Melakukan perubahan pada fungsi getAllBooks
![Screenshot perubahan fungsi getAllBooks](../Screenshot/praktikum3/24.png)

6. Melakukan perubahan pada fungsi getOneBook
![Screenshot perubahan getOneBook](../Screenshot/praktikum3/25.png)

7. Menampilkan semua buku dengan Postman
![Screenshot menampilkan semua buku](../Screenshot/praktikum3/26.png)

8. Menampilkan buku Dilan 1990 dengan Postman
![Screenshot menampilkan buku Dilan 1990](../Screenshot/praktikum3/27.png)

9. Melakukan perubahan pada fungsi updateBook
![Screenshot perubahan fungsi updateBook](../Screenshot/praktikum3/28.png)

10. Mengubah judul buku Dilan 1991 menjadi `Nama Panggilan` dengan Postman
![Screenshot ubah nama panggilan](../Screenshot/praktikum3/29.png)

11. Melakukan perubahan pada fungsi deleteBook
![Screenshot ubah fungsi deleteBook](../Screenshot/praktikum3/30.png)

12. Menghapus buku Dilan 1990 dengan Postman
![Screenshot hapus buku dilan 1990](../Screenshot/praktikum3/31.png)



