# Catatan Studi: Web Hosting Gratis dengan GitHub Pages

## Overview

GitHub Pages adalah fitur yang disediakan oleh GitHub yang memungkinkan pengguna untuk membuat dan menghosting halaman website statis secara gratis. Fitur ini sangat berguna untuk menampilkan informasi mengenai repositori proyek atau sebagai solusi web hosting pribadi. GitHub Pages dirancang khusus untuk website yang dibangun menggunakan **HTML, CSS, dan JavaScript** saja, sehingga tidak mendukung bahasa pemrograman *server-side* seperti PHP atau Python, maupun sistem manajemen basis data seperti MySQL. Meskipun gratis, ada batasan tertentu terkait ukuran maksimal website dan *bandwidth* yang perlu diperhatikan.

## Apa itu GitHub Pages?

GitHub Pages adalah layanan hosting gratis yang disediakan oleh GitHub, memungkinkan pengguna untuk menerbitkan konten web langsung dari repositori mereka.

### Karakteristik dan Keterbatasan

*   **Website Statis**: GitHub Pages hanya mendukung **website statis**, yaitu website yang hanya terdiri dari file HTML, CSS, dan JavaScript.
*   **Tanpa Server-side**: Tidak ada dukungan untuk *server-side scripting* (misalnya PHP, Python, Ruby) atau database (misalnya MySQL), karena GitHub Pages tidak menyediakan web server (seperti Apache) atau database server.
*   **Hosting Gratis**: Merupakan solusi hosting web gratis yang populer untuk proyek-proyek pribadi, portofolio, atau dokumentasi.
*   **Batasan**: Terdapat batasan ukuran maksimal website dan *bandwidth* yang dapat digunakan, meskipun detail spesifiknya perlu dicek di dokumentasi resmi GitHub Pages.

## Jenis-jenis GitHub Pages

Ada dua jenis utama GitHub Pages, masing-masing dengan tujuan dan konvensi penamaan yang berbeda:

### 1. Halaman Akun Pengguna/Organisasi (User/Organization Pages)

Jenis ini digunakan untuk membuat website utama yang terkait langsung dengan akun GitHub pribadi atau organisasi.

*   **Konvensi Penamaan Repositori**: Repositori harus diberi nama khusus: `username.github.io` (misalnya, `sandikagali.github.io`).
*   **URL**: Alamat website akan secara otomatis menjadi `username.github.io`.
*   **Jumlah**: Setiap akun GitHub hanya dapat memiliki satu Halaman Akun Pengguna/Organisasi.

### 2. Halaman Repositori Proyek (Project Pages)

Jenis ini memungkinkan setiap repositori proyek memiliki halaman website-nya sendiri.

*   **Konvensi Penamaan Repositori**: Nama repositori bisa bebas (misalnya, `wpu-landing`).
*   **URL**: Alamat website akan mengikuti format `username.github.io/nama-repositori` (misalnya, `webprogrammingunpass.github.io/wpu-landing`).
*   **Jumlah**: Setiap repositori dapat memiliki Halaman Proyeknya sendiri.

## Cara Membuat GitHub Pages

Proses pembuatan GitHub Pages melibatkan beberapa langkah, mulai dari menyiapkan repositori lokal hingga mengaktifkannya di GitHub.

### Prasyarat Umum

*   Memiliki akun GitHub.
*   Memiliki folder website statis (HTML, CSS, JavaScript) di komputer lokal.
*   Pastikan file utama website diberi nama `index.html` agar dapat langsung ditampilkan.

### Langkah-langkah untuk Halaman Akun Pengguna/Organisasi

1.  **Buat Repositori Baru di GitHub**:
    *   Masuk ke GitHub, klik tanda `+` di kanan atas, lalu pilih `New repository`.
    *   Beri nama repositori sesuai format `username.github.io`.
    *   Tambahkan deskripsi (opsional) dan pilih `Public`.
    *   **Penting**: Jangan centang `Add a README file` untuk memudahkan inisialisasi dari lokal.
    *   Klik `Create repository`.
