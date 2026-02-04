# Git Rebase: Memahami dan Menggunakan Sejarah Komit yang Bersih

Git Rebase adalah perintah Git yang kuat untuk mengintegrasikan perubahan dari satu cabang ke cabang lain, dengan cara menulis ulang riwayat komit. Ini memungkinkan pengembang untuk menjaga riwayat proyek tetap linier dan bersih, berbeda dengan `git merge` yang menciptakan komit gabungan (merge commit).

## Apa itu Git Rebase?

**Git Rebase** adalah proses memindahkan atau menggabungkan urutan komit ke komit dasar (base commit) yang berbeda. Alih-alih membuat komit gabungan baru, rebase mengambil semua komit dari cabang Anda, "memutar ulang" komit-komit tersebut, dan kemudian menerapkannya kembali satu per satu di atas komit terbaru dari cabang target. Hasilnya adalah riwayat komit yang tampak seolah-olah pekerjaan Anda selalu dilakukan di atas versi terbaru dari cabang target.

### Perbedaan dengan Git Merge

| Fitur           | Git Rebase                                                                                                | Git Merge                                                                                               |
| :-------------- | :-------------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------ |
| **Riwayat**     | Menciptakan riwayat yang linier dan bersih dengan menulis ulang komit.                                    | Mempertahankan riwayat asli dan menciptakan komit gabungan (merge commit).                              |
| **Komit**       | Komit-komit dari cabang sumber diterapkan ulang di atas cabang target, mengubah hash komit.               | Menambahkan komit gabungan baru yang menyatukan riwayat kedua cabang.                                  |
| **Kompleksitas**| Membutuhkan resolusi konflik yang berulang jika ada banyak komit dan konflik.                             | Resolusi konflik dilakukan sekali pada komit gabungan.                                                  |
| **Penggunaan**  | Ideal untuk membersihkan riwayat komit lokal sebelum mendorong ke repositori bersama.                     | Umumnya digunakan untuk mengintegrasikan cabang fitur ke cabang utama yang sudah dibagikan.             |
| **Risiko**      | Berisiko jika digunakan pada cabang yang sudah dibagikan, karena menulis ulang riwayat publik.            | Aman untuk cabang yang sudah dibagikan karena tidak mengubah riwayat yang ada.                          |

### Tujuan Git Rebase

Tujuan utama menggunakan `git rebase` adalah untuk:
*   **Menjaga riwayat proyek tetap linier dan bersih**: Memudahkan pelacakan perubahan dan pemahaman alur kerja.
*   **Menghindari komit gabungan yang tidak perlu**: Mengurangi "kebisingan" dalam riwayat komit.
*   **Mengintegrasikan perubahan dari cabang utama**: Memastikan cabang fitur Anda selalu diperbarui dengan perubahan terbaru dari cabang utama (misalnya, `main` atau `master`) sebelum digabungkan.

## Cara Kerja Git Rebase

Ketika Anda menjalankan `git rebase <target-branch>` dari cabang fitur Anda, Git akan melakukan langkah-langkah berikut:
1.  **Mencari komit umum**: Git menemukan komit umum terakhir antara cabang fitur Anda dan `<target-branch>`.
2.  **Menyimpan komit cabang fitur**: Semua komit unik di cabang fitur Anda (yaitu, komit yang tidak ada di `<target-branch>`) disimpan sementara.
3.  **Memindahkan HEAD cabang fitur**: HEAD dari cabang fitur Anda dipindahkan ke ujung `<target-branch>`.
4.  **Menerapkan ulang komit**: Komit-komit yang disimpan sementara diterapkan ulang satu per satu di atas `<target-branch>` yang baru. Setiap komit akan mendapatkan hash ID baru karena konteksnya telah berubah.

Contoh:
Jika Anda memiliki cabang `feature` yang bercabang dari `main`, dan `main` telah maju dengan komit baru:

