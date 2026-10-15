# DOKUMEN EVALUASI PELATIHAN WEB DEVELOPER

- **Materi:** Pemrograman Web (PHP & MySQL), Pengujian (UAT), Deployment & Pemeliharaan Sistem
- **Jumlah Soal:** 20 Butir Pilihan Ganda (Pre-Test) & 20 Butir Pilihan Ganda (Post-Test)
- **Bobot Nilai:** 5 Poin / Soal (Total Nilai Maksimal: 100)
- **Waktu Pengerjaan:** 15 Menit

---

## KISI-KISI KESEIMBANGAN MATERI

| Nomor | Indikator Kompetensi | Fokus Soal Pre-Test | Fokus Soal Post-Test |
| :--- | :--- | :--- | :--- |
| **1–2** | Lingkungan Kerja & Koneksi DB | Fungsi utama PHP & `mysqli_connect()` | Paket web server lokal (XAMPP) & parameter koneksi |
| **3–5** | Eksekusi Query & Baca Data (`SELECT`) | `SELECT *`, `INSERT`, dan `mysqli_query()` | `SELECT ... WHERE`, `INSERT INTO`, dan `mysqli_fetch_assoc()` |
| **6–7** | Output, Format JSON & Variabel PHP | Cetak teks (`echo`) & penulisan `$variabel` | Konversi JSON (`json_encode()`) & superglobal `$_POST` |
| **8–10** | Struktur Tabel & Pembaruan (`UPDATE`) | `CREATE TABLE`, `mysqli_close()`, dan `UPDATE` | `ALTER TABLE`, tujuan tutup koneksi, dan risiko `UPDATE` tanpa `WHERE` |
| **11–14** | Autentikasi, Hapus Data & Keamanan | `isset()`, `DELETE`, *Prepared Statement*, `CREATE DATABASE` | Fitur login (`$_SESSION`), `DELETE FROM`, *hash* password, tipe data MySQL |
| **15–16** | Ruang Lingkup & Kualitas Proyek | Konsep ruang lingkup (*scope*) & kualitas proyek | Pengendalian perubahan proyek & efisiensi pemrosesan paralel |
| **17–18** | Pengujian (UAT) & Migrasi (*Cutover*) | Tujuan *User Acceptance Test* (UAT) & *cutover* | Pelaksana UAT & tujuan migrasi *localhost* ke server produksi |
| **19–20** | Pemantauan Server & Pemeliharaan | Monitoring *resource* server & konsep *maintenance* | Fungsi *alert notification* & perbedaan *update* vs *maintenance* |

---

## BAGIAN 1: SOAL PRE-TEST WEB DEVELOPER

### Petunjuk Pengerjaan:
1. Isilah nama lengkap dengan benar pada kolom yang tersedia.
2. Pilihlah salah satu jawaban yang Anda anggap paling tepat.
3. Waktu yang tersedia untuk mengerjakan soal adalah 15 menit.
4. Soal terdiri dari 20 butir pilihan ganda (masing-masing bernilai 5 poin).
5. Periksa kembali pekerjaan Anda sebelum menekan tombol Kirim/Submit.

---

### Daftar Soal Pre-Test

**1. Apa fungsi utama dari bahasa pemrograman PHP?**

- a. Membuat aplikasi desktop
- b. Membuat aplikasi mobile
- c. Membuat situs web dinamis
- d. Membuat sistem operasi

> **Kunci Jawaban:** c. Membuat situs web dinamis

---

**2. Fungsi `mysqli_connect()` pada PHP digunakan untuk:**

- a. Membuat query ke database
- b. Membuka koneksi ke server MySQL
- c. Menutup koneksi database
- d. Membuat tabel di database

> **Kunci Jawaban:** b. Membuka koneksi ke server MySQL

---

**3. Query SQL yang benar untuk menampilkan semua data dari tabel "products" adalah:**

- a. `SHOW * FROM products;`
- b. `SELECT * FROM products;`
- c. `GET * FROM products;`
- d. `DISPLAY * FROM products;`

> **Kunci Jawaban:** b. `SELECT * FROM products;`

