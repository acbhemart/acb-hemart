# ACB HEMART

Situs toko sederhana untuk kebutuhan sehari-hari (HTML/CSS/JS). Halaman utama ada pada `index.html` — Anda bisa membuka file tersebut langsung di browser untuk melihat tampilan toko.

Link ke file sumber yang digunakan:
https://github.com/acbhemart/acb-hemart/blob/4ed76fe8d20fad3680cc755de94ab6c256f393d3/index.html

## Ringkasan
ACB HEMART adalah demo toko online ringan yang dibuat dengan HTML, CSS, dan JavaScript tanpa backend. Fitur utama:
- Tampilan produk (kategori & pencarian)
- Keranjang belanja (lokal via LocalStorage)
- Checkout yang mengirim pesan pesanan ke WhatsApp
- Sidebar keranjang, notifikasi toast, dan modal input pelanggan

## Cara melihat / menjalankan
1. Clone repository atau unduh file `index.html` dan folder gambar bila ada.
2. Cara cepat (langsung): buka `index.html` di browser.
3. Cara dengan web server (lebih baik untuk beberapa browser dan asset):
   - Python 3:
     - Jalankan di folder proyek: `python -m http.server 8000`
     - Buka: `http://localhost:8000/`
   - Atau gunakan Live Server di VS Code, atau server static lain.

## Menghubungkan dengan WhatsApp (ganti nomor)
Checkout akan membuka WhatsApp menggunakan link `wa.me`. Untuk mengganti nomor tujuan:
1. Buka `index.html`
2. Cari baris ini (di bagian script):
   ```js
   const whatsappNumber = "081234567890"; // ← GANTI DENGAN NOMOR ANDA!
   ```
3. Ganti dengan nomor Anda dalam format internasional tanpa tanda `+` atau spasi. Contoh untuk nomor Indonesia:
   - Benar: `"6282123861749"`
   - Salah: `"+6282123861749"` atau `"0812..."` (walau contoh saat ini memakai 08..., WA lebih andal menerima format internasional 62...)
4. Simpan dan refresh halaman. Saat checkout, halaman akan membuka `https://wa.me/<nomor>?text=...` dengan detail pesanan.

Catatan: Pastikan nomor yang dimasukkan benar agar tautan WhatsApp bekerja.

## Struktur & file penting
- `index.html` — Halaman frontend utama (HTML, CSS & JS inline).
- Gambar produk — beberapa produk memakai URL placeholder; jika Anda menambahkan gambar lokal, letakkan di folder yang sama dan perbarui path pada array `products` di `index.html`.

## Mengedit produk
Produk didefinisikan di dalam `index.html` (variabel `products`):
```js
const products = [
  { id: 1, name: "Beras Premium sigeulis 5kg", price: 74500, stock: 24, category: "makanan", image: "sigeulis.png" },
  ...
];
```
Ubah / tambahkan objek produk sesuai kebutuhan. Pastikan setiap `id` unik.

## Catatan teknis & aksesibilitas
- Elemen cart memiliki `aria-label` dan badge dengan `aria-live` untuk membantu pengguna pembaca layar.
- Form checkout memiliki validasi sederhana (nama wajib, alamat wajib bila memilih antar).
- Pesanan disimpan sementara di `localStorage` sehingga keranjang tetap ada saat reload.

## Kustomisasi cepat
- Warna dan tipografi dapat disesuaikan lewat style di kepala (`<style>`).
- Untuk memisahkan CSS/JS, Anda bisa mengekstrak stylesheet dan script ke file terpisah (`styles.css`, `app.js`) dan memuatnya dari `index.html`.

## Kontribusi
PR dan issue diterima. Contoh hal yang bisa ditingkatkan:
- Penyimpanan pesanan ke backend / Firebase
- Autentikasi pengguna
- Pembayaran online
- Halaman admin untuk mengelola produk & stok

Jika ingin bantuan menambahkan README ke repo Anda (commit/push), beri tahu saya dan saya bisa bantu siapkan patch/PR.

## Lisensi
Lisensi default: MIT — ubah sesuai kebutuhan proyek Anda.

---

Terakhir, saya sudah menyiapkan README ini yang menghubungkan dan menjelaskan `index.html`. Bila Anda mau, saya bisa:
- Membuat `README.md` langsung di repo dan membuka PR, atau
- Membuat contoh `index.html` yang menggunakan nomor WhatsApp dalam format internasional, atau
- Memecah CSS/JS ke file terpisah dan menambahkan instruksi deploy GitHub Pages. Pilih yang Anda inginkan.
