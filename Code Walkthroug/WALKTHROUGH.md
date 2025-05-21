# 📘 Code Walkthrough Report - Bookshelf App

## 👥 Tim Walkthrough
- **Reviewer 1**: Santi
---

## 🎯 Tujuan Walkthrough

Melakukan penelusuran menyeluruh terhadap struktur kode aplikasi **Bookshelf App** berbasis JavaScript guna:
- Menemukan kesalahan logika
- Memastikan setiap fungsi sesuai spesifikasi
- Menyusun dokumentasi White Box Testing yang sistematis

---

## 🧠 Overview Aplikasi

Bookshelf App adalah aplikasi manajemen daftar buku yang disimpan di `localStorage` browser. Fitur utama:
- Menambahkan buku
- Mengubah status dibaca/belum
- Menghapus buku
- Menyimpan data lokal tanpa server

---

## 🧾 Struktur Berkas yang Ditinjau

| File              | Deskripsi                                      |
|-------------------|-----------------------------------------------|
| `main.js`         | Script utama yang memuat logika aplikasi      |
| `index.html`      | Antarmuka pengguna dasar                      |
| `style.css`       | Tata letak dan gaya tampilan aplikasi         |

---

## 🔍 Prosedur Walkthrough

1. Membaca kode baris per baris (`main.js`)
2. Mengidentifikasi fungsi-fungsi utama
3. Menelusuri logika alur data
4. Menandai bagian kode yang berisiko error
5. Mencatat saran perbaikan dan anomali

---

## 🔧 Fungsi-Fungsi Utama yang Ditinjau

### 🧩 `addBookToShelf()`
- ⛳ Menambahkan data buku baru ke array dan menyimpannya ke `localStorage`.
- ✅ Fungsi sesuai, namun tidak ada validasi input kosong → *perlu perbaikan*.

### 🔁 `toggleBookStatus(bookId)`
- 🔄 Mengubah status `isCompleted` buku.
- ✅ Sesuai dengan logika UX, namun tidak mengubah tanggal modifikasi.

### ❌ `removeBook(bookId)`
- 🗑️ Menghapus buku berdasarkan ID dari array dan DOM.
- ⚠️ Tidak menampilkan konfirmasi → *berisiko salah hapus*.

### 💾 `saveData()`
- 📥 Menyimpan array ke `localStorage` dalam format JSON.
- ⚠️ Tidak ada `try-catch`, bisa error bila kuota storage penuh.

---

## ❗ Temuan dan Rekomendasi

| Baris | Masalah                            | Rekomendasi                                           |
|-------|------------------------------------|--------------------------------------------------------|
| 25    | Tidak ada validasi input judul     | Tambahkan validasi input `title !== ""`               |
| 58    | `removeBook` langsung hapus        | Tambahkan konfirmasi `confirm("Yakin?")`              |
| 78    | Tidak ada error handling storage   | Tambahkan blok `try-catch` pada `localStorage`       |
| 102   | Tidak ada filter pencarian         | Tambahkan fitur filter dengan `Array.filter()`        |

---

## ✅ Tindakan Perbaikan yang Dilakukan

- Menambahkan validasi input form sebelum `addBookToShelf()`
- Memasukkan dialog konfirmasi sebelum menghapus buku
- Menambahkan try-catch di `saveData()`
- Commit perbaikan: `3a1f4c2 - fix input validation & localStorage error handling`

---

## 📌 Catatan Tambahan

- Semua fungsi disusun secara modular dan rapi
- Event Listener sudah dipisah dengan baik dari logika bisnis
- Rekomendasi untuk refactor ke **OOP JavaScript (Class)** di masa depan

---

## 📎 Referensi
- Struktur aplikasi diambil dari repo: [`supyan38/SWQ-White-Box-testing`](https://github.com/supyan38/SWQ-White-Box-testing)
- Panduan white-box: IEEE Std 1028-2008

---

## ✍️ Disusun Oleh:
Supyan, Santi, Didi  
Program Studi Teknik Informatika – Semester 6
