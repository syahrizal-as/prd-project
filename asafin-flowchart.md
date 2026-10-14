# AsaFin — Feature Addition Flowchart
> Panduan keputusan saat menambah fitur baru
> Dibuat 14 Oktober 2026

---

## Flowchart 1: Feature Prioritization Framework

```
                    ┌─────────────────────────┐
                    │   Ada ide / request      │
                    │       fitur baru?        │
                    └───────────┬─────────────┘
                                │
                    ┌───────────▼─────────────┐
                    │  Apakah fitur ini        │
                    │  diminta oleh ≥3 user?   │
                    └───────────┬─────────────┘
                       NO │         │ YES
                          │         ▼
                          │   ┌──────────────────┐
                          │   │ Masuk backlog     │
                          │   │ sebagai kandidat  │
                          │   └──────────┬───────┘
                          │              │
                    ┌─────▼──────────────▼───────────┐
                    │  Apakah fitur ini memperkuat    │
                    │  CORE MOAT AsaFin?              │
                    │  (WA/TG input, auto-jurnal,     │
                    │   SAK EMKM, multi-bisnis)       │
                    └──────────┬──────────────────────┘
                       NO │         │ YES
                          │         ▼
                          │   ┌──────────────────────┐
                          │   │  PRIORITAS TINGGI    │
                          │   │  → Masuk sprint      │
                          │   │    berikutnya        │
                          │   └──────────────────────┘
                          │
                    ┌─────▼────────────────────────────┐
                    │  Apakah fitur ini mengurangi      │
                    │  CHURN / naikkan RETENTION?       │
                    └──────────┬───────────────────────┘
                       NO │         │ YES
                          │         ▼
                          │   ┌──────────────────────┐
                          │   │  PRIORITAS MEDIUM    │
                          │   │  → Roadmap Q+1       │
                          │   └──────────────────────┘
                          │
                    ┌─────▼────────────────────────────┐
                    │  Apakah fitur ini bisa naikkan    │
                    │  ARPU / buka revenue baru?        │
                    └──────────┬───────────────────────┘
                       NO │         │ YES
                          │         ▼
                          │   ┌──────────────────────┐
                          │   │  PRIORITAS MEDIUM    │
                          │   │  → Evaluasi ulang    │
                          │   │    di akhir quarter  │
                          │   └──────────────────────┘
                          ▼
                   ┌──────────────┐
                   │   PARKIR     │
                   │  (Nice to    │
                   │   have, not  │
                   │   now)       │
                   └──────────────┘
```

---

## Flowchart 2: Feature Development Lifecycle

