# Git Branch & Merge: Manajemen Alur Kerja Kode Lokal

## Pendahuluan

Catatan ini membahas konsep dasar dan implementasi Git Branch dan Merge pada repositori lokal. Git Branch memungkinkan pengembangan fitur secara terpisah tanpa memengaruhi kode utama, sementara Git Merge digunakan untuk menggabungkan perubahan dari satu cabang ke cabang lainnya. Pemahaman tentang kedua konsep ini sangat penting untuk manajemen proyek yang efektif, baik secara individu maupun dalam tim.

## 1. Konsep Dasar Git Branch

**Branch** adalah "cabang bebas dari komit-komit kita". Ini memungkinkan pengembang untuk membuat jalur pengembangan terpisah dari jalur utama proyek.

### 1.1 Mengapa Menggunakan Branch?

Penggunaan branch sangat dianjurkan dalam skenario berikut:
*   **Pengembangan Fitur Baru**: Ketika ingin menambahkan fitur baru tetapi belum yakin dengan implementasinya atau tidak ingin mengganggu stabilitas kode utama.
*   **Kerja Tim/Kolaborasi**: Memungkinkan beberapa pengembang bekerja pada bagian proyek yang berbeda secara bersamaan tanpa saling menimpa pekerjaan.

### 1.2 Cara Kerja Branch di Git

Setiap **commit** memiliki identifikasi unik berupa **hash**, nama pengguna, email, dan stempel waktu. Commit ini terhubung ke sebuah branch, sehingga Git mengetahui commit mana yang terkait dengan branch tertentu.

*   **Branch `master`**: Secara *default*, nama branch utama yang dibuat oleh Git adalah `master`.
*   **Pointer `HEAD`**: Git menggunakan pointer `HEAD` untuk menunjukkan branch yang sedang aktif. Ini membantu Git mengetahui branch mana yang sedang dikerjakan saat ini, terutama jika ada banyak branch dalam repositori.

Ketika sebuah commit baru dibuat, `HEAD` dan pointer branch yang aktif akan ikut maju ke commit terbaru tersebut.

## 2. Mengelola Branch

### 2.1 Inisialisasi Repositori

Untuk memulai, buat folder baru (misalnya, `wpu-test-repo-2`) dan inisialisasi sebagai repositori Git:
```bash
git init
```
Secara *default*, repositori akan berada di branch `master`.

### 2.2 Membuat Commit Awal

1.  Buat file baru (misalnya, `mahasiswa.html`).
2.  Periksa status file: `git status`. File baru akan berstatus `untracked`.
3.  Tambahkan file ke *staging area*: `git add .` (untuk semua file baru/modifikasi) atau `git add mahasiswa.html` (untuk file spesifik).
4.  Buat commit pertama: `git commit -m "menambahkan file mahasiswa"`.
5.  Untuk perubahan pada file yang sudah di-track, bisa langsung commit dengan `git commit -am "menambahkan data satu mahasiswa"`.

### 2.3 Membuat Branch Baru

Untuk membuat branch baru dari commit saat ini, gunakan perintah `git branch <nama_branch>`.
*   Contoh: `git branch dosen` dan `git branch staff`.
*   Hasilnya, branch baru akan menunjuk ke commit yang sama dengan branch saat ini.

### 2.4 Melihat Daftar Branch

Untuk melihat semua branch yang ada dan branch yang aktif, gunakan `git branch`.
*   Branch aktif akan ditandai dengan warna hijau dan tanda bintang (`*`) di sebelah kirinya.

### 2.5 Berpindah Antar Branch (`git checkout`)

Untuk berpindah ke branch lain, gunakan `git checkout <nama_branch>`.
*   Contoh: `git checkout dosen`.
*   Ketika berpindah branch, pointer `HEAD` akan ikut berpindah.
*   **Penting**: Git akan secara otomatis mengubah isi direktori kerja Anda sesuai dengan kondisi branch yang dipilih. File-file yang ada di branch sebelumnya tetapi tidak ada di branch baru akan hilang sementara, dan sebaliknya.

### 2.6 Menambahkan Commit pada Branch Baru

Setelah berpindah ke branch baru (misalnya `dosen`), Anda dapat membuat perubahan dan commit seperti biasa.
1.  Buat file baru (misalnya, `dosen.html`).
2.  Tambahkan dan commit perubahan:
    ```bash
    git add .
    git commit -m "menambahkan file dosen"
    ```
