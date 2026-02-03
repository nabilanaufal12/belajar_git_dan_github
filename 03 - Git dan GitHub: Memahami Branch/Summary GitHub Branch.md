# Git dan GitHub: Memahami Branch

## Overview
Video ini menjelaskan konsep **branch** dalam Git dan GitHub, sebuah fitur fundamental untuk pengembangan perangkat lunak yang memungkinkan pengerjaan fitur baru atau eksperimen tanpa mengganggu jalur utama proyek. Pembahasan mencakup definisi, tujuan, cara membuat, mengelola, hingga menggabungkan branch, serta mengatasi konflik yang mungkin terjadi.

## Konsep Dasar Branch
### Definisi Branch
**Branch** (cabang) adalah jalur pengembangan independen dari sebuah komit. Ini memungkinkan Anda membuat "snapshot" dari repositori tanpa mengganggu jalur utama atau *Master branch*.

### Tujuan dan Manfaat Branching
Penggunaan branch sangat penting untuk:
*   **Pengembangan Fitur Eksperimental**: Membuat fitur baru yang belum tentu akan diimplementasikan. Jika fitur tidak jadi, branch bisa dihapus tanpa memengaruhi proyek utama.
*   **Kolaborasi Tim**: Memungkinkan beberapa anggota tim mengerjakan bagian berbeda dari proyek secara bersamaan pada branch masing-masing.
*   **Isolasi Perubahan**: Setiap perubahan yang dilakukan pada sebuah branch tidak akan memengaruhi branch lain sampai digabungkan.

### Master Branch
**Master branch** (atau di GitHub sekarang sering disebut `main` branch) adalah cabang utama atau *default* yang dibuat secara otomatis oleh Git. Ini adalah jalur utama pengembangan proyek.

## Alur Kerja Branching di GitHub
### Membuat Branch Baru
Ada dua cara utama untuk membuat branch baru di GitHub:
1.  **Saat Melakukan Commit**: Ketika mengedit atau menambahkan file, Anda bisa memilih opsi untuk membuat branch baru berdasarkan commit tersebut.
2.  **Melalui Antarmuka Branch**:
    *   Navigasi ke repositori Anda.
    *   Klik pada nama branch saat ini (biasanya "master" atau "main").
    *   Ketik nama branch baru yang diinginkan (misalnya, `rencana-konten`).
    *   Jika nama belum ada, akan muncul opsi "Create branch `nama-branch`". Klik opsi tersebut.
    *   Setelah dibuat, Anda akan otomatis berada di branch baru tersebut.

### Melakukan Commit pada Branch
Setelah membuat branch baru, Anda dapat melakukan perubahan (misalnya, membuat file baru atau mengedit yang sudah ada) dan melakukan commit seperti biasa. Commit ini hanya akan tersimpan pada branch aktif tersebut.

### Berpindah Antar Branch (Checkout)
Proses berpindah dari satu branch ke branch lain disebut **checkout**. Di GitHub, ini dilakukan dengan mengklik nama branch dan memilih branch tujuan. Perubahan yang ada di branch lain tidak akan terlihat sampai Anda melakukan checkout ke branch tersebut.

### Menggabungkan Branch (Merge)
Setelah fitur atau perubahan pada sebuah branch selesai dan dianggap stabil, branch tersebut dapat digabungkan kembali ke Master branch. Proses ini disebut **merging**.

#### Pull Request (Permintaan Tarik)
*   **Definisi**: **Pull Request** (PR) adalah mekanisme untuk meminta agar perubahan dari sebuah branch ditarik (digabungkan) ke branch lain, biasanya Master branch.
*   **Proses**:
    1.  Setelah melakukan commit pada branch fitur, akan muncul tombol "Compare & pull request".
    2.  Klik tombol tersebut untuk membuat PR. GitHub akan secara otomatis memeriksa apakah ada konflik yang mungkin terjadi.
    3.  Berikan judul dan deskripsi untuk PR Anda.
    4.  Buat PR. Meskipun Anda pemilik repositori, proses ini tetap dilakukan untuk menjaga alur kerja standar.

#### Proses Merge
*   Setelah PR dibuat dan tidak ada konflik, Anda dapat langsung melakukan merge.
*   Klik "Merge pull request" dan konfirmasi.
*   Setelah merge berhasil, perubahan dari branch fitur akan masuk ke Master branch.
*   Visualisasi di tab "Network" akan menunjukkan jalur branch fitur bergabung kembali ke Master branch.

### Mengatasi Konflik Merge (Merge Conflict)
**Merge Conflict** terjadi ketika dua branch yang berbeda mengubah baris kode yang sama atau bagian yang berdekatan dari file yang sama. Git tidak dapat memutuskan secara otomatis perubahan mana yang harus dipertahankan.

#### Penyebab Konflik
Konflik muncul ketika:
*   Dua branch memodifikasi baris yang sama dalam file yang sama.
*   Satu branch menghapus baris yang dimodifikasi oleh branch lain.

#### Langkah Resolusi
1.  Ketika mencoba merge dan terdeteksi konflik, GitHub akan memberi tahu bahwa merge tidak dapat dilakukan secara otomatis.
2.  Klik "Resolve conflicts" untuk masuk ke editor konflik.
3.  Anda akan melihat penanda konflik (`<<<<<<<`, `=======`, `>>>>>>>`) yang menunjukkan bagian kode dari masing-masing branch.
4.  Edit file secara manual untuk memilih perubahan mana yang ingin Anda pertahankan atau gabungkan. Hapus penanda konflik.
5.  Setelah konflik diselesaikan, klik "Mark as resolved" dan kemudian "Commit merge".
6.  Setelah commit, Anda dapat melanjutkan proses merge.

### Menghapus Branch
Setelah sebuah branch berhasil digabungkan ke Master branch dan tidak lagi diperlukan, branch tersebut dapat dihapus.
*   Navigasi ke tab "Branches" di repositori Anda.
*   Cari branch yang ingin dihapus dan klik ikon tempat sampah di sampingnya.

## Rekapitulasi Istilah Penting
*   **Branch**: Jalur pengembangan bebas dari sebuah komit.
*   **Checkout**: Proses berpindah ke branch lain atau bahkan ke komit tertentu dalam riwayat proyek.
*   **Pull Request**: Cara untuk meminta pemilik repositori atau Master branch untuk menarik perubahan dari branch Anda.
*   **Merge**: Menggabungkan dua buah branch menjadi satu.
*   **Merge Conflict**: Situasi di mana Git tidak dapat menggabungkan perubahan secara otomatis karena adanya modifikasi pada baris kode yang sama di branch yang berbeda. Konflik harus diselesaikan secara manual.