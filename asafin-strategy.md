# AsaFin — Pricing Strategy & Feature Roadmap
> Dokumen internal · Dibuat 14 Oktober 2026
> Produk: keuangan.asabisa.co.id

---

## 1. Competitive Positioning

```
Kompleksitas Fitur ↑
──────────────────────────────────────────────────────
  Mekari Jurnal      │ Enterprise, mahal, rumit
  Accurate Online    │ Double-entry, harga tinggi
  ─ ─ ─ ─ ─ ─ ─ ─ ─ ┤ ← AsaFin bisa tumbuh ke sini
  Kledo              │ Cloud, manual input, ~200rb/bln
  ★ AsaFin           │ WA/TG input, SAK EMKM, otomatis
  BukuKas/BukuWarung │ Catat saja, bukan akuntansi
──────────────────────────────────────────────────────
Kompleksitas Fitur ↓
```

**Sweet spot AsaFin:**
> UMKM yang butuh akuntansi beneran (double-entry, SAK EMKM, laporan siap audit)
> tapi tidak mau ribet install software atau belajar akuntansi dari nol.

---

## 2. Pricing Strategy

### Prinsip
- Harga harus lebih murah dari Kledo (Rp 200rb/bln) untuk compete di UMKM
- Ada free tier untuk akuisisi organik
- Upsell ke fitur premium (multi-bisnis, pajak, stok)
- Annual discount untuk reduce churn

### Tier Pricing yang Direkomendasikan

| Tier | Harga | Fitur |
|------|-------|-------|
| **Starter** (Gratis) | Rp 0/bln | 1 bisnis, 50 transaksi/bln, laporan dasar, WA input |
| **Growth** | Rp 99rb/bln atau Rp 990rb/thn | 1 bisnis, unlimited transaksi, import rekening koran, invoice PDF, semua laporan |
| **Pro** | Rp 199rb/bln atau Rp 1.9jt/thn | 5 bisnis, multi-user (Owner + Staff), priority support, laporan custom |
| **Business** | Rp 399rb/bln atau Rp 3.9jt/thn | Unlimited bisnis, API access, integrasi POS, laporan pajak (PPh/PPN draft) |

### Catatan Pricing
- **Annual saving ~17%** → dorong ke tahunan untuk cash flow stabil
- **Free trial 14 hari** untuk Growth/Pro (no CC required)
- **Diskon 50% bulan pertama** untuk konversi dari free ke berbayar
- Bandingkan: Kledo Rp 200rb, Jurnal custom (mahal), iREAP Rp 99rb (POS only)

---

## 3. Feature Roadmap

### Fase 1 — Foundation (Current / Q4 2026)
> Stabilkan core, polish UX, validasi market

- [x] Input transaksi via WhatsApp & Telegram
- [x] Import rekening koran (BCA, Mandiri, BRI, BNI, BSI)
- [x] Auto-generate jurnal double-entry SAK EMKM
- [x] Laporan: Laba Rugi, Neraca, Arus Kas
- [x] Invoice penjualan + tracking piutang
- [x] Multi-bisnis dalam 1 akun
- [ ] **Pricing page yang jelas** (saat ini tidak ada di landing page)
- [ ] **Onboarding flow** 3 langkah (setup bisnis → input pertama → lihat laporan)
- [ ] **Free tier** (batas 50 trx/bln) untuk akuisisi organik

### Fase 2 — Growth (Q1 2027)
> Tambah fitur yang mengurangi churn & naikkan ARPU

- [ ] **WhatsApp reminder piutang jatuh tempo** otomatis
- [ ] **Rekonsiliasi bank otomatis** (match statement vs jurnal)
- [ ] **Manajemen pengeluaran** (expense tracking + foto nota via WA)
- [ ] **Dashboard mobile-friendly** (PWA atau React Native)
- [ ] **Export laporan** ke Excel, PDF, Google Sheets
- [ ] **Budgeting & target keuangan** per periode
- [ ] **Multi-user role** (Owner, Akuntan, Staff input)

### Fase 3 — Moat (Q2-Q3 2027)
> Bangun keunggulan yang susah ditiru kompetitor

