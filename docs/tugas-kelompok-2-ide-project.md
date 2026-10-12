# Tugas Kelompok 2 — Judul / Ide Project Akhir

## 1. Judul Final

**Kelompok-05-SILAB-Elibrary**

## 2. Cerita yang Dipilih dan Alasan

Kelompok kami memilih cerita nomor 4, yaitu Elibrary (Perpustakaan Digital). Kami memilih project ini karena permasalahan yang dibahas dekat dengan kehidupan mahasiswa, terutama ketika mencari buku referensi untuk kebutuhan perkuliahan. Kami berencana mencari informasi melalui wawancara dengan pustakawan kampus pada minggu ini untuk mengetahui proses pencarian buku, peminjaman, pengembalian, dan pengelolaan koleksi. Untuk data contoh, kami dapat menyiapkan data awal berupa judul buku, nama pengarang, ISBN, jumlah eksemplar, dan status ketersediaan buku. Data tersebut akan digunakan untuk membantu menyusun kebutuhan sistem dan mengembangkan fitur awal aplikasi.

## 3. Masalah, Pengguna, dan Fitur MVP

1. **Masalah:** Anggota perpustakaan kesulitan mengetahui ketersediaan buku dan memantau informasi peminjaman sebelum datang ke perpustakaan.
2. **Pengguna:** Sistem ditujukan untuk anggota perpustakaan, pustakawan, dan pimpinan yang membutuhkan informasi pengelolaan serta penggunaan koleksi.
3. **Fitur MVP:** Aplikasi menyediakan login sesuai peran, pencarian dan informasi ketersediaan buku, pengelolaan katalog, pencatatan peminjaman dan pengembalian, serta tampilan ringkasan transaksi perpustakaan.

## 4. Tiga Peran Pengguna

| No. | Peran | Tanggung Jawab |
|---|---|---|
| 1 | Anggota | Mencari buku, melihat ketersediaan koleksi, serta memantau informasi peminjaman dan pengembalian. |
| 2 | Pustakawan | Mengelola katalog buku, data anggota, transaksi peminjaman, pengembalian, dan denda. |
| 3 | Pimpinan | Melihat laporan dan statistik penggunaan koleksi untuk membantu evaluasi perpustakaan. |

## 5. Arsitektur Aplikasi

Project Elibrary menggunakan arsitektur berikut:

**Aplikasi Web:**

Svelte → REST → Express → Prisma → Database

**Aplikasi Mobile:**

Flutter → REST → Express → Prisma → Database

Svelte digunakan untuk membangun antarmuka web, sedangkan Flutter digunakan untuk membangun antarmuka mobile. Keduanya mengakses backend melalui REST API yang dibuat menggunakan Express. Prisma digunakan untuk menghubungkan backend dengan database sehingga pengelolaan data dapat dilakukan secara terstruktur.

## 6. Kesimpulan

Berdasarkan pertimbangan masalah, pengguna sasaran, dan ketersediaan data awal, kelompok kami menetapkan Elibrary sebagai ide project akhir yang akan dikembangkan sampai UAS. Kebutuhan dan fitur aplikasi akan diperbarui secara bertahap berdasarkan hasil pengamatan, wawancara, dan evaluasi selama praktikum.
