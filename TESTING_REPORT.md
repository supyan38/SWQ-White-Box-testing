# 🧪 White Box Testing - Code Walkthrough: Bookshelf App

## 📂 Struktur Awal


---

## 🔍 Apa itu Code Walkthrough?

**Code Walkthrough** adalah teknik pengujian white box yang dilakukan dengan membaca dan meninjau kode secara manual untuk mencari kesalahan logika, struktur kontrol, atau error tersembunyi.

---

## 🔧 Langkah-langkah Walkthrough

### 1. Persiapan

```bash
npm install
const addBookHandler = (request, h) => {
    const { name, year, author, summary, publisher, pageCount, readPage, reading } = request.payload;

    if (!name) {
        return h.response({
            status: 'fail',
            message: 'Gagal menambahkan buku. Mohon isi nama buku',
        }).code(400);
    }

    if (readPage > pageCount) {
        return h.response({
            status: 'fail',
            message: 'Gagal menambahkan buku. readPage tidak boleh lebih besar dari pageCount',
        }).code(400);
    }

    const id = nanoid(16);
    ...
}
const getAllBooksHandler = (request, h) => {
    const { name, reading, finished } = request.query;

    let filteredBooks = books;
    if (name !== undefined) {
        filteredBooks = filteredBooks.filter((book) =>
            book.name.toLowerCase().includes(name.toLowerCase())
        );
    }
    ...

---