- [ ] **Integrasi POS ringan** (catat penjualan langsung → otomatis masuk jurnal)
  - Bisa via API ke Moka/Kasir Pintar, atau build mini-POS sendiri
- [ ] **Manajemen stok dasar** (barang masuk/keluar, HPP otomatis)
- [ ] **Laporan pajak draft** (PPh 21 karyawan, PPN sederhana)
- [ ] **AI insight** ("bulan ini pengeluaran utilitas naik 30%")
- [ ] **Template chart of accounts** per industri (F&B, Retail, Jasa, dll)
- [ ] **Integrasi marketplace** (Tokopedia, Shopee → auto-import penjualan)

### Fase 4 — Ekosistem (Q4 2027+)
> Platform play, revenue baru

- [ ] **API publik** untuk integrasi third-party
- [ ] **Marketplace add-on** (laporan khusus, template, konsultasi akuntan)
- [ ] **Integrasi payroll sederhana** (gaji karyawan → otomatis jurnal beban gaji)
- [ ] **Integrasi e-Faktur / Coretax** (untuk UMKM PKP)
- [ ] **White-label** untuk konsultan/akuntan publik

---

## 4. Weakness vs Kompetitor & Mitigation Plan

| Kelemahan AsaFin | Kompetitor Unggul | Mitigation |
|------------------|-------------------|------------|
| Tidak ada POS | Moka, Kasir Pintar | Fase 3: mini-POS atau API integrasi |
| Tidak ada manajemen stok | Kledo, Jurnal | Fase 3: stok dasar (barang masuk/keluar) |
| Tidak ada integrasi pajak | Mekari Jurnal | Fase 3: laporan PPh/PPN draft |
| Tidak ada mobile app native | Semua kompetitor | Fase 2: PWA dulu, native kemudian |
| Brand masih kecil | Kledo, BukuKas | Growth hacking: komunitas WA, YouTube |
| Pricing tidak terlihat | Semua kompetitor transparan | Fase 1: tambah pricing page ASAP |
| No offline mode | Kasir Pintar, iREAP | Bukan prioritas (target UMKM urban) |

---

## 5. Growth Strategy

### Akuisisi
- **SEO**: target keyword "aplikasi akuntansi UMKM", "pembukuan online gratis", "aplikasi kasir dengan akuntansi"
- **YouTube/TikTok**: demo 60 detik "dari foto rekening koran → laporan keuangan"
- **Komunitas**: grup Facebook UMKM, Telegram pengusaha, komunitas akuntan
- **Referral**: user undang user → bonus 1 bulan gratis

### Retensi
- **Onboarding email series** 7 hari (edukasi fitur satu per satu)
- **Monthly insight report** otomatis via WA ("Rekap keuangan Anda bulan Oktober")
- **In-app reminder** kalau belum input 7 hari

### Monetisasi Tambahan
- **Jasa setup COA** (Rp 500rb one-time, tim AsaFin setup chart of accounts)
- **Konsultasi akuntan** (marketplace, AsaFin ambil komisi)

---

## 6. Key Metrics to Track

| Metric | Target 6 Bulan | Target 12 Bulan |
|--------|---------------|-----------------|
| Free users | 500 | 2.000 |
| Paying users | 50 | 300 |
| MRR | Rp 5jt | Rp 30jt |
| Churn rate | < 10%/bln | < 7%/bln |
| ARPU | Rp 100rb | Rp 150rb |
| NPS | > 40 | > 60 |

---

## 7. Competitive Moat AsaFin

Keunggulan yang harus dipertahankan & diperdalam:

1. **WA/Telegram input** — ini differentiator utama, tidak ada yang punya
2. **Auto-import rekening koran bank Indonesia** — sangat praktis, pertahankan coverage bank
3. **SAK EMKM compliant** — positioning profesional, bukan sekadar "catatan"
4. **Setup < 2 menit** — frictionless onboarding vs kompetitor yang butuh jam
5. **Multi-bisnis dalam 1 akun** — sangat dicari owner yang punya beberapa usaha