2.  **Inisialisasi Git di Folder Lokal**:
    *   Buka folder website statis Anda di komputer lokal.
    *   Buka Git Bash (atau terminal) di dalam folder tersebut.
    *   Jalankan perintah `git init`.
3.  **Tambahkan Remote ke Repositori GitHub**:
    *   Hubungkan repositori lokal ke repositori di GitHub dengan perintah:
        `git remote add origin https://github.com/username/username.github.io.git`
4.  **Tambahkan dan Commit File**:
    *   Tambahkan semua file ke *staging area*: `git add .`
    *   Buat commit awal: `git commit -m "Initial commit"`
5.  **Push ke GitHub**:
    *   Unggah kode dari lokal ke GitHub: `git push -u origin master`
    *   Tunggu hingga proses unggah selesai.
6.  **Akses Halaman**: Setelah berhasil di-*push*, website Anda akan langsung dapat diakses melalui URL `username.github.io`.

### Langkah-langkah untuk Halaman Repositori Proyek

1.  **Inisialisasi Git di Folder Lokal**:
    *   Masuk ke folder proyek website statis Anda.
    *   Jalankan `git init`.
2.  **Tambahkan dan Commit File**:
    *   Tambahkan semua file ke *staging area*: `git add .`
    *   Buat commit awal: `git commit -m "Initial commit"`
3.  **Buat Repositori Baru di GitHub**:
    *   Buat repositori baru di GitHub dengan nama bebas (misalnya, `wpu-landing`).
    *   Pilih `Public` dan jangan centang `Add a README file`.
    *   Klik `Create repository`.
4.  **Tambahkan Remote dan Push ke GitHub**:
    *   Salin dan jalankan perintah `git remote add origin ...` dan `git push -u origin master` yang disediakan oleh GitHub di halaman repositori baru Anda.
5.  **Aktifkan GitHub Pages di Pengaturan Repositori**:
    *   Setelah berhasil di-*push*, navigasi ke repositori Anda di GitHub.
    *   Klik tab `Settings` di kanan atas.
    *   Gulir ke bawah dan cari bagian `GitHub Pages`.
    *   Pada opsi `Source`, pilih `master branch` (atau branch yang berisi file website Anda).
    *   Tunggu beberapa saat hingga proses aktivasi selesai.
6.  **Akses Halaman**: URL website Anda akan muncul di bawah bagian `GitHub Pages` (misalnya, `username.github.io/wpu-landing`).

## Fitur dan Pertimbangan Penting

*   **Pembaruan Otomatis**: Setiap kali Anda melakukan `git commit` dan `git push` ke repositori yang terhubung, perubahan pada website Anda akan secara otomatis diperbarui dan diterbitkan.
*   **Custom Domain**: GitHub Pages mendukung penggunaan **custom domain** (misalnya, `webprogrammingunpass.com`) untuk menggantikan URL default `username.github.io`. Pengaturan ini dapat dilakukan di bagian `Custom domain` pada pengaturan GitHub Pages repositori Anda.
*   **Repositori Non-Website**: Jika repositori Anda bukan merupakan website statis (misalnya, hanya berisi kode sumber, dokumentasi, atau skrip yang memerlukan *web server*), Anda tetap dapat mengaktifkan GitHub Pages. Dalam kasus ini, GitHub akan menawarkan opsi untuk memilih tema yang akan menampilkan konten repositori Anda dalam format yang lebih terstruktur dan menarik, seringkali menggunakan Markdown.

## Kesimpulan

GitHub Pages adalah alat yang sangat powerful dan gratis untuk menghosting website statis, portofolio, atau dokumentasi proyek. Dengan integrasi yang mulus dengan alur kerja Git dan GitHub, ia menyediakan cara yang efisien untuk menerbitkan konten web secara online.