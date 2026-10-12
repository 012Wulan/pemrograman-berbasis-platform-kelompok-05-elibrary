# Ide Project Akhir

### Judul: Kelompok-01-SILAB-Elibrary
Kelompok kami memilih Elibrary (Perpustakaan Digital) sebagai project akhir yang akan dikembangkan sampai UAS. Aplikasi ini dirancang untuk membantu anggota mencari koleksi buku dan memantau ketersediaannya, membantu pustakawan mengelola katalog serta transaksi peminjaman, dan menyediakan statistik bagi pimpinan. Pengembangan akan dimulai dari fitur utama yang dibutuhkan pengguna, dengan pengumpulan informasi melalui wawancara pustakawan dan penyusunan data contoh katalog buku.

## Elibrary — Sistem Perpustakaan Digital
Elibrary merupakan aplikasi perpustakaan digital yang dikembangkan untuk mempermudah anggota mencari koleksi buku, memantau ketersediaan buku, dan mengelola proses peminjaman serta pengembalian. Aplikasi ini juga mendukung pustakawan dalam mengelola koleksi dan membantu pimpinan melihat statistik perpustakaan.

## Identitas Anggota Kelompok

| No. | Nama | NIM | GitHub | Peran |
|---|---|---|---|---|
| 1 | Septiana Wulandari | 2024520012 | 012Wulan | Backend Developer |
| 2 | Hoirul Umam | 2024520014 | 014Hoirul | Frontend Developer |
| 2 | Wulidati Trixiana | 2024520046 | 046trixi | Dokumenter dan Tester |

## Fitur Utama

- Pencarian buku berdasarkan judul, pengarang, atau ISBN.
- Informasi ketersediaan koleksi.
- Pengelolaan data buku dan anggota.
- Pencatatan peminjaman dan pengembalian.
- Perhitungan denda keterlambatan.
- Antrean pemesanan buku.
- Akses e-book sesuai hak akses.
- Laporan dan statistik perpustakaan.

## Peran Pengguna

1.**Anggota**: mencari buku dan memantau peminjaman.
2.**Pustakawan**: mengelola katalog serta transaksi sirkulasi.
3.**Pimpinan**: memantau laporan dan statistik perpustakaan.

## Struktur Proyek

- `docs/` — proposal, backlog, dokumentasi, dan laporan proyek.
- `backend/` — layanan API dan pengelolaan data.
- `frontend/web/` — antarmuka aplikasi berbasis web.
- `frontend/mobile/` — antarmuka aplikasi mobile.

## Cara Menjalankan Aplikasi

Petunjuk menjalankan aplikasi akan dilengkapi sesuai teknologi dan konfigurasi yang digunakan kelompok.

### Backend

1. Buka terminal pada folder backend.
2. Instal dependensi menggunakan `npm install` jika backend menggunakan Node.js.
3. Konfigurasikan database dan variabel lingkungan sesuai file konfigurasi proyek.
4. Jalankan perintah pengembangan sesuai script yang tersedia pada `package.json`.

### Frontend Web

1. Buka terminal pada folder aplikasi web.
2. Instal dependensi sesuai teknologi yang digunakan.
3. Jalankan aplikasi menggunakan perintah yang tersedia pada `package.json`.

### Frontend Mobile

1. Buka folder aplikasi mobile menggunakan IDE yang sesuai.
2. Siapkan dependensi dan perangkat atau emulator.
3. Jalankan aplikasi sesuai petunjuk framework yang digunakan.

### Arsitektur

1. **Web**: Svelte → REST → Express → Prisma → Database.
2.**Mobile**: Flutter → REST → Express → Prisma → Database.

## Dokumentasi

- Proposal: `docs/proposal.md`
- Identitas kelompok: `docs/tugas-kelompok-1-kelompok.md`
- Backlog: `docs/backlog.md`
- Tautan video pengujian: `docs/tautan-video-pengujian.md`
- Laporan proyek: `docs/Laporan-Kelompok-01-Mikrokredensial.docx`
