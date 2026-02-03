# Bekerja dengan Git Secara Lokal

## Gambaran Umum

Catatan ini membahas dasar-dasar penggunaan Git secara lokal di komputer, mulai dari instalasi hingga perintah-perintah dasar untuk mengelola proyek. Git adalah sistem kontrol versi yang penting bagi pengembang, memungkinkan pelacakan perubahan kode secara efisien. Meskipun GitHub menyediakan antarmuka web untuk Git, fokus utama di sini adalah implementasi Git langsung melalui konsol atau *command prompt*.

## Pengenalan Git

*   **Apa itu Git?**
    Git adalah perangkat lunak yang digunakan untuk sistem kontrol versi. Berbeda dengan GitHub yang merupakan platform berbasis web, Git adalah alat yang diinstal dan dijalankan secara lokal di komputer Anda.
*   **Pentingnya Git**
    Kemampuan menggunakan Git telah menjadi **keterampilan wajib** di industri IT, bahkan untuk perusahaan-perusahaan besar yang menggunakannya untuk mengelola *source code* mereka.
*   **Git Client (GUI)**
    Selain menggunakan konsol, Git juga memiliki *client* berbasis GUI (Graphical User Interface) seperti SourceTree atau bahkan GitHub Desktop. Namun, disarankan untuk mempelajari Git melalui konsol terlebih dahulu untuk memahami cara kerjanya secara mendalam sebelum beralih ke GUI.
*   **Sumber Belajar Tambahan**
    Semua materi yang dibahas dalam video ini, dan bahkan lebih banyak lagi, tersedia dalam *e-book* gratis yang sangat direkomendasikan bernama **ProGit**. *E-book* ini dapat diunduh dari situs web Git dan tersedia juga versi bahasa Indonesianya.

## Instalasi Git

1.  **Mengunjungi Situs Web Git**
    Unduh perangkat lunak Git dari `git-scm.com`. Situs ini akan secara otomatis mendeteksi sistem operasi Anda (Windows, macOS, Linux) dan menawarkan unduhan yang sesuai.
2.  **Proses Instalasi (Contoh di Windows)**
    *   Jalankan *installer* yang telah diunduh.
    *   Ikuti langkah-langkah instalasi standar (persetujuan lisensi, lokasi penyimpanan).
    *   **Git Bash**: Selama instalasi di Windows, Git akan secara otomatis menyertakan **Git Bash**, sebuah terminal khusus untuk Git yang dapat menerima perintah *bash* atau *shell command*. Ini penting karena *command prompt* bawaan Windows tidak dapat menerima perintah *shell* secara *default*.
    *   **Pilih Editor Teks Default**: Anda akan diminta untuk memilih editor teks default yang akan digunakan Git, misalnya Vim (default), Sublime Text, atau Visual Studio Code.
    *   **Pilih Lingkungan Penggunaan Git**: Anda dapat memilih apakah Git hanya akan digunakan di Git Bash, atau juga di *command prompt* bawaan sistem Anda. Disarankan untuk memilih opsi yang memungkinkan penggunaan di *command prompt* juga.
    *   Lanjutkan dengan pengaturan *default* lainnya hingga instalasi selesai.
3.  **Verifikasi Instalasi**
    Setelah instalasi, buka Git Bash atau *command prompt* Anda.
    *   Ketik `git` dan tekan Enter. Jika instalasi berhasil, akan muncul daftar perintah bantuan Git.
    *   Ketik `git --version` untuk melihat versi Git yang terinstal.
    *   Sebelum instalasi, perintah `git` tidak akan dikenali di *command prompt*. Setelah instalasi, *command prompt* Anda juga akan dapat menjalankan perintah Git.

## Konsep Dasar Git: Tiga Area

Setelah Git terinstal dan Anda membuat sebuah *repository* (repo), Git akan mengenali tiga area utama:

1.  **Working Tree** (atau *Working Directory*)
    Ini adalah folder tempat Anda bekerja dan menyimpan file-file proyek Anda. Ini adalah area di mana Anda membuat, mengedit, dan menghapus file seperti biasa.
