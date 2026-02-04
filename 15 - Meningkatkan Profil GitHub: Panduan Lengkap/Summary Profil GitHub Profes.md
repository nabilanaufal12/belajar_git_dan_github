# Meningkatkan Profil GitHub: Panduan Lengkap

Profil GitHub berfungsi sebagai "etalase" utama bagi para programmer dan developer untuk memamerkan keahlian coding serta proyek-proyek yang telah dibuat. Profil yang menarik dapat membuat pengunjung betah dan tertarik melihat portofolio Anda. Panduan ini akan membahas berbagai cara untuk mempercantik profil GitHub Anda, mulai dari dasar hingga tingkat lanjut.

## 1. Kustomisasi Dasar: Repositori Spesial `README.md`

Langkah pertama dan paling fundamental adalah membuat repositori khusus yang akan menjadi dasar profil GitHub Anda.

### Membuat Repositori Profil

1.  Masuk ke akun GitHub Anda.
2.  Klik tanda `+` di pojok kanan atas, lalu pilih **New repository**.
3.  Beri nama repositori sama persis dengan **username GitHub Anda** (contoh: `SandikaGali/SandikaGali`). GitHub akan mengidentifikasi ini sebagai repositori spesial untuk profil Anda.
4.  Pastikan visibilitas diatur ke **Public**.
5.  Centang opsi **Initialize this repository with a README**.
6.  Klik **Create repository**.

Setelah dibuat, profil Anda akan menampilkan `README.md` default dengan tulisan "Hi there!".

### Mengedit `README.md` Secara Lokal

Untuk kemudahan pengeditan, disarankan untuk mengkloning repositori ini ke komputer lokal Anda dan mengeditnya menggunakan *code editor* seperti Visual Studio Code.

1.  Masuk ke repositori profil Anda di GitHub.
2.  Klik tombol **Code**, lalu pilih **Copy URL to clipboard**.
3.  Buka terminal atau *command prompt* di direktori lokal yang Anda inginkan (misalnya, Desktop).
4.  Ketik perintah `git clone [URL_yang_disalin]`.
5.  Masuk ke direktori repositori dengan `cd [nama_repositori]`.
6.  Buka di VS Code dengan `code .`.

### Sintaks Markdown Dasar

File `README.md` menggunakan format **Markdown**. Anda dapat melihat pratinjau langsung di VS Code dengan menginstal ekstensi "Markdown Preview Enhanced".

*   **Heading**: Gunakan `#` untuk H1, `##` untuk H2, dan seterusnya.
*   **Teks Tebal**: Gunakan `**teks**` atau `Ctrl+B`.
*   **Teks Miring/Coret**: Sintaks serupa tersedia.
*   **Tautan (Link)**: `[Teks Tautan](URL)`.
*   **Emoji**: Di Windows, tekan `Windows + .` untuk memunculkan panel emoji.
*   **Gambar**: `![Teks Alternatif](URL_Gambar)`.
    *   Gambar dapat diambil dari layanan hosting online (misalnya Giphy).
    *   Atau simpan gambar langsung di repositori Anda (misalnya di folder `img/`).
*   Untuk referensi lengkap, kunjungi dokumentasi GitHub tentang Markdown (`Writing on GitHub` -> `Basic formatting syntax`).

Setelah selesai mengedit, simpan perubahan, *commit*, dan *push* ke GitHub Anda.

## 2. Menambahkan Elemen Grafis (Level Menengah)

Untuk membuat profil lebih menarik, Anda bisa menambahkan elemen grafis seperti *banner*, *badge*, ikon, dan statistik menggunakan repositori GitHub pihak ketiga.

### Generator Banner

*   **Alat**: Banner generator oleh Levi Arista.
*   **Fungsi**: Membuat *banner* kustom dengan mudah. Anda dapat menyesuaikan teks (judul, *tagline*), warna, jenis huruf, pola latar belakang, dan ikon dekorasi.
*   **Penggunaan**: Unduh *banner* yang sudah jadi, lalu gunakan sebagai gambar di `README.md` Anda.

### Badge

