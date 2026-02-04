# Git Remote: Menghubungkan Repositori Lokal dengan GitHub

## Gambaran Umum

Catatan ini membahas konsep **Git Remote**, sebuah fitur penting dalam Git yang memungkinkan repositori lokal terhubung dan berinteraksi dengan repositori duplikat yang disimpan di lokasi lain, seperti GitHub. Pembahasan mencakup definisi, tujuan, jenis-jenis remote, perintah-perintah dasar, serta skenario umum penggunaan Git Remote, termasuk kloning, mendorong repositori lokal ke GitHub, dan menangani konflik penggabungan.

## Apa itu Git Remote?

**Git Remote** adalah duplikat dari repositori Git lokal yang disimpan di lokasi lain, biasanya di internet atau server lain. Tujuan utamanya adalah untuk:
*   **Sinkronisasi**: Memastikan kode yang ada di repositori lokal dan remote selalu mutakhir dan sama.
*   **Kolaborasi**: Memungkinkan beberapa pengembang bekerja pada proyek yang sama dengan berbagi perubahan melalui remote.
*   **Pencadangan (Backup)**: Menyimpan salinan kode di lokasi eksternal untuk keamanan data.

## Jenis-jenis Remote

Meskipun GitHub adalah contoh remote yang paling umum digunakan dalam seri ini, Git Remote dapat terhubung ke berbagai platform dan lokasi lain:
*   **GitHub**: Platform hosting repositori Git berbasis web yang populer.
*   **GitLab**: Alternatif GitHub yang juga menyediakan fitur CI/CD terintegrasi.
*   **Bitbucket**: Platform hosting repositori Git yang mendukung Git dan Mercurial.
*   **Server Lokal atau Komputer Rekan Kerja**: Repositori dapat dihubungkan ke komputer lain dalam jaringan lokal, seperti server kantor atau komputer rekan kerja.
*   **Forked Repository**: Repositori yang di-fork dari repositori orang lain juga dapat menjadi remote untuk repositori lokal Anda.
*   **Folder Lokal Lain**: Bahkan folder lain di komputer yang sama dapat dijadikan remote, meskipun kasus ini jarang digunakan.

## Perintah Dasar Git Remote

Berikut adalah perintah-perintah Git yang esensial saat bekerja dengan remote:

*   `git init`: Menginisialisasi folder lokal sebagai repositori Git baru.
*   `git clone <URL>`: Mengunduh (menduplikat) repositori dari remote ke komputer lokal. Ini secara otomatis menginisialisasi repositori lokal dan menghubungkannya dengan remote.
*   `git remote`: Menampilkan daftar nama remote yang terhubung ke repositori lokal.
*   `git remote -v`: Menampilkan daftar nama remote beserta URL-nya (verbose).
*   `git add <file>` / `git add .`: Menambahkan perubahan dari *working directory* ke *staging area*.
*   `git commit -m "Pesan commit"`: Menyimpan perubahan dari *staging area* ke riwayat repositori lokal.
*   `git push`: Mengirimkan perubahan (commit) dari repositori lokal ke repositori remote.
    *   Saat pertama kali push ke remote baru, gunakan `git push -u origin master` (atau `main`) untuk mengatur *upstream*.
*   `git fetch`: Mengambil informasi perubahan terbaru dari repositori remote tanpa menggabungkannya ke repositori lokal.
*   `git pull`: Mengambil perubahan terbaru dari repositori remote dan secara otomatis menggabungkannya ke repositori lokal.
*   `git status`: Menampilkan status *working directory* dan *staging area*, termasuk informasi tentang status branch lokal relatif terhadap remote.
*   `git log --all --decorate --one-line --graph`: Menampilkan riwayat commit dalam format grafis yang mudah dibaca, termasuk posisi branch lokal dan remote.

### Nama Remote Default: `origin`

Ketika Anda mengkloning repositori dari GitHub, nama remote default yang dibuat secara otomatis adalah `origin`. Nama ini dapat diubah, tetapi `origin` adalah konvensi yang umum.

## Skenario Penggunaan Git Remote

### Skenario 1: Mengkloning Repositori GitHub yang Sudah Ada

Ini adalah skenario ketika Anda ingin mendapatkan salinan repositori yang sudah ada di GitHub ke komputer lokal Anda.

1.  **Buat Repositori di GitHub**:
    *   Masuk ke akun GitHub Anda.
    *   Buat repositori baru (`New repository`).
    *   Berikan nama (misalnya, `WPU-Git-Test`).
    *   **Penting**: Centang opsi `Add a README file` untuk memastikan repositori tidak kosong.
    *   Klik `Create repository`.
2.  **Kloning ke Lokal**:
    *   Di halaman repositori GitHub, klik tombol `Code` (atau `Clone or download`).
    *   Pilih metode `HTTPS` (lebih mudah untuk pemula karena tidak memerlukan konfigurasi SSH key).
    *   Salin URL kloning.
    *   Buka Git Bash (atau terminal) di lokasi di mana Anda ingin menyimpan repositori (misalnya, Desktop).
    *   Jalankan perintah: `git clone <URL_yang_disalin>`.
    *   Repositori akan diunduh dan folder baru akan dibuat di lokasi tersebut, berisi semua file dari GitHub dan sudah terhubung sebagai repositori Git lokal.
3.  **Verifikasi Koneksi Remote**:
    *   Masuk ke folder repositori yang baru dikloning (`cd WPU-Git-Test`).
    *   Jalankan `git remote -v` untuk melihat remote yang terhubung (akan ada `origin` yang menunjuk ke URL GitHub Anda).
    *   Jalankan `git status` untuk melihat status branch lokal Anda (seharusnya `Your branch is up to date with 'origin/master'`).