---

**4. Perintah SQL untuk menambahkan data ke dalam tabel adalah:**

- a. `SELECT`
- b. `DELETE`
- c. `INSERT`
- d. `UPDATE`

> **Kunci Jawaban:** c. `INSERT`

---

**5. Apa fungsi dari perintah `mysqli_query()`?**

- a. Menjalankan query SQL ke database
- b. Menutup koneksi ke database
- c. Membuka koneksi ke database
- d. Mengecek apakah koneksi berhasil

> **Kunci Jawaban:** a. Menjalankan query SQL ke database

---

**6. Dalam PHP, untuk mencetak teks atau data ke layar dapat menggunakan:**

- a. `echo`
- b. `print_r`
- c. `printf`
- d. Semua benar

> **Kunci Jawaban:** d. Semua benar

---

**7. Bagaimana cara mendefinisikan variabel yang benar dalam PHP?**

- a. `var variabel = "nilai";`
- b. `int variabel = "nilai";`
- c. `$variabel = "nilai";`
- d. `String variabel = "nilai";`

> **Kunci Jawaban:** c. `$variabel = "nilai";`

---

**8. Perintah SQL untuk membuat tabel baru adalah:**

- a. `CREATE DATABASE`
- b. `CREATE TABLE`
- c. `ADD TABLE`
- d. `NEW TABLE`

> **Kunci Jawaban:** b. `CREATE TABLE`

---

**9. Fungsi `mysqli_close()` pada PHP digunakan untuk:**

- a. Membuka koneksi database
- b. Menutup koneksi database
- c. Menjalankan query ke database
- d. Menampilkan error dari database

> **Kunci Jawaban:** b. Menutup koneksi database

---

**10. Perintah SQL yang digunakan untuk memperbarui atau mengubah data yang sudah ada di dalam tabel adalah:**

- a. `UPDATE`
- b. `MODIFY`
- c. `REPLACE`
- d. `CHANGE`

> **Kunci Jawaban:** a. `UPDATE`

---

**11. Dalam PHP, apa fungsi dari `isset()`?**

- a. Mengecek apakah variabel sudah dihapus
- b. Mengecek apakah variabel terdefinisi dan tidak bernilai null
- c. Menghapus variabel
- d. Mengubah tipe data variabel

> **Kunci Jawaban:** b. Mengecek apakah variabel terdefinisi dan tidak bernilai null

---

**12. Untuk menghapus baris data dari tabel di database, perintah SQL yang digunakan adalah:**

- a. `REMOVE`
- b. `DELETE`
- c. `DROP`
- d. `ALTER`

> **Kunci Jawaban:** b. `DELETE`

---

**13. Metode yang direkomendasikan untuk mencegah serangan SQL Injection di MySQLi adalah:**

- a. Menggunakan query string biasa
- b. Menggunakan prepared statement
- c. Menambahkan titik koma di akhir query
- d. Menutup koneksi setelah query

> **Kunci Jawaban:** b. Menggunakan prepared statement

---

**14. Perintah `CREATE DATABASE` pada SQL digunakan untuk:**

- a. Membuat tabel baru
- b. Membuat database baru
- c. Menghapus database
- d. Memperbarui struktur database

> **Kunci Jawaban:** b. Membuat database baru

---

**15. Dalam pengembangan proyek aplikasi web, manajemen ruang lingkup proyek (project scope) bertujuan untuk:**

- a. Menentukan merek komputer yang harus dibeli oleh klien
- b. Memastikan batasan fitur yang dikerjakan sesuai dengan kesepakatan awal
- c. Mengganti bahasa pemrograman di tengah proyek secara sepihak
- d. Menghapus seluruh dokumentasi setelah aplikasi selesai

> **Kunci Jawaban:** b. Memastikan batasan fitur yang dikerjakan sesuai dengan kesepakatan awal

---

**16. Fokus utama dari manajemen kualitas perangkat lunak dalam pengembangan aplikasi web adalah:**

