# Product Requirement Document (PRD) & Database Schema
## Cloud-Based Accounting Software (SaaS)

---

## 1. Document Overview

* **Product Name:** AccuCloud / Smart Ledger Engine
* **Target Audience:** UMKM, Perusahaan Menengah (SMEs), Konsultan Pajak & Akuntan
* **Platform:** Web Application (Responsive) & API Gateway
* **Document Version:** v1.1.0
* **Author:** Lead Product Manager & System Architect
* **Last Updated:** 01-08-2026

### Changelog

| Version | Tanggal | Perubahan |
|---|---|---|
| v1.0.0 | - | Versi awal PRD & schema |
| v1.1.0 | 01-08-2026 | Tambah tabel pajak (tax_rates, invoice_taxes), payments & payment_allocations, bank_accounts/bank_statements/reconciliation_entries, sales_orders & purchase_orders, exchange_rates, audit_logs, roles, fiscal_periods; tambah kolom multi-currency, tax_invoice_number (e-Faktur), source_type, cash_flow_category, normal_balance, updated_at/deleted_at; tambah Row Level Security & aturan validasi double-entry; tambah FR pajak, multi-currency, import, dashboard, audit trail |

---

## 2. Executive Summary & Vision

Produk ini dirancang sebagai platform akuntansi berbasis cloud (*SaaS*) yang intuitif, aman, dan mematuhi standar akuntansi Indonesia (PSAK). Fokus utama platform ini adalah otomatisasi pembukuan, pencatatan transaksi multi-mata uang, rekonsiliasi bank otomatis, serta integrasi pelaporan pajak (e-Faktur & e-Bupot). Target kompetitif: **Jurnal.id / Accurate Online** — menyasar segmen SME & konsultan pajak yang butuh pembukuan proper + kepatuhan pajak, bukan sekadar pencatatan transaksi.

---

## 3. Product Goals & Target Metrics

1. **Efisiensi Waktu:** Mengurangi waktu proses pembukuan bulanan hingga 60% melalui otomatisasi pencatatan dan rekonsiliasi.
2. **Kepatuhan Pajak:** Memfasilitasi ekspor data transaksi ke format standar PPN & PPh (e-Faktur & e-Bupot) secara presisi.
3. **Kemudahan Kolaborasi:** Memungkinkan pemilik bisnis, staf keuangan, dan konsultan pajak bekerja dalam satu platform dengan hak akses berbasis peran (RBAC).
4. **Onboarding Cepat:** Import data Excel (COA, kontak, saldo awal, transaksi) dengan tingkat keberhasilan mapping ≥ 95% untuk mempercepat migrasi dari Excel/software lama.
5. **Akurasi Data:** 100% jurnal yang diposting harus balance (debit = kredit); nol transaksi nyangkut di period closing.

---

## 4. Key Features & Functional Requirements

### 4.1. General Ledger & Chart of Accounts (CoA)
* **FR-GL-001:** Pengelolaan Bagan Akun (Chart of Accounts) standar sesuai PSAK dengan struktur hirarkis (Header vs Account).
* **FR-GL-002:** Pencatatan Jurnal Umum (*General Journal*) secara manual dan otomatis dari modul pembantu (Penjualan, Pembelian, Kas/Bank).
* **FR-GL-003:** Penguncian Buku Kas/Periode (*Period Closing*) untuk mencegah perubahan data pada periode yang telah ditutup.
* **FR-GL-004:** Setiap akun memiliki *normal balance* (DEBIT/CREDIT) dan klasifikasi arus kas (Operating/Investing/Financing) untuk mendukung validasi jurnal & laporan arus kas.
* **FR-GL-005:** Koreksi data finansial pasca-posting hanya melalui *reversal entry* (jurnal pembalik) — tidak ada UPDATE langsung pada jurnal yang sudah diposting.

### 4.2. Sales & Accounts Receivable (Piutang Usaha)
* **FR-AR-001:** Pembuatan Penawaran (*Quotation*), Pesanan Penjualan (*Sales Order*), dan Faktur Penjualan (*Sales Invoice*).
* **FR-AR-002:** Tracking status pembayaran faktur (Draft, Unpaid, Partially Paid, Paid, Overdue, Cancelled).
* **FR-AR-003:** Penerimaan Pembayaran (*Customer Receipt*) dengan alokasi piutang multi-faktur.
* **FR-AR-004:** Faktur menyimpan nomor seri e-Faktur (tax invoice number) untuk keperluan pelaporan PPN.

### 4.3. Purchasing & Accounts Payable (Hutang Usaha)
* **FR-AP-001:** Pembuatan Pesanan Pembelian (*Purchase Order*) dan Tagihan Pemasok (*Vendor Bill*).
* **FR-AP-002:** Pelunasan Hutang (*Vendor Payment*) dan pencatatan potongan/diskon pembelian.
* **FR-AP-003:** Pencatatan PPN Masukan (Input VAT) dari tagihan pemasok untuk dikreditkan pada SPT PPN.

### 4.4. Cash & Bank Management
* **FR-CB-001:** Pengelolaan akun Kas, Bank, dan e-Wallet (GoPay, OVO, dll).
* **FR-CB-002:** Import rekening koran (Format CSV/Excel/MT940) dan pencocokan otomatis (*Bank Reconciliation*).
* **FR-CB-003:** Pencatatan Transfer Antar Bank dan Biaya Admin.
* **FR-CB-004:** Setiap rekening bank memiliki saldo awal dan mata uang sendiri.

### 4.5. Financial Reporting
* **FR-REP-001:** Laporan Laba Rugi (*Profit and Loss / Income Statement*).
* **FR-REP-002:** Laporan Neraca (*Balance Sheet*).
* **FR-REP-003:** Laporan Arus Kas (*Cash Flow Statement* - Direct & Indirect) — klasifikasi berdasarkan kategori arus kas per akun.
* **FR-REP-004:** Laporan Buku Besar (*General Ledger Detail*) dan Neraca Saldo (*Trial Balance*).
* **FR-REP-005:** Laporan Piutang Usia (*Aging Report*) dan Hutang Usia.

### 4.6. Tax Compliance (PPN & PPh) — **BARU di v1.1**
* **FR-TAX-001:** Manajemen tarif pajak (PPN 11%, PPh 21/23/4(2)) per organisasi dengan masa berlaku.
* **FR-TAX-002:** Perhitungan pajak otomatis per faktur dengan breakdown DPP, PPN, dan PPh (tabel `invoice_taxes`).
* **FR-TAX-003:** PPN Masukan vs PPN Keluaran untuk persiapan SPT PPN (e-Faktur).
* **FR-TAX-004:** Ekspor data pajak ke format e-Faktur & e-Bupot (CSV/XML sesuai ketentuan DJP).

