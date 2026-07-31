# Product Requirement Document (PRD) & Database Schema
## Cloud-Based Accounting Software (SaaS)

---

## 1. Document Overview

* **Product Name:** AccuCloud / Smart Ledger Engine
* **Target Audience:** UMKM, Perusahaan Menengah (SMEs), Konsultan Pajak & Akuntan
* **Platform:** Web Application (Responsive) & API Gateway
* **Document Version:** v1.0.0
* **Author:** Lead Product Manager & System Architect

---

## 2. Executive Summary & Vision

Produk ini dirancang sebagai platform akuntansi berbasis cloud (*SaaS*) yang intuitif, aman, dan mematuhi standar akuntansi Indonesia (PSAK). Fokus utama platform ini adalah otomatisasi pembukuan, pencatatan transaksi multi-mata uang, rekonsiliasi bank otomatis, serta integrasi pelaporan pajak (e-Faktur & e-Bupot).

---

## 3. Product Goals & Target Metrics

1. **Efisiensi Waktu:** Mengurangi waktu proses pembukuan bulanan hingga 60% melalui otomatisasi pencatatan dan rekonsiliasi.
2. **Kepatuhan Pajak:** Memfasilitasi ekspor data transaksi ke format standar PPN & PPh secara presisi.
3. **Kemudahan Kolaborasi:** Memungkinkan pemilik bisnis, staf keuangan, dan konsultan pajak bekerja dalam satu platform dengan hak akses berbasis peran (RBAC).

---

## 4. Key Features & Functional Requirements

### 4.1. General Ledger & Chart of Accounts (CoA)
* **FR-GL-001:** Pengelolaan Bagan Akun (Chart of Accounts) standar sesuai PSAK dengan struktur hirarkis (Header vs Account).
* **FR-GL-002:** Pencatatan Jurnal Umum (*General Journal*) secara manual dan otomatis dari modul pembantu (Penjualan, Pembelian, Kas/Bank).
* **FR-GL-003:** Penguncian Buku Kas/Periode (*Period Closing*) untuk mencegah perubahan data pada periode yang telah ditutup.

### 4.2. Sales & Accounts Receivable (Piutang Usaha)
* **FR-AR-001:** Pembuatan Penawaran (*Quotation*), Pesanan Penjualan (*Sales Order*), dan Faktur Penjualan (*Sales Invoice*).
* **FR-AR-002:** Tracking status pembayaran faktur (Draft, Unpaid, Partially Paid, Paid, Overdue).
* **FR-AR-003:** Penerimaan Pembayaran (*Customer Receipt*) dengan alokasi piutang multi-faktur.

### 4.3. Purchasing & Accounts Payable (Hutang Usaha)
* **FR-AP-001:** Pembuatan Pesanan Pembelian (*Purchase Order*) dan Tagihan Pemasok (*Vendor Bill*).
* **FR-AP-002:** Pelunasan Hutang (*Vendor Payment*) dan pencatatan potongan/diskon pembelian.

### 4.4. Cash & Bank Management
* **FR-CB-001:** Pengelolaan akun Kas, Bank, dan e-Wallet.
* **FR-CB-002:** Import rekening koran (Format CSV/Excel/MT940) dan pencocokan otomatis (*Bank Reconciliation*).
* **FR-CB-003:** Pencatatan Transfer Antar Bank dan Biaya Admin.

### 4.5. Financial Reporting
* **FR-REP-001:** Laporan Laba Rugi (*Profit and Loss / Income Statement*).
* **FR-REP-002:** Laporan Neraca (*Balance Sheet*).
* **FR-REP-003:** Laporan Arus Kas (*Cash Flow Statement* - Direct & Indirect).
* **FR-REP-004:** Laporan Buku Besar (*General Ledger Detail*) dan Neraca Saldo (*Trial Balance*).

---

## 5. Non-Functional Requirements (NFR)

* **Security:** Enkripsi data *at-rest* (AES-256) & *in-transit* (TLS 1.3), Multi-Factor Authentication (MFA), audit logging komprehensif.
* **Scalability:** Arsitektur multi-tenant dengan isolasi data antar entitas/organisasi.
* **Availability:** SLA Uptime minimum 99.9%.

---

## 6. Database Schema Design (Entity Relationship Layout)

Database dirancang menggunakan pendekatan **Relational Database Management System (RDBMS)** seperti PostgreSQL dengan pola multi-tenant.

