# GIT MERGE CONFLICT dan Detached HEAD

Video ini membahas secara mendalam tentang **merge conflict** di Git, penyebabnya, dan cara menyelesaikannya secara manual. Selain itu, dijelaskan juga konsep **detached HEAD** yang terjadi ketika berpindah ke sebuah commit tertentu, serta cara mengelola situasi tersebut.

## Merge Conflict

**Merge conflict** terjadi ketika dua *branch* yang berbeda melakukan perubahan pada baris yang sama dalam satu *file* yang sama. Git tidak dapat secara otomatis memutuskan perubahan mana yang harus diambil, sehingga memerlukan intervensi manual untuk menyelesaikannya.

### Penyebab Merge Conflict
Konflik muncul saat dua *branch* (misalnya, `master` dan `dev`) mengubah bagian kode yang sama secara berbeda. Git tidak bisa melakukan *merge* secara otomatis dan memerlukan resolusi manual.

### Skenario Konflik
1.  **Membuat Branch Baru**: Dari *branch* `master`, buat *branch* baru, misalnya `dev`, menggunakan `git branch dev` dan pindah ke *branch* tersebut dengan `git checkout dev`.
2.  **Perubahan di Branch `dev`**:
    *   Ubah tag `H3` menjadi `H1` di `mahasiswa.html`.
    *   Ganti nilai NPM.
    *   Tambahkan paragraf baru.
    *   Simpan perubahan ke *staging area* (`git add .`) dan *commit* (`git commit -m "mengubah file mahasiswa"`).
3.  **Kembali ke Branch `master`**: Pindah kembali ke *branch* `master` dengan `git checkout master`.
4.  **Perubahan di Branch `master` (Konflik)**:
    *   Ubah tag `H3` menjadi `H4` (berbeda dengan `dev` yang menjadi `H1`).
    *   Hapus data mahasiswa yang sebelumnya diubah di `dev`.
    *   Tambahkan paragraf baru dengan teks yang sedikit berbeda.
    *   Simpan perubahan ke *staging area* dan *commit* (`git commit -am "mengubah isi dari file mahasiswa HTML"`).

### Proses Resolusi Konflik
Ketika mencoba menggabungkan `dev` ke `master` (`git merge dev`), Git akan mendeteksi konflik dan menampilkan pesan `Automatic merge failed; fix conflicts and then commit the result`.

1.  **Identifikasi Konflik**: Git akan secara otomatis membuka *file* yang berkonflik di editor teks dan menandai area konflik dengan penanda khusus:
    ```
    <<<<<<< HEAD
    <!-- Perubahan di branch aktif (HEAD, dalam kasus ini master) -->
    =======
    <!-- Perubahan di branch yang akan digabungkan (dev) -->
    >>>>>>> dev
    ```
    *   Bagian antara `<<<<<<< HEAD` dan `=======` adalah perubahan dari *branch* aktif (`master`).
    *   Bagian antara `=======` dan `>>>>>>> dev` adalah perubahan dari *branch* yang akan digabungkan (`dev`).
2.  **Penyelesaian Manual**: Pilih baris kode mana yang ingin dipertahankan dari kedua *branch*. Anda bisa memilih salah satu, menggabungkan keduanya, atau menulis ulang bagian tersebut. Setelah memilih, hapus semua penanda konflik (`<<<<<<< HEAD`, `=======`, `>>>>>>> dev`).
    *   Contoh: Memilih `H4` dari `master`, mempertahankan NPM baru dari `dev`, dan memilih paragraf dari `dev`.
3.  **Simpan dan Commit**: Setelah *file* diselesaikan dan penanda konflik dihapus, simpan *file* tersebut. Kemudian, tambahkan *file* yang sudah dimodifikasi ke *staging area* (`git add .`) dan lakukan *commit* untuk menyelesaikan *merge* (`git commit -m "Merge branch 'dev'"`). Git akan memberikan pesan *commit* *default* yang bisa digunakan.

## Visualisasi Git Graph

Untuk melihat riwayat *commit* dan struktur *branch* secara visual, gunakan perintah `git log --all --decorate --one-line --graph`. Perintah ini dapat di-*alias* menjadi `graph` untuk kemudahan penggunaan.

## Detached HEAD

**Detached HEAD** adalah kondisi di mana pointer `HEAD` tidak menunjuk ke ujung (*tip*) dari sebuah *branch*, melainkan langsung menunjuk ke sebuah *commit* tertentu. Ini terjadi ketika Anda melakukan `git checkout` ke sebuah *commit hash* alih-alih ke nama *branch*.

### Cara Terjadi
Ketika Anda ingin kembali ke keadaan *commit* sebelumnya, Anda dapat menggunakan `git log` untuk menemukan *hash* *commit* yang diinginkan, lalu `git checkout <commit_hash>`.

### Implikasi
Dalam keadaan **detached HEAD**, jika Anda membuat *commit* baru, *commit* tersebut tidak akan menjadi bagian dari *branch* mana pun. Ini berarti *commit* tersebut "mengambang" dan bisa hilang jika Anda berpindah *branch* tanpa membuat *branch* baru dari *commit* tersebut.

### Mengelola Detached HEAD
1.  **Kembali ke Branch**: Untuk kembali ke keadaan normal, cukup `git checkout <nama_branch_yang_ada>`, misalnya `git checkout master`.
2.  **Membuat Branch Baru dari Detached HEAD**: Jika Anda ingin melanjutkan pekerjaan dari *commit* saat ini (dalam keadaan detached HEAD), Anda bisa membuat *branch* baru dari *commit* tersebut.
    *   `git branch <nama_branch_baru>` (misalnya, `git branch test`).
    *   Kemudian, pindah ke *branch* baru tersebut: `git checkout <nama_branch_baru>` (misalnya, `git checkout test`). Sekarang `HEAD` akan menunjuk ke *branch* `test` dan *commit* baru yang Anda buat akan menjadi bagian dari *branch* `test`.