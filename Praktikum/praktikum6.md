# :ledger: Praktikum Model, Controller dan Request-Response Handler
Praktikum ini dilakukan pada 11 Oktober 2023. Pada repository ini berisikan source code dan screenshot penerapan dari praktikum modul 6 mengenai Model, Controller dan Request-Response Handler

## Tujuan
Setelah mengikuti praktikum ini, mahasiswa diharapkan dapat:
1. Mengimplementasikan model
2. Mengimplementasikan controller
3. Mengimplementasikan request handler
4. Mengimplementasikan response handler

## Dasar Teori
### Model
<p align= "justify">
Model merupakan bagian yang bertugas untuk menyiapkan, mengatur, memanipulasi, dan mengorganisasikan data yang ada di database. Model merepresentasikan kolom apa saja yang ada pada databas, termasuk relasi dan primary key dapat didefinisikan di dalam model. Dengan menggunakan perintah Artisan, pembuatan model pada Laravel dapat dilakukan dengan satu perintah menggunakan
</p>

`php artisan make:model nama_model`

Namun karena perintah Artisan yang terbatas pada Lumen, pembuatan model harus dilakukan secara manual.

### Controller
<p align= "justify">
Controller merupakan bagian yang menjadi tempat berkumpulnya logika pemrograman yang digunakan untuk memisahkan organisasi data pada database. Dalam beberapa kasus, controller menjadi penghubung antara model dan view pada arsitektur MVC
</p>

### Request Handler
<p align= "justify">
Request handler adalah fungsi yang digunakan untuk berinteraksi dengan request yang datang. Request handler dapat digunakan untuk melihat apa saja yang dikirimkan oleh user seperti parameter, query, dan body.
</p>

### Response Handler
<p align= "justify">
Response handler adalah fungsi yang digunakan untuk membentuk output yang diharapkan kepada user dan beberapa properti selain data seperti status code dan header.
</p>

## Langkah Percobaan
### Model
1. Pastikan terdapat tabel users yang dibuat menggunakan migration pada bab sebelumnya. Berikut informasi kolom yang harus ada
    ![Screenshot ..](../Screenshot/praktikum6/61.png)

2. Bersihkan isi User.php yang ada sebelumnya dan isi dengan baris kode berikut
    ![Screenshot ..](../Screenshot/praktikum6/62.png)

### Controller
1. Buatlah salinan `ExampleController.php` pada folder `app/Http/Controllers` dengan nama `HomeController.php` dan buatlah fungsi `index()` yang berisi
    ![Screenshot ..](../Screenshot/praktikum6/63.png)

2. Ubah route `/` pada file `routes/web.php` menjadi seperti ini
    ![Screenshot ..](../Screenshot/praktikum6/64.png)

3. Jalankan aplikasi
    ![Screenshot ..](../Screenshot/praktikum6/65.png)

### Request Handler
1. Lakukan import library Request dengan menambahkan baris berikut di bagian atas file
    ![Screenshot ..](../Screenshot/praktikum6/66.png)

2. Ubah fungsi index menjadi
    ![Screenshot ..](../Screenshot/praktikum6/67.png)

3. Jalankan aplikasi
    ![Screenshot ..](../Screenshot/praktikum6/68.png)

### Response Handler
1. Lakukan import library Response dengan menambahkan baris berikut di bagian atas file
    ![Screenshot ..](../Screenshot/praktikum6/69.png)

2. Buatlah fungsi `hello()` yang berisi
    ![Screenshot ..](../Screenshot/praktikum6/610.png)

3. Tambahkan route `/hello` pada file `routes/web.php`
    ![Screenshot ..](../Screenshot/praktikum6/611.png)

4. Jalankan aplikasi pada route `/hello`
    ![Screenshot ..](../Screenshot/praktikum6/612.png)

### Penerapan
1. Lakukan import model User dengan menambahkan baris berikut di bagian atas file
    ![Screenshot ..](../Screenshot/praktikum6/613.png)

2. Tambahkan ketiga fungsi berikut di `HomeController.php`
    ![Screenshot ..](../Screenshot/praktikum6/614.png)

3. Tambahkan ketiga route pada file `routes/web.php` menggunakan group route
    ![Screenshot ..](../Screenshot/praktikum6/615.png)
    
4. Jalankan aplikasi pada route `/users/default` menggunakan Thunder Client / Postman
    ![Screenshot ..](../Screenshot/praktikum6/616.png)

5. Jalankan aplikasi pada route `/users/new` dengan mengisi body sebagai berikut
    ![Screenshot ..](../Screenshot/praktikum6/617.png)

6. Jalankan aplikasi pada route `/users/all`
    ![Screenshot ..](../Screenshot/praktikum6/618.png)