```
A -- B -- C (main)
      \
       D -- E (feature)
```

Setelah `git rebase main` dari cabang `feature`:

```
A -- B -- C -- D' -- E' (main, feature)
```

Komit `D` dan `E` diterapkan ulang sebagai `D'` dan `E'` di atas `C`.

## Penggunaan Umum Git Rebase

### Membersihkan Riwayat Komit Lokal

Rebase sangat berguna untuk membersihkan riwayat komit Anda sebelum mendorongnya ke repositori bersama. Ini memungkinkan Anda untuk:
*   **Menggabungkan (squash) beberapa komit kecil menjadi satu komit yang lebih besar**: Misalnya, jika Anda memiliki serangkaian komit "perbaikan kecil", "debug", atau "WIP".
*   **Mengubah pesan komit**: Memperbaiki kesalahan ketik atau membuat pesan lebih deskriptif.
*   **Menghapus komit yang tidak perlu**: Menghilangkan komit yang tidak relevan atau salah.
*   **Mengurutkan ulang komit**: Mengubah urutan komit untuk alur cerita yang lebih logis.

### Mengintegrasikan Perubahan dari Cabang Utama

Sebelum menggabungkan cabang fitur Anda ke `main`, Anda dapat merebase cabang fitur Anda di atas `main` untuk memastikan bahwa semua perubahan terbaru dari `main` sudah termasuk dalam cabang fitur Anda. Ini mengurangi kemungkinan konflik saat penggabungan akhir.

1.  `git checkout feature-branch`
2.  `git rebase main`
3.  Jika ada konflik, selesaikan.
4.  `git add .`
5.  `git rebase --continue`
6.  Setelah rebase selesai, Anda dapat menggabungkan cabang fitur Anda ke `main` dengan `git merge feature-branch` (yang akan menjadi fast-forward merge jika tidak ada komit baru di `main` sejak rebase).

## Git Rebase Interaktif (`git rebase -i`)

`git rebase -i` (interaktif) adalah alat yang sangat kuat yang memungkinkan Anda untuk memodifikasi riwayat komit secara lebih detail. Ketika Anda menjalankan `git rebase -i <base-commit-hash>` atau `git rebase -i HEAD~N` (untuk N komit terakhir), Git akan membuka editor teks dengan daftar komit dan instruksi tentang apa yang dapat Anda lakukan.

### Perintah-perintah Interaktif Utama

*   `pick` (p): Gunakan komit ini. Ini adalah default.
*   `reword` (r): Gunakan komit ini, tetapi ubah pesan komit.
*   `edit` (e): Gunakan komit ini, tetapi berhenti untuk mengedit file atau memecah komit.
*   `squash` (s): Gunakan komit ini dan gabungkan dengan komit sebelumnya. Pesan komit akan digabungkan.
*   `fixup` (f): Mirip dengan `squash`, tetapi membuang pesan komit dari komit ini.
*   `drop` (d): Hapus komit ini sepenuhnya.
*   `reorder`: Anda dapat mengubah urutan baris komit untuk mengubah urutan penerapan komit.

**Contoh Alur Kerja `git rebase -i`:**
Misalkan Anda memiliki komit `A -- B -- C -- D -- E` di cabang lokal Anda dan Anda ingin menggabungkan `D` dan `E` menjadi satu komit, dan mengubah pesan komit `C`.

1.  `git rebase -i HEAD~3` (untuk 3 komit terakhir: C, D, E)
2.  Editor akan terbuka dengan:
    ```
    pick <hash-C> C: pesan komit C
    pick <hash-D> D: pesan komit D
    pick <hash-E> E: pesan komit E
    ```
3.  Ubah menjadi:
    ```
    reword <hash-C> C: pesan komit C
    pick <hash-D> D: pesan komit D
    squash <hash-E> E: pesan komit E
    ```
