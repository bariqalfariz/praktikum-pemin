# :ledger: Praktikum CRUD MongoDB
Praktikum ini dilakukan pada 13 September 2023. Pada repository ini berisikan source code dan screenshot penerapan dari praktikum modul 2.

## Dasar Teori
* ### MongoDB Compass 
    MongoDB Compass adalah tool berbasis Graphical User Interface (GUI) yang digunakan untuk berinteraksi dengan MongoDB yang terpasang secara on-premise dan MongoDB Atlas yang berbasis cloud. Tool ini dapat melakukan aktivitas dasar seperti CREATE, READ, UPDATE, dan DELETE (CRUD) tanpa berhadapan dengan baris perintah (command line).

- ### MongoDB Shell
    Walaupun dapat melakukan operasi seperti MongoDB Compass, interaksi yang dilakukan MongoDB Shell berbasis Command Line Interface (CLI) sehingga diperlukan baris perintah untuk melakukan aktivitas dasar. MongoDB Shell dapat diakses langsung dari MongoDB Compass atau menggunakan mongosh pada Command Prompt.

## Langkah Percobaan
- ### MongoDB Compass
    1. Melakukan koneksi ke MongoDB menggunakan connection string ``` mongodb://localhost:27017``` secara lokal. <br/>
    ![Screenshot connection MongoDB Compass](../Screenshot/praktikum2/1.png)

    1. Membuat Database bookstore dengan melakukan klik "Create Database"
    ![Screenshot create database](../Screenshot/praktikum2/2.png)

    1. Melakukan insert buku pertama dengan melakukan klik “Add Data”, pilih “Insert Document”, isi dengan data yang diinginkan dan klik “Insert”
    ![Screenshot Insert Document](../Screenshot/praktikum2/3.png)
          ![Screenshot Add Data](../Screenshot/praktikum2/4.png)

    1. Melakukan insert buku kedua dengan cara yang sama
    ![Screenshot Insert buku kedua](../Screenshot/praktikum2/5.png)

    1. Melakukan pencarian buku dengan author “Osamu Dazai” dengan mengisi filter yang diinginkan dan klik “Find”
    ![Screenshot Pencarian buku](../Screenshot/praktikum2/6.png)

    1. Melakukan perubahan summary pada buku “No Longer Human” menjadi “Buku yang bagus (<NAMA>,<NIM>) dengan melakukan klik “Edit Document” (berlambang pensil), mengisi nilai summary yang baru, dan melakukan klik “Update”
    ![Screenshot perubahan summary](../Screenshot/praktikum2/7.png)
    1. Melakukan penghapusan pada buku “I Am a Cat” dengan melakukan klik “Remove Document” (berlambang tong sampah) dan melakukan klik “Delete”
    ![Screenshot delete](../Screenshot/praktikum2/8.png)
    ![Screenshot delete](../Screenshot/praktikum2/9.png)

- ### MongoDB Shell
    1. Melakukan koneksi ke MongoDB Server dengan menjalankan command mongosh bagi yang menggunakan terminal build in OS sehingga tampilan terminal kalian akan menjadi seperti berikut
    ![Screenshot .. ](../Screenshot/praktikum2/10.png)

    2. Menjalankan beberapa command berikut: 
    ![Screenshot .. ](../Screenshot/praktikum2/11.png)
    
    **Penjelasan :** 

        show dbs : melihat isi database yang ada di server
        use <database_name> : berpindah ke database yang diinginkan
        show collection :  melihat collection yang ada pada database yang digunakan

    3. Melakukan insert buku “Overlord I” dengan menggunakan command ```db.books.insertOne(<data kalian>)``` , setelah insert buku berhasil maka MongoDB akan mengembalikan pesan sebagai berikut.
    ![Screenshot .. ](../Screenshot/praktikum2/12.png)

    4. Melakukan insert buku “The Setting Sun” dan “Hujan” dengan insert many dengan menggunakan command ```db.books.insertMany(<data kalian>)```, dan akan mengembalikan pesan sebagai berikut.
    ![Screenshot .. ](../Screenshot/praktikum2/13.png)

    5. Lakukan pencarian buku dengan menggunakan ```command db.books.find()``` untuk melakukan pencarian semua buku.
    ![Screenshot .. ](../Screenshot/praktikum2/14.png)

    6. Tampilkan seluruh buku dengan author “Osamu Dazai” dengan mengisi argument pada find() dengan menggunakan command ```db.books.find({<filter yang ingin diisi>})```
    ![Screenshot .. ](../Screenshot/praktikum2/15.png)

    7. Melakukan perubahan summary pada buku “Hujan” menjadi “Buku yang bagus (<NAMA>,<NIM>) dengan mengunakan command ```db.books.updateOne({<filter>}, {$set: {<data yang akan di update>}})``` sehingga output yang dihasilkan oleh MongoDB akan menjadi seperti berikut
    ![Screenshot .. ](../Screenshot/praktikum2/16.png)

    8. Melakukan perubahan publisher menjadi “Yen Press” pada semua buku “Osamu Dazai” dengan menggunakan command ```db.books.updateMany({<filter>}, {$set: {<data yang akan di update>}})```
    ![Screenshot .. ](../Screenshot/praktikum2/17.png)

    9. Lakukan penghapusan pada buku “Overlord I” dengan menggunakan command ```db.books.deleteOne({<argument>})```
    ![Screenshot .. ](../Screenshot/praktikum2/18.png)

    10. Lakukan penghapusan pada semua buku “Osamu Dazai dengan menggunakan command ```db.books.deleteMany({<argument>})```
    ![Screenshot .. ](../Screenshot/praktikum2/19.png)