```
  ┌──────────────────────────────────────────────────────────────────┐
  │                    IDEA / REQUEST MASUK                          │
  └─────────────────────────┬────────────────────────────────────────┘
                             │
  ┌──────────────────────────▼────────────────────────────────────────┐
  │  1. DISCOVERY                                                      │
  │  • Validate: siapa yang minta? berapa banyak?                     │
  │  • User interview: pain point apa yang diselesaikan?              │
  │  • Competitor check: ada yang sudah punya? kita mau diferensiasi? │
  └──────────────────────────┬────────────────────────────────────────┘
                             │
                    Lolos? ──┤
                   YES │     │ NO → PARKIR
                       ▼
  ┌──────────────────────────────────────────────────────────────────┐
  │  2. SCOPING                                                       │
  │  • Definisi MVP: fitur minimal yang deliver value                 │
  │  • Estimasi effort: S / M / L / XL                               │
  │  • Impact vs Effort matrix → tentukan urutan                      │
  │  • Tentukan metric sukses (activation rate, usage, revenue)       │
  └──────────────────────────┬────────────────────────────────────────┘
                             │
  ┌──────────────────────────▼────────────────────────────────────────┐
  │  3. DESIGN & SPEC                                                  │
  │  • Wireframe / mockup alur utama                                  │
  │  • Update ERD / schema database jika perlu                        │
  │  • Update API contract jika ada endpoint baru                     │
  │  • Checklist: apakah ada breaking change ke fitur existing?       │
  └──────────────────────────┬────────────────────────────────────────┘
                             │
  ┌──────────────────────────▼────────────────────────────────────────┐
  │  4. DEVELOPMENT                                                    │
  │  • Feature branch dari main                                       │
  │  • Unit test untuk logic akuntansi (WAJIB — debit=kredit)        │
  │  • Integration test dengan WA/TG bot jika fitur menyentuh input  │
  │  • Code review sebelum merge                                      │
  └──────────────────────────┬────────────────────────────────────────┘
                             │
  ┌──────────────────────────▼────────────────────────────────────────┐
  │  5. STAGING & QA                                                   │
  │  • Deploy ke staging                                              │
  │  • Test manual: happy path + edge case                            │
  │  • Test rekening koran import: pastikan balance tetap seimbang    │
  │  • Test multi-bisnis: pastikan data isolasi tidak bocor           │
  └──────────────────────────┬────────────────────────────────────────┘
                             │
                    Lulus? ──┤
                   YES │     │ NO → Kembali ke Development
                       ▼
  ┌──────────────────────────────────────────────────────────────────┐
  │  6. RELEASE                                                       │
  │  • Merge ke main → CI/CD otomatis deploy                         │
  │  • Update changelog / release notes                              │
  │  • Notif ke user via WA broadcast atau in-app notification       │
  │  • Update landing page / pricing page jika fitur masuk tier baru │
  └──────────────────────────┬────────────────────────────────────────┘
                             │
  ┌──────────────────────────▼────────────────────────────────────────┐
  │  7. MONITOR & ITERATE                                              │
  │  • Pantau error log 48 jam pertama                               │
  │  • Track metric yang sudah didefinisikan di Scoping               │
  │  • Collect feedback user aktif                                    │
  │  • Jika adoption rendah dalam 30 hari → analisis ulang            │
  └──────────────────────────────────────────────────────────────────┘
```

---

## Flowchart 3: Roadmap Fase per Fase

```
  Q4 2026 — FOUNDATION
  ┌─────────────────────────────────────────────────────────────┐
  │  ★ Core sudah live                                          │
  │  ├─ WA/TG input ✅                                          │
  │  ├─ Import rekening koran ✅                                 │
  │  ├─ Jurnal double-entry SAK EMKM ✅                          │
  │  ├─ Invoice + piutang ✅                                     │
  │  ├─ Multi-bisnis ✅                                          │
  │  │                                                          │
  │  TO DO sebelum tutup Q4:                                    │
  │  ├─ [ ] Pricing page (ASAP)                                 │
  │  ├─ [ ] Onboarding 3-step                                   │
  │  └─ [ ] Free tier (limit 50 trx)                            │
  └──────────────────────────┬──────────────────────────────────┘
                             │
                             ▼
  Q1 2027 — GROWTH
  ┌─────────────────────────────────────────────────────────────┐
  │  Fokus: Retensi & ARPU naik                                 │
  │  ├─ [ ] WA reminder piutang jatuh tempo                     │
  │  ├─ [ ] Rekonsiliasi bank otomatis                          │
  │  ├─ [ ] Expense tracking (foto nota via WA)                 │
  │  ├─ [ ] Export Excel / PDF / Google Sheets                  │
  │  ├─ [ ] Mobile-friendly PWA                                 │
  │  ├─ [ ] Multi-user role (Owner, Staff, Akuntan)             │
  │  └─ [ ] Budgeting & target per periode                      │
  └──────────────────────────┬──────────────────────────────────┘
                             │
                             ▼
  Q2–Q3 2027 — MOAT
  ┌─────────────────────────────────────────────────────────────┐
  │  Fokus: Diferensiasi yang susah ditiru                      │
  │  ├─ [ ] Mini POS / integrasi POS (Moka/Kasir Pintar API)   │
  │  ├─ [ ] Manajemen stok dasar + HPP otomatis                 │
  │  ├─ [ ] Laporan pajak draft (PPh 21, PPN)                   │
  │  ├─ [ ] AI insight otomatis ("pengeluaran naik 30%")        │
  │  ├─ [ ] Template COA per industri (F&B, Retail, Jasa)       │
  │  └─ [ ] Integrasi marketplace (Tokopedia, Shopee)           │
  └──────────────────────────┬──────────────────────────────────┘
                             │
                             ▼
  Q4 2027+ — EKOSISTEM
  ┌─────────────────────────────────────────────────────────────┐
  │  Fokus: Platform, revenue baru                              │
  │  ├─ [ ] API publik                                          │
  │  ├─ [ ] Marketplace add-on (template, konsultasi akuntan)   │
  │  ├─ [ ] Payroll sederhana → auto-jurnal beban gaji          │
  │  ├─ [ ] Integrasi e-Faktur / Coretax (UMKM PKP)            │
  │  └─ [ ] White-label untuk konsultan/akuntan publik          │
  └─────────────────────────────────────────────────────────────┘
```