- a. Memastikan aplikasi bebas dari bug kritis serta memenuhi standar performa dan kebutuhan fungsional
- b. Memperbanyak jumlah halaman web meskipun tidak dibutuhkan pengguna
- c. Membatasi akses internet bagi tim pengembang
- d. Menggunakan ukuran file gambar sebesar mungkin pada halaman utama

> **Kunci Jawaban:** a. Memastikan aplikasi bebas dari bug kritis serta memenuhi standar performa dan kebutuhan fungsional

---

**17. Tahapan User Acceptance Test (UAT) sebelum aplikasi web dirilis bertujuan untuk:**

- a. Menguji apakah pengguna akhir dapat menggunakan sistem sesuai kebutuhan bisnis mereka
- b. Menginstal ulang sistem operasi pada komputer pengembang
- c. Membuat skema tabel baru di dalam database lokal
- d. Menghapus kode program yang sudah selesai diuji

> **Kunci Jawaban:** a. Menguji apakah pengguna akhir dapat menggunakan sistem sesuai kebutuhan bisnis mereka

---

**18. Proses cutover atau migrasi aplikasi dalam tahapan deployment merujuk pada aktivitas:**

- a. Memindahkan aplikasi dari lingkungan pengembangan lokal (localhost) ke server produksi (online)
- b. Mematikan server secara permanen karena proyek telah selesai
- c. Menghapus seluruh data pengguna lama tanpa membuat cadangan (backup)
- d. Mengubah desain logo perusahaan pada dokumen kontrak

> **Kunci Jawaban:** a. Memindahkan aplikasi dari lingkungan pengembangan lokal (localhost) ke server produksi (online)

---

**19. Mengapa pemantauan sumber daya (resource monitoring) seperti penggunaan CPU, RAM, dan ruang penyimpanan penting dilakukan pada server aplikasi?**

- a. Agar tampilan warna situs web berubah secara otomatis setiap hari
- b. Untuk mendeteksi beban berlebih sejak dini dan mencegah server mengalami kelumpuhan (down)
- c. Untuk menggantikan fungsi database MySQL dalam menyimpan data
- d. Agar pengguna tidak perlu memasukkan kata sandi saat login

> **Kunci Jawaban:** b. Untuk mendeteksi beban berlebih sejak dini dan mencegah server mengalami kelumpuhan (down)

---

**20. Kegiatan pemeliharaan perangkat lunak (software maintenance) setelah aplikasi web beroperasi meliputi:**

- a. Perbaikan bug atau kendala teknis yang ditemukan serta menjaga stabilitas sistem
- b. Pembuatan proposal penawaran proyek kepada calon klien baru
- c. Penentuan struktur organisasi perusahaan klien
- d. Pembelian meja dan kursi kerja untuk ruang server

> **Kunci Jawaban:** a. Perbaikan bug atau kendala teknis yang ditemukan serta menjaga stabilitas sistem

---

## BAGIAN 2: SOAL POST-TEST WEB DEVELOPER

### Petunjuk Pengerjaan:
1. Isilah nama lengkap dengan benar pada kolom yang tersedia.
2. Pilihlah salah satu jawaban yang Anda anggap paling tepat.
3. Waktu yang tersedia untuk mengerjakan soal adalah 15 menit.
4. Soal terdiri dari 20 butir pilihan ganda (masing-masing bernilai 5 poin).
5. Periksa kembali pekerjaan Anda sebelum menekan tombol Kirim/Submit.

---

### Daftar Soal Post-Test

**1. Paket aplikasi web server lokal (mencakup Apache dan MySQL) yang umum digunakan untuk pengembangan web pada sistem operasi Windows adalah:**

- a. Laravel
- b. XAMPP
- c. Python
- d. Figma

> **Kunci Jawaban:** b. XAMPP

---

**2. Saat memanggil fungsi `mysqli_connect()` di PHP untuk terhubung ke database, informasi utama yang harus disertakan sebagai parameter adalah:**

- a. Nama domain, alamat email, nomor telepon, dan kode pos
- b. Host server, username database, password, dan nama database
- c. Nama file HTML, ukuran layar, jenis huruf, dan warna latar
- d. Alamat IP pengguna, jenis browser, dan sistem operasi

