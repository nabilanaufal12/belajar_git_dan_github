# GitHub: Forking Repository

## Pendahuluan

**Fork** atau **forking** adalah sebuah proses di GitHub yang memungkinkan pengguna untuk menduplikasi (menyalin) sebuah repositori milik orang lain ke akun GitHub mereka sendiri. Proses ini tidak hanya menyalin kode, tetapi juga seluruh riwayat *commit* dari repositori asli.

## Tujuan dan Manfaat Forking

Forking memiliki dua tujuan utama:

1.  **Memodifikasi Repositori untuk Proyek Pribadi**: Pengguna dapat menduplikasi repositori orang lain untuk digunakan dan dimodifikasi sesuai kebutuhan proyek mereka sendiri, tanpa mengganggu repositori asli. Contohnya, jika ada repositori yang menyediakan fungsi *login*, pengguna bisa me-*fork*-nya dan mengintegrasikan fungsi tersebut ke aplikasi mereka.
2.  **Berkontribusi ke Repositori Asli**: Setelah me-*fork* dan memodifikasi repositori, pengguna dapat mengusulkan perubahan yang mereka buat kembali ke pemilik repositori asli. Jika perubahan tersebut lebih baik atau menambahkan fungsionalitas, pemilik repositori asli dapat menerapkannya. Proses pengusulan perubahan ini disebut **Pull Request**.

## Fork vs. Clone

Penting untuk membedakan antara **fork** dan **clone**:

*   **Fork**: Menduplikasi repositori orang lain dari GitHub ke **akun GitHub kita sendiri**. Hasilnya adalah salinan repositori di *remote* (GitHub) kita.
*   **Clone**: Menduplikasi repositori (baik milik sendiri maupun hasil *fork*) dari *remote* (GitHub) ke **komputer lokal kita**. Hasilnya adalah salinan repositori di mesin lokal kita.

Meskipun keduanya berfungsi menduplikasi repositori, *fork* menciptakan salinan di GitHub, sementara *clone* menciptakan salinan di komputer lokal.

## Cara Melakukan Fork (Studi Kasus: Fork `WPU Resolusi`)

Berikut adalah langkah-langkah untuk melakukan *fork* repositori di GitHub:

1.  **Kunjungi Repositori Target**: Masuk ke akun GitHub Anda (misalnya, Sandika Gali) dan kunjungi repositori yang ingin di-*fork* (misalnya, `WPU Resolusi` milik Web Programming Unpas).
2.  **Klik Tombol Fork**: Di halaman repositori, klik tombol **"Fork"** yang biasanya terletak di kanan atas.
3.  **Verifikasi Fork**: Setelah di-*fork*, Anda akan diarahkan ke halaman repositori yang sama, tetapi sekarang berada di akun Anda sendiri. Akan ada informasi yang menunjukkan bahwa repositori ini di-*fork* dari akun mana, sebagai bentuk kredit.

**Catatan**: Ada juga opsi untuk mengedit file secara langsung, yang secara otomatis akan melakukan *fork* jika Anda belum memiliki salinannya. Namun, disarankan untuk menggunakan tombol *fork* untuk proses yang lebih jelas.

## Memodifikasi Repositori yang Sudah Di-fork

Setelah repositori di-*fork* ke akun Anda, Anda dapat memodifikasinya:

1.  **Membuat File Baru**:
    *   Pilih opsi untuk membuat file baru.
    *   Berikan nama file (misalnya, `Sandika-resolusi.txt`).
    *   Tambahkan konten ke dalam file tersebut (misalnya, resolusi pribadi).
    *   **Commit** perubahan dengan pesan yang deskriptif (misalnya, "Membuat file Sandika Resolusi TXT").
2.  **Mengedit File yang Ada**:
    *   Pilih file yang ingin diedit (misalnya, `rencana konten`).
    *   Tambahkan atau ubah konten (misalnya, menambahkan "angular" ke daftar *framework* JavaScript).
    *   **Commit** perubahan dengan pesan yang relevan (misalnya, "Menambahkan angular pada framework JavaScript").
    *   Perubahan ini dilakukan pada *branch* `master` di repositori Anda sendiri.

## Mengusulkan Perubahan (Pull Request)

Setelah melakukan modifikasi pada repositori yang di-*fork*, Anda dapat mengusulkan perubahan tersebut ke repositori asli melalui **Pull Request**:

1.  **Buat Pull Request Baru**: Klik tombol **"New pull request"** di halaman repositori Anda.
2.  **Konfigurasi Pull Request**:
    *   GitHub akan menampilkan perbandingan antara repositori asli (basis) dan repositori Anda (komparasi).
    *   Pastikan Anda mengusulkan perubahan dari *branch* yang benar di repositori Anda ke *branch* yang benar di repositori asli (biasanya `master` ke `master`).
    *   Jika tidak ada konflik, akan muncul pesan "Able to merge".
3.  **Buat Pull Request**: Klik tombol **"Create pull request"**.
4.  **Tambahkan Pesan**: Berikan pesan kepada pemilik repositori asli mengenai perubahan yang Anda usulkan (misalnya, "Halo pak, Saya menambahkan File baru Dan usulan konten baru").
5.  **Kirim Pull Request**: Klik **"Create pull request"** lagi untuk mengirimnya.

Setelah ini, tugas Anda sebagai pengusul perubahan selesai, dan Anda tinggal menunggu apakah *pull request* Anda diterima atau ditolak oleh pemilik repositori asli.

## Menerima dan Menggabungkan Pull Request (Perspektif Pemilik Repositori Asli)

Dari sisi pemilik repositori asli (misalnya, Web Programming Unpas), prosesnya adalah sebagai berikut:

1.  **Menerima Notifikasi Pull Request**: Pemilik repositori akan melihat notifikasi adanya *pull request* baru.
2.  **Melihat Detail Pull Request**: Pemilik dapat melihat siapa yang mengirim *pull request* dan pesan yang disertakan. Mereka juga bisa melihat *commit* apa saja yang dilakukan oleh pengusul.
3.  **Review Perubahan**: Pemilik dapat meninjau perubahan yang diusulkan. Jika diperlukan, mereka bisa mengedit atau memberikan komentar.
4.  **Menggabungkan (Merge) Pull Request**: Jika perubahan dianggap baik dan tidak ada masalah, pemilik dapat **"Merge pull request"**.
5.  **Konfirmasi Merge**: Konfirmasi penggabungan.
6.  **Hasil**: Setelah di-*merge*, file baru atau perubahan akan muncul di repositori asli. Jumlah **kontributor** pada repositori juga akan bertambah, menunjukkan kolaborasi yang terjadi.

Proses ini memungkinkan kolaborasi yang sederhana dan efektif di GitHub, bahkan tanpa menggunakan Git secara lokal.