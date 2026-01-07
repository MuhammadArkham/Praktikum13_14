# Laporan Praktikum 13 & 14

**Nama:** M.ARKHAMULLAH RIFAI ASSHIDIQ

**NIM:** 312410545

**Kelas:** TI 24 A5

**Mata Kuliah:** PEMROGRAMAN WEB 1

---

## 1. Praktikum 13: Pagination (Pembagian Halaman)
**Tujuan:** Membatasi jumlah data yang tampil agar tidak menumpuk di satu halaman, serta membaginya menjadi beberapa halaman (Page 1, 2, dst).

###  Implementasi Kode
1.  **Konfigurasi Limit & Offset (`index.php`)**:
    * Menentukan variabel `$per_page = 5` (menampilkan 5 barang per halaman).
    * Menangkap parameter halaman dari URL (`$_GET['page']`). Jika tidak ada, default ke halaman 1.
    * Menghitung **Offset** (posisi awal data) dengan rumus: `($page - 1) * $per_page`.
    * *Contoh:* Halaman 1 offset 0, Halaman 2 offset 5.

2.  **Modifikasi Query SQL**:
    * Menambahkan klausa `LIMIT` pada query utama.
    * Syntax SQL menjadi: `SELECT * FROM barang LIMIT offset, limit`.

3.  **Navigasi Halaman**:
    * Menghitung total data menggunakan `COUNT(*)`.
    * Menghitung total halaman dengan fungsi `ceil()` (pembulatan ke atas).
    * Membuat *looping* tombol angka navigasi di bagian bawah tabel.

###  Alur Kerja
User membuka halaman -> Sistem menghitung total data -> Sistem memotong data menggunakan Query `LIMIT` -> Data ditampilkan sebagian sesuai halaman yang dipilih.

---

## 2. Praktikum 14: Searching (Pencarian Data)
**Tujuan:** Memudahkan pengguna mencari data barang spesifik berdasarkan nama barang atau kategori.

###  Implementasi Kode
1.  **Form Pencarian HTML**:
    * Menambahkan form dengan method `GET` agar kata kunci tampil di URL.
    * Input text diberi nama `name="q"`.

2.  **Logika Filter Query**:
    * Menambahkan logika pengecekan `if (isset($_GET['q']))`.
    * Jika ada input pencarian, variable `$sql_where` diisi dengan klausa `WHERE nama LIKE '%keyword%'`.
    * Query utama digabung dengan filter tersebut.

3.  **Integrasi Search & Pagination**:
    * Menjaga agar kata kunci pencarian tidak hilang saat user berpindah halaman.
    * Menambahkan parameter `&q=...` pada setiap link tombol pagination.
    * *Contoh URL Hasil:* `index.php?page=2&q=samsung`

###  Alur Kerja
User mengetik kata kunci -> Klik Cari -> URL berubah membawa parameter `?q=kata_kunci` -> Sistem menangkap `$_GET['q']` -> Query database difilter menggunakan `LIKE` -> Data yang cocok ditampilkan.

---

##  Hasil Implementasi

### 1. Tampilan Awal (Data Barang)
![Tampilan Awal](https://github.com/MuhammadArkham/Praktikum13_14/blob/main/FOTO/Screenshot%202026-01-07%20093340.png?raw=true)

### 2. Fitur Pagination (Navigasi Halaman)
![Fitur Pagination](https://github.com/MuhammadArkham/Praktikum13_14/blob/main/FOTO/Screenshot%202026-01-07%20093140.png?raw=true)

### 3. Fitur Pencarian Data
![Fitur Searching](https://github.com/MuhammadArkham/Praktikum13_14/blob/main/FOTO/Screenshot%202026-01-07%20093620.png?raw=true)