> **Kunci Jawaban:** b. Host server, username database, password, dan nama database

---

**3. Query SQL yang tepat untuk menampilkan data pengguna dari tabel `users` yang hanya memiliki status "aktif" adalah:**

- a. `SELECT * FROM users WHERE status = 'aktif';`
- b. `SHOW * FROM users IF status = 'aktif';`
- c. `GET users WHERE status = 'aktif';`
- d. `SELECT ALL FROM users HAVING status = 'aktif';`

> **Kunci Jawaban:** a. `SELECT * FROM users WHERE status = 'aktif';`

---

**4. Dalam eksekusi perintah SQL, pernyataan `INSERT INTO` digunakan ketika pengembang ingin:**

- a. Memantau penggunaan memori pada server aplikasi
- b. Menambahkan baris data baru ke dalam tabel database
- c. Menghapus data lama yang sudah tidak terpakai
- d. Mengubah struktur kolom pada tabel yang sudah ada

> **Kunci Jawaban:** b. Menambahkan baris data baru ke dalam tabel database

---

**5. Setelah menjalankan query `SELECT` menggunakan `mysqli_query()`, fungsi PHP yang digunakan untuk mengambil baris hasilnya menjadi associative array adalah:**

- a. `mysqli_connect_error()`
- b. `mysqli_fetch_assoc()`
- c. `mysqli_num_fields()`
- d. `mysqli_close()`

> **Kunci Jawaban:** b. `mysqli_fetch_assoc()`

---

**6. Pada pengembangan API atau pertukaran data di PHP, fungsi `json_encode()` digunakan untuk:**

- a. Mengubah array atau objek PHP menjadi string berformat JSON
- b. Menyimpan file gambar langsung ke dalam database MySQL
- c. Mengenkripsi password pengguna sebelum disimpan ke tabel
- d. Membuka koneksi baru ke server database eksternal

> **Kunci Jawaban:** a. Mengubah array atau objek PHP menjadi string berformat JSON

---

**7. Variabel superglobal pada PHP yang digunakan untuk menangkap data sensitif (seperti email dan password) yang dikirim dari formulir HTML dengan `method="POST"` adalah:**

- a. `$_GET`
- b. `$_POST`
- c. `$_SERVER`
- d. `$_FILES`

> **Kunci Jawaban:** b. `$_POST`

---

**8. Perintah SQL `ALTER TABLE` digunakan oleh pengembang database ketika perlu:**

- a. Menghapus seluruh isi tabel beserta strukturnya
- b. Memodifikasi struktur tabel yang sudah ada, seperti menambah atau mengubah kolom
- c. Membuat database baru di dalam server lokal
- d. Menampilkan daftar pengguna yang sedang aktif

> **Kunci Jawaban:** b. Memodifikasi struktur tabel yang sudah ada, seperti menambah atau mengubah kolom

---

**9. Mengapa praktik menutup koneksi database menggunakan `mysqli_close()` setelah seluruh proses selesai dianggap baik dalam pemrograman web?**

- a. Untuk membebaskan sumber daya (resource) memori dan koneksi pada server database
- b. Agar seluruh data di dalam tabel terhapus secara otomatis saat halaman ditutup
- c. Untuk mengubah tampilan halaman web menjadi mode gelap (dark mode)
- d. Agar file PHP tidak bisa dibuka melalui web browser

> **Kunci Jawaban:** a. Untuk membebaskan sumber daya (resource) memori dan koneksi pada server database

---

**10. Apa dampak yang akan terjadi apabila kita menjalankan perintah `UPDATE users SET role = 'admin';` tanpa menyertakan klausa `WHERE`?**

- a. Query gagal dijalankan dan menampilkan pesan error sintaks
- b. Seluruh baris data pada tabel `users` akan berubah kolom role-nya menjadi 'admin'
- c. Hanya baris pertama saja yang berubah menjadi 'admin'
- d. Tabel `users` akan terhapus dari database

> **Kunci Jawaban:** b. Seluruh baris data pada tabel `users` akan berubah kolom role-nya menjadi 'admin'

