# Bekerja dengan GitHub: Membuat Akun dan Repositori

## Pendahuluan GitHub

Video ini adalah bagian kedua dari seri Git dan GitHub, berfokus pada pengenalan GitHub. Asumsi dasarnya adalah pengguna belum memiliki akun GitHub, sehingga akan dipandu mulai dari pembuatan akun hingga pengelolaan repositori dasar.

## Membuat Akun GitHub

Untuk memulai menggunakan GitHub, langkah pertama adalah membuat akun:

1.  **Kunjungi Situs GitHub**: Buka peramban web dan navigasi ke `github.com`.
2.  **Proses Pendaftaran (Sign Up)**:
    *   Isi kolom pendaftaran yang tersedia atau klik tombol "Sign up" di kanan atas.
    *   Masukkan data yang diminta seperti nama pengguna, alamat email, dan kata sandi.
    *   Lakukan verifikasi akun, biasanya berupa captcha atau teka-teki visual.
    *   Pilih paket yang diinginkan. GitHub menawarkan versi **gratis** dan **berbayar**.
        *   Versi gratis memungkinkan pembuatan repositori **private** atau **public**. Namun, repositori private hanya boleh memiliki maksimal tiga kolaborator.
        *   Versi berbayar menawarkan fleksibilitas lebih dalam jumlah kolaborator.
    *   Isi informasi profil tambahan, seperti level pengalaman pemrograman, tujuan penggunaan GitHub (misalnya, untuk pengembangan), dan peran (misalnya, pelajar).
    *   **Verifikasi Email**: Setelah pendaftaran, buka email yang didaftarkan dan klik tautan verifikasi email.
    *   Setelah verifikasi, Anda dapat langsung masuk ke akun GitHub Anda.

## Membuat Repositori Baru

**Repositori** adalah folder tempat kita menyimpan proyek atau kode kita. Di GitHub, repositori ini berada di *cloud* dan dapat diakses secara publik atau privat.

Ada dua cara utama untuk membuat repositori baru:

1.  Klik "Start a project" di halaman utama setelah login.
2.  Klik ikon tanda tambah (+) di kanan atas halaman, lalu pilih "New repository".

Setelah memilih salah satu opsi, Anda akan diarahkan ke halaman pembuatan repositori dengan beberapa pengaturan:

*   **Nama Repositori**: Berikan nama yang deskriptif untuk proyek Anda. Penting untuk diingat bahwa nama repositori tidak boleh mengandung spasi; spasi akan otomatis diganti dengan tanda hubung (`-`). Contoh: `wpu-resolusi`.
*   **Deskripsi (Opsional)**: Tambahkan deskripsi singkat tentang tujuan repositori.
*   **Visibilitas**:
    *   **Public**: Repositori dapat dilihat oleh siapa saja.
    *   **Private**: Repositori hanya dapat dilihat oleh Anda dan kolaborator yang Anda undang. Untuk akun gratis, repositori private dibatasi hingga tiga kolaborator.
*   **Initialize this repository with a README**:
    *   **README** adalah file penting yang biasanya berisi penjelasan tentang proyek, cara instalasi, atau panduan penggunaan singkat.
    *   Jika Anda mencentang opsi ini, GitHub akan secara otomatis membuat file README default untuk Anda.
    *   Jika tidak dicentang, Anda dapat mengunggah file README Anda sendiri nanti.
*   **Git ignore & License**: Untuk saat ini, opsi ini dapat diabaikan.

Setelah semua pengaturan selesai, klik "Create repository". Repositori Anda akan dibuat, dan Anda akan melihat URL unik untuk repositori tersebut (misalnya, `github.com/username/nama-repositori`). File README (jika dibuat) akan otomatis ditampilkan di halaman utama repositori.

## Membuat dan Mengedit File di GitHub

Anda dapat membuat dan mengedit file langsung di antarmuka web GitHub tanpa perlu mengunduh repositori ke komputer lokal Anda.

### Membuat File Baru

1.  Di halaman repositori Anda, klik tombol "Create new file".
2.  Beri nama file, termasuk ekstensinya (contoh: `wpu-resolusi.txt`).
3.  Tulis konten file di area editor yang disediakan.
4.  Setelah selesai, *scroll* ke bawah untuk melakukan **commit**.

### Melakukan Commit

Setiap kali Anda selesai membuat atau mengubah file, Anda harus "commit" perubahan tersebut. **Commit** adalah tindakan menyimpan perubahan ke riwayat repositori.

1.  **Pesan Commit**: Tulis pesan yang jelas dan ringkas yang menjelaskan perubahan apa yang Anda lakukan. Contoh: "Membuat file resolusi.txt".
2.  Anda dapat menambahkan deskripsi commit yang lebih detail di area teks di bawahnya jika diperlukan.
3.  Pilih opsi commit: "Commit directly to the master branch" (menyimpan langsung ke cabang utama) atau "Create a new branch for this commit" (membuat cabang baru). Untuk saat ini, pilih opsi pertama.
4.  Klik "Commit new file".

File Anda sekarang tersimpan di repositori.

### Mengedit File yang Sudah Ada

1.  Di halaman repositori, klik pada file yang ingin Anda edit.
2.  Klik tombol "Edit this file" (ikon pensil) di kanan atas tampilan file.
3.  Lakukan perubahan yang diinginkan pada konten file.
4.  Setelah selesai, lakukan **commit** lagi dengan pesan yang menjelaskan perubahan yang baru saja Anda buat (contoh: "Menambahkan merch shop dan kolaborasi").

## Melihat Riwayat Perubahan (History)

GitHub melacak semua perubahan yang terjadi pada repositori Anda.

### Riwayat File Spesifik

1.  Untuk melihat riwayat perubahan pada satu file tertentu, klik file tersebut.
2.  Kemudian, klik tombol "History" di bagian atas tampilan file.
3.  Anda akan melihat daftar semua *commit* yang memengaruhi file tersebut.
4.  Saat melihat detail *commit*, perubahan akan ditandai: baris yang ditambahkan akan berwarna hijau dengan tanda `+`, dan baris yang dihapus akan berwarna merah dengan tanda `-`.

### Riwayat Repositori Keseluruhan

1.  Untuk melihat semua *commit* yang terjadi di seluruh repositori (termasuk perubahan pada banyak file), kembali ke halaman utama repositori.
2.  Klik "Commits" di bagian atas halaman.
3.  Ini akan menampilkan daftar semua *commit* yang pernah dilakukan pada repositori, beserta pesan *commit* dan siapa yang melakukannya.
4.  Setiap *commit* memiliki **hash** unik (serangkaian karakter alfanumerik) yang digunakan Git untuk melacak perubahan.

## Visualisasi Perubahan (Network Graph)

GitHub juga menyediakan cara visual untuk melihat riwayat perubahan, terutama berguna dalam kolaborasi tim.

1.  Di halaman repositori, navigasikan ke tab "Insights".
2.  Pilih "Network".
3.  Anda akan melihat grafik visual (berupa titik-titik dan garis) yang menunjukkan *commit*, *branch* (cabang), dan *merge* (penggabungan) yang terjadi di repositori. Ini membantu memahami alur kerja dan kontribusi dalam tim.

## Kesimpulan

Video ini telah membahas langkah-langkah dasar untuk membuat akun GitHub, membuat repositori, membuat dan mengedit file langsung di GitHub, serta melacak riwayat perubahan menggunakan *commit* dan fitur *history*. Pemahaman istilah-istilah dasar Git yang dibahas di video sebelumnya akan membantu dalam penggunaan GitHub. Video selanjutnya akan membahas konsep *branch* atau cabang dalam Git.