```
                    +-------------------+
                    |   organizations   |
                    +---------+---------+
                              |
        +---------------------+---------------------+
        |                     |                     |
+-------v-------+     +-------v-------+     +-------v-------+
|     users     |     +      coa      +     |   contacts    |
+---------------+     +-------+-------+     +-------+-------+
                              |                     |
                              +----------+----------+
                                         |
                                  +------v------+
                                  | Invoices /  |
                                  | Payments    |
                                  +-------------+
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
| `created_at` | TIMESTAMP | DEFAULT CURRENT_TIMESTAMP | Waktu Dibuat |

#### Table: `users`
| Column Name | Data Type | Constraints | Description |
|---|---|---|---|
| `id` | UUID | PRIMARY KEY | ID Unik Pengguna |
| `organization_id` | UUID | FOREIGN KEY -> organizations(id) | Tenant/Organisasi |
| `full_name` | VARCHAR(150) | NOT NULL | Nama Lengkap |
| `email` | VARCHAR(150) | UNIQUE, NOT NULL | Email Pengguna |
| `password_hash` | VARCHAR(255) | NOT NULL | Hash Password |
| `role` | VARCHAR(50) | NOT NULL | Role: admin, accountant, viewer |
| `is_active` | BOOLEAN | DEFAULT TRUE | Status Keaktifan |

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

#### Table: `journal_entries`
| Column Name | Data Type | Constraints | Description |
|---|---|---|---|
| `id` | UUID | PRIMARY KEY | ID Transaksi Jurnal |
| `organization_id` | UUID | FOREIGN KEY -> organizations(id) | Tenant Owner |
| `entry_number` | VARCHAR(100) | NOT NULL, UNIQUE | Nomor Bukti Jurnal |
| `entry_date` | DATE | NOT NULL | Tanggal Transaksi |
| `description` | TEXT | NULLABLE | Keterangan Jurnal |
| `status` | VARCHAR(30) | DEFAULT 'POSTED' | DRAFT, POSTED, VOID |
| `created_by` | UUID | FOREIGN KEY -> users(id) | User Pembuat |

#### Table: `journal_items`
| Column Name | Data Type | Constraints | Description |
|---|---|---|---|
| `id` | UUID | PRIMARY KEY | ID Detail Baris |
| `journal_entry_id` | UUID | FOREIGN KEY -> journal_entries(id) | Reference Jurnal |
| `account_id` | UUID | FOREIGN KEY -> accounts(id) | Akun yang Di-debit/Kredit |
| `debit` | NUMERIC(18,2) | DEFAULT 0.00 | Nilai Debit |
| `credit` | NUMERIC(18,2) | DEFAULT 0.00 | Nilai Kredit |
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

#### Table: `invoices`
| Column Name | Data Type | Constraints | Description |
|---|---|---|---|
| `id` | UUID | PRIMARY KEY | ID Faktur |
| `organization_id` | UUID | FOREIGN KEY -> organizations(id) | Tenant Owner |
| `contact_id` | UUID | FOREIGN KEY -> contacts(id) | Customer/Vendor |
| `invoice_type` | VARCHAR(30) | NOT NULL | SALES (Penjualan) / PURCHASE (Pembelian) |
| `invoice_number` | VARCHAR(100) | NOT NULL | Nomor Invoice |
| `issue_date` | DATE | NOT NULL | Tanggal Terbit |
| `due_date` | DATE | NOT NULL | Tanggal Jatuh Tempo |
| `subtotal` | NUMERIC(18,2) | NOT NULL | Total Sebelum Pajak |
| `tax_amount` | NUMERIC(18,2) | DEFAULT 0.00 | Total Pajak (PPN/PPh) |
| `total_amount` | NUMERIC(18,2) | NOT NULL | Total Akhir |
| `status` | VARCHAR(30) | DEFAULT 'UNPAID' | DRAFT, UNPAID, PARTIAL, PAID, CANCELLED |

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

---

## 8. SQL DDL Implementation Code

```sql
-- Create Enum Types
CREATE TYPE account_type_enum AS ENUM ('ASSET', 'LIABILITY', 'EQUITY', 'REVENUE', 'EXPENSE');
CREATE TYPE invoice_type_enum AS ENUM ('SALES', 'PURCHASE');
CREATE TYPE invoice_status_enum AS ENUM ('DRAFT', 'UNPAID', 'PARTIALLY_PAID', 'PAID', 'CANCELLED');

-- Organizations
CREATE TABLE organizations (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    name VARCHAR(255) NOT NULL,
    tax_number VARCHAR(50),
    currency_code VARCHAR(3) DEFAULT 'IDR',
    created_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP
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
    created_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP
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
    created_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP,
    CONSTRAINT uq_org_account_code UNIQUE (organization_id, code)
);

-- Journal Entries
CREATE TABLE journal_entries (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    organization_id UUID NOT NULL REFERENCES organizations(id) ON DELETE CASCADE,
    entry_number VARCHAR(100) NOT NULL,
    entry_date DATE NOT NULL,
    description TEXT,
    status VARCHAR(30) DEFAULT 'POSTED',
    created_by UUID REFERENCES users(id),
    created_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP,
    CONSTRAINT uq_org_entry_number UNIQUE (organization_id, entry_number)
);

-- Journal Items
CREATE TABLE journal_items (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    journal_entry_id UUID NOT NULL REFERENCES journal_entries(id) ON DELETE CASCADE,
    account_id UUID NOT NULL REFERENCES accounts(id),
    debit NUMERIC(18,2) NOT NULL DEFAULT 0.00,
    credit NUMERIC(18,2) NOT NULL DEFAULT 0.00,
    memo VARCHAR(255)
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
    created_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP
);

-- Invoices
CREATE TABLE invoices (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    organization_id UUID NOT NULL REFERENCES organizations(id) ON DELETE CASCADE,
    contact_id UUID NOT NULL REFERENCES contacts(id),
    invoice_type invoice_type_enum NOT NULL,
    invoice_number VARCHAR(100) NOT NULL,
    issue_date DATE NOT NULL,
    due_date DATE NOT NULL,
    subtotal NUMERIC(18,2) NOT NULL DEFAULT 0.00,
    tax_amount NUMERIC(18,2) NOT NULL DEFAULT 0.00,
    total_amount NUMERIC(18,2) NOT NULL DEFAULT 0.00,
    status invoice_status_enum DEFAULT 'UNPAID',
    created_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP,
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
```

---

## 9. Conclusion & Next Steps

PRD dan Schema Database ini menjadi landasan teknis untuk fase pengembangan MVP (*Minimum Viable Product*). Tahap berikutnya meliputi:
1. Perancangan UI/UX (Wireframing & Prototyping).
2. Setup API Gateway & Microservices Architecture.
3. Implementasi Double-Entry Engine Validation (pengecekan Keseimbangan Debit/Kredit sebelum transaksi dikomit).
