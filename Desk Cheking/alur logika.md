| Fungsi                   | Apakah bekerja sesuai alur logika? | Catatan                                 |
| ------------------------ | ---------------------------------- | --------------------------------------- |
| `addBook()`              | ✅                                  | Mengatur ID unik, tipe data benar       |
| `toggleBookCompletion()` | ✅                                  | Mengubah boolean `isComplete`           |
| `deleteBook()`           | ✅                                  | Menghapus dengan `filter()`             |
| `editBook()`             | ✅                                  | Menggunakan popup dan event listener    |
| `renderBooks()`          | ✅                                  | Membersihkan list dan menambahkan ulang |
| `loadFromLocalStorage()` | ✅                                  | JSON.parse bekerja aman jika data ada   |
| `saveToLocalStorage()`   | ✅                                  | Menyimpan array sebagai string          |
