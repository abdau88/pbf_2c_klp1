<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400" alt="Laravel Logo"></a></p>

<p align="center">
<a href="https://github.com/laravel/framework/actions"><img src="https://github.com/laravel/framework/workflows/tests/badge.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

# README - Panduan Mengakses dan Menjalankan Sistem KRS Online

## 1. Persyaratan Awal
Sebelum menjalankan proyek Laravel ini, pastikan Anda telah menginstal perangkat lunak berikut:

### a) Instalasi Wajib:
1. **XAMPP** atau **Laragon** (untuk menjalankan server dan database MySQL)
2. **Composer** (Dependency Manager untuk PHP) - [Download Composer](https://getcomposer.org/download/)
3. **Node.js** dan **npm** (untuk menjalankan frontend jika diperlukan) - [Download Node.js](https://nodejs.org/)
4. **Git** (opsional, jika ingin mengunduh proyek dari repository GitHub) - [Download Git](https://git-scm.com/)

## 2. Clone atau Download Proyek Laravel
Jika proyek disimpan di GitHub, clone dengan perintah:
```sh
  git clone https://github.com/username/nama-repo.git
```
Atau jika proyek sudah ada, langsung pindah ke foldernya:
```sh
  cd nama-folder-proyek
```

## 3. Instalasi Dependency Laravel
Setelah masuk ke folder proyek, jalankan perintah berikut untuk menginstal semua dependency:
```sh
  composer install
```

## 4. Konfigurasi Environment
1. Duplikat file `.env.example` dan ubah namanya menjadi `.env`
2. Buka file `.env` dan sesuaikan konfigurasi database:
   ```env
   DB_CONNECTION=mysql
   DB_HOST=127.0.0.1
   DB_PORT=3306
   DB_DATABASE=nama_database
   DB_USERNAME=root
   DB_PASSWORD=
   ```

   Karena disini membahas tentang SI-KRS, jadi nama database yang digunakan adalah db_krs. Bisa kalian ganti di bagian
   DB_DATABASE=nama_database menjadi DB_DATABASE=db_krs


4. Jalankan perintah berikut untuk menghasilkan kunci enkripsi aplikasi Laravel:
   ```sh
   php artisan key:generate
   ```

## 5. Buat Database dan Jalankan Migrasi
1. Buka **phpMyAdmin** melalui browser (`http://localhost/phpmyadmin/`) dan buat database sesuai dengan nama yang ada di `.env`.
2. Jalankan migrasi untuk membuat tabel-tabel yang diperlukan:
   ```sh
   php artisan migrate
   ```
3. Jika terdapat data seeder, jalankan juga:
   ```sh
   php artisan db:seed
   ```

## 6. Menjalankan Server Laravel
Setelah semua langkah di atas selesai, jalankan server Laravel dengan perintah:
```sh
  php artisan serve
```
Secara default, proyek akan berjalan di: [http://127.0.0.1:8000](http://127.0.0.1:8000)

## 7. Menjalankan Frontend (Jika Ada)
Jika proyek memiliki frontend terpisah dengan **Vue.js / React.js**, jalankan perintah berikut:
```sh
  npm install
  npm run dev
```
Lalu akses frontend melalui: [http://localhost:5173](http://localhost:5173) (jika menggunakan Vite)

Tapi di script diatas, admin tidak menggunakan vue.js atau react.js.

## 8. Troubleshooting Umum
### a) Jika Composer tidak dikenali:
   **Solusi:** Pastikan Composer sudah diinstal dan tambahkan ke PATH sistem.
### b) Jika muncul error migrasi:
   **Solusi:** Coba jalankan `php artisan migrate:fresh --seed`
### c) Jika server tidak berjalan:
   **Solusi:** Pastikan tidak ada port 8000 yang sedang digunakan, atau ubah port dengan `php artisan serve --port=8080`

---

