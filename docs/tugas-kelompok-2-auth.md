# Tugas Kelompok 2 — Matriks Auth dan Endpoint yang Dilindungi
## 1. Daftar Peran Pengguna
| No. | Peran | Keterangan |
| --- | --- | --- |
| 1. | Anggota | Mencari buku, melihat ketersediaan, mengajukan peminjaman, dan memantau transaksi pribadi |
| 2. | Pustakawan | Mengelola data buku dan anggota, memproses peminjaman dan pengembalian, serta mengelola denda |
| 3. | Pimpinan | Melihat laporan dan statistik perpustakaan untuk memantau aktivitas layanan |

## 2. Matriks Hak Akses dan Endpoint API
# Tugas Kelompok 2 — Matriks Auth dan Endpoint yang Dilindungi
| No. | Fitur | Method | Endpoint | Anggota | Pustakawan | Pimpinan |
|---|---|---|---|:---:|:---:|:---:|
| 1 | Registrasi akun | POST | `/api/v1/auth/register` | ✅ | ❌ | ❌ |
| 2 | Login | POST | `/api/v1/auth/login` | ✅ | ✅ | ✅ |
| 3 | Melihat profil sendiri | GET | `/api/v1/auth/me` | ✅ | ✅ | ✅ |
| 4 | Melihat daftar jadwal | GET | `/api/v1/jadwal` | ✅ | ✅ | ✅ |
| 5 | Melihat daftar peserta | GET | `/api/v1/peserta` | ❌ | ✅ | ❌ |
| 6 | Mengelola data buku | POST, PUT, DELETE | `/api/v1/books` dan `/api/v1/books/:id` | ❌ | ✅ | ❌ |
| 7 | Mengajukan peminjaman | POST | `/api/v1/loans` | ✅ | ❌ | ❌ |
| 8 | Melihat peminjaman sendiri | GET | `/api/v1/loans/me` | ✅ | ❌ | ❌ |
| 9 | Memproses pengembalian | PUT | `/api/v1/loans/:id/return` | ❌ | ✅ | ❌ |
| 10 | Melihat laporan statistik | GET | `/api/v1/admin/rekap` | ❌ | ✅ | ✅ |
| 11 | Mengelola data anggota | POST, PUT, DELETE | `/api/v1/peserta` dan `/api/v1/peserta/:id` | ❌ | ✅ | ❌ |

## 3. Aturan Autentikasi dan Otorisasi
### a. Autentikasi dengan JWT
Autentikasi digunakan untuk memastikan bahwa pengguna yang mengakses endpoint terlindungi telah berhasil login. Setelah login berhasil, backend memberikan token JWT. Token tersebut dikirim melalui header HTTP `Authorization` menggunakan format:
```http
Authorization: Bearer <token>
```
Middleware `requireAuth` memeriksa keberadaan token, validitas tanda tangan, dan masa berlaku token sebelum permintaan diteruskan ke proses berikutnya.

### b. Aturan Status HTTP

| Status | Kondisi | Penjelasan |
|---|---|---|
| `200 OK` | Permintaan berhasil | Data berhasil dibaca atau proses berhasil dilakukan. |
| `201 Created` | Data berhasil dibuat | Misalnya, akun atau data buku berhasil ditambahkan. |
| `400 Bad Request` | Data tidak valid | Permintaan tidak memenuhi validasi. |
| `401 Unauthorized` | Token tidak ada atau tidak valid | Pengguna harus login atau memperoleh token yang valid. |
| `403 Forbidden` | Pengguna tidak memiliki izin | Pengguna sudah terautentikasi, tetapi perannya tidak diizinkan mengakses fitur. |
| `404 Not Found` | Data atau endpoint tidak ditemukan | Sumber daya yang diminta tidak tersedia. |

Aturan utama: permintaan ke endpoint terlindungi tanpa token valid harus menghasilkan 401 Unauthorized. Jika pengguna memiliki token valid tetapi perannya tidak memiliki izin, backend harus menghasilkan 403 Forbidden.

## 4. Middleware yang Digunakan
### a. Middleware requireAuth
requireAuth digunakan untuk memeriksa apakah pengguna sudah terautentikasi menggunakan JWT.
Middleware ini bertanggung jawab untuk:
1. Membaca token dari header Authorization.
2. Memverifikasi token menggunakan JWT_SECRET.
3. Memastikan token masih berlaku.
4. Menyediakan identitas pengguna bagi proses otorisasi berikutnya.
5. Menghentikan permintaan jika token tidak valid.

