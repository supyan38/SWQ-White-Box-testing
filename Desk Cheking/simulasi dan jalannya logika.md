🔎 Jalannya kode:
Event submit form ditangkap
addBook() dipanggil → membuat objek book dengan ID unik (timestamp)
Buku dimasukkan ke array books, disimpan ke localStorage
renderBooks() menggambar ulang tampilan rak buku

1. Saat halaman dimuat
DOMContentLoaded dipicu → loadFromLocalStorage() membaca data → renderBooks() menampilkan buku di dua rak.

2. Tambah Buku
Misal input:
Judul: "Laskar Pelangi"
Penulis: "Andrea Hirata"
Tahun: 2005
Checkbox: dicentang

3. Edit Buku
Tombol “Edit Buku” diklik → editBook() dipanggil
Popup muncul, pengguna ubah data → klik “Simpan”
Data diperbarui → localStorage diperbarui → renderBooks() dijalankan ulang

4. Toggle Selesai Dibaca
Klik “Selesai dibaca” → toggleBookCompletion() dipanggil
Status isComplete dibalik
Perubahan disimpan dan tampilan diperbarui

5. Hapus Buku
Klik tombol “Hapus Buku” → deleteBook() dipanggil
Buku dihapus dari array books
Data disimpan dan halaman diperbarui