*   **Alat**: Repositori *badges* oleh Alex Andre Sunanlim.
*   **Fungsi**: Menampilkan keahlian, teknologi yang dikuasai, atau tautan media sosial dalam bentuk ikon kecil yang menarik.
*   **Penggunaan**: Salin URL gambar *badge* untuk keahlian, atau gabungkan dengan sintaks *link* Markdown untuk media sosial yang dapat diklik. Repositori ini menyediakan berbagai *badge* untuk bahasa pemrograman, *framework*, media sosial, dan lainnya.

### Ikon

*   **Alat**: Repositori ikon oleh Tendy Pun.
*   **Fungsi**: Alternatif visual untuk *badge* berbasis teks, dengan opsi tema gelap atau terang.
*   **Penggunaan**: Mirip dengan menambahkan gambar atau *badge*.

### Statistik GitHub

*   **Alat**: Repositori statistik oleh Anurag Hazra.
*   **Fungsi**: Menampilkan statistik GitHub Anda seperti jumlah *star*, *commit*, *pull request*, dan nilai keseluruhan profil GitHub.
*   **Kustomisasi**: Tersedia berbagai tema, opsi untuk menyembunyikan/menampilkan statistik tertentu, dan dukungan bahasa (locale).
*   **Penting**: Pastikan untuk mengganti *placeholder* `username` dengan username GitHub Anda.

## 3. Menggunakan Generator Profil (Level Lanjut)

Bagi Anda yang ingin proses kustomisasi lebih otomatis, ada generator profil yang dapat membantu.

### GPRM.svg.in

*   **Cara Kerja**: Cukup masukkan *username* GitHub Anda.
*   **Fitur**: Menyediakan berbagai bagian seperti "About", statistik, media sosial, *tech stack*, tautan donasi, GitHub Trophies, jumlah pengunjung, dan kontributor teratas.
*   **Output**: Akan menghasilkan kode Markdown yang siap disalin atau diunduh.
*   **Keuntungan**: Proses cepat dan mudah, tidak perlu mencari URL *badge* atau statistik secara manual.

Ada juga generator serupa lainnya seperti yang dibuat oleh Rahul DK Jain. Anda dapat menggabungkan komponen dari berbagai generator atau mengeditnya secara manual untuk hasil yang paling sesuai.

## 4. Kustomisasi Elite: GitHub Actions untuk Game

Untuk sentuhan yang sangat unik, Anda dapat mengintegrasikan elemen interaktif seperti game langsung ke profil Anda menggunakan **GitHub Actions**.

### Menambahkan Game (Pacman & Snake)

Beberapa generator profil (misalnya, yang disebutkan pada) memungkinkan Anda menambahkan game seperti Pacman dan Snake. Generator ini akan menyediakan kode Markdown spesifik untuk game tersebut.

### Mengatur GitHub Actions

Agar game dapat berjalan secara dinamis, Anda perlu mengonfigurasi GitHub Actions di repositori Anda:

1.  **Buat Struktur Folder**:
    *   Di *root* repositori Anda, buat folder baru bernama `.github`.
    *   Di dalam folder `.github`, buat folder lain bernama `workflows`.
    *   Di dalam folder `workflows`, buat dua file `.yml` untuk setiap game (misalnya, `pacman.yml` dan `snake.yml`).
    *   Salin konten konfigurasi YAML yang disediakan oleh generator game ke dalam file-file ini.
2.  **Push Perubahan**: *Commit* dan *push* semua file baru ini ke GitHub Anda.
3.  **Konfigurasi Izin GitHub Actions**:
    *   Masuk ke repositori Anda di GitHub, lalu ke **Settings** -> **Actions** -> **General**.
    *   Di bagian **Action permissions**, pilih **"Allow all actions and reusable workflows"**.
    *   Gulir ke bawah ke **Workflow permissions**, pilih **"Read and write permissions"**.
    *   Simpan perubahan.
4.  **Verifikasi**: Periksa tab **Actions** untuk memastikan *workflow* telah berjalan dengan sukses.

Setelah langkah-langkah ini selesai, game (Pacman, Snake) akan muncul dan berjalan secara dinamis di profil GitHub Anda.

## Kesimpulan

Kombinasikan berbagai teknik dan alat yang telah dijelaskan sesuai dengan gaya dan kreativitas pribadi Anda. Profil GitHub adalah etalase Anda, jadi buatlah semenarik mungkin. Jangan ragu untuk berbagi profil GitHub Anda yang telah diperbarui.