3.  Ulangi langkah yang sama untuk branch `staff`:
    *   `git checkout staff`
    *   Buat `staff.html`
    *   `git add .`
    *   `git commit -m "menambahkan file atau fitur staff"`

### 2.7 Visualisasi Sejarah Branch

Untuk melihat sejarah commit dan struktur branch dalam bentuk grafis, gunakan perintah berikut:
```bash
git log --all --decorate --oneline --graph
```

Untuk mempermudah, Anda bisa membuat alias (nama panggilan) untuk perintah panjang ini:
```bash
alias grab="git log --all --decorate --oneline --graph"
```
Setelah alias dibuat, cukup ketik `grab` untuk melihat visualisasi.

## 3. Menggabungkan Branch (`git merge`)

**Merge** adalah proses menggabungkan perubahan dari satu branch ke branch lain. Ada dua jenis merge utama:

### 3.1 Fast-Forward Merge

Terjadi ketika branch yang akan digabungkan berada dalam "jalur langsung" (direct path) dari branch target. Artinya, tidak ada commit baru di branch target sejak branch yang akan digabungkan dibuat.

*   **Cara Kerja**: Git hanya akan memindahkan pointer branch target ke commit terbaru dari branch yang digabungkan. Tidak ada commit merge baru yang dibuat.
*   **Contoh**: Menggabungkan branch `dosen` ke `master` (asumsi `master` tidak memiliki commit baru setelah `dosen` dibuat).
    1.  Pastikan Anda berada di branch target (`master`): `git checkout master`.
    2.  Lakukan merge: `git merge dosen`.
    3.  Git akan menampilkan pesan "Fast-forward".
    4.  Verifikasi: File `dosen.html` sekarang akan muncul di branch `master`.

### 3.2 3-Way Merge (Merge Commit)

Terjadi ketika branch yang akan digabungkan dan branch target telah "bercabang" (diverged), yaitu keduanya memiliki commit baru yang tidak ada di branch lain sejak titik percabangan.

*   **Cara Kerja**: Git akan membuat commit baru, yang disebut "merge commit", yang menggabungkan perubahan dari kedua branch. Merge commit ini memiliki dua *parent* (commit terakhir dari kedua branch yang digabungkan).
*   **Contoh**: Menggabungkan branch `staff` ke `master` (setelah `master` sudah memiliki perubahan dari `dosen`).
    1.  Pastikan Anda berada di branch target (`master`): `git checkout master`.
    2.  Lakukan merge: `git merge staff`.
    3.  Karena ini adalah 3-Way Merge, Git akan membuka editor teks (seperti Vim atau VS Code) untuk meminta pesan commit untuk merge commit yang baru.
    4.  Simpan dan keluar dari editor (misalnya, di Vim: tekan `Esc`, lalu ketik `:wq!` dan `Enter`).
    5.  Git akan menampilkan pesan bahwa merge dilakukan menggunakan strategi rekursif.
    6.  Verifikasi: File `staff.html` sekarang akan muncul di branch `master`, dan `grab` akan menunjukkan commit merge baru.

## 4. Menghapus Branch

Setelah branch berhasil digabungkan ke branch utama dan tidak lagi diperlukan, Anda dapat menghapusnya.

### 4.1 Melihat Branch yang Sudah Digabungkan

Untuk melihat branch mana saja yang sudah berhasil digabungkan ke branch saat ini, gunakan:
```bash
git branch --merged
```

### 4.2 Menghapus Branch yang Sudah Digabungkan

Gunakan opsi `-d` (huruf kecil) untuk menghapus branch yang sudah digabungkan:
```bash
git branch -d <nama_branch>
```
*   Contoh: `git branch -d dosen`.
*   Git akan menolak menghapus branch jika belum digabungkan untuk mencegah kehilangan pekerjaan.

### 4.3 Menghapus Branch Secara Paksa

Jika Anda ingin menghapus branch yang belum digabungkan (misalnya, karena fitur dibatalkan), gunakan opsi `-D` (huruf besar):
```bash
git branch -D <nama_branch>
```
*   **Perhatian**: Menggunakan `-D` akan menghapus branch tanpa peduli apakah perubahannya sudah digabungkan atau belum, berpotensi menyebabkan kehilangan data jika belum di-merge.

Dengan memahami dan menguasai Git Branch dan Merge, Anda dapat mengelola alur kerja pengembangan kode dengan lebih efisien dan terstruktur.