### 4.7. Multi-Currency — **BARU di v1.1**
* **FR-MC-001:** Transaksi (jurnal, invoice, pembayaran) dapat memakai mata uang selain IDR dengan kurs harian.
* **FR-MC-002:** Manajemen kurs (tabel `exchange_rates`) per pasangan mata uang per tanggal; laporan tetap dalam mata uang dasar organisasi.

### 4.8. Import & Data Migration — **BARU di v1.1**
* **FR-IMP-001:** Import data dari Excel/CSV: Chart of Accounts, kontak, saldo awal, dan transaksi.
* **FR-IMP-002:** Validasi & mapping kolom sebelum commit; laporan hasil import (sukses/gagal + alasan) untuk memastikan migrasi aman.

### 4.9. Dashboard — **BARU di v1.1**
* **FR-DSH-001:** Dashboard ringkas: saldo kas/bank, laba bulan berjalan, piutang & hutang jatuh tempo, grafik tren pendapatan.

### 4.10. Access Control & Audit — **BARU di v1.1**
* **FR-ACC-001:** Role default (admin, accountant, viewer, consultant) + role kustom dengan permission per modul (tabel `roles`).
* **FR-AUD-001:** Audit trail lengkap: siapa, kapan, aksi apa (create/update/delete/void/close), nilai sebelum & sesudah, IP address.

---

## 5. Non-Functional Requirements (NFR)

* **Security:** Enkripsi data *at-rest* (AES-256) & *in-transit* (TLS 1.3), Multi-Factor Authentication (MFA), audit logging komprehensif (tabel `audit_logs`), rate limiting pada API.
* **Scalability:** Arsitektur multi-tenant dengan isolasi data antar entitas/organisasi — **wajib menggunakan Row Level Security (RLS) PostgreSQL**, bukan hanya filter WHERE di query.
* **Availability:** SLA Uptime minimum 99.9%.
* **Data Integrity:** Soft delete (`deleted_at`) untuk semua data finansial — tidak ada hard delete; jurnal wajib balance sebelum diposting; period closing menolak perubahan.
* **Backup & DR:** Backup otomatis harian + point-in-time recovery; retensi minimum 30 hari.

---

## 6. Database Schema Design (Entity Relationship Layout)

Database dirancang menggunakan pendekatan **Relational Database Management System (RDBMS)** seperti PostgreSQL dengan pola multi-tenant (shared schema + organization_id + Row Level Security).

```
                        +---------------------+
                        |    organizations    |
                        +----------+----------+
                                   |
         +----------------+--------+--------+----------------+----------------+
         |                |                 |                |                |
+--------v-------+ +------v-------+ +-------v-------+ +------v-------+ +-----v-------+
|     users      | |    roles     | |   accounts    | |  contacts    | | bank_accounts|
+--------+-------+ +--------------+ +-------+-------+ +-------+-------+ +-----+-------+
         |                                  |                 |               |
         |                          +-------+--------+       |               |
         |                          | fiscal_periods |       |               |
         |                          +-------+--------+       |               |
         |                                  |                 |               |
+--------v----------------------------------v-----------------v---------------v-------+
|                        journal_entries (currency_code, exchange_rate,                |
|                                reversed_entry_id, fiscal_period_id)                  |
+--------+----------------------------------+------------------------------------------+
         |                                  |
+--------v---------+               +--------v---------+
|  journal_items   |               |  audit_logs      |
| (debit, credit,  |               +------------------+
|  account_id)     |
+------------------+
```

```
contacts (customer/vendor)
   |
   +--> invoices (invoice_type, source_type, tax_invoice_number, currency_code)
   |        +--> invoice_items
   |        +--> invoice_taxes (tax_rate_id, tax_base/DPP, tax_amount)
   |
   +--> payments (payment_type: RECEIPT/PAYMENT, payment_method)
            +--> payment_allocations (payment_id, invoice_id, amount)
```

```
contacts --> sales_orders --> invoices   (alur penjualan: Quotation/SO -> Invoice)
contacts --> purchase_orders --> invoices (alur pembelian: PO -> Vendor Bill)
bank_accounts --> bank_statements --> reconciliation_entries (payment_id / journal_entry_id)
organizations --> tax_rates --> invoice_taxes
organizations --> exchange_rates (base_currency, quote_currency, rate, rate_date)
```

---

## 7. Database Tables Definition & DDL Spec

### 7.1. Organization & User Management (Multi-Tenancy)

#### Table: `organizations`
| Column Name | Data Type | Constraints | Description |
|---|---|---|---|
| `id` | UUID | PRIMARY KEY, DEFAULT gen_random_uuid() | ID Unik Organisasi |
| `name` | VARCHAR(255) | NOT NULL | Nama Perusahaan/Entitas |
| `tax_number` | VARCHAR(50) | NULLABLE | NPWP Perusahaan |
| `currency_code` | VARCHAR(3) | DEFAULT 'IDR' | Mata Uang Utama |
| `fiscal_year_start` | DATE | NULLABLE | Awal tahun buku |
| `created_at` | TIMESTAMPTZ | DEFAULT CURRENT_TIMESTAMP | Waktu Dibuat |
| `updated_at` | TIMESTAMPTZ | DEFAULT CURRENT_TIMESTAMP | Waktu Diubah |

#### Table: `users`
| Column Name | Data Type | Constraints | Description |
|---|---|---|---|
| `id` | UUID | PRIMARY KEY | ID Unik Pengguna |
| `organization_id` | UUID | FOREIGN KEY -> organizations(id) | Tenant/Organisasi |
| `full_name` | VARCHAR(150) | NOT NULL | Nama Lengkap |
| `email` | VARCHAR(150) | UNIQUE, NOT NULL | Email Pengguna |
| `password_hash` | VARCHAR(255) | NOT NULL | Hash Password |
| `role` | VARCHAR(50) | NOT NULL | Role: admin, accountant, viewer, consultant |
| `is_active` | BOOLEAN | DEFAULT TRUE | Status Keaktifan |
| `mfa_enabled` | BOOLEAN | DEFAULT FALSE | Status MFA |
| `last_login_at` | TIMESTAMPTZ | NULLABLE | Login Terakhir |
| `created_at` | TIMESTAMPTZ | DEFAULT CURRENT_TIMESTAMP | Waktu Dibuat |
| `updated_at` | TIMESTAMPTZ | DEFAULT CURRENT_TIMESTAMP | Waktu Diubah |

#### Table: `roles` — BARU v1.1 (RBAC granular)
| Column Name | Data Type | Constraints | Description |
|---|---|---|---|
| `id` | UUID | PRIMARY KEY | ID Role |
| `organization_id` | UUID | FOREIGN KEY -> organizations(id) | Tenant Owner |
| `name` | VARCHAR(100) | NOT NULL | Nama Role |
| `permissions` | JSONB | DEFAULT '{}' | Permission per modul, e.g. {"invoice": ["create","approve"]} |

