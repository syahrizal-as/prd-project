# Keamanan Data Saat Menggunakan AI

**Panduan singkat untuk peserta sharing session**

## 1. Apakah data yang diunggah ke AI aman?

Keamanan data bergantung pada platform AI yang digunakan, jenis akun,
pengaturan privasi, kebijakan penyedia layanan, serta jenis informasi
yang diunggah.

Saat kita mengunggah dokumen atau menempelkan teks ke layanan AI
berbasis cloud, informasi tersebut dikirim ke sistem penyedia layanan
untuk diproses. Data dapat diproses atau disimpan sesuai ketentuan
layanan yang berlaku.

Karena itu, jangan berasumsi bahwa:

-   Semua platform AI memiliki kebijakan privasi yang sama.
-   Semua data yang diunggah otomatis digunakan untuk melatih model AI.
-   Semua data yang diunggah otomatis langsung dihapus setelah jawaban
    diberikan.
-   Akun berbayar personal pasti memiliki perlindungan yang sama dengan
    layanan bisnis atau enterprise.

**Prinsip utama: jangan mengunggah informasi rahasia sebelum memahami
kebijakan dan mendapatkan izin yang diperlukan.**

## 2. Data apa yang perlu dilindungi?

Dalam pekerjaan profesional, khususnya pajak dan akuntansi,
berhati-hatilah terhadap informasi berikut:

-   Identitas pribadi: NIK, NPWP, nomor telepon, alamat, dan tanggal
    lahir.
-   Informasi keuangan: nomor rekening, mutasi bank, gaji, dan detail
    transaksi.
-   Dokumen perpajakan: SPT, bukti potong, faktur, dan dokumen pendukung
    milik klien.
-   Informasi perusahaan: laporan keuangan internal, daftar pelanggan,
    kontrak, dan strategi bisnis.
-   Kredensial akses: kata sandi, API key, token, kode OTP, dan data
    autentikasi.

Jangan memasukkan kata sandi, API key, token, atau kode OTP ke dalam
percakapan AI.

## 3. Cara lebih aman menggunakan AI

### A. Samarkan informasi identitas

Ganti identitas asli dengan label umum sebelum menggunakan data untuk
analisis.

  Sebelum disamarkan           Setelah disamarkan
  ---------------------------- -------------------------------------
  Nama klien sebenarnya        Klien A
  Nama perusahaan sebenarnya   Perusahaan X
  NIK atau NPWP                Hapus atau ganti dengan `[DIHAPUS]`
  Nomor rekening               Hapus atau ganti dengan `[DIHAPUS]`
  Alamat lengkap               Hapus jika tidak diperlukan

Catatan: mengganti nama saja belum tentu cukup. Kombinasi informasi
lain, seperti lokasi, jabatan, tanggal, atau nominal yang sangat
spesifik, masih dapat mengidentifikasi seseorang atau perusahaan.

### B. Gunakan data seminimal mungkin

Berikan hanya informasi yang diperlukan untuk menyelesaikan tugas. Jika
ingin meminta AI membuat format laporan, biasanya kita tidak perlu
mengunggah seluruh dokumen klien.

### C. Periksa platform dan pengaturannya

Sebelum menggunakan layanan AI:

1.  Pastikan platform tersebut diizinkan oleh organisasi atau
    perusahaan.
2.  Baca kebijakan privasi dan ketentuan penggunaan.
3.  Periksa pengaturan penggunaan data untuk peningkatan atau pelatihan
    model.
4.  Pahami kebijakan retensi dan penghapusan data.
5.  Periksa pengaturan akses akun, riwayat percakapan, dan fitur
    berbagi.
6.  Gunakan layanan bisnis atau enterprise yang telah disetujui
    organisasi jika pekerjaan memerlukan perlindungan dan kontrol
    tambahan.

Layanan bisnis atau API dapat memiliki ketentuan berbeda dari layanan
personal. Jangan menyimpulkan tingkat perlindungan hanya dari label
gratis atau berbayar; periksa ketentuan layanan yang benar-benar
digunakan.

### D. Ikuti aturan kerahasiaan organisasi

