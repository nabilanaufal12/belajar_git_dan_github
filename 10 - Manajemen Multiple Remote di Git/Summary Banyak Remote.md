# Manajemen Multiple Remote di Git

Ketika bekerja dengan Git dan GitHub, seringkali kita perlu berinteraksi dengan lebih dari satu repositori jarak jauh (remote). Konsep **multiple remote** memungkinkan kita untuk menyinkronkan repositori lokal dengan beberapa repositori di GitHub secara bersamaan. Hal ini sangat berguna dalam skenario seperti melakukan *fork* repositori orang lain dan ingin tetap *up-to-date* dengan perubahan di repositori aslinya, atau ketika bekerja dalam tim dengan struktur repositori yang berbeda.

## Studi Kasus: Forking dan Sinkronisasi

Mari kita ambil contoh kasus di mana kita ingin melakukan *fork* repositori orang lain dan menjaga agar repositori lokal, repositori *fork* di akun kita, dan repositori asli tetap sinkron.

1.  **Fork Repositori Asli**:
    *   Misalnya, kita tertarik pada repositori `Simple Landing Page` milik Sandika Gali.
    *   Dengan melakukan **fork**, kita membuat duplikat repositori tersebut ke akun GitHub kita sendiri (misalnya, akun Web Programming Unpass).
    *   Sekarang ada dua repositori di GitHub: yang asli di akun Sandika Gali, dan duplikatnya di akun Web Programming Unpass.

2.  **Kloning Repositori Fork ke Lokal**:
    *   Selanjutnya, kita akan mengkloning repositori yang sudah di-*fork* (yang ada di akun Web Programming Unpass) ke komputer lokal kita.
    *   Gunakan perintah `git clone <URL_repositori_fork>`.
    *   Setelah kloning selesai, jika kita memeriksa remote menggunakan `git remote -v`, kita akan melihat bahwa hanya ada satu remote bernama **origin**, yang menunjuk ke repositori *fork* di akun Web Programming Unpass.
    *   Pada tahap ini, repositori lokal kita hanya terhubung ke repositori *fork* kita sendiri. Kita tidak akan tahu jika ada perubahan di repositori asli Sandika Gali.

## Menambahkan Remote Baru (Repositori Asli)

Agar repositori lokal kita bisa mengetahui perubahan dari repositori asli, kita perlu menambahkan repositori asli tersebut sebagai remote baru.

1.  **Perintah untuk Menambahkan Remote**:
    *   Gunakan perintah `git remote add <nama_remote_baru> <URL_repositori_asli>`.
    *   Pilih nama remote yang deskriptif, misalnya `SandikaGali` untuk repositori asli.
    *   Contoh: `git remote add SandikaGali https://github.com/SandikaGali/Simple-Landing-Page.git`.

2.  **Verifikasi Remote**:
    *   Setelah menambahkan, periksa kembali dengan `git remote -v`.
    *   Sekarang akan terlihat dua remote: **origin** (menunjuk ke repositori *fork* kita) dan **SandikaGali** (menunjuk ke repositori asli).

## Sinkronisasi Awal dengan Remote Asli

Meskipun kita sudah menambahkan remote asli, riwayat *commit* dari remote asli belum tentu ada di repositori lokal kita.

1.  **Melihat Status Awal**:
    *   Jika kita menggunakan `git graph`, mungkin hanya akan terlihat *branch* lokal dan *branch* dari remote **origin**.
    *   *Branch* dari remote `SandikaGali` belum terlihat.

2.  **Mengambil Riwayat Commit**:
    *   Untuk mengambil riwayat *commit* dari remote baru ke repositori lokal, gunakan perintah `git fetch <nama_remote>`.
    *   Contoh: `git fetch SandikaGali`.
    *   Setelah *fetch*, `git graph` akan menunjukkan bahwa semua *branch* (lokal, origin, dan SandikaGali) berada pada *commit* yang sama, menandakan sinkronisasi awal berhasil.

## Menangani Perubahan dari Remote Asli

Skenario selanjutnya adalah ketika repositori asli (milik Sandika Gali) mengalami perubahan, dan kita ingin repositori lokal serta repositori *fork* kita juga *up-to-date* dengan perubahan tersebut.

1.  **Perubahan pada Repositori Asli**:
    *   Misalnya, Sandika Gali mengubah warna tombol di `Simple Landing Page` dan mendorong perubahan tersebut ke repositori aslinya.

2.  **Mendeteksi Perubahan**:
    *   Pada repositori lokal kita, `git status` mungkin masih menunjukkan "up to date" karena belum ada komunikasi dengan remote asli.
    *   Untuk mendeteksi perubahan dari remote asli, kita harus melakukan `git fetch <nama_remote_asli>` lagi.
    *   Contoh: `git fetch SandikaGali`.
    *   Setelah *fetch*, `git graph` akan menunjukkan bahwa *branch* `SandikaGali/master` (atau nama *branch* utama lainnya) berada satu *commit* di depan *branch* lokal kita.

3.  **Menggabungkan Perubahan ke Lokal**:
    *   Untuk menggabungkan perubahan dari remote asli ke *branch* lokal kita, gunakan perintah `git merge <nama_remote_asli>/<nama_branch>`.
    *   Contoh: `git merge SandikaGali/master`.
    *   Setelah *merge*, *branch* lokal kita akan sinkron dengan *branch* `SandikaGali/master`.

4.  **Mendorong Perubahan ke Repositori Fork**:
    *   Meskipun repositori lokal sudah *up-to-date*, repositori *fork* kita di GitHub (Web Programming Unpass) belum berubah.
    *   Untuk memperbarui repositori *fork*, kita perlu mendorong perubahan dari lokal ke remote **origin**.
    *   Gunakan perintah `git push -u origin master`.
    *   Setelah *push*, semua repositori (lokal, *fork* di GitHub, dan asli di GitHub) akan kembali sinkron.

## Ringkasan Alur Kerja Sinkronisasi

Berikut adalah langkah-langkah umum untuk menjaga sinkronisasi antara repositori lokal, *fork*, dan asli:

1.  **Kloning** repositori *fork* Anda.
2.  **Tambahkan** remote untuk repositori asli: `git remote add <nama_remote_asli> <URL_repositori_asli>`.
3.  **Ambil** riwayat *commit* dari remote asli: `git fetch <nama_remote_asli>`.
4.  **Gabungkan** perubahan dari remote asli ke *branch* lokal Anda: `git merge <nama_remote_asli>/<nama_branch>`.
5.  **Dorong** perubahan dari lokal ke repositori *fork* Anda: `git push -u origin master`.

Proses ini memastikan bahwa Anda selalu dapat mengikuti perkembangan dari repositori asli sambil tetap memiliki salinan *fork* Anda sendiri. Di video selanjutnya, akan dibahas skenario sebaliknya, yaitu bagaimana mengusulkan perubahan dari repositori *fork* ke repositori asli melalui **Pull Request**.