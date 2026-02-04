# Integrasi Git dengan Web Hosting

## Gambaran Umum
Catatan ini membahas cara mengintegrasikan Git dengan layanan web hosting untuk mengelola dan menyebarkan situs web secara lebih efisien. Metode ini menawarkan alternatif yang lebih modern dibandingkan proses unggah manual tradisional, memungkinkan sinkronisasi otomatis perubahan dari repositori Git ke server hosting.

## Sponsor: Niaga Hoster
Niaga Hoster adalah penyedia layanan hosting yang menawarkan berbagai layanan seperti *unlimited hosting* (untuk *shared hosting*), *cloud hosting*, VPS, dan domain. Didirikan pada tahun 2014, Niaga Hoster telah berkembang menjadi salah satu penyedia hosting dengan lebih dari 52 ribu klien di seluruh Indonesia.

### Fitur dan Keunggulan
*   **Layanan Beragam**: Menawarkan berbagai kategori layanan hosting dengan harga yang relatif terjangkau.
*   **Uptime Tinggi**: Menjamin *uptime* server sebesar 99,9%, memastikan situs web selalu dapat diakses dan tidak akan *down*.
*   **Kecepatan**: Didukung oleh **Lightspeed Web Server** untuk kecepatan *load* halaman yang sangat cepat.
*   **Dukungan Cepat**: Layanan dukungan pelanggan yang responsif, terutama melalui *live chat*.
*   **Tutorial Lengkap**: Menyediakan banyak tutorial dalam bentuk artikel dan video melalui kanal YouTube mereka, yang bermanfaat bagi pengguna pemula.

### Penawaran Khusus
Pengguna dapat memperoleh diskon hingga 10% untuk pembelian layanan Niaga Hoster dengan menggunakan kode promo **WPUNPAS**. Contoh pembelian paket personal selama 1 tahun dapat mencakup diskon 50% dan domain gratis.

## Alur Kerja Penyebaran Web Tradisional
Sebelum adanya integrasi Git, proses mengunggah situs web ke *web hosting* biasanya melibatkan langkah-langkah berikut:
1.  **Pengembangan Lokal**: Situs web (HTML, CSS, PHP, dll.) dikembangkan dan disimpan di komputer lokal.
2.  **Unggah Manual**: File-file diunggah ke *web hosting* menggunakan salah satu cara berikut:
    *   **cPanel/Control Panel**: Mengunggah file secara langsung melalui antarmuka *control panel* hosting, seringkali setelah mengompres file menjadi ZIP.
    *   **FTP Client**: Menggunakan aplikasi seperti FileZilla untuk mentransfer file melalui FTP.
3.  **Pembaruan Manual**: Setiap kali ada perubahan pada situs web, pengembang harus mengedit file secara lokal, lalu mengunggah ulang file yang telah dimodifikasi ke *hosting*.

## Alur Kerja Penyebaran Web dengan Git
Integrasi Git menawarkan alternatif yang lebih efisien dan terstruktur untuk mengunggah dan mengelola situs web di *web hosting*.

### Alur Kerja yang Direkomendasikan
1.  **Pengembangan Lokal dengan Git**:
    *   Kerjakan proyek di lingkungan lokal.
    *   Inisialisasi Git di proyek lokal untuk melacak perubahan (*commit*).
2.  **Sinkronisasi dengan GitHub**:
    *   Unggah repositori lokal ke **GitHub** (atau platform Git *remote* lainnya).
    *   Atau, jika proyek sudah ada di GitHub, *clone* ke lokal terlebih dahulu.
3.  **Penyebaran ke Web Hosting**:
    *   **Web hosting menarik (*pull*) dari GitHub**: Konfigurasikan *web hosting* untuk menarik perubahan langsung dari repositori GitHub.
    *   **Proses Pembaruan**:
        *   Edit kode di lingkungan lokal.
        *   *Push* perubahan dari lokal ke GitHub.
        *   *Web hosting* akan menarik (*pull*) perubahan terbaru dari GitHub secara otomatis atau manual.

