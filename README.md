# Laravel_Fundamentals
This repository serves as a comprehensive resource for understanding the core concepts and fundamental principles of Laravel, a popular PHP web application framework. It is designed to guide beginners through the essential features of Laravel, enabling them to build robust and scalable web applications.

# Laravel_Fundamentals: Membangun Pondasi Aplikasi Web dengan Laravel

---

## Gambaran Umum Proyek

Repositori ini adalah panduan praktis dan komprehensif yang didedikasikan untuk memahami **konsep inti dan prinsip fundamental Laravel**, *framework* aplikasi web PHP yang paling populer. Proyek ini, yang berfokus pada **"Laravel Fundamentals"**, dirancang untuk memandumu langkah demi langkah dari nol hingga mahir dalam penggunaan fitur-fitur dasar dan esensial Laravel untuk membangun aplikasi web yang kokoh dan efisien.

**Dalam panduan ini, kamu akan mendalami:**

* **Pengenalan & Instalasi Laravel:** Memahami cara memulai proyek Laravel dari awal, struktur direktori standar, dan siklus hidup permintaan (request lifecycle) dalam aplikasi Laravel.
* **Routing & Controller:** Mengelola alur permintaan HTTP ke dalam aplikasi, memetakan URL ke logika bisnis, dan mengorganisir kode dengan *controller*.
* **Views & Blade Templating:** Membuat antarmuka pengguna yang dinamis dan modular menggunakan sistem *templating* Blade yang powerful dan intuitif.
* **Database & Eloquent ORM:** Berinteraksi dengan database secara efisien menggunakan Eloquent ORM Laravel yang elegan, termasuk definisi *model*, penggunaan *migration* untuk manajemen skema database, dan *seeding* untuk mengisi data awal.
* **Artisan Console:** Memanfaatkan *command-line interface* (CLI) Laravel yang serbaguna untuk mengotomatisasi berbagai tugas pengembangan.
* **Middleware:** Memahami dan mengimplementasikan lapisan *middleware* untuk memfilter permintaan HTTP sebelum mencapai *controller*.
* **Validasi Data:** Menerapkan aturan validasi yang kuat untuk memastikan integritas dan keamanan data dari input pengguna.
* **Autentikasi & Otorisasi:** Mengimplementasikan sistem pendaftaran, login, logout, dan manajemen akses pengguna dasar.
* **Penanganan Error & Debugging:** Strategi untuk mengidentifikasi, mencatat, dan menyelesaikan kesalahan dalam aplikasi Laravel.

**Repositori ini sangat ideal untuk:**

* **Pemula di Laravel:** Jika kamu baru mengenal Laravel dan ingin membangun pemahaman yang kuat dari dasar.
* **Pengembang PHP:** Yang ingin beralih ke Laravel atau memperkuat pemahaman tentang praktik terbaik dan fitur-fitur modern *framework* ini.
* **Siapa saja:** Yang mencari contoh kode praktis, panduan langkah demi langkah yang detail, dan penjelasan konsep dasar Laravel yang jernih.

---

## Persyaratan Sistem

Sebelum memulai, pastikan lingkungan pengembanganmu memenuhi persyaratan minimum berikut untuk memastikan Laravel berjalan dengan lancar:

* **PHP:** Versi **8.1** atau lebih tinggi.
    * *Tips:* Kamu bisa memeriksa versi PHP dengan menjalankan `php -v` di terminal atau *command prompt*.
* **Composer:** Versi **2.x** atau lebih tinggi.
    * *Tips:* Composer adalah manajer dependensi utama untuk PHP. Pastikan sudah terinstal dan berfungsi dengan `composer -v`.
* **Database:** **MySQL** (direkomendasikan), PostgreSQL, SQLite, atau SQL Server. Proyek ini akan dikonfigurasi secara *default* untuk MySQL.
* **Web Server:** Apache atau Nginx. Umumnya sudah termasuk jika kamu menggunakan lingkungan pengembangan lokal seperti XAMPP, MAMP, atau Laragon.

---

## Panduan Instalasi & Penyiapan Proyek Laravel

Ikuti langkah-langkah ini untuk menyiapkan dan menjalankan proyek Laravel-mu di lingkungan pengembangan lokal.

### 1. Penyiapan Proyek Laravel Awal

Ini adalah fondasi dari setiap proyek Laravel.

1.  **Buat Proyek Laravel Baru:**
    Jalankan perintah Composer ini di terminal atau *command prompt* pilihanmu. Kita akan menamai proyek ini `my_laravel_app` sebagai contoh, kamu bisa menggantinya.
    ```bash
    composer create-project laravel/laravel my_laravel_app
    ```
    *Perintah ini akan membuat folder baru bernama `my_laravel_app` di direktori saat ini, mengunduh semua dependensi inti Laravel, dan menginstal *framework*.*

2.  **Masuk ke Direktori Proyek:**
    Setelah instalasi selesai, navigasikan ke dalam direktori proyek yang baru dibuat:
    ```bash
    cd my_laravel_app
    ```

### 2. Konfigurasi Database

Koneksi database adalah komponen vital untuk aplikasi web yang menyimpan data.

1.  **Buat Database Baru:**
    Akses *tool* manajemen database-mu (misalnya phpMyAdmin, Adminer, MySQL Workbench, DBeaver, atau klien CLI) dan buat database baru.
    * **Nama Database yang Direkomendasikan untuk Proyek Ini:** `my_laravel_db` (Kamu bisa menggantinya)

2.  **Konfigurasi File `.env`:**
    Laravel menggunakan file `.env` untuk menyimpan konfigurasi spesifik lingkungan (misalnya, kredensial database, kunci API).
    * Pastikan kamu memiliki file `.env` di *root* proyekmu. Jika tidak ada, salin dari `.env.example`:
        ```bash
        cp .env.example .env
        ```
    * Selanjutnya, buka file `.env` dengan editor teks favoritmu dan sesuaikan pengaturan koneksi database-mu agar sesuai dengan database yang baru saja kamu buat:
        ```dotenv
        DB_CONNECTION=mysql
        DB_HOST=127.0.0.1
        DB_PORT=3306
        DB_DATABASE=my_laravel_db    # Sesuaikan dengan nama database yang kamu buat
        DB_USERNAME=root             # Sesuaikan dengan username database lokalmu (umumnya 'root' untuk XAMPP/MAMP)
        DB_PASSWORD=                 # Sesuaikan dengan password database lokalmu (biarkan kosong jika tidak ada password)
        ```

3.  **Jalankan Migrasi Database:**
    Laravel Migrations adalah sistem kontrol versi untuk skema database-mu. Perintah ini akan membuat semua tabel dasar yang dibutuhkan Laravel (seperti `users`, `password_reset_tokens`, dll.) di database-mu, berdasarkan *file-file* migrasi yang ada di folder `database/migrations/`:
    ```bash
    php artisan migrate
    ```
    * **Tips Pro:** Jika kamu mengkloning repositori Laravel yang sudah ada atau menarik perubahan dari *branch* lain, selalu jalankan `php artisan migrate` untuk memastikan skema database-mu selalu mutakhir dengan perubahan terbaru.

### 4. Menjalankan Server Pengembangan

Setelah semua konfigurasi awal selesai, kamu bisa menjalankan server pengembangan bawaan Laravel:

```bash
php artisan serve