---

### 7.2. Chart of Accounts (CoA) & General Ledger

#### Table: `accounts`
| Column Name | Data Type | Constraints | Description |
|---|---|---|---|
| `id` | UUID | PRIMARY KEY | ID Akun |
| `organization_id` | UUID | FOREIGN KEY -> organizations(id) | Organization Owner |
| `code` | VARCHAR(50) | NOT NULL | Kode Akun (e.g. 1110-01) |
| `name` | VARCHAR(150) | NOT NULL | Nama Akun (e.g. Kas Utama) |
| `account_type` | VARCHAR(50) | NOT NULL | Asset, Liability, Equity, Revenue, Expense |
| `parent_id` | UUID | FOREIGN KEY -> accounts(id) | Akun Induk (Sub-Account) |
| `is_header` | BOOLEAN | DEFAULT FALSE | Apakah Akun Header (Non-Posting) |
| `normal_balance` | VARCHAR(6) | DEFAULT 'DEBIT' | DEBIT/CREDIT — validasi jurnal |
| `cash_flow_category` | VARCHAR(20) | DEFAULT 'NONE' | OPERATING/INVESTING/FINANCING/NONE — utk laporan arus kas |
| `is_active` | BOOLEAN | DEFAULT TRUE | Status Akun |
| `created_at` | TIMESTAMPTZ | DEFAULT CURRENT_TIMESTAMP | Waktu Dibuat |
| `updated_at` | TIMESTAMPTZ | DEFAULT CURRENT_TIMESTAMP | Waktu Diubah |
| `deleted_at` | TIMESTAMPTZ | NULLABLE | Soft delete |

#### Table: `fiscal_periods` — BARU v1.1 (Period Closing)
| Column Name | Data Type | Constraints | Description |
|---|---|---|---|
| `id` | UUID | PRIMARY KEY | ID Periode |
| `organization_id` | UUID | FOREIGN KEY -> organizations(id) | Tenant Owner |
| `name` | VARCHAR(100) | NOT NULL | Nama Periode (e.g. "Januari 2026") |
| `start_date` | DATE | NOT NULL | Tanggal Mulai |
| `end_date` | DATE | NOT NULL | Tanggal Selesai |
| `is_closed` | BOOLEAN | DEFAULT FALSE | Status Closed |
| `closed_at` | TIMESTAMPTZ | NULLABLE | Waktu Ditutup |
| `closed_by` | UUID | FOREIGN KEY -> users(id) | User Penutup |

#### Table: `journal_entries`
| Column Name | Data Type | Constraints | Description |
|---|---|---|---|
| `id` | UUID | PRIMARY KEY | ID Transaksi Jurnal |
| `organization_id` | UUID | FOREIGN KEY -> organizations(id) | Tenant Owner |
| `fiscal_period_id` | UUID | FOREIGN KEY -> fiscal_periods(id) | Periode — validasi period closing |
| `entry_number` | VARCHAR(100) | NOT NULL, UNIQUE | Nomor Bukti Jurnal |
| `entry_date` | DATE | NOT NULL | Tanggal Transaksi |
| `description` | TEXT | NULLABLE | Keterangan Jurnal |
| `status` | VARCHAR(30) | DEFAULT 'POSTED' | DRAFT, POSTED, VOID |
| `currency_code` | VARCHAR(3) | DEFAULT 'IDR' | Mata uang jurnal |
| `exchange_rate` | NUMERIC(18,6) | DEFAULT 1.0 | Kurs saat transaksi |
| `reversed_entry_id` | UUID | FOREIGN KEY -> journal_entries(id) | Jurnal pembalik (koreksi) |
| `created_by` | UUID | FOREIGN KEY -> users(id) | User Pembuat |
| `created_at` | TIMESTAMPTZ | DEFAULT CURRENT_TIMESTAMP | Waktu Dibuat |
| `updated_at` | TIMESTAMPTZ | DEFAULT CURRENT_TIMESTAMP | Waktu Diubah |
| `deleted_at` | TIMESTAMPTZ | NULLABLE | Soft delete |

#### Table: `journal_items`
| Column Name | Data Type | Constraints | Description |
|---|---|---|---|
| `id` | UUID | PRIMARY KEY | ID Detail Baris |
| `journal_entry_id` | UUID | FOREIGN KEY -> journal_entries(id) | Reference Jurnal |
| `account_id` | UUID | FOREIGN KEY -> accounts(id) | Akun yang Di-debit/Kredit |
| `debit` | NUMERIC(18,2) | DEFAULT 0.00 | Nilai Debit (>= 0) |
| `credit` | NUMERIC(18,2) | DEFAULT 0.00 | Nilai Kredit (>= 0) |
| `memo` | VARCHAR(255) | NULLABLE | Catatan Khusus Baris |

---

### 7.3. Contacts & Transactions (AR & AP)

#### Table: `contacts`
| Column Name | Data Type | Constraints | Description |
|---|---|---|---|
| `id` | UUID | PRIMARY KEY | ID Kontak |
| `organization_id` | UUID | FOREIGN KEY -> organizations(id) | Tenant Owner |
| `name` | VARCHAR(200) | NOT NULL | Nama Pelanggan/Pemasok |
| `type` | VARCHAR(50) | NOT NULL | CUSTOMER, VENDOR, BOTH |
| `email` | VARCHAR(100) | NULLABLE | Kontak Email |
| `phone` | VARCHAR(50) | NULLABLE | Nomor Telepon |
| `tax_id` | VARCHAR(50) | NULLABLE | NPWP Kontak |
| `address` | TEXT | NULLABLE | Alamat |
| `bank_name` | VARCHAR(100) | NULLABLE | Bank utk transfer |
| `bank_account_number` | VARCHAR(50) | NULLABLE | No. Rekening utk transfer |
| `is_active` | BOOLEAN | DEFAULT TRUE | Status Kontak |
| `created_at` | TIMESTAMPTZ | DEFAULT CURRENT_TIMESTAMP | Waktu Dibuat |
| `updated_at` | TIMESTAMPTZ | DEFAULT CURRENT_TIMESTAMP | Waktu Diubah |
| `deleted_at` | TIMESTAMPTZ | NULLABLE | Soft delete |

