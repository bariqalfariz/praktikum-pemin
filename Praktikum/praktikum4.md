# :ledger: Praktikum Basic Routing dan Migration
Praktikum ini dilakukan pada 27 September 2023. Pada repository ini berisikan source code dan screenshot penerapan dari praktikum modul 4 mengenai Basic Routing dan Migration

## Tujuan
Mahasiswa diharapkan dapat : 
1. Melakukan basic routing.
1. Mengakses routing
1. Melakukan migration ke database

## Langkah Percobaan
1. GET 
    Untuk menambahkan endpoint dengan method GET pada aplikasi kita, kita dapat mengunjungi file ``web.php`` pada folder routes. Kemudian tambahkan baris ini pada akhir file
    
    ![Screenshot node -v](../Screenshot/praktikum4/1.png)

    Setelah itu coba jalankan aplikasi dengan command,

    ![Screenshot node -v](../Screenshot/praktikum4/2.png)

    Hasilnya :

    ![Screenshot node -v](../Screenshot/praktikum4/3.png)

        Setelah aplikasi berhasil dijalankan, kita dapat membuka browser dengan url, ``http://localhost:8000/get`` , path yang akan kita akses akan berbentuk demikian, http://{BASE_URL}{PATH} , jika BASE_URL kita adalah localhost:8000 dan PATH kita adalah /get , maka url akan berbentuk seperti diatas.

2. POST, PUT, PATCH, DELETE, dan OPTIONS
    Sama halnya saat menambahkan method GET, kita dapat menambahkan methode POST, PUT, PATCH, DELETE, dan OPTIONS pada file web.php dengan code seperti ini,

        ...
        $router->post('/post', function () {
            return 'POST';
        });
        $router->put('/put', function () {
            return 'PUT';
        });
        $router->patch('/patch', function () {
            return 'PATCH';
        });
        $router->delete('/delete', function () {
            return 'DELETE';
        });
        $router->options('/options', function () {
            return 'OPTIONS';
        });

    ![Screenshot node -v](../Screenshot/praktikum4/4.png)

    Setelah selesai menambahkan route untuk method POST, PUT, PATCH, DELETE, dan OPTIONS, kita dapat menjalankan server seperti pada saat percobaan GET. Setelah server berhasil menyala, kita dapat membuka aplikasi Postman atau Insomnia atau kita juga dapat menggunakan PowerShell (Windows) / Terminal (Linux atau Mac) untuk melakukan request ke server. Namun, pada percobaan kali ini kita akan menggunakan extensions pada VSCode yaitu Thunder Client.

    a. Kita dapat menginstall ekstensi dengan membuka panel extensions lalu mencari thunder client

    ![Screenshot node -v](../Screenshot/praktikum4/5.png)

    b. Setelah menginstall Thunder Client, kita akan melihat logo seperti petir pada activity bar kita (sebelah kiri).

    c. Kita dapat membuat request dengan menekan "New Request" pada ekstensi

    d. Setelah itu kita dapat memasukkan method dan url yang dituju
    ![Screenshot node -v](../Screenshot/praktikum4/6.png)

    e. Akses url yang baru saja ditambahkan pada aplikasi dengan methodnya

    POST : 
    ![Screenshot node -v](../Screenshot/praktikum4/7.png)

    PUT :
    ![Screenshot node -v](../Screenshot/praktikum4/8.png)

    PATCH :
    ![Screenshot node -v](../Screenshot/praktikum4/9.png)

    DELETE :
    ![Screenshot node -v](../Screenshot/praktikum4/10.png)

    OPTIONS : 
    ![Screenshot node -v](../Screenshot/praktikum4/11.png)

3. Migrasi Database
    
    a. Sebelum melakukan migrasi database pastikan server database aktif kemudian pastikan sudah membuat database dengan nama ``lumenapi``

    ![Screenshot node -v](../Screenshot/praktikum4/createdb.png)

    b. Kemudian ubah konfigurasi database pada file .env menjadi seperti ini
        
        DB_CONNECTION=mysql
        DB_HOST=127.0.0.1
        DB_PORT=3306
        DB_DATABASE=lumenapi
        DB_USERNAME=root
        DB_PASSWORD=<<password masing-masing>>
        
    ![Screenshot node -v](../Screenshot/praktikum4/12.png)



    c. Setelah mengubah konfigurasi pada file .env, kita juga perlu menghidupkan beberapa library bawaan dari lumen dengan membuka file ``app.php`` pada folder bootstrap dan mengubah baris ini,

        //$app->withFacades();
        //$app->withEloquent(); 

    Menjadi : 

        $app->withFacades();
        $app->withEloquent();

    ![Screenshot node -v](../Screenshot/praktikum4/13.png)

    d. Setelah itu jalankan command berikut untuk membuat file migration,

        php artisan make:migration create_users_table # membuat migrasi untuk tabel users
        php artisan make:migration create_products_table # membuat migrasi untuk tabel products

    ![Screenshot node -v](../Screenshot/praktikum4/14.png)

    Setelah menjalankan 2 syntax diatas akan terbuat 2 file pada folder ``database/migrations`` dengan format YYYY_MM_DD_HHmmss_nama_migrasi. Pada file migrasi kita akan menemukan fungsi up() dan fungsi down(), fungsi up() akan digunakan pada saat kita melakukan migrasi, fungsi down() akan digunakan saat kita ingin me-rollback migrasi

    ![Screenshot node -v](../Screenshot/praktikum4/15.png)

    e. Ubah fungsi up pada file migrasi ``create_users_table``

        # sebelumnya
        ...
            public function up()
            {
                Schema::create('users', function (Blueprint $table) {
                    $table->id();
                    $table->timestamps();
                });
            }
        ...
        # diubah menjadi
        ...
            public function up()
            {
                Schema::create('users', function (Blueprint $table) {
                    $table->id();
                    $table->timestamps();
                    $table->string('name');
                    $table->string('email');
                    $table->string('password');
                });
            }
        ...

    ![Screenshot node -v](../Screenshot/praktikum4/16.png)


    f. Ubah fungsi up pada file migrasi ``create_products_table``

        # sebelumnya
        ...
        public function up()
        {
            Schema::create('products', function (Blueprint $table) {
                $table->id();
                $table->timestamps();
            });
        }
        ...
        # diubah menjadi
        ...
        public function up()
        {
            Schema::create('products', function (Blueprint $table) {
                $table->id();
                $table->timestamps();
                $table->string('name');
                $table->integer('category_id');
                $table->string('slug');
                $table->integer('price');
                $table->integer('weight');
                $table->text('description');
            });
        }
        ...

    ![Screenshot node -v](../Screenshot/praktikum4/17.png)


    g. Kemudian jalankan command,
        php artisan migrate

    ![Screenshot node -v](../Screenshot/praktikum4/18.png)
    
    ![Screenshot node -v](../Screenshot/praktikum4/19.png)    