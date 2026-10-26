# Tugas Kelompok 1 — Design System Elibrary
## 1. Token Desain
### a. Palet Warna
| Nama Token | Kode Hex | Penggunaan |
| --- | --- | --- |
| Primary Pink | #F4A6C1 | Tombol utama dan elemen penting |
| White | #FFFFFF | Latar kartu dan area konten |
| Dark Purple | #49354F | Judul, teks utama, dan navigasi |

Warna pink digunakan sebagai identitas visual Elibrary, putih untuk menjaga tampilan tetap bersih, sedangkan ungu tua digunakan untuk teks agar mudah dibaca.

### b. Tipografi
| Elemen | Font | Ukuran |
| --- | --- | --- |
| Judul halaman | Poppins | 24-32 px |
| Subjudul | Poppins | 18-22 px |
| Teks isi | Inter | 14-16 px |
| Label dan tombol | Inter | 14-16 px |

### c. Radius Sudut 
| Token | Nilai | Penggunaan | 
| --- | --- | --- |
| Radius Small | 16px | Input dan tombol kecil |
| Radius Medium | 12px | Tombol dan kartu |
| Radius Large | 20px | Panel dan kartu utama |

### d. Skala Jarak 
| Token | Nilai |
| --- | --- |
| Spacing 1 | 4px |
| Spacing 2 | 8px |
| Spacing 3 | 12px |
| Spacing 4 | 16px |
| Spacing 6 | 24px |
| Spacing 8 | 32px |

### e. Gaya Bayangan 
| Token | Nilai | Penggunaan | 
| --- | --- | --- |
| Shadow Small | 0 2px 6px rgba(73, 53, 79, 0.08) | Tombol dan input |
| Shadow Medium | 0 4px 12px rgba(73, 53, 79, 0.12) | Kartu buku |
| Shadow Large | 0 8px 24px rgba(73, 53, 79, 0.16) | Modal dan panel utama |


## 2. Elemen UI
### a. Tombol 
Kode HTML dan Tailwind CSS:
<button
  class="rounded-xl bg-[#F4A6C1] px-4 py-2
         font-medium text-[#49354F]
         transition hover:bg-[#E88FB0]
         focus-visible:outline-2
         focus-visible:outline-offset-2
         focus-visible:outline-[#49354F]
         disabled:cursor-not-allowed
         disabled:opacity-50"
>
  Pinjam Buku
</button>

State tombol:
- Normal: tombol berwarna pink pastel.
- Hover: warna tombol menjadi lebih gelap.
- Focus: muncul garis penanda saat tombol menerima fokus keyboard.
- Disabled: tombol tidak dapat digunakan dan tampil lebih transparan.
Pendekatan: tombol dibuat sebagai komponen siap pakai karena digunakan berulang kali pada halaman katalog, detail buku, dan transaksi peminjaman.

### b. Kartu Buku
Kode HTML dan Tailwind CSS:
<article
  class="rounded-xl bg-white p-4
         shadow-[0_4px_12px_rgba(73,53,79,0.12)]
         transition hover:-translate-y-1
         hover:shadow-lg"
>
  <h3 class="text-lg font-semibold text-[#49354F]">
    Pemrograman Web
  </h3>

  <p class="mt-2 text-sm text-[#49354F]">
    Pengarang: Budi Santoso
  </p>

  <p class="mt-1 text-sm text-[#49354F]">
    Stok tersedia: 5 buku
  </p>

  <button
    class="mt-4 rounded-xl bg-[#F4A6C1]
           px-4 py-2 text-[#49354F]"
  >
    Lihat Detail
  </button>
</article>

State kartu:
- Normal: kartu memiliki latar putih dan bayangan ringan.
- Hover: kartu sedikit terangkat dan bayangannya lebih jelas.
- Stok habis: informasi stok ditampilkan sebagai habis dan tombol peminjaman dinonaktifkan.
Pendekatan: kartu buku dibuat sebagai komponen siap pakai karena struktur kartu digunakan berulang kali untuk menampilkan banyak buku.

### c. Input Form
Kode HTML dan Tailwind CSS:
<div class="space-y-2">
  <label
    for="judul"
    class="block text-sm font-medium text-[#49354F]"
  >
    Judul Buku
  </label>

  <input
    id="judul"
    type="text"
    placeholder="Masukkan judul buku"
    class="w-full rounded-md border border-gray-300
           bg-white px-3 py-2 text-[#49354F]
           placeholder:text-gray-400
           focus:border-[#F4A6C1]
           focus:outline-none focus:ring-2
           focus:ring-[#F4A6C1]"
  />
</div>

State input:
- Normal: memiliki garis tepi abu-abu.
- Focus: garis tepi dan ring berubah menjadi pink.
- Error: garis tepi berubah menjadi merah dan pesan kesalahan ditampilkan.
- Disabled: input tidak dapat diedit.
Pendekatan: input dibuat sebagai komponen siap pakai karena digunakan pada formulir login, pencarian, pengelolaan buku, dan pengelolaan anggota.

## 3. Keputusan Component vs Utility
Kelompok memutuskan menggunakan pendekatan gabungan antara komponen siap pakai dan utility Tailwind CSS.
| Elemen | Pendekatan | Alasan |
|---|---|---|
| Tombol | Komponen | Digunakan pada banyak halaman dengan variasi state |
| Kartu buku | Komponen | Memiliki struktur yang berulang |
| Input form | Komponen | Digunakan pada berbagai formulir |
| Layout halaman | Utility | Setiap halaman memiliki susunan yang berbeda |
| Grid katalog | Utility | Memerlukan penyesuaian responsif |
| Jarak dan alignment | Utility | Memudahkan pengaturan tata letak |

Komponen siap pakai digunakan untuk elemen yang berulang, sedangkan utility Tailwind digunakan untuk menyusun layout dan mengatur tampilan halaman.

## 4. Keputusan Desain Halaman
### a. Halaman Publik
Halaman publik mencakup beranda, katalog buku, pencarian, detail buku, dan halaman login. Pendekatan yang digunakan adalah kombinasi komponen dan utility Tailwind CSS. Komponen tombol, kartu buku, dan input digunakan kembali, sedangkan utility digunakan untuk mengatur layout, jarak, dan responsivitas.

### b. Halaman Admin
Halaman admin mencakup pengelolaan buku, pengelolaan anggota, transaksi peminjaman, pengembalian, dan laporan. Pendekatan yang digunakan tetap berupa kombinasi komponen dan utility Tailwind CSS. Komponen tabel, tombol aksi, input, dan status transaksi digunakan kembali agar tampilan antarhalaman tetap konsisten. Perbedaan halaman publik dan admin terletak pada susunan konten dan fungsi yang tersedia, bukan pada standar warna dan tipografi.