#### Table: `sales_orders` — BARU v1.1 (FR-AR-001)
| Column Name | Data Type | Constraints | Description |
|---|---|---|---|
| `id` | UUID | PRIMARY KEY | ID Sales Order |
| `organization_id` | UUID | FOREIGN KEY -> organizations(id) | Tenant Owner |
| `contact_id` | UUID | FOREIGN KEY -> contacts(id) | Customer |
| `so_number` | VARCHAR(100) | NOT NULL | Nomor SO |
| `order_date` | DATE | NOT NULL | Tanggal Order |
| `status` | VARCHAR(30) | DEFAULT 'DRAFT' | DRAFT, CONFIRMED, INVOICED, CANCELLED |
| `subtotal` | NUMERIC(18,2) | DEFAULT 0.00 | Total Sebelum Pajak |
| `tax_amount` | NUMERIC(18,2) | DEFAULT 0.00 | Total Pajak |
| `total_amount` | NUMERIC(18,2) | DEFAULT 0.00 | Total Akhir |
| `created_by` | UUID | FOREIGN KEY -> users(id) | User Pembuat |
| `created_at` | TIMESTAMPTZ | DEFAULT CURRENT_TIMESTAMP | Waktu Dibuat |
| `updated_at` | TIMESTAMPTZ | DEFAULT CURRENT_TIMESTAMP | Waktu Diubah |

#### Table: `sales_order_items` — BARU v1.1
| Column Name | Data Type | Constraints | Description |
|---|---|---|---|
| `id` | UUID | PRIMARY KEY | ID Item SO |
| `sales_order_id` | UUID | FOREIGN KEY -> sales_orders(id) | Reference SO |
| `account_id` | UUID | FOREIGN KEY -> accounts(id) | Akun Pendapatan |
| `description` | TEXT | NOT NULL | Deskripsi |
| `quantity` | NUMERIC(12,4) | DEFAULT 1 | Jumlah |
| `unit_price` | NUMERIC(18,2) | NOT NULL | Harga Satuan |
| `amount` | NUMERIC(18,2) | NOT NULL | Total Baris |

#### Table: `purchase_orders` — BARU v1.1 (FR-AP-001)
| Column Name | Data Type | Constraints | Description |
|---|---|---|---|
| `id` | UUID | PRIMARY KEY | ID Purchase Order |
| `organization_id` | UUID | FOREIGN KEY -> organizations(id) | Tenant Owner |
| `contact_id` | UUID | FOREIGN KEY -> contacts(id) | Vendor |
| `po_number` | VARCHAR(100) | NOT NULL | Nomor PO |
| `order_date` | DATE | NOT NULL | Tanggal Order |
| `status` | VARCHAR(30) | DEFAULT 'DRAFT' | DRAFT, CONFIRMED, BILLED, CANCELLED |
| `subtotal` | NUMERIC(18,2) | DEFAULT 0.00 | Total Sebelum Pajak |
| `tax_amount` | NUMERIC(18,2) | DEFAULT 0.00 | Total Pajak |
| `total_amount` | NUMERIC(18,2) | DEFAULT 0.00 | Total Akhir |
| `created_by` | UUID | FOREIGN KEY -> users(id) | User Pembuat |
| `created_at` | TIMESTAMPTZ | DEFAULT CURRENT_TIMESTAMP | Waktu Dibuat |
| `updated_at` | TIMESTAMPTZ | DEFAULT CURRENT_TIMESTAMP | Waktu Diubah |

#### Table: `purchase_order_items` — BARU v1.1
| Column Name | Data Type | Constraints | Description |
|---|---|---|---|
| `id` | UUID | PRIMARY KEY | ID Item PO |
| `purchase_order_id` | UUID | FOREIGN KEY -> purchase_orders(id) | Reference PO |
| `account_id` | UUID | FOREIGN KEY -> accounts(id) | Akun Beban/Aset |
| `description` | TEXT | NOT NULL | Deskripsi |
| `quantity` | NUMERIC(12,4) | DEFAULT 1 | Jumlah |
| `unit_price` | NUMERIC(18,2) | NOT NULL | Harga Satuan |
| `amount` | NUMERIC(18,2) | NOT NULL | Total Baris |

#### Table: `invoices`
| Column Name | Data Type | Constraints | Description |
|---|---|---|---|
| `id` | UUID | PRIMARY KEY | ID Faktur |
| `organization_id` | UUID | FOREIGN KEY -> organizations(id) | Tenant Owner |
| `contact_id` | UUID | FOREIGN KEY -> contacts(id) | Customer/Vendor |
| `invoice_type` | VARCHAR(30) | NOT NULL | SALES (Penjualan) / PURCHASE (Pembelian) |
| `invoice_number` | VARCHAR(100) | NOT NULL | Nomor Invoice |
| `source_type` | VARCHAR(30) | DEFAULT 'INVOICE' | QUOTATION/SALES_ORDER/PURCHASE_ORDER/INVOICE/MANUAL |
| `source_id` | UUID | NULLABLE | Ref SO/PO asal |
| `issue_date` | DATE | NOT NULL | Tanggal Terbit |
| `due_date` | DATE | NOT NULL | Tanggal Jatuh Tempo |
| `subtotal` | NUMERIC(18,2) | NOT NULL | Total Sebelum Pajak |
| `tax_amount` | NUMERIC(18,2) | DEFAULT 0.00 | Total Pajak (PPN/PPh) |
| `total_amount` | NUMERIC(18,2) | NOT NULL | Total Akhir |
| `currency_code` | VARCHAR(3) | DEFAULT 'IDR' | Mata uang faktur |
| `exchange_rate` | NUMERIC(18,6) | DEFAULT 1.0 | Kurs saat faktur |
| `tax_invoice_number` | VARCHAR(100) | NULLABLE | Nomor seri e-Faktur |
| `status` | VARCHAR(30) | DEFAULT 'UNPAID' | DRAFT, UNPAID, PARTIALLY_PAID, PAID, OVERDUE, CANCELLED |
| `created_at` | TIMESTAMPTZ | DEFAULT CURRENT_TIMESTAMP | Waktu Dibuat |
| `updated_at` | TIMESTAMPTZ | DEFAULT CURRENT_TIMESTAMP | Waktu Diubah |
| `deleted_at` | TIMESTAMPTZ | NULLABLE | Soft delete |

#### Table: `invoice_items`
| Column Name | Data Type | Constraints | Description |
|---|---|---|---|
| `id` | UUID | PRIMARY KEY | ID Item Faktur |
| `invoice_id` | UUID | FOREIGN KEY -> invoices(id) | Reference Invoice |
| `account_id` | UUID | FOREIGN KEY -> accounts(id) | Akun Pendapatan/Beban |
| `description` | TEXT | NOT NULL | Deskripsi Barang/Jasa |
| `quantity` | NUMERIC(12,4) | DEFAULT 1 | Jumlah |
| `unit_price` | NUMERIC(18,2) | NOT NULL | Harga Satuan |
| `amount` | NUMERIC(18,2) | NOT NULL | Total Baris (Qty * Price) |