### b. Middleware requireRole
requireRole digunakan untuk membatasi akses berdasarkan peran pengguna.
Contoh penerapan:

```javascript
router.get(
  '/rekap',
  requireAuth,
  requireRole('PUSTAKAWAN', 'PIMPINAN'),
  getRekap
);
```

Contoh tersebut menunjukkan bahwa endpoint rekap hanya dapat diakses oleh pengguna yang sudah terautentikasi dan memiliki peran Pustakawan atau Pimpinan.

## 5. Daftar Endpoint yang Dilindungi pada Pertemuan 3
Berdasarkan struktur praktikum, endpoint yang perlu diperiksa penerapan middleware-nya adalah:
| No. | Endpoint | Middleware yang Diharapkan | Keterangan |
|---|---|---|---|
| 1 | `GET /api/v1/auth/me` | `requireAuth` | Melihat identitas pengguna yang sedang login. |
| 2 | `GET /api/v1/admin/rekap` | `requireAuth`, `requireRole` | Membatasi akses laporan berdasarkan peran. |
| 3 | `GET /api/v1/peserta` | `requireAuth`, `requireRole` | Membatasi akses data peserta sesuai kebijakan. |
| 4 | `POST /api/v1/auth/register` | Validasi registrasi | Endpoint publik dengan validasi input. |
| 5 | `POST /api/v1/auth/login` | Validasi login | Endpoint publik untuk memperoleh token JWT. |

## 6. Endpoint Tambahan untuk Pertemuan 4–7
Pengembangan Elibrary memerlukan endpoint tambahan untuk mendukung transaksi perpustakaan.
| No. | Fitur | Endpoint | Middleware yang Direncanakan |
|---|---|---|---|
| 1 | Mengelola buku | `POST /api/v1/books` | `requireAuth`, `requireRole('PUSTAKAWAN')` |
| 2 | Mengajukan peminjaman | `POST /api/v1/loans` | `requireAuth`, validasi peminjam |
| 3 | Memproses pengembalian | `PUT /api/v1/loans/:id/return` | `requireAuth`, `requireRole('PUSTAKAWAN')` |
| 4 | Melihat laporan statistik | `GET /api/v1/reports/summary` | `requireAuth`, `requireRole('PUSTAKAWAN', 'PIMPINAN')` |

Endpoint tambahan tersebut merupakan rancangan pengembangan dan belum boleh dianggap selesai sebelum diimplementasikan dan diuji. Selain pemeriksaan peran, backend harus memastikan anggota hanya dapat mengakses data transaksi miliknya sendiri. Pemeriksaan ini mencegah pengguna mengakses transaksi milik anggota lain hanya dengan mengganti ID pada URL.

## 7. Pengelolaan JWT_SECRET
### a. Lokasi penyimpanan JWT_SECRET
JWT_SECRET disimpan di file backend/.env dan digunakan untuk membantu proses penandatanganan serta verifikasi token JWT pada backend. File .env tidak boleh dimasukkan ke repositori Git karena berisi informasi rahasia yang tidak boleh diketahui oleh orang lain.

### b. Cara anggota memperoleh JWT_SECRET
Setiap anggota kelompok dapat memperoleh nilai JWT_SECRET melalui komunikasi pribadi yang aman dari anggota yang bertanggung jawab mengelola backend. Anggota kemudian menyimpan nilai tersebut di file backend/.env pada komputer masing-masing. File .env tidak dikirim melalui repositori Git. Sebagai gantinya, repositori menyediakan file backend/.env.example yang berisi contoh konfigurasi tanpa secret asli.
File `.gitignore` juga memuat aturan `.env` dan `**/.env` agar file `.env` diabaikan oleh Git.

### c. Bukti file backend/.env tidak dilacak Git
Pemeriksaan dilakukan menggunakan perintah berikut pada terminal di direktori utama proyek:
![hasil pengujian](screenshot/BUKTI-FILE-BACKEND.png)

Hasil pemeriksaan: Perintah tidak menampilkan output apa pun. Hasil tersebut menunjukkan bahwa backend/.env tidak tercatat sebagai file yang dilacak Git. Dengan demikian, file konfigurasi yang berisi secret tidak dimasukkan ke dalam daftar file yang dikelola Git.

