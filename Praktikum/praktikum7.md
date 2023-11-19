# :ledger: Praktikum Relasi One-to-Many dan Many-to-Many
Praktikum ini dilakukan pada 18 Oktober 2023. Pada repository ini berisikan source code dan screenshot penerapan dari praktikum modul 7 mengenai Relasi One-to-Many dan Many-to-Many

## Tujuan
Setelah mengikuti praktikum ini, mahasiswa diharapkan dapat:
1. Memahami relasi dan foreign key
2. Mengimplementasikan relasi one-to-many
3. Mengimplementasikan relasi many-to-many


## Dasar Teori
### Relasi
<p align= "justify">
Hubungan antar tabel yang dilakukan dengan pencocokan primary key dengan foreign key untuk mengombinasikan data dari satu tabel dengan tabel lainnya.
</p>

### Foreign Key
<p align= "justify">
Properti yang digunakan untuk menandai hubungan dua tabel atau lebih. Foreign key pada tabel anak (child) akan menunjuk tabel induk (parent) yang menjadi referensinya(reference).
</p>

### One-to-Many
<p align= "justify">
Relasi yang menunjukkan hubungan antar tabel dimana baris pada tabel induk dapat terhubung dengan satu atau lebih baris di tabel anak. Sementara baris pada tabel anak hanya dapat terhubung dengan satu baris di tabel induk.

Contoh penerapan one-to-many

- Satu tutorial dapat memiliki banyak komentar, namun satu komentar hanya dapat berada di satu tutorial
- Satu dosbing dapat memiliki banyak mahasiswa, namun mahasiswa hanya dapat dibimbing satu dosen

</p>

### Many-to-Many
<p align= "justify">
Relasi yang menunjukkan hubungan antar tabel dimana baris pada tabel induk dapat terhubung dengan satu atau lebih baris di tabel anak. Berlaku sebaliknya pada tabel anak yang dapat terhubung dengan satu atau lebih baris di tabel induk.

Contoh penerapan many-to-many
- Satu mahasiswa dapat mengambil banyak mata kuliah, namun satu mata kuliah dapat diambil banyak mahasiswa
- Postingan dapat memiliki banyak tag, namun satu tag dapat dimiliki banyak postingan.
</p>
    

Kombinasi baris pada relasi many-to-many diatur dengan junction table.

### Junction Table
<p align= "justify">
Tabel yang digunakan untuk mengatur kombinasi baris pada relasi many-to-many. Junction table berisi foreign key dari kedua tabel yang memiliki relasi many-to-many.
Contoh penerapan junction table adalah tabel Enrollment pada relasi many-to-many di atas
</p>

## Langkah Percobaan
### Pembuatan Tabel
Berikut adalah tabel yang akan digunakan pada percobaan ini
<table>
 	<tr>
 		<td> posts </td>
		<td> comments </td>
		<td> tags </td>
		<td> post_tag </td>
 	</tr>
 	<tr>
 		<td> id </td>
		<td> id </td>
		<td> id </td>
		<td> postId </td>
 	</tr>
  <tr>
 		<td> content(STRING) </td>
		<td> review(STRING) </td>
		<td> name </td>
		<td> tagId </td>
 	</tr>
  
  
 </table><br />

1. Sebelum membuat migrasi database atau membuat tabel pastikan server database aktif kemudian pastikan sudah membuat database dengan nama `lumenapi`
    ![Screenshot .. ](../Screenshot/praktikum7/71.png)

2. Kemudian ubah konfigurasi database pada file ``.env`` 
    ![Screenshot .. ](../Screenshot/praktikum7/72.png)

3. Menghidupkan beberapa library bawaan dari lumen dengan membuka file ``app.php`` pada folder ``bootstrap``
    ![Screenshot .. ](../Screenshot/praktikum7/73.png)

4. Setelah itu jalankan command berikut untuk membuat file migration
    ![Screenshot .. ](../Screenshot/praktikum7/74.png)

5. Ubah fungsi ``up()`` pada file migrasi ``create_posts_table``
    ![Screenshot .. ](../Screenshot/praktikum7/75.png)
    
6. Ubah fungsi ``up()`` pada file ``create_comments_table``
    ![Screenshot .. ](../Screenshot/praktikum7/76.png)