#### Table: `tax_rates` — BARU v1.1 (FR-TAX-001)
| Column Name | Data Type | Constraints | Description |
|---|---|---|---|
| `id` | UUID | PRIMARY KEY | ID Tarif Pajak |
| `organization_id` | UUID | FOREIGN KEY -> organizations(id) | Tenant Owner |
| `code` | VARCHAR(20) | NOT NULL | PPN, PPH21, PPH23, PPH42 |
| `name` | VARCHAR(100) | NOT NULL | Nama Pajak |
| `rate` | NUMERIC(5,2) | NOT NULL | Tarif, e.g. 11.00 (PPN), 2.00 (PPh23) |
| `tax_type` | VARCHAR(10) | NOT NULL | OUTPUT (PPN keluaran) / INPUT (PPN masukan) / WITHHOLDING |
| `is_active` | BOOLEAN | DEFAULT TRUE | Status Aktif |
| `effective_date` | DATE | DEFAULT CURRENT_DATE | Tanggal Efektif |

#### Table: `invoice_taxes` — BARU v1.1 (FR-TAX-002)
| Column Name | Data Type | Constraints | Description |
|---|---|---|---|
| `id` | UUID | PRIMARY KEY | ID Pajak Faktur |
| `invoice_id` | UUID | FOREIGN KEY -> invoices(id) | Reference Invoice |
| `tax_rate_id` | UUID | FOREIGN KEY -> tax_rates(id) | Jenis Pajak |
| `tax_base` | NUMERIC(18,2) | NOT NULL | DPP |
| `tax_amount` | NUMERIC(18,2) | NOT NULL | Nilai Pajak |

#### Table: `payments` — BARU v1.1 (FR-AR-003 / FR-AP-002)
| Column Name | Data Type | Constraints | Description |
|---|---|---|---|
| `id` | UUID | PRIMARY KEY | ID Pembayaran |
| `organization_id` | UUID | FOREIGN KEY -> organizations(id) | Tenant Owner |
| `contact_id` | UUID | FOREIGN KEY -> contacts(id) | Customer/Vendor |
| `payment_type` | VARCHAR(20) | NOT NULL | RECEIPT (terima) / PAYMENT (bayar) |
| `payment_date` | DATE | NOT NULL | Tanggal Bayar |
| `amount` | NUMERIC(18,2) | NOT NULL, CHECK (amount > 0) | Nilai Pembayaran |
| `payment_method` | VARCHAR(20) | DEFAULT 'CASH' | CASH, BANK, EWALLET |
| `bank_account_id` | UUID | FOREIGN KEY -> bank_accounts(id) | Rekening asal/tujuan |
| `reference_number` | VARCHAR(100) | NULLABLE | No. bukti transfer |
| `memo` | TEXT | NULLABLE | Keterangan |
| `created_by` | UUID | FOREIGN KEY -> users(id) | User Pembuat |
| `created_at` | TIMESTAMPTZ | DEFAULT CURRENT_TIMESTAMP | Waktu Dibuat |
| `updated_at` | TIMESTAMPTZ | DEFAULT CURRENT_TIMESTAMP | Waktu Diubah |

#### Table: `payment_allocations` — BARU v1.1 (alokasi multi-faktur)
| Column Name | Data Type | Constraints | Description |
|---|---|---|---|
| `id` | UUID | PRIMARY KEY | ID Alokasi |
| `payment_id` | UUID | FOREIGN KEY -> payments(id) | Reference Payment |
| `invoice_id` | UUID | FOREIGN KEY -> invoices(id) | Invoice yang Dilunasi |
| `amount` | NUMERIC(18,2) | NOT NULL, CHECK (amount > 0) | Nilai Alokasi |

---

### 7.4. Cash & Bank (FR-CB-001/002/003)

#### Table: `bank_accounts` — BARU v1.1
| Column Name | Data Type | Constraints | Description |
|---|---|---|---|
| `id` | UUID | PRIMARY KEY | ID Rekening |
| `organization_id` | UUID | FOREIGN KEY -> organizations(id) | Tenant Owner |
| `name` | VARCHAR(150) | NOT NULL | Nama (e.g. "BCA 1234567", "GoPay") |
| `bank_name` | VARCHAR(100) | NULLABLE | Nama Bank |
| `account_number` | VARCHAR(50) | NULLABLE | No. Rekening |
| `account_holder` | VARCHAR(150) | NULLABLE | Pemilik Rekening |
| `currency_code` | VARCHAR(3) | DEFAULT 'IDR' | Mata Uang |
| `opening_balance` | NUMERIC(18,2) | DEFAULT 0.00 | Saldo Awal |
| `is_active` | BOOLEAN | DEFAULT TRUE | Status Aktif |

#### Table: `bank_statements` — BARU v1.1
| Column Name | Data Type | Constraints | Description |
|---|---|---|---|
| `id` | UUID | PRIMARY KEY | ID Baris Mutasi |
| `organization_id` | UUID | FOREIGN KEY -> organizations(id) | Tenant Owner |
| `bank_account_id` | UUID | FOREIGN KEY -> bank_accounts(id) | Rekening |
| `statement_date` | DATE | NOT NULL | Tanggal Mutasi |
| `reference` | VARCHAR(100) | NULLABLE | Referensi Bank |
| `description` | VARCHAR(255) | NULLABLE | Deskripsi |
| `debit` | NUMERIC(18,2) | DEFAULT 0.00 | Masuk |
| `credit` | NUMERIC(18,2) | DEFAULT 0.00 | Keluar |
| `balance` | NUMERIC(18,2) | NULLABLE | Saldo Bank (cross-check) |
| `is_reconciled` | BOOLEAN | DEFAULT FALSE | Status Cocok |

#### Table: `reconciliation_entries` — BARU v1.1
| Column Name | Data Type | Constraints | Description |
|---|---|---|---|
| `id` | UUID | PRIMARY KEY | ID Rekonsiliasi |
| `organization_id` | UUID | FOREIGN KEY -> organizations(id) | Tenant Owner |
| `bank_statement_id` | UUID | FOREIGN KEY -> bank_statements(id) | Baris Mutasi |
| `payment_id` | UUID | FOREIGN KEY -> payments(id) | Cocok dgn Pembayaran |
| `journal_entry_id` | UUID | FOREIGN KEY -> journal_entries(id) | Atau jurnal langsung |
| `status` | VARCHAR(20) | DEFAULT 'MATCHED' | MATCHED, UNMATCHED, ADJUSTED |

---

### 7.5. Multi-Currency & Audit

#### Table: `exchange_rates` — BARU v1.1 (FR-MC-002)
| Column Name | Data Type | Constraints | Description |
|---|---|---|---|
| `id` | UUID | PRIMARY KEY | ID Kurs |
| `organization_id` | UUID | FOREIGN KEY -> organizations(id) | Tenant Owner |
| `base_currency` | VARCHAR(3) | NOT NULL | e.g. IDR |
| `quote_currency` | VARCHAR(3) | NOT NULL | e.g. USD |
| `rate` | NUMERIC(18,6) | NOT NULL | Nilai Kurs |
| `rate_date` | DATE | NOT NULL | Tanggal Kurs |