---

**11. Dalam pengembangan aplikasi web dengan PHP, fitur untuk menyimpan status autentikasi pengguna yang sudah berhasil login antar-halaman menggunakan mekanisme:**

- a. Update
- b. Destroy
- c. Insert
- d. Session

> **Kunci Jawaban:** d. Session

---

**12. Perintah DML (Data Manipulation Language) pada SQL yang benar untuk menghapus data transaksi tertentu dari dalam tabel database adalah:**

- a. `DESTROY FROM transaksi WHERE id = 1;`
- b. `DELETE FROM transaksi WHERE id = 1;`
- c. `REMOVE TABLE transaksi WHERE id = 1;`
- d. `DROP FROM transaksi WHERE id = 1;`

> **Kunci Jawaban:** b. `DELETE FROM transaksi WHERE id = 1;`

---

**13. Sebagai bagian dari pengelolaan risiko keamanan informasi pada aplikasi web, cara yang aman untuk menyimpan kata sandi (password) pengguna di database adalah:**

- a. Menyimpannya dalam bentuk teks biasa (plain text) agar mudah dibaca admin
- b. Melakukan proses hashing terlebih dahulu (misalnya dengan fungsi `password_hash()`)
- c. Menampilkan kata sandi tersebut pada URL halaman profil
- d. Menyimpan kata sandi di dalam file CSS eksternal

> **Kunci Jawaban:** b. Melakukan proses hashing terlebih dahulu (misalnya dengan fungsi `password_hash()`)

---

**14. Pada database MySQL, pasangan tipe data yang paling tepat untuk menyimpan isi artikel berita yang panjang dan harga barang dalam angka bulat secara berurutan adalah:**

- a. `CHAR` dan `VARCHAR`
- b. `TEXT` dan `INT`
- c. `BOOLEAN` dan `DATE`
- d. `INT` dan `TIME`

> **Kunci Jawaban:** b. `TEXT` dan `INT`

---

**15. Pengendalian perubahan (change control) dalam manajemen ruang lingkup proyek dilakukan agar:**

- a. Proyek tetap berjalan terarah sesuai rencana pengembangan dan terhindar dari penambahan fitur liar (scope creep)
- b. Pengembang bebas mengganti tujuan utama aplikasi tanpa sepengetahuan pemilik proyek
- c. Spesifikasi perangkat keras komputer pengguna dapat ditentukan secara sepihak
- d. Pengujian aplikasi tidak perlu lagi dilakukan sebelum rilis

> **Kunci Jawaban:** a. Proyek tetap berjalan terarah sesuai rencana pengembangan dan terhindar dari penambahan fitur liar (scope creep)

---

**16. Apa alasan utama diterapkannya pemrograman paralel (parallel programming) pada sistem komputasi berskala besar?**

- a. Memperbaiki kesalahan penulisan sintaks HTML secara otomatis
- b. Meningkatkan efisiensi waktu eksekusi dan performa komputasi dengan membagi beban tugas secara bersamaan
- c. Mengurangi biaya langganan nama domain tahunan
- d. Mempercepat koneksi jaringan internet di sisi pengguna

> **Kunci Jawaban:** b. Meningkatkan efisiensi waktu eksekusi dan performa komputasi dengan membagi beban tugas secara bersamaan

---

**17. Pengujian User Acceptance Test (UAT) pada tahap akhir pengembangan bertujuan untuk memastikan sistem telah sesuai dengan kebutuhan bisnis, dan pengujian ini divalidasi oleh:**

- a. Teknisi jaringan internet gedung
- b. Pengguna akhir (end-user) atau perwakilan pemilik sistem (client)
- c. Penyedia layanan listrik server
- d. Mesin pencari (search engine) secara otomatis

> **Kunci Jawaban:** b. Pengguna akhir (end-user) atau perwakilan pemilik sistem (client)

---

**18. Tujuan utama dilakukannya tahapan cutover atau migrasi aplikasi web dari server lokal (localhost) ke server produksi (hosting/cloud) adalah:**

