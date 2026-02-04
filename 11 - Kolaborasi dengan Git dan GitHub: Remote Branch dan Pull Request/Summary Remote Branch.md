# Kolaborasi dengan Git dan GitHub: Remote Branch dan Pull Request

Video ini menjelaskan proses kolaborasi menggunakan Git dan GitHub, khususnya mengenai penggunaan *remote branch* dan *pull request* (PR) untuk mengusulkan perubahan ke repositori asli. Proses ini sangat penting ketika berkontribusi pada proyek yang bukan milik kita secara langsung, di mana kita tidak memiliki hak akses untuk langsung mendorong perubahan ke repositori sumber.

## Konsep Dasar Kolaborasi dengan Pull Request

Ketika bekerja pada repositori hasil *fork* dari repositori orang lain, kita tidak bisa langsung mengirimkan perubahan ke repositori sumber karena tidak memiliki hak akses. GitHub menyediakan fitur **Pull Request** untuk mengatasi hal ini. Pull Request adalah permintaan agar perubahan yang kita buat ditarik (diterima) masuk ke dalam repositori utama.

## Alur Kerja Kolaborasi

### 1. Mempersiapkan Lingkungan Lokal

Pastikan repositori lokal sudah disinkronkan dengan repositori sumber. Ini melibatkan proses `git fetch` dan `git merge` untuk memastikan `master` lokal kita *up to date* dengan `master` repositori sumber. Setelah itu, buka proyek di *code editor* favorit Anda.

### 2. Membuat Branch untuk Perubahan

**Penting**: Jangan pernah melakukan perubahan langsung pada *branch* `master` di repositori lokal Anda saat berkontribusi. *Branch* `master` harus selalu disinkronkan dengan *branch* `master` repositori asli. Untuk setiap perubahan atau fitur baru, buatlah *branch* terpisah.

Langkah-langkah membuat *branch* baru:
*   Periksa *branch* yang ada: `git branch`
*   Buat *branch* baru dan langsung pindah ke *branch* tersebut:
    ```bash
    git checkout -b <nama_branch>
    ```
    Contoh: `git checkout -b feature`
    *Alternatif*: Jika ingin membuat dan pindah secara terpisah:
    ```bash
    git branch <nama_branch>
    git checkout <nama_branch>
    ```
*   Verifikasi bahwa Anda sudah berada di *branch* baru (misalnya, di Visual Studio Code, nama *branch* akan terlihat di kiri bawah).

### 3. Melakukan Perubahan dan Commit

Setelah berada di *branch* baru, lakukan perubahan yang diinginkan pada kode Anda. Setelah selesai, simpan perubahan dan *commit* ke *branch* lokal Anda:
*   Periksa status perubahan (opsional, namun disarankan): `git status`
*   *Commit* perubahan dengan pesan yang deskriptif:
    ```bash
    git commit -am "Pesan commit Anda"
    ```
    Contoh: `git commit -am "Mengubah tulisan pada testimonial"`
*   Lihat riwayat *commit* Anda: `git graph`

### 4. Mendorong Branch ke Remote (GitHub)

Setelah perubahan di-*commit* secara lokal, dorong (*push*) *branch* baru ini ke repositori GitHub Anda (repositori *fork* Anda):
```bash
git push origin <nama_branch>
```
Contoh: `git push origin features`
Verifikasi dengan `git graph` bahwa *branch* lokal dan *remote* Anda sudah sinkron.

### 5. Membuat Pull Request di GitHub

Proses pembuatan *pull request* dilakukan melalui antarmuka GitHub:
1.  Buka repositori *fork* Anda di GitHub.
2.  Pilih *branch* `feature` yang baru saja Anda dorong.
3.  GitHub akan menampilkan tombol **"Compare & pull request"**. Klik tombol ini.
4.  Periksa detail *pull request*:
    *   Pastikan repositori utama adalah repositori sumber (misalnya, `SandikaGali/simple-landing-page`).
    *   Pastikan *branch* target adalah `master` dari repositori sumber.
    *   Pastikan *branch* sumber adalah `feature` dari repositori Anda (`webprogrammingunpas/simple-landing-page`).
    *   GitHub akan memberi tahu jika ada konflik yang perlu diselesaikan.
5.  Berikan judul dan deskripsi yang jelas mengenai perubahan yang Anda usulkan. Jelaskan mengapa perubahan ini penting atau apa yang telah Anda lakukan.
6.  Klik **"Create pull request"**.

Setelah ini, tugas Anda sebagai kontributor selesai. Anda tinggal menunggu pemilik repositori asli untuk meninjau dan menerima PR Anda.

### 6. Meninjau dan Menggabungkan Pull Request (Perspektif Pemilik Repo Asli)

Dari sisi pemilik repositori asli (misalnya, Sandika Gali):
1.  Pemilik repositori akan melihat notifikasi *pull request* baru.
2.  Mereka dapat meninjau perubahan yang diusulkan, melihat *commit*, dan membandingkan perubahan file.
3.  Pemilik dapat:
    *   Memberikan komentar atau memulai diskusi.
    *   Meminta perubahan tambahan.
    *   Menyetujui (*approve*) *pull request* jika perubahan sudah sesuai.
4.  Jika disetujui, pemilik akan **"Merge pull request"** dan **"Confirm merge"**.
5.  Setelah digabungkan, *branch* `master` di repositori asli akan diperbarui dengan perubahan yang Anda usulkan.

### 7. Sinkronisasi Repositori Lokal Setelah PR di-Merge

Setelah *pull request* Anda digabungkan, Anda perlu memperbarui repositori lokal dan *remote* Anda sendiri:
1.  Kembali ke repositori *fork* Anda di GitHub. Status PR Anda akan berubah menjadi "Closed".
2.  Di terminal lokal Anda, *fetch* perubahan terbaru dari repositori asli:
    ```bash
    git fetch <nama_remote_repositori_asli>
    ```
    Contoh: `git fetch SandikaGali`
    *   `git graph` akan menunjukkan bahwa `master` repositori asli (`SandikaGali/master`) sudah maju beberapa *commit*.
3.  Pindah ke *branch* `master` lokal Anda: `git checkout master`.
4.  Gabungkan (*merge*) *master* dari repositori asli ke *master* lokal Anda:
    ```bash
    git merge <nama_remote_repositori_asli>/master
    ```
    Contoh: `git merge SandikaGali/master`
    *   `git graph` akan menunjukkan bahwa `master` lokal Anda sudah sinkron dengan `master` repositori asli.
5.  Dorong perubahan ini ke *master* repositori *fork* Anda di GitHub:
    ```bash
    git push origin master
    ```
    *   `git graph` akan menunjukkan bahwa semua *branch* (lokal, *remote* Anda, dan *remote* asli) sudah sinkron.

### 8. Menghapus Branch

Setelah *pull request* digabungkan dan semua *branch* sudah sinkron, *branch* fitur yang Anda buat tidak lagi diperlukan. Anda bisa menghapusnya secara lokal dan *remote*:
1.  Hapus *branch* lokal:
    ```bash
    git branch -d <nama_branch>
    ```
    Contoh: `git branch -d features`
    *   Verifikasi dengan `git branch`.
2.  Hapus *branch* di repositori *remote* Anda (GitHub):
    ```bash
    git push origin --delete <nama_branch>
    ```
    Contoh: `git push origin --delete feature`
    *   Verifikasi di GitHub bahwa *branch* tersebut sudah tidak ada.