4.  Simpan dan tutup editor.
5.  Git akan berhenti pada komit `C` untuk Anda mengubah pesannya. Setelah selesai, `git commit --amend` dan `git rebase --continue`.
6.  Git akan berhenti lagi untuk Anda menggabungkan pesan komit `D` dan `E`. Setelah selesai, simpan dan tutup editor.
7.  Rebase selesai, dan riwayat Anda sekarang lebih bersih.

## Resolusi Konflik Selama Rebase

Konflik dapat terjadi selama rebase jika perubahan yang Anda buat di cabang fitur bertabrakan dengan perubahan di cabang target. Ketika konflik terjadi, Git akan berhenti dan memberi tahu Anda.

**Langkah-langkah Resolusi Konflik:**
1.  Git akan menampilkan pesan konflik.
2.  Buka file yang berkonflik dan selesaikan konflik secara manual.
3.  Setelah konflik diselesaikan, tambahkan file yang dimodifikasi ke area staging: `git add <file-yang-berkonflik>`.
4.  Lanjutkan proses rebase: `git rebase --continue`.
5.  Jika Anda memutuskan untuk membatalkan rebase, gunakan: `git rebase --abort`. Ini akan mengembalikan cabang Anda ke keadaan sebelum rebase dimulai.

## Kapan Menggunakan dan Kapan Menghindari Git Rebase

### Aturan Emas Rebase

**Jangan pernah merebase cabang yang telah Anda dorong ke repositori publik dan dibagikan dengan orang lain.**
Merebase menulis ulang riwayat komit. Jika Anda merebase cabang yang sudah dibagikan, orang lain yang telah menarik cabang tersebut akan memiliki riwayat yang berbeda, yang dapat menyebabkan masalah serius saat mereka mencoba mendorong atau menarik perubahan di kemudian hari. Ini akan memaksa mereka untuk melakukan rebase atau reset yang rumit.

### Kapan Menggunakan Rebase

*   **Membersihkan komit lokal**: Sebelum mendorong cabang fitur Anda untuk pertama kalinya, gunakan `git rebase -i` untuk membersihkan dan merapikan riwayat komit Anda.
*   **Mengintegrasikan perubahan dari cabang utama ke cabang fitur lokal**: Ini menjaga cabang fitur Anda tetap diperbarui dan riwayatnya bersih sebelum penggabungan akhir.
*   **Ketika Anda adalah satu-satunya yang bekerja di cabang tersebut**: Jika cabang Anda bersifat pribadi dan belum dibagikan, rebase adalah alat yang aman dan efektif.

### Kapan Menghindari Rebase

*   **Pada cabang yang sudah dibagikan**: Hindari merebase cabang `main`, `develop`, atau cabang fitur apa pun yang telah didorong ke repositori publik dan mungkin sedang dikerjakan oleh orang lain.
*   **Ketika Anda tidak nyaman dengan resolusi konflik**: Rebase bisa menjadi rumit jika ada banyak konflik, dan `git merge` mungkin merupakan pilihan yang lebih aman bagi pemula.

## Praktik Terbaik dan Peringatan

*   **Gunakan `git push --force-with-lease`**: Jika Anda merebase cabang lokal yang *sudah* Anda dorong ke remote (tetapi Anda yakin tidak ada orang lain yang menariknya), Anda perlu melakukan `git push --force` atau `git push --force-with-lease`. `force-with-lease` lebih aman karena akan gagal jika ada orang lain yang telah mendorong perubahan ke cabang yang sama sejak terakhir Anda menariknya, mencegah penimpaan yang tidak disengaja.
*   **Buat cadangan**: Sebelum melakukan rebase yang kompleks, pertimbangkan untuk membuat cabang cadangan (`git branch backup-feature`) jika terjadi kesalahan.
*   **Pahami apa yang Anda lakukan**: Rebase adalah perintah yang kuat. Pastikan Anda memahami implikasinya sebelum menggunakannya.