Jika data berasal dari klien atau perusahaan, pastikan penggunaannya
sesuai perjanjian kerahasiaan, kebijakan internal, ketentuan hukum yang
berlaku, dan persetujuan yang diperlukan.

## 4. Contoh penggunaan yang lebih aman

**Situasi:** Peserta ingin meminta AI membantu merangkum transaksi.

Hindari mengunggah dokumen asli yang memuat nama klien, nomor rekening,
NPWP, dan informasi rahasia lainnya.

Sebagai alternatif, siapkan data simulasi atau data yang sudah
disamarkan:

``` text
Perusahaan: Perusahaan X
Periode: Januari 2026

Total transaksi: Rp125.000.000
Jumlah transaksi: 48
Kategori transaksi:
- Operasional: Rp45.000.000
- Persediaan: Rp60.000.000
- Lainnya: Rp20.000.000

Tugas:
Buat ringkasan berdasarkan data di atas.
Jangan menambahkan informasi yang tidak tersedia.
```

Dengan cara ini, AI dapat membantu mengolah informasi yang relevan tanpa
perlu menerima identitas asli klien.

## 5. Apakah layanan AI gratis, personal, bisnis, dan API berbeda?

Ya. Ketentuan penggunaan data dapat berbeda menurut produk dan jenis
akun.

  -----------------------------------------------------------------------
  Jenis layanan                       Hal yang perlu diperhatikan
  ----------------------------------- -----------------------------------
  AI gratis atau personal             Periksa pengaturan privasi,
                                      penggunaan data, dan kebijakan
                                      layanan.

  AI berbayar personal                Pembayaran tidak otomatis berarti
                                      data mendapat perlindungan setara
                                      layanan organisasi.

  AI Business atau Enterprise         Umumnya menyediakan kontrol dan
                                      ketentuan perlindungan data untuk
                                      organisasi. Tetap periksa
                                      konfigurasi dan ketentuannya.

  AI melalui API                      Periksa ketentuan pemrosesan,
                                      retensi, logging, dan pengelolaan
                                      data dari penyedia API.
  -----------------------------------------------------------------------

**Contoh:** Pada ChatGPT, penggunaan konten untuk peningkatan model
berbeda menurut jenis layanan dan pengaturan. OpenAI menyatakan bahwa
data dari ChatGPT Business dan Enterprise tidak digunakan untuk melatih
model secara default. Namun, organisasi tetap perlu memperhatikan
pengaturan, akses, penyimpanan, dan kebijakan yang berlaku.

Kebijakan penyedia layanan dapat berubah. Selalu periksa dokumentasi
resmi terbaru sebelum mengirim data pekerjaan.

## 6. Lima prinsip sebelum mengunggah data

1.  **Kenali datanya.** Apakah informasi tersebut publik, internal,
    rahasia, atau data pribadi?
2.  **Periksa izinnya.** Apakah penggunaan layanan AI diperbolehkan oleh
    organisasi dan pemilik data?
3.  **Samarkan identitas.** Hapus informasi sensitif yang tidak
    diperlukan.
4.  **Pilih layanan yang sesuai.** Periksa kebijakan privasi, retensi,
    dan kontrol akses.
5.  **Verifikasi hasilnya.** AI dapat keliru. Manusia tetap bertanggung
    jawab memeriksa hasil sebelum digunakan atau dibagikan.

## 7. Jika ragu, apa yang harus dilakukan?

Jika tidak yakin apakah suatu dokumen boleh diunggah:

-   Jangan unggah terlebih dahulu.
-   Tanyakan kepada atasan atau penanggung jawab keamanan informasi.
-   Gunakan data simulasi atau data yang telah disamarkan.
-   Konsultasikan dengan tim IT, legal, atau pengelola perlindungan data
    organisasi.

## Kesimpulan

AI dapat membantu pekerjaan menjadi lebih cepat, tetapi pengguna tetap
bertanggung jawab atas data yang diberikan kepada layanan AI.

> **AI boleh membantu mengolah informasi, tetapi bukan berarti semua
> informasi boleh diberikan kepada AI.**

Gunakan AI secara bijak: lindungi data klien, patuhi kebijakan
organisasi, dan lakukan pemeriksaan manusia sebelum hasilnya digunakan.