4.  **Melakukan Perubahan dan Push**:
    *   Buat perubahan pada file di repositori lokal (misalnya, menambahkan `index.html`).
    *   `git add .`
    *   `git commit -m "Menambahkan file index.html"`.
    *   Setelah commit, `git status` akan menunjukkan `Your branch is ahead of 'origin/master' by 1 commit`.
    *   `git push` untuk mengirim perubahan ke GitHub. Anda mungkin diminta login GitHub jika menggunakan HTTPS.
    *   Setelah push berhasil, `git status` akan kembali `up to date`.
    *   Periksa GitHub, file `index.html` akan muncul.

#### Mengatur Informasi Pengguna Git

Penting untuk memastikan `user.name` dan `user.email` Git lokal Anda sesuai dengan akun GitHub Anda agar commit tercatat dengan benar.
*   Periksa konfigurasi: `git config --list`.
*   Atur secara global (berlaku untuk semua repositori di komputer):
    *   `git config --global user.name "Nama Pengguna GitHub Anda"`.
    *   `git config --global user.email "email_github_anda@example.com"`.

### Skenario 2: Mendorong Repositori Lokal yang Sudah Ada ke GitHub

Ini adalah skenario ketika Anda memiliki repositori Git lokal yang sudah berisi commit, dan Anda ingin menyimpannya sebagai repositori baru di GitHub.

1.  **Buat Repositori Lokal**:
    *   Buat folder baru (misalnya, `WPU-Git-Test-2`).
    *   Masuk ke folder tersebut (`cd WPU-Git-Test-2`).
    *   Inisialisasi sebagai repositori Git: `git init`.
    *   Buat beberapa file dan commit di lokal (misalnya, `index.php` dengan beberapa commit).
2.  **Buat Repositori Kosong di GitHub**:
    *   Masuk ke akun GitHub Anda.
    *   Buat repositori baru (`New repository`).
    *   Berikan nama yang sama dengan folder lokal (misalnya, `WPU-Git-Test-2`).
    *   **Penting**: **Jangan** centang opsi `Add a README file` atau inisialisasi lainnya. Biarkan repositori benar-benar kosong.
    *   Klik `Create repository`.
3.  **Hubungkan Lokal ke Remote**:
    *   Setelah repositori kosong dibuat di GitHub, Anda akan melihat halaman "Quick setup" dengan instruksi.
    *   Salin baris perintah untuk menambahkan remote yang ada (biasanya `git remote add origin <URL>`).
    *   Di Git Bash (di dalam folder repositori lokal Anda), jalankan perintah tersebut: `git remote add origin <URL_repositori_GitHub>`.
    *   Verifikasi dengan `git remote -v`.
4.  **Push Perubahan ke GitHub**:
    *   Jalankan perintah: `git push -u origin master` (atau `main` jika branch utama Anda bernama `main`).
        *   Opsi `-u` (atau `--set-upstream`) akan mengatur branch lokal Anda untuk melacak branch remote `origin/master`, sehingga push berikutnya cukup `git push`.
    *   Anda mungkin diminta login GitHub.
    *   Setelah push berhasil, periksa GitHub, file-file dari repositori lokal Anda akan muncul.

### Skenario 3: Menangani Konflik Penggabungan (Merge Conflict)

Konflik terjadi ketika ada perubahan yang bertentangan pada baris kode yang sama di repositori lokal dan remote secara bersamaan.

1.  **Situasi Konflik**:
    *   Anda membuat perubahan dan commit di lokal (misalnya, menambahkan `style.css` dengan `font-family: Arial`).
    *   Secara bersamaan, orang lain (atau Anda sendiri melalui antarmuka GitHub) membuat perubahan pada file yang sama di remote (misalnya, menambahkan `style.css` dengan `font-family: Georgia`).
    *   Anda mencoba `git push`, tetapi push akan ditolak dengan pesan kesalahan karena remote memiliki perubahan yang belum Anda miliki.
2.  **Mendeteksi Perubahan Remote**:
    *   Gunakan `git fetch` untuk mengambil informasi commit terbaru dari remote tanpa menggabungkannya.
    *   `git status` setelah fetch akan menunjukkan `Your branch and 'origin/master' have diverged` (branch Anda dan remote telah bercabang).
    *   `git log --graph` akan menunjukkan dua cabang commit yang berbeda.
3.  **Menggabungkan Perubahan dan Menyelesaikan Konflik**:
    *   Gunakan `git pull` untuk mengambil perubahan dari remote dan mencoba menggabungkannya ke lokal.
    *   Git akan mendeteksi konflik dan menandai bagian yang bertentangan dalam file dengan penanda khusus (misalnya, `<<<<<<< HEAD`, `=======`, `>>>>>>>`).
    *   Buka file yang berkonflik di editor kode Anda. Anda harus secara manual memilih baris kode mana yang ingin Anda pertahankan atau bagaimana Anda ingin menggabungkannya.
    *   Setelah konflik diselesaikan (penanda konflik dihapus dan kode yang benar dipilih), simpan file.
4.  **Commit dan Push Hasil Konflik**:
    *   `git add .` untuk menambahkan file yang telah diselesaikan konfliknya ke *staging area*.
    *   `git commit -m "Mengatasi konflik dan menggabungkan perubahan"`.
    *   `git push` untuk mengirimkan commit gabungan ke remote.
    *   Setelah push berhasil, `git status` akan kembali `up to date`, dan `git log --graph` akan menunjukkan bahwa branch lokal dan remote telah bergabung kembali.