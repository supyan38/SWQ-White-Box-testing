# 🧪 FORMAL INSPECTION REPORT - `main.js`

## 📅 Tanggal: 21 Mei 2025  
## 👥 Tim Review:
- Moderator: Supyan
- Developer: Supyan
- Reviewer: Santi, Didi

---

## 1. 📝 PLANNING
File yang diperiksa:
- `/main.js`

---

## 2. 🔍 OVERVIEW
Aplikasi ini adalah sistem pencatatan buku sederhana berbasis JavaScript. Fitur utama:
- Menambahkan buku
- Mengubah status buku (dibaca / belum dibaca)
- Menghapus buku
- Penyimpanan menggunakan `localStorage`

---

## 3. 📖 PREPARATION
Reviewer membaca kode secara mandiri dan mencatat temuan awal.

Contoh Temuan:
| Baris | Masalah                         | Saran Perbaikan                          |
|-------|----------------------------------|------------------------------------------|
| 22    | Tidak ada validasi input kosong | Tambahkan pengecekan `title !== ""`      |
| 61    | `localStorage` bisa gagal       | Tambahkan try-catch                      |

---

## 4. 🔎 INSPECTION MEETING
Dilakukan melalui Google Meet, dengan notulen sebagai berikut:
- Baris 22: Validasi kosong disetujui untuk ditambahkan
- Baris 61: Perlu try-catch untuk mencegah data korup

---

## 5. 🔧 REWORK
Developer menambahkan:
- Validasi input form
- Try-catch saat menggunakan `localStorage.setItem()`

---

## 6. ✅ FOLLOW-UP
Moderator memverifikasi bahwa perbaikan telah dilakukan dan commit sudah ditambahkan di branch `formal-inspection`.