- a. Agar aplikasi dapat diakses dan digunakan secara luas oleh pengguna melalui jaringan internet
- b. Untuk menentukan arsitektur perangkat keras komputer pribadi pengembang
- c. Untuk menghentikan seluruh layanan aplikasi secara permanen
- d. Agar kode sumber aplikasi tidak perlu lagi dihubungkan dengan database

> **Kunci Jawaban:** a. Agar aplikasi dapat diakses dan digunakan secara luas oleh pengguna melalui jaringan internet

---

**19. Penerapan fitur alert notification (notifikasi peringatan) pada sistem pemantauan server bertujuan untuk:**

- a. Memberikan peringatan cepat kepada tim teknis apabila aplikasi mengalami gangguan, error kritis, atau lonjakan beban
- b. Mengirimkan iklan promosi produk kepada seluruh pengunjung situs web
- c. Menggantikan proses debugging kode pada tahap awal penulisan program
- d. Menentukan anggaran pembelian perangkat keras kantor

> **Kunci Jawaban:** a. Memberikan peringatan cepat kepada tim teknis apabila aplikasi mengalami gangguan, error kritis, atau lonjakan beban

---

**20. Apa perbedaan utama antara pembaruan perangkat lunak (software update) dan pemeliharaan perangkat lunak (software maintenance)?**

- a. Pembaruan berfokus pada penambahan fitur baru atau peningkatan fungsi, sedangkan pemeliharaan berfokus pada perbaikan bug dan menjaga kestabilan teknis
- b. Pembaruan dilakukan oleh pengguna akhir, sedangkan pemeliharaan dilakukan oleh pelanggan
- c. Pembaruan hanya memperbaiki bug kecil, sedangkan pemeliharaan merombak seluruh bisnis perusahaan
- d. Tidak ada perbedaan, keduanya merupakan istilah untuk proses penghapusan aplikasi

> **Kunci Jawaban:** a. Pembaruan berfokus pada penambahan fitur baru atau peningkatan fungsi, sedangkan pemeliharaan berfokus pada perbaikan bug dan menjaga kestabilan teknis

---

## REKAPITULASI KUNCI JAWABAN

| No | Kunci Pre-Test | Kunci Post-Test | Topik Bahasan |
| :-: | :-: | :-: | :--- |
| **1** | **C** | **B** | Dasar PHP & Web Server Lokal |
| **2** | **B** | **B** | Koneksi Database (`mysqli_connect`) |
| **3** | **B** | **A** | Query `SELECT` pada SQL |
| **4** | **C** | **B** | Query `INSERT` pada SQL |
| **5** | **A** | **B** | Eksekusi & Pengambilan Data Query MySQLi |
| **6** | **D** | **A** | Output PHP & Format Data JSON |
| **7** | **C** | **B** | Variabel Dasar & Variabel Superglobal PHP |
| **8** | **B** | **B** | Pembuatan & Modifikasi Struktur Tabel (`DDL`) |
| **9** | **B** | **A** | Penutupan Koneksi Database (`mysqli_close`) |
| **10** | **A** | **B** | Pembaruan Data (`UPDATE`) pada SQL |
| **11** | **B** | **D** | Pemeriksaan Variabel (`isset`) & Autentikasi (`Session`) |
| **12** | **B** | **B** | Penghapusan Data (`DELETE`) pada SQL |
| **13** | **B** | **B** | Keamanan Aplikasi (*SQL Injection* & *Password Hashing*) |
| **14** | **B** | **B** | Pembuatan Database & Tipe Data MySQL |
| **15** | **B** | **A** | Manajemen Ruang Lingkup Proyek (*Project Scope*) |
| **16** | **A** | **B** | Kualitas Perangkat Lunak & Efisiensi Komputasi |
| **17** | **A** | **B** | *User Acceptance Test* (UAT) |
| **18** | **A** | **A** | *Cutover* & Migrasi ke Server Produksi (*Deployment*) |
| **19** | **B** | **A** | *Resource Monitoring* & *Alert Notification* |
| **20** | **A** | **A** | Pemeliharaan (*Maintenance*) vs Pembaruan (*Update*) |