7. Ubah fungsi ``up()`` pada file ``create_tags_table``
    ![Screenshot .. ](../Screenshot/praktikum7/77.png)

8. Ubah fungsi ``up()`` pada file ``create_post_tag_table``
    ![Screenshot .. ](../Screenshot/praktikum7/78.png)

9. Kemudian jalankan command ``php artisan migrate``
    ![Screenshot .. ](../Screenshot/praktikum7/79.png)


### Pembuatan Model
1. Buatlah file dengan nama ``Post.php`` dan isi dengan baris kode berikut
    ![Screenshot .. ](../Screenshot/praktikum7/710.png)

2. Buatlah file dengan nama ``Comment.php`` dan isi dengan baris kode berikut
    ![Screenshot .. ](../Screenshot/praktikum7/711.png)

3. Buatlah file dengan nama ``Tag.php`` dan isi dengan baris kode berikut
    ![Screenshot .. ](../Screenshot/praktikum7/712.png)


### Relasi One-to-Many
1. Tambahkan fungsi ``comments()`` pada file ``Post.php``
    ![Screenshot .. ](../Screenshot/praktikum7/713.png)

2. Tambahkan fungsi ``post()`` dan atribut postId pada ``$fillable`` pada file ``Comment.php``
    ![Screenshot .. ](../Screenshot/praktikum7/714.png)

3. Buatlah file ``PostController.php`` dan isilah dengan baris kode berikut
    ![Screenshot .. ](../Screenshot/praktikum7/715.png)

4. Buatlah file ``CommentController.php`` dan isilah dengan baris kode berikut
    ![Screenshot .. ](../Screenshot/praktikum7/716.png)

5. Tambahkan baris berikut pada ``routes/web.php``
    ![Screenshot .. ](../Screenshot/praktikum7/717.png)

6. Buatlah satu post menggunakan Postman / Thunder Client
    ![Screenshot .. ](../Screenshot/praktikum7/718.png)

7. Buatlah satu comment menggunakan Postman / Thunder Client
    ![Screenshot .. ](../Screenshot/praktikum7/719.png)

8. Tampilkan post menggunakan Postman / Thunder Client
    ![Screenshot .. ](../Screenshot/praktikum7/720.png)


### Relasi Many-to-Many
1. Tambahkan fungsi ``tags()`` pada file ``Post.php``
    ![Screenshot .. ](../Screenshot/praktikum7/721.png)

2. Tambahkan fungsi ``posts()`` pada file ``Tag.php``
    ![Screenshot .. ](../Screenshot/praktikum7/722.png)
    
3. Buatlah file ``TagController.php`` dan isilah dengan baris kode berikut
    ![Screenshot .. ](../Screenshot/praktikum7/723.png)
    
4. Tambahkan fungsi ``addTag`` dan response tags pada ``PostController.php``
    ![Screenshot .. ](../Screenshot/praktikum7/724.png)
    
5. Tambahkan baris berikut pada ``routes/web.php``
    ![Screenshot .. ](../Screenshot/praktikum7/725.png)
    
6. Buatlah satu tag menggunakan Postman / Thunder Client
    ![Screenshot .. ](../Screenshot/praktikum7/726.png)
    
7. Tambahkan tag ``jadul`` pada post ``disana engkau berdua``
    ![Screenshot .. ](../Screenshot/praktikum7/727.png)
    
8. Tampilkan post ``disana engkau berdua`` menggunakan Postman
    ![Screenshot .. ](../Screenshot/praktikum7/728.png)
    
9. Buatlah postingan ``tanpamu apa artinya`` menggunakan Postman
    ![Screenshot .. ](../Screenshot/praktikum7/729.png)
    
10. Tambahkan tag ``jadul`` pada postingan ``tanpamu apa artinya``
    ![Screenshot .. ](../Screenshot/praktikum7/730.png)
    
11. Buatlah tag ``lagu`` menggunakan Postman
    ![Screenshot .. ](../Screenshot/praktikum7/731.png)
    
12. Tambahkan tag ``lagu`` pada postingan ``tanpamu apa artinya``
    ![Screenshot .. ](../Screenshot/praktikum7/732.png)
    
13. Tampilkan post pertama
    ![Screenshot .. ](../Screenshot/praktikum7/733.png)
    
14. Tampilkan post kedua
    ![Screenshot .. ](../Screenshot/praktikum7/734.png)
    