#### Table: `audit_logs` — BARU v1.1 (FR-AUD-001)
| Column Name | Data Type | Constraints | Description |
|---|---|---|---|
| `id` | UUID | PRIMARY KEY | ID Log |
| `organization_id` | UUID | FOREIGN KEY -> organizations(id) | Tenant Owner |
| `user_id` | UUID | FOREIGN KEY -> users(id) | User Pelaku |
| `action` | VARCHAR(50) | NOT NULL | CREATE, UPDATE, DELETE, VOID, CLOSE, APPROVE |
| `entity_type` | VARCHAR(50) | NOT NULL | invoice, journal_entry, payment, dll |
| `entity_id` | UUID | NOT NULL | ID Entitas |
| `old_value` | JSONB | NULLABLE | Nilai Sebelum |
| `new_value` | JSONB | NULLABLE | Nilai Sesudah |
| `ip_address` | INET | NULLABLE | IP User |
| `created_at` | TIMESTAMPTZ | DEFAULT CURRENT_TIMESTAMP | Waktu Aksi |

---

## 8. SQL DDL Implementation Code

```sql
-- ============================================================================
-- DDL v1.1 — AccuCloud / Smart Ledger Engine
-- ============================================================================

-- Create Enum Types
CREATE TYPE account_type_enum AS ENUM ('ASSET', 'LIABILITY', 'EQUITY', 'REVENUE', 'EXPENSE');
CREATE TYPE invoice_type_enum AS ENUM ('SALES', 'PURCHASE');
CREATE TYPE invoice_status_enum AS ENUM ('DRAFT', 'UNPAID', 'PARTIALLY_PAID', 'PAID', 'CANCELLED', 'OVERDUE');
CREATE TYPE payment_type_enum AS ENUM ('RECEIPT', 'PAYMENT');
CREATE TYPE payment_method_enum AS ENUM ('CASH', 'BANK', 'EWALLET');
CREATE TYPE cash_flow_category_enum AS ENUM ('OPERATING', 'INVESTING', 'FINANCING', 'NONE');
CREATE TYPE source_type_enum AS ENUM ('QUOTATION', 'SALES_ORDER', 'PURCHASE_ORDER', 'INVOICE', 'MANUAL');

-- Organizations
CREATE TABLE organizations (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    name VARCHAR(255) NOT NULL,
    tax_number VARCHAR(50),
    currency_code VARCHAR(3) DEFAULT 'IDR',
    fiscal_year_start DATE,
    created_at TIMESTAMPTZ DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMPTZ DEFAULT CURRENT_TIMESTAMP
);

-- Users
CREATE TABLE users (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    organization_id UUID NOT NULL REFERENCES organizations(id) ON DELETE CASCADE,
    full_name VARCHAR(150) NOT NULL,
    email VARCHAR(150) NOT NULL UNIQUE,
    password_hash VARCHAR(255) NOT NULL,
    role VARCHAR(50) NOT NULL DEFAULT 'accountant',
    is_active BOOLEAN DEFAULT TRUE,
    mfa_enabled BOOLEAN DEFAULT FALSE,
    last_login_at TIMESTAMPTZ,
    created_at TIMESTAMPTZ DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMPTZ DEFAULT CURRENT_TIMESTAMP
);

-- Roles (RBAC granular)
CREATE TABLE roles (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    organization_id UUID NOT NULL REFERENCES organizations(id) ON DELETE CASCADE,
    name VARCHAR(100) NOT NULL,
    permissions JSONB NOT NULL DEFAULT '{}',
    UNIQUE (organization_id, name)
);

-- Chart of Accounts
CREATE TABLE accounts (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    organization_id UUID NOT NULL REFERENCES organizations(id) ON DELETE CASCADE,
    code VARCHAR(50) NOT NULL,
    name VARCHAR(150) NOT NULL,
    account_type account_type_enum NOT NULL,
    parent_id UUID REFERENCES accounts(id) ON DELETE SET NULL,
    is_header BOOLEAN DEFAULT FALSE,
    normal_balance VARCHAR(6) DEFAULT 'DEBIT',
    cash_flow_category cash_flow_category_enum DEFAULT 'NONE',
    is_active BOOLEAN DEFAULT TRUE,
    created_at TIMESTAMPTZ DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMPTZ DEFAULT CURRENT_TIMESTAMP,
    deleted_at TIMESTAMPTZ,
    CONSTRAINT uq_org_account_code UNIQUE (organization_id, code)
);

-- Fiscal Periods (Period Closing)
CREATE TABLE fiscal_periods (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    organization_id UUID NOT NULL REFERENCES organizations(id) ON DELETE CASCADE,
    name VARCHAR(100) NOT NULL,
    start_date DATE NOT NULL,
    end_date DATE NOT NULL,
    is_closed BOOLEAN DEFAULT FALSE,
    closed_at TIMESTAMPTZ,
    closed_by UUID REFERENCES users(id),
    UNIQUE (organization_id, start_date)
);

-- Journal Entries
CREATE TABLE journal_entries (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    organization_id UUID NOT NULL REFERENCES organizations(id) ON DELETE CASCADE,
    fiscal_period_id UUID REFERENCES fiscal_periods(id),
    entry_number VARCHAR(100) NOT NULL,
    entry_date DATE NOT NULL,
    description TEXT,
    status VARCHAR(30) DEFAULT 'POSTED',
    currency_code VARCHAR(3) DEFAULT 'IDR',
    exchange_rate NUMERIC(18,6) DEFAULT 1.0,
    reversed_entry_id UUID REFERENCES journal_entries(id),
    created_by UUID REFERENCES users(id),
    created_at TIMESTAMPTZ DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMPTZ DEFAULT CURRENT_TIMESTAMP,
    deleted_at TIMESTAMPTZ,
    CONSTRAINT uq_org_entry_number UNIQUE (organization_id, entry_number)
);

-- Journal Items
CREATE TABLE journal_items (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    journal_entry_id UUID NOT NULL REFERENCES journal_entries(id) ON DELETE CASCADE,
    account_id UUID NOT NULL REFERENCES accounts(id),
    debit NUMERIC(18,2) NOT NULL DEFAULT 0.00,
    credit NUMERIC(18,2) NOT NULL DEFAULT 0.00,
    memo VARCHAR(255),
    CONSTRAINT chk_no_negative CHECK (debit >= 0 AND credit >= 0)
);

-- Contacts
CREATE TABLE contacts (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    organization_id UUID NOT NULL REFERENCES organizations(id) ON DELETE CASCADE,
    name VARCHAR(200) NOT NULL,
    type VARCHAR(50) NOT NULL,
    email VARCHAR(100),
    phone VARCHAR(50),
    tax_id VARCHAR(50),
    address TEXT,
    bank_name VARCHAR(100),
    bank_account_number VARCHAR(50),
    is_active BOOLEAN DEFAULT TRUE,
    created_at TIMESTAMPTZ DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMPTZ DEFAULT CURRENT_TIMESTAMP,
    deleted_at TIMESTAMPTZ
);

-- Sales Orders
CREATE TABLE sales_orders (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    organization_id UUID NOT NULL REFERENCES organizations(id) ON DELETE CASCADE,
    contact_id UUID NOT NULL REFERENCES contacts(id),
    so_number VARCHAR(100) NOT NULL,
    order_date DATE NOT NULL,
    status VARCHAR(30) DEFAULT 'DRAFT',
    subtotal NUMERIC(18,2) NOT NULL DEFAULT 0.00,
    tax_amount NUMERIC(18,2) NOT NULL DEFAULT 0.00,
    total_amount NUMERIC(18,2) NOT NULL DEFAULT 0.00,
    created_by UUID REFERENCES users(id),
    created_at TIMESTAMPTZ DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMPTZ DEFAULT CURRENT_TIMESTAMP,
    CONSTRAINT uq_org_so_number UNIQUE (organization_id, so_number)
);

CREATE TABLE sales_order_items (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    sales_order_id UUID NOT NULL REFERENCES sales_orders(id) ON DELETE CASCADE,
    account_id UUID NOT NULL REFERENCES accounts(id),
    description TEXT NOT NULL,
    quantity NUMERIC(12,4) NOT NULL DEFAULT 1,
    unit_price NUMERIC(18,2) NOT NULL DEFAULT 0.00,
    amount NUMERIC(18,2) NOT NULL DEFAULT 0.00
);

-- Purchase Orders
CREATE TABLE purchase_orders (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    organization_id UUID NOT NULL REFERENCES organizations(id) ON DELETE CASCADE,
    contact_id UUID NOT NULL REFERENCES contacts(id),
    po_number VARCHAR(100) NOT NULL,
    order_date DATE NOT NULL,
    status VARCHAR(30) DEFAULT 'DRAFT',
    subtotal NUMERIC(18,2) NOT NULL DEFAULT 0.00,
    tax_amount NUMERIC(18,2) NOT NULL DEFAULT 0.00,
    total_amount NUMERIC(18,2) NOT NULL DEFAULT 0.00,
    created_by UUID REFERENCES users(id),
    created_at TIMESTAMPTZ DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMPTZ DEFAULT CURRENT_TIMESTAMP,
    CONSTRAINT uq_org_po_number UNIQUE (organization_id, po_number)
);

CREATE TABLE purchase_order_items (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    purchase_order_id UUID NOT NULL REFERENCES purchase_orders(id) ON DELETE CASCADE,
    account_id UUID NOT NULL REFERENCES accounts(id),
    description TEXT NOT NULL,
    quantity NUMERIC(12,4) NOT NULL DEFAULT 1,
    unit_price NUMERIC(18,2) NOT NULL DEFAULT 0.00,
    amount NUMERIC(18,2) NOT NULL DEFAULT 0.00
);

-- Tax Rates
CREATE TABLE tax_rates (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    organization_id UUID NOT NULL REFERENCES organizations(id) ON DELETE CASCADE,
    code VARCHAR(20) NOT NULL,
    name VARCHAR(100) NOT NULL,
    rate NUMERIC(5,2) NOT NULL,
    tax_type VARCHAR(10) NOT NULL,
    is_active BOOLEAN DEFAULT TRUE,
    effective_date DATE DEFAULT CURRENT_DATE,
    UNIQUE (organization_id, code)
);

-- Invoices
CREATE TABLE invoices (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    organization_id UUID NOT NULL REFERENCES organizations(id) ON DELETE CASCADE,
    contact_id UUID NOT NULL REFERENCES contacts(id),
    invoice_type invoice_type_enum NOT NULL,
    invoice_number VARCHAR(100) NOT NULL,
    source_type source_type_enum DEFAULT 'INVOICE',
    source_id UUID,
    issue_date DATE NOT NULL,
    due_date DATE NOT NULL,
    subtotal NUMERIC(18,2) NOT NULL DEFAULT 0.00,
    tax_amount NUMERIC(18,2) NOT NULL DEFAULT 0.00,
    total_amount NUMERIC(18,2) NOT NULL DEFAULT 0.00,
    currency_code VARCHAR(3) DEFAULT 'IDR',
    exchange_rate NUMERIC(18,6) DEFAULT 1.0,
    tax_invoice_number VARCHAR(100),
    status invoice_status_enum DEFAULT 'UNPAID',
    created_at TIMESTAMPTZ DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMPTZ DEFAULT CURRENT_TIMESTAMP,
    deleted_at TIMESTAMPTZ,
    CONSTRAINT uq_org_invoice_number UNIQUE (organization_id, invoice_type, invoice_number)
);

-- Invoice Items
CREATE TABLE invoice_items (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    invoice_id UUID NOT NULL REFERENCES invoices(id) ON DELETE CASCADE,
    account_id UUID NOT NULL REFERENCES accounts(id),
    description TEXT NOT NULL,
    quantity NUMERIC(12,4) NOT NULL DEFAULT 1,
    unit_price NUMERIC(18,2) NOT NULL DEFAULT 0.00,
    amount NUMERIC(18,2) NOT NULL DEFAULT 0.00
);

-- Invoice Taxes (breakdown DPP + PPN/PPh)
CREATE TABLE invoice_taxes (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    invoice_id UUID NOT NULL REFERENCES invoices(id) ON DELETE CASCADE,
    tax_rate_id UUID NOT NULL REFERENCES tax_rates(id),
    tax_base NUMERIC(18,2) NOT NULL,
    tax_amount NUMERIC(18,2) NOT NULL,
    UNIQUE (invoice_id, tax_rate_id)
);

-- Payments
CREATE TABLE payments (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    organization_id UUID NOT NULL REFERENCES organizations(id) ON DELETE CASCADE,
    contact_id UUID NOT NULL REFERENCES contacts(id),
    payment_type payment_type_enum NOT NULL,
    payment_date DATE NOT NULL,
    amount NUMERIC(18,2) NOT NULL,
    payment_method payment_method_enum DEFAULT 'CASH',
    bank_account_id UUID REFERENCES bank_accounts(id),
    reference_number VARCHAR(100),
    memo TEXT,
    created_by UUID REFERENCES users(id),
    created_at TIMESTAMPTZ DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMPTZ DEFAULT CURRENT_TIMESTAMP,
    CONSTRAINT chk_payment_amount CHECK (amount > 0)
);

-- Payment Allocations (multi-invoice)
CREATE TABLE payment_allocations (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    payment_id UUID NOT NULL REFERENCES payments(id) ON DELETE CASCADE,
    invoice_id UUID NOT NULL REFERENCES invoices(id),
    amount NUMERIC(18,2) NOT NULL,
    UNIQUE (payment_id, invoice_id),
    CONSTRAINT chk_alloc_amount CHECK (amount > 0)
);

-- Bank Accounts
CREATE TABLE bank_accounts (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    organization_id UUID NOT NULL REFERENCES organizations(id) ON DELETE CASCADE,
    name VARCHAR(150) NOT NULL,
    bank_name VARCHAR(100),
    account_number VARCHAR(50),
    account_holder VARCHAR(150),
    currency_code VARCHAR(3) DEFAULT 'IDR',
    opening_balance NUMERIC(18,2) DEFAULT 0.00,
    is_active BOOLEAN DEFAULT TRUE,
    created_at TIMESTAMPTZ DEFAULT CURRENT_TIMESTAMP
);

-- Bank Statements (rekening koran / MT940)
CREATE TABLE bank_statements (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    organization_id UUID NOT NULL REFERENCES organizations(id) ON DELETE CASCADE,
    bank_account_id UUID NOT NULL REFERENCES bank_accounts(id),
    statement_date DATE NOT NULL,
    reference VARCHAR(100),
    description VARCHAR(255),
    debit NUMERIC(18,2) DEFAULT 0.00,
    credit NUMERIC(18,2) DEFAULT 0.00,
    balance NUMERIC(18,2),
    is_reconciled BOOLEAN DEFAULT FALSE,
    UNIQUE (bank_account_id, statement_date, reference, description)
);

-- Reconciliation Entries
CREATE TABLE reconciliation_entries (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    organization_id UUID NOT NULL REFERENCES organizations(id) ON DELETE CASCADE,
    bank_statement_id UUID NOT NULL REFERENCES bank_statements(id),
    payment_id UUID REFERENCES payments(id),
    journal_entry_id UUID REFERENCES journal_entries(id),
    status VARCHAR(20) DEFAULT 'MATCHED',
    created_at TIMESTAMPTZ DEFAULT CURRENT_TIMESTAMP
);

-- Exchange Rates (multi-currency)
CREATE TABLE exchange_rates (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    organization_id UUID NOT NULL REFERENCES organizations(id) ON DELETE CASCADE,
    base_currency VARCHAR(3) NOT NULL,
    quote_currency VARCHAR(3) NOT NULL,
    rate NUMERIC(18,6) NOT NULL,
    rate_date DATE NOT NULL,
    UNIQUE (organization_id, base_currency, quote_currency, rate_date)
);

-- Audit Logs
CREATE TABLE audit_logs (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    organization_id UUID NOT NULL REFERENCES organizations(id) ON DELETE CASCADE,
    user_id UUID REFERENCES users(id),
    action VARCHAR(50) NOT NULL,
    entity_type VARCHAR(50) NOT NULL,
    entity_id UUID NOT NULL,
    old_value JSONB,
    new_value JSONB,
    ip_address INET,
    created_at TIMESTAMPTZ DEFAULT CURRENT_TIMESTAMP
);
CREATE INDEX idx_audit_org_entity ON audit_logs (organization_id, entity_type, entity_id);

-- Important Indexes
CREATE INDEX idx_journal_org_date    ON journal_entries (organization_id, entry_date);
CREATE INDEX idx_journal_items_entry ON journal_items (journal_entry_id);
CREATE INDEX idx_invoices_org_status ON invoices (organization_id, status);
CREATE INDEX idx_invoices_org_due    ON invoices (organization_id, due_date);
CREATE INDEX idx_payments_org_date   ON payments (organization_id, payment_date);
CREATE INDEX idx_payment_alloc_inv   ON payment_allocations (invoice_id);
CREATE INDEX idx_bank_stmt_acct      ON bank_statements (bank_account_id, is_reconciled);
```

---

## 9. Row Level Security (Multi-Tenant Isolation) — BARU v1.1

Isolasi antar tenant TIDAK boleh hanya mengandalkan filter `WHERE organization_id = ?` di query. Wajib mengaktifkan **Row Level Security (RLS)** di PostgreSQL untuk semua tabel yang memiliki `organization_id`:

```sql
-- Aktifkan RLS pada SEMUA tabel ber-organization_id (contoh: users)
ALTER TABLE users ENABLE ROW LEVEL SECURITY;
ALTER TABLE accounts ENABLE ROW LEVEL SECURITY;
ALTER TABLE journal_entries ENABLE ROW LEVEL SECURITY;
-- ... dan seterusnya untuk semua tabel tenant ...

-- Policy isolasi tenant
CREATE POLICY tenant_isolation ON users
  USING (organization_id = current_setting('app.organization_id')::uuid);

-- App set session variable setelah autentikasi:
-- SET app.organization_id = '<uuid-tenant>';
-- Service role (migration/backfill) pakai BYPASSRLS.
```

---

## 10. Data Integrity Rules (Double-Entry Engine) — BARU v1.1

Aturan validasi WAJIB diimplementasikan di app-layer sebelum transaksi di-commit:

1. **Jurnal wajib balance:** `SUM(debit) == SUM(credit)` sebelum status berubah menjadi POSTED. Jangan pernah commit jurnal yang tidak balance.
2. **Period closing:** Jurnal tidak boleh masuk ke periode yang sudah `is_closed = TRUE` (kecuali reversal khusus dengan approval).
3. **Alokasi pembayaran:** `SUM(payment_allocations) <= payments.amount` dan `SUM(alokasi per invoice) <= invoices.total_amount` (sisa piutang/hutang).
4. **Total faktur:** `invoices.total_amount == invoices.subtotal + SUM(invoice_taxes.tax_amount)`.
5. **Soft delete:** Data finansial tidak pernah di-hard delete; gunakan `deleted_at`.
6. **Koreksi pasca-posting:** Perubahan data finansial yang sudah diposting WAJIB melalui jurnal pembalik (`reversed_entry_id`), bukan UPDATE langsung.

---

## 11. Conclusion & Next Steps

PRD dan Schema Database v1.1 ini menjadi landasan teknis untuk fase pengembangan produk setara **Jurnal.id / Accurate Online**. Tahap berikutnya meliputi:

1. Perancangan UI/UX (Wireframing & Prototyping).
2. Setup API Gateway & Microservices Architecture.
3. Implementasi Double-Entry Engine Validation (pengecekan Keseimbangan Debit/Kredit sebelum transaksi dikomit).
4. Implementasi Row Level Security & seed data (COA standar PSAK, tax_rates default PPN 11% / PPh 21/23/4(2)).
5. Import engine (Excel/CSV) dengan validasi & mapping — pintu masuk utama migrasi user.
6. Modul pajak (e-Faktur & e-Bupot export) sebagai diferensiator kompetitif.
