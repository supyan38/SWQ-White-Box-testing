# 🧪 FORMAL INSPECTION REPORT - Bookshelf App

## 👥 Tim Pemeriksa
| Peran        | Nama        |
|--------------|-------------|
| Reviewer     | Santi       |

---

## 1. 📋 PLANNING

### File yang diperiksa:
- `main.js`
- `index.html`
- `style.css`

### Tujuan:
Menemukan dan mendokumentasikan kesalahan logika, potensi bug, serta bagian yang perlu ditingkatkan berdasarkan struktur kode sebelum pengujian lebih lanjut dilakukan.

---

## 2. 🧠 OVERVIEW SISTEM

Aplikasi **Bookshelf App** adalah sistem manajemen buku berbasis web yang memungkinkan pengguna:
- Menambahkan buku
- Menghapus buku
- Mengubah status selesai/belum
- Menyimpan data buku di `localStorage`

Aplikasi ditulis menggunakan HTML, CSS, dan JavaScript tanpa framework eksternal.

---

## 3. 🧾 PREPARATION

Masing-masing reviewer membaca dan menelaah kode sumber secara mandiri.

### Temuan Awal:
| Baris | File       | Masalah                          | Rekomendasi                             |
|-------|------------|----------------------------------|------------------------------------------|
| 22    | `main.js`  | Tidak ada validasi input kosong | Tambahkan `if (title === "") return;`    |
| 61    | `main.js`  | Tidak ada try-catch di `saveData()` | Tambahkan pengecekan error storage   |
| 58    | `main.js`  | `removeBook()` tanpa konfirmasi | Tambahkan `confirm("Yakin ingin hapus?")`|
| -     | `index.html` | Tidak ada atribut `required` | Tambahkan ke input form                 |

---

## 4. 🔍 INSPECTION MEETING

**Tanggal:** 21 Mei 2025  
**Durasi:** 45 menit  
**Metode:** Google Meet  
**Notulen:**
- Semua masalah di atas disetujui untuk direvisi
- Disepakati untuk tidak menambahkan fitur baru saat inspeksi

---

## 5. 🔧 REWORK

Developer melakukan:
- Validasi input di `addBookToShelf()`
- Tambahan try-catch di `saveData()`
- Konfirmasi saat `removeBook()`
- `required` pada form input HTML

---

## 6. ✅ FOLLOW-UP

Moderator mengecek bahwa:
- Semua revisi telah di-*commit*
- Tidak ada bug baru
- Commit hash: `d7a41fe - perbaikan hasil formal inspection`

---

## 📎 REFERENSI
- Repository: [https://github.com/supyan38/SWQ-White-Box-testing](https://github.com/supyan38/SWQ-White-Box-testing)
- Standar inspeksi: IEEE 1028-2008