## Demonstrasi Integrasi Git dengan Niaga Hoster
Berikut adalah langkah-langkah praktis untuk mengintegrasikan Git dengan layanan *cloud hosting* Niaga Hoster:

### 1. Akses cPanel dan Git Version Control
*   Masuk ke area anggota Niaga Hoster dan akses panel admin.
*   Pilih layanan hosting yang digunakan (misalnya, *cloud hosting* basic atau *shared hosting*).
*   Di pengaturan akun hosting, klik **All Features** untuk mengakses semua fitur cPanel.
*   Di bagian **Files**, temukan dan pilih **Git Version Control**.

### 2. Mempersiapkan Direktori Hosting
*   Gunakan **File Manager** di cPanel untuk melihat struktur direktori.
*   Situs web biasanya disimpan di folder `public_html`. Pastikan direktori ini kosong atau sesuai dengan kebutuhan.
*   Repositori Git akan disimpan di dalam `public_html`.

### 3. Mengkloning Repositori GitHub ke Hosting
*   Di halaman **Git Version Control**, klik **Create**.
*   Pilih opsi **Clone a Repository**.
*   Dapatkan **Clone URL** dari repositori GitHub yang ingin disebarkan (gunakan HTTPS).
    *   Contoh: `https://github.com/sandikagalih/simple-landing-page.git`.
*   Tempel URL ke kolom **Clone URL**.
*   Atur **Repository Path** ke `public_html` (misalnya, `/home/user/public_html`). Ini memastikan isi repositori langsung berada di *root* situs web.
*   Biarkan **Repository Name** sesuai dengan nama repositori GitHub.
*   Klik **Create**. Setelah proses *clone* selesai, akan muncul notifikasi `Clone is complete`.

### 4. Verifikasi Penyebaran
*   Setelah *clone* berhasil, situs web akan langsung tampil saat diakses melalui domain. Ini menunjukkan bahwa situs web kini mengambil konten dari GitHub, bukan lagi dari komputer lokal.

### 5. Memperbarui Situs Web (Lokal -> GitHub -> Hosting)
*   **Kloning Repositori ke Lokal**: Kloning repositori GitHub ke komputer lokal jika belum ada.
    *   Contoh perintah: `git clone [URL_repositori]`.
*   **Modifikasi Lokal**: Lakukan perubahan pada kode di lingkungan lokal menggunakan editor kode.
    *   Contoh: Mengubah teks *heading* dari "Sandika Gali" menjadi "Sandika".
*   **Commit dan Push ke GitHub**:
    *   Simpan perubahan.
    *   Lakukan *commit* perubahan dengan pesan yang deskriptif.
        *   Contoh perintah: `git commit -am "Mengubah tulisan brand menjadi Sandika"`.
    *   *Push* perubahan dari repositori lokal ke repositori GitHub.
        *   Contoh perintah: `git push -u origin master`.
    *   (Catatan: Untuk alur kerja yang lebih baik, disarankan menggunakan *branch* terpisah sebelum *merge* ke *master*).
*   **Pull Perubahan ke Web Hosting**:
    *   Setelah perubahan di-*push* ke GitHub, masuk kembali ke **Git Version Control** di cPanel.
    *   Pilih repositori yang ingin diperbarui.
    *   Klik **Pull or Deploy** lalu **Update**.
    *   Sistem akan menarik perubahan terbaru dari GitHub. Verifikasi dengan melihat *commit* terakhir yang ditampilkan.
*   **Verifikasi di Situs Web**: Refresh situs web di *browser*. Perubahan yang dilakukan secara lokal dan di-*push* ke GitHub kini akan terlihat di situs web yang di-*hosting*.

## Kesimpulan
Integrasi Git dengan *web hosting* memungkinkan alur kerja yang lebih modern dan efisien untuk pengembangan dan penyebaran situs web. Dengan mengelola kode di repositori Git seperti GitHub dan mengkonfigurasi *hosting* untuk menarik perubahan, proses pembaruan menjadi lebih cepat dan terkontrol.