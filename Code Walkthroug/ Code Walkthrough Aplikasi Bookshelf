## 📘 White Box Testing Code Walkthrough untuk Aplikasi Bookshelf

Dokumen ini adalah **walkthrough** White Box Testing yang disesuaikan dengan struktur dan fungsi pada aplikasi `bookshelf-app` yang Anda unggah.

---

### 🔍 1. Pendahuluan

1. **Tujuan**: Menguji logika internal file `main.js` (manajemen array `books`, interaksi dengan `localStorage`, DOM manipulation) agar memastikan fungsi bekerja sesuai ekspektasi.
2. **Ruang Lingkup**: Fungsi-fungsi di `main.js`:

   * `saveToLocalStorage()`
   * `loadFromLocalStorage()`
   * `addBook(title, author, year, isComplete)`
   * `toggleBookCompletion(bookId)`
   * `deleteBook(bookId)`
   * `editBook(bookId)` (logika popup & penyimpanan)
   * `renderBooks()` & `createBookElement(book)`
3. **Prasyarat**:

   * Node.js & npm terpasang.
   * Git di-setup pada repository.
   * Framework testing: [Jest](https://jestjs.io/) dan [`jsdom`](https://github.com/jsdom/jsdom).
   * File `main.js` diekspor sebagai modul (modifikasi kecil diperlukan).

### 📂 2. Struktur Repository (Setelah Setup Testing)

```
/ (root)
|-- README.md
|-- index.html
|-- styles.css
|-- main.js            ← fungsi aplikasi
|-- package.json       ← tambahkan dependensi jest, jsdom
|-- jest.config.js     ← konfigurasi tes (untuk jsdom)
|-- tests/
    |-- main.test.js   ← unit tests untuk fungsi di main.js
|-- assets/            ← FontAwesome dan lain-lain
```

**Catatan Setup**:

```bash
npm init -y
npm install --save-dev jest jsdom
```

**`package.json`** (tambah script):

```json
  "scripts": {
    "test": "jest",
    "coverage": "jest --coverage"
  }
```

**`jest.config.js`**:

```js
module.exports = {
  testEnvironment: 'jsdom',
};
```

---

### 🛠️ 3. Langkah-langkah White Box Testing

1. \*\*Modularisasi \*\***`main.js`**

   * Ubah file `main.js` agar ekspor fungsi:

     ```js
     // Di akhir main.js
     export {
       saveToLocalStorage,
       loadFromLocalStorage,
       addBook,
       toggleBookCompletion,
       deleteBook,
       editBook,
       renderBooks,
       createBookElement,
       books
     };
     ```

2. **Analisis Kode**

   * Buka `main.js`, pahami alur:

     * Operasi array `books`
     * Konversi data dan parsing JSON
     * Manipulasi DOM (popup edit)

3. **Penentuan Jalur Uji**

   * **`saveToLocalStorage()`** ➔ menulis `localStorage` dengan key `BOOKSHELF_APP`.
   * **`loadFromLocalStorage()`**:

     * Ketika `localStorage` kosong,
     * Ketika berisi data valid → memuat ke `books`.
   * **`addBook()`**:

     * Menambah objek `book` dengan id unik,
     * Memanggil `saveToLocalStorage()` dan `renderBooks()`.
   * **`toggleBookCompletion()`**:

     * Mengubah properti `isComplete`,
     * Tidak ada book dengan `bookId` yang tidak ada.
   * **`deleteBook()`**:

     * Menghapus berdasarkan `bookId`.
   * **`renderBooks()`**\*\* & \*\*\*\*`createBookElement()`\*\*:

     * Mencetak elemen DOM berdasarkan isi `books`.
   * **`editBook()`**:

     * Popup muncul,
     * Simpan perubahan memanggil `saveToLocalStorage()`.

4. **Desain Test Case**

   * Gunakan mocking `localStorage` (Jest sudah menyediakan jsdom).
   * Contoh *table* test cases:

   | Fungsi                      | Kondisi                                      | Output / Efek                                                                        |
   | --------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------------ |
   | `saveToLocalStorage()`      | `books = [{id:1}]`                           | `localStorage.getItem('BOOKSHELF_APP')==='[{"id":1}]'`                               |
   | `loadFromLocalStorage()`    | `localStorage['BOOKSHELF_APP']='[{"id":2}]'` | `books` array berisi objek `{id:2}`                                                  |
   | `addBook()`                 | `addBook('A','B','2020',false)`              | `books.length` bertambah; `books[...].title==='A'`; memanggil `renderBooks()`        |
   | `toggleBookCompletion()`    | `books=[{id:1,isComplete:false}]`            | `books[0].isComplete===true`                                                         |
   | `deleteBook()`              | `books=[{id:1},{id:2}]; deleteBook(1)`       | `books` hanya berisi objek dengan `id:2`                                             |
   | `renderBooks()`             | `books` berisi 1 item                        | DOM container memiliki 1 child                                                       |
   | `editBook()` (logika dasar) | Memanggil `editBook(unknownId)`              | Tidak melempar exception; tidak memanggil `saveToLocalStorage()` jika book tidak ada |

5. **Implementasi Test**

   * Contoh file: `tests/main.test.js`

     ```js
     import {
       saveToLocalStorage,
       loadFromLocalStorage,
       addBook,
       toggleBookCompletion,
       deleteBook,
       books
     } from '../main.js';

     beforeEach(() => {
       localStorage.clear();
       books.length = 0;
     });

     test('saveToLocalStorage writes correct JSON', () => {
       books.push({ id:1 });
       saveToLocalStorage();
       expect(localStorage.getItem('BOOKSHELF_APP')).toBe(JSON.stringify(books));
     });

     test('loadFromLocalStorage loads books', () => {
       localStorage.setItem('BOOKSHELF_APP', JSON.stringify([{id:2}]));
       loadFromLocalStorage();
       expect(books).toEqual([{id:2}]);
     });

     test('addBook adds new book object', () => {
       addBook('Title','Author','2021',true);
       expect(books.length).toBe(1);
       expect(books[0].title).toBe('Title');
     });

     test('toggleBookCompletion flips isComplete', () => {
       books.push({ id:10, isComplete: false });
       toggleBookCompletion(10);
       expect(books[0].isComplete).toBe(true);
     });

     test('deleteBook removes target book', () => {
       books.push({ id:5 }, { id:6 });
       deleteBook(5);
       expect(books).toHaveLength(1);
       expect(books[0].id).toBe(6);
     });
     ```

6. **Jalankan Test & Analisis Coverage**

```bash
npm test
npm run coverage
```

Pastikan coverage ≥ 80% untuk:

* Statement Coverage
* Branch Coverage
* Function Coverage
* Line Coverage

---

### ✅ 4. Dokumentasi Hasil

* Tambahkan screenshot laporan coverage di `docs/coverage.png` atau GitHub Wiki.
* Buat Issue/GitHub Project card untuk jalur yang belum teruji.
* Pastikan CI (GitHub Actions) menjalankan `npm test` pada setiap PR.

---

> *Dengan mengikuti walkthrough ini, Anda akan menguji secara menyeluruh logika internal aplikasi "Bookshelf" Anda dan menjaga kualitas kode di repositori GitHub.*

---

### 🚀 5. Commit dan Push ke GitHub

Setelah membuat dan menyimpan dokumen ini di root repo Anda (misal `docs/Whitebox_Testing_Walkthrough.md`), ikuti langkah berikut untuk commit & push ke GitHub:

1. **Tambahkan file ke staging**

   ```bash
   git add docs/Whitebox_Testing_Walkthrough.md
   ```
2. **Commit dengan pesan yang jelas**

   ```bash
   git commit -m "docs(test): add white box testing walkthrough for Bookshelf app"
   ```
3. **Push ke remote branch**

   ```bash
   git push origin docs/whitebox-testing
   ```
4. **Buat Pull Request (PR)**

   * Masuk ke GitHub, buka repository Anda.
   * Klik tombol **Compare & pull request**.
   * Isi judul PR: `docs: add white box testing walkthrough`.
   * Berikan deskripsi singkat tentang apa yang ditambahkan.
   * Submit PR untuk review tim.

> **Tips**: Gunakan nama branch deskriptif (`docs/whitebox-testing`) agar manajemen branch lebih terstruktur.