---

## Flowchart 4: Keputusan Tambah Fitur POS (Keputusan Kritis)

```
          ┌─────────────────────────────────┐
          │  Mau tambah fitur POS ke        │
          │  AsaFin?                        │
          └──────────────┬──────────────────┘
                         │
          ┌──────────────▼──────────────────┐
          │  Berapa % user AsaFin yang      │
          │  juga butuh kasir/POS?          │
          └──────────────┬──────────────────┘
                < 30% │       │ > 30%
                      │       ▼
                      │  ┌────────────────────────────────────┐
                      │  │  Apakah mau build sendiri          │
                      │  │  atau integrasi ke POS existing?   │
                      │  └────────────────┬───────────────────┘
                      │      BUILD │            │ INTEGRASI
                      │      SENDIRI│           ▼
                      │            │   ┌────────────────────┐
                      │            │   │  Prioritaskan API  │
                      │            │   │  ke Moka atau      │
                      │            │   │  Kasir Pintar      │
                      │            │   │  (Faster to market)│
                      │            │   └────────────────────┘
                      │            ▼
                      │   ┌────────────────────────────────────┐
                      │   │  Scope mini-POS dulu:              │
                      │   │  • Input item + qty + harga        │
                      │   │  • QRIS / cash / transfer          │
                      │   │  • Auto-create jurnal penjualan    │
                      │   │  • Bukan feature-complete kasir    │
                      │   └────────────────────────────────────┘
                      ▼
          ┌───────────────────────────────┐
          │  PARKIR — fokus core dulu,    │
          │  revisit saat ada user demand │
          └───────────────────────────────┘
```

---

## Quick Reference: Impact vs Effort Matrix

```
                HIGH IMPACT
                     │
    ┌────────────────┬┼──────────────────────┐
    │ DO NEXT        ││ DO NOW               │
    │                ││                      │
    │ • Stok dasar   ││ • Pricing page       │
    │ • WA reminder  ││ • Onboarding flow    │
    │   piutang      ││ • Free tier          │
    │ • Mobile PWA   ││ • Export PDF/Excel   │
    │ • Multi-user   ││ • Rekonsiliasi bank  │
    │                ││                      │
LOW ├────────────────┼┼──────────────────────┤ HIGH
EFFORT           EFFORT
    │ SKIP / PARKIR  ││ PLAN CAREFULLY       │
    │                ││                      │
    │ • White-label  ││ • POS integration    │
    │ • Payroll      ││ • Integrasi pajak    │
    │ • API publik   ││ • Marketplace        │
    │ • AI insight   ││ • e-Faktur/Coretax   │
    │                ││                      │
    └────────────────┴┼──────────────────────┘
                      │
                LOW IMPACT
```