2.  **Staging Area** (atau *Index*)
    Area ini berfungsi sebagai "keranjang belanja" untuk perubahan yang ingin Anda simpan. Ketika Anda melakukan perubahan pada file di *working tree*, Anda harus secara eksplisit "menambahkan" perubahan tersebut ke *staging area* sebelum dapat di-*commit*. Ini memungkinkan Anda untuk memilih perubahan mana yang akan disertakan dalam *commit* berikutnya.
3.  **History** (atau *Repository*)
    Ini adalah tempat di mana semua *commit* (rekaman perubahan) disimpan secara permanen. Setiap *commit* memiliki ID unik dan mencatat riwayat perubahan proyek Anda.

*   **Folder `.git`**
    Dua area terakhir (Staging Area dan History) disimpan dalam sebuah folder tersembunyi bernama `.git` di dalam *root directory* proyek Anda. Folder ini dibuat secara otomatis saat Anda menginisialisasi sebuah *repository* Git (`git init`). Anda tidak perlu memanipulasi isinya secara langsung.

## Perintah Dasar Git dan Alur Kerja

Berikut adalah alur kerja dasar menggunakan Git dengan contoh praktis:

### 1. Menginisialisasi Repository (`git init`)

*   **Tujuan**: Mengubah folder biasa menjadi *repository* Git, sehingga Git dapat mulai melacak perubahan di dalamnya.
*   **Langkah-langkah**:
    1.  Buka Git Bash atau terminal Anda.
    2.  Navigasi ke folder proyek Anda menggunakan perintah `cd` (change directory).
        *   `pwd` (print working directory) untuk melihat lokasi saat ini.
        *   `ls` untuk melihat isi folder.
        *   Contoh: `cd Desktop/wpu-tesrepo`.
    3.  Di dalam folder proyek, ketik `git init`.
    4.  Setelah berhasil, akan muncul pesan `Initialized empty Git repository in ...` dan nama *branch* default (misalnya `master`) akan muncul di terminal Anda.
    5.  Secara otomatis, folder tersembunyi `.git` akan dibuat di dalam folder proyek Anda.

### 2. Memeriksa Status Repository (`git status`)

*   **Tujuan**: Melihat status *working tree* dan *staging area* Anda. Ini akan menunjukkan file mana yang baru, dimodifikasi, atau dihapus, dan mana yang sudah di-*stage* atau belum.
*   **Contoh**:
    *   Setelah membuat file `index.html` di *working tree*.
    *   Ketik `git status`. Git akan melaporkan bahwa ada file `index.html` yang **untracked** (belum dilacak) dan berwarna merah.

### 3. Menambahkan File ke Staging Area (`git add`)

*   **Tujuan**: Memindahkan perubahan dari *working tree* ke *staging area*, menandakan bahwa perubahan ini siap untuk di-*commit*.
*   **Langkah-langkah**:
    *   Untuk menambahkan satu file: `git add index.html`.
    *   Untuk menambahkan semua perubahan (file baru, modifikasi, penghapusan) di *working tree* ke *staging area*: `git add .`.
*   **Verifikasi**: Setelah `git add`, ketik `git status` lagi. File yang sebelumnya `untracked` atau `modified` akan berubah menjadi hijau dan tercantum sebagai `Changes to be committed`.

### 4. Mengkonfigurasi Identitas Pengguna (`git config`)

*   **Tujuan**: Sebelum melakukan *commit* pertama, Git perlu tahu siapa yang melakukan *commit* tersebut (nama dan *email*). Informasi ini akan disertakan dalam setiap *commit*.
*   **Langkah-langkah**:
    1.  Atur nama pengguna: `git config --global user.name "Nama Anda"`.
        *   Disarankan untuk menggunakan nama yang sama dengan akun GitHub Anda.
    2.  Atur *email* pengguna: `git config --global user.email "emailanda@example.com"`.
    *   Parameter `--global` berarti konfigurasi ini akan berlaku untuk semua *repository* Git di komputer Anda.

### 5. Melakukan Commit (`git commit`)

*   **Tujuan**: Menyimpan perubahan yang ada di *staging area* ke dalam *history* *repository* Anda sebagai satu unit perubahan yang koheren.
*   **Langkah-langkah**:
    1.  **Dengan Pesan Singkat**: `git commit -m "Pesan commit Anda"`.
        *   Pesan *commit* harus deskriptif tentang perubahan yang dilakukan.
    2.  **Tanpa Pesan (`git commit`)**: Jika Anda hanya mengetik `git commit` tanpa `-m`, Git akan membuka editor teks default Anda (misalnya Vim) untuk menulis pesan *commit*.
        *   **Keluar dari Vim**: Jika Anda tidak terbiasa dengan Vim, tekan `Esc`, lalu ketik `:q!` dan tekan Enter untuk keluar tanpa menyimpan.
*   **Verifikasi**: Setelah *commit*, Git akan menampilkan informasi *commit* (ID *hash*, *branch*, pesan, jumlah file/baris yang berubah). Ketik `git status` lagi, dan akan muncul `nothing to commit, working tree clean`.

### 6. Melihat Riwayat Commit (`git log`)

*   **Tujuan**: Menampilkan daftar semua *commit* yang telah dilakukan di *repository*.
*   **Perintah**:
    *   `git log`: Menampilkan semua *commit* secara lengkap (ID *hash*, penulis, tanggal, pesan).
    *   `git log -<n>`: Menampilkan `<n>` *commit* terakhir. Contoh: `git log -3`.
    *   `git log -- <file>`: Menampilkan *commit* yang terkait dengan perubahan pada file tertentu. Contoh: `git log -- style.css`.

### 7. Mengembalikan Perubahan File (`git checkout`)

*   **Tujuan**: Mengembalikan satu atau lebih file ke keadaan pada *commit* tertentu.
*   **Langkah-langkah**:
    1.  Identifikasi *commit hash* dari *commit* yang ingin Anda kembalikan. Anda bisa melihatnya dari `git log`.
    2.  Ketik `git checkout <5-7_digit_commit_hash> -- <nama_file>`.
        *   Contoh: `git checkout 7667B -- style.css` (mengembalikan file `style.css` ke keadaan pada *commit* yang diawali dengan `7667B`).
    3.  Setelah perintah ini, file akan kembali muncul di *working tree* Anda dan akan terdeteksi sebagai `modified` atau `untracked` oleh `git status`. Anda perlu `git add` dan `git commit` lagi untuk menyimpan pengembalian ini sebagai *commit* baru.

## Contoh Alur Kerja Lengkap

1.  **Inisialisasi Repo dan Commit Pertama**
    *   Buat folder `wpu-tesrepo`.
    *   `cd wpu-tesrepo`.
    *   `git init`.
    *   Buat file `index.html` dengan konten sederhana.
    *   `git status` (akan menunjukkan `index.html` sebagai `untracked`).
    *   `git add index.html`.
    *   `git commit -m "Menambahkan file index.html"`.
    *   `git status` (akan menunjukkan `nothing to commit`).

2.  **Modifikasi dan Commit Kedua**
    *   Edit `index.html` (tambahkan `<h1>Hello World</h1>`).
    *   Buat file `style.css` dengan konten sederhana.
    *   Hubungkan `style.css` ke `index.html`.
    *   `git status` (akan menunjukkan `index.html` sebagai `modified` dan `style.css` sebagai `untracked`).
    *   `git add .` (menambahkan semua perubahan).
    *   `git commit -m "Mengubah file index dan menambahkan file style.css"`.

3.  **Perubahan Kompleks dan Commit Ketiga**
    *   Edit `index.html` (hapus *link* ke `style.css`, tambahkan *inline style* `<style>`).
    *   Hapus file `style.css`.
    *   Buat file `script.js` dan hubungkan ke `index.html`.
    *   `git status` (akan menunjukkan `index.html` sebagai `modified`, `style.css` sebagai `deleted`, dan `script.js` sebagai `untracked`).
    *   `git add .`.
    *   `git commit -m "Menyesuaikan styling dan menambahkan script.js"`.

4.  **Melihat Log dan Mengembalikan File**
    *   `git log` (akan menampilkan ketiga *commit* Anda).
    *   `git log -- style.css` (akan menunjukkan *commit* saat `style.css` ditambahkan dan dihapus).
    *   `git checkout <commit_hash_saat_style.css_ada> -- style.css` (mengembalikan `style.css`).
    *   `git status` (akan menunjukkan `style.css` sebagai `new file`).
    *   `git add style.css`.
    *   `git commit -m "Mengembalikan style CSS"`.

Dengan memahami dan mempraktikkan perintah-perintah ini, Anda dapat secara efektif mengelola perubahan pada proyek Anda menggunakan Git secara lokal.