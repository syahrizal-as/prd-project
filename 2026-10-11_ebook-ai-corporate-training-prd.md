# PRD — Platform E-book & Pelatihan AI Korporat

**Status:** Draft v1.0  
**Tanggal:** 11 Oktober 2026  
**Product owner:** Syahrizal Alisadikin  
**Nama kerja:** SyntaxDev Academy  
**Format utama:** Website materi berbasis teks, e-book gratis/berbayar, dan pelatihan AI korporat  
**Tidak termasuk MVP:** video course, marketplace banyak instruktur, LMS kompleks

---

## 1. Ringkasan Eksekutif

SyntaxDev Academy adalah platform edukasi praktis milik Syahrizal Alisadikin untuk membantu individu dan organisasi mempelajari web development, AI praktis, AI-assisted software development, keamanan, dan otomasi kerja.

Platform menggunakan pendekatan **text-first**:

1. artikel dan e-book gratis untuk membangun kepercayaan dan audiens;
2. e-book berbayar untuk pembelajaran mandiri yang lebih terstruktur;
3. pelatihan publik untuk validasi materi dan pengembangan komunitas;
4. pelatihan AI korporat sebagai produk bernilai tinggi;
5. pendampingan implementasi sebagai layanan lanjutan jika dibutuhkan.

Platform tidak bergantung pada video. Nilai utamanya berasal dari materi tertulis yang jelas, contoh nyata, latihan, workbook, template, studi kasus, assessment, dan fasilitasi langsung.

### Visi

Menjadi pusat pembelajaran software dan AI praktis berbahasa Indonesia yang mengajarkan peserta menghasilkan pekerjaan nyata secara aman, terukur, dan dapat diverifikasi.

### Positioning

> Belajar software dan AI dari pengalaman membangun serta memelihara produk nyata—bukan sekadar mengikuti tutorial.

### Keunggulan utama

- Materi berasal dari pengalaman membangun SaaS dan sistem production.
- Fokus pada hasil kerja peserta, bukan banyaknya modul.
- AI diajarkan bersama verifikasi, privasi, keamanan, dan human review.
- Tersedia jalur individu dan korporat.
- Materi text-first mudah diperbarui ketika teknologi berubah.
- Tidak menjual “prompt ajaib” atau janji otomatisasi yang tidak realistis.

---

## 2. Latar Belakang dan Peluang

Syahrizal rutin memberikan pelatihan web development dan AI. Materi, pengalaman, contoh, serta pertanyaan peserta saat ini belum dikemas menjadi aset digital yang terstruktur dan dapat digunakan kembali.

Masalah yang ditemukan:

- materi pelatihan tersebar di slide, catatan, chat, dan contoh proyek;
- calon peserta sulit menilai kedalaman dan gaya pengajaran sebelum mengikuti kelas;
- pendapatan masih bergantung pada waktu mengajar secara langsung;
- organisasi membutuhkan pelatihan AI yang sesuai pekerjaan mereka, bukan materi generik;
- banyak materi AI berfokus pada tool, tetapi lemah dalam verifikasi, privasi, keamanan, dan penerapan;
- video cepat usang dan mahal diproduksi ulang ketika tool AI berubah.

Peluang:

- mengubah pengalaman mengajar menjadi intellectual property;
- membangun trafik dan personal brand melalui materi gratis;
- menghasilkan pendapatan berulang dari e-book berbayar;
- membuka jalur penjualan B2B melalui pelatihan korporat;
- menggunakan e-book dan workbook yang sama sebagai pre-read dan post-training reference;
- membangun portofolio hasil peserta dan studi kasus organisasi secara bertahap.

---

## 3. Sasaran Produk

### 3.1 Sasaran bisnis 12 bulan

1. Memublikasikan minimal 12 materi gratis berkualitas.
2. Meluncurkan minimal 2 e-book berbayar.
3. Menghasilkan minimal 3 cohort pelatihan publik.
4. Mendapatkan minimal 3 engagement pelatihan korporat.
5. Membangun daftar audiens opt-in yang dapat dihubungi secara sah.
6. Mengubah materi yang berulang menjadi modul, workbook, rubric, dan assessment reusable.
7. Mengumpulkan bukti hasil belajar, bukan hanya testimoni kepuasan.

Target numerik harga, omzet, konversi, dan peserta harus ditetapkan setelah discovery pasar dan pilot pertama; PRD tidak mengarang angka tersebut.

### 3.2 Sasaran pengguna

- Pengguna dapat menemukan materi yang sesuai tingkat dan kebutuhan.
- Pengguna dapat membaca e-book gratis tanpa alur rumit.
- Pembeli dapat membayar dan mengakses e-book dengan aman.
- Peserta memahami prasyarat, hasil belajar, dan ruang lingkup sebelum membeli.
- Perusahaan dapat meminta proposal pelatihan yang relevan dengan pekerjaannya.
- Trainer dapat mengelola konten, produk, pesanan, inquiry, cohort, dan assessment tanpa proses manual berlebihan.

### 3.3 Non-goals MVP

MVP tidak bertujuan menjadi:

- platform video course;
- marketplace instruktur;
- aplikasi mobile native;
- sistem sertifikasi kompetensi resmi;
- platform ujian berproctoring;
- komunitas sosial lengkap;
- AI tutor otonom yang mengambil keputusan belajar;
- generator sertifikat yang menyatakan kompetensi tanpa assessment;
- learning management system enterprise penuh.

---

## 4. Target Pengguna

### Persona A — Pembaca gratis

**Profil:** mahasiswa, junior developer, pekerja nonteknis, pemilik UMKM, guru/dosen, atau profesional yang ingin memahami AI dan web development.  
**Kebutuhan:** materi terpercaya dan praktis sebelum membeli produk.  
**Hambatan:** terlalu banyak tutorial generik, istilah teknis, dan klaim berlebihan.  
**Tujuan:** menyelesaikan satu masalah kecil dan memahami kualitas pengajar.

### Persona B — Pembeli e-book

**Profil:** individu yang ingin belajar mandiri dan membutuhkan jalur terstruktur.  
**Kebutuhan:** penjelasan lengkap, latihan, contoh, checklist, template, dan pembaruan materi.  
**Tujuan:** menghasilkan artefak nyata tanpa harus mengikuti video panjang.

### Persona C — Peserta pelatihan publik

**Profil:** individu yang membutuhkan fasilitasi, feedback, dan struktur waktu.  
**Kebutuhan:** demo, praktik, review, dan kesempatan bertanya.  
**Tujuan:** menyelesaikan proyek atau workflow yang dapat ditunjukkan.

### Persona D — Decision maker korporat

**Profil:** HR/L&D, pimpinan unit, CTO/CIO, Head of Digital, manajer operasional, atau pemilik bisnis.  
**Kebutuhan:** pelatihan yang relevan, aman, dapat diukur, serta tidak mengganggu operasi.  
**Tujuan:** meningkatkan produktivitas atau kapabilitas tim dengan outcome yang terlihat.

### Persona E — Peserta korporat

**Profil:** karyawan teknis atau nonteknis dengan kemampuan beragam.  
**Kebutuhan:** kasus penggunaan sesuai pekerjaan, data latihan yang aman, dan panduan yang dapat digunakan setelah pelatihan.  
**Tujuan:** menerapkan AI pada pekerjaan dengan standar review yang disepakati perusahaan.

---

## 5. Prinsip Produk

1. **Text-first:** materi utama berbentuk tulisan, diagram, template, dan latihan.
2. **Output-first:** setiap modul berakhir dengan artefak yang dapat dinilai.
3. **Verification-led AI:** setiap hasil AI penting memiliki langkah pemeriksaan.
4. **Human accountable:** keputusan akhir tetap pada manusia yang berwenang.
5. **Privacy by default:** latihan memakai data sintetis atau data yang secara eksplisit disetujui.
6. **Honest scope:** jelaskan batas materi, alat, data, dan kemampuan peserta.
7. **Progressive disclosure:** materi pemula ringkas; pembahasan teknis mendalam tersedia bertahap.
8. **Reusable:** e-book dapat menjadi pre-read, workbook, dan referensi pascapelatihan.
9. **Evidence over certificate:** sertifikat kehadiran berbeda dari bukti kompetensi.
10. **Simple before scalable:** validasi produk sebelum membangun LMS besar.

---

## 6. Portofolio Produk

### 6.1 Produk gratis

#### A. Artikel publik

Kategori awal:

- AI untuk produktivitas kerja;
- AI literacy dan verifikasi;
- secure vibe coding;
- web development praktis;
- membangun SaaS;
- deployment dan production readiness;
- keamanan aplikasi;
- otomasi workflow.

Setiap artikel idealnya memiliki:

- masalah yang diselesaikan;
- target pembaca dan prasyarat;
- konsep inti;
- contoh;
- langkah praktik;
- checklist verifikasi;
- batasan/risiko;
- CTA ke e-book atau pelatihan yang relevan.

#### B. E-book gratis

Tujuan:

- memberi hasil cepat;
- membangun mailing list dengan persetujuan jelas;
- memperlihatkan gaya dan kualitas pembelajaran;
- menjadi pre-read untuk webinar atau pelatihan.

Kandidat pertama:

**“Checklist Aman Memakai AI untuk Pekerjaan”**

Isi awal:

1. kapan AI cocok digunakan;
2. data apa yang tidak boleh dimasukkan;
3. cara menulis instruksi kerja yang jelas;
4. cara memeriksa fakta dan sumber;
5. review sebelum hasil dikirim;
6. template kebijakan penggunaan sederhana.

Format:

- PDF;
- versi web yang dapat dibaca;
- worksheet/checklist terpisah;
- tidak memakai video.

### 6.2 Produk berbayar

#### E-book 1 — Vibe Coding yang Bertanggung Jawab

**Janji hasil:** pembaca mampu menggunakan AI untuk membangun aplikasi tanpa menyerahkan seluruh pemikiran, keamanan, dan kualitas kepada model.

Outline:

1. cara kerja AI coding secara praktis;
2. requirement sebelum prompt;
3. memecah pekerjaan menjadi task kecil;
4. membaca kode yang dibuat AI;
5. test-first dan acceptance criteria;
6. keamanan secret, authentication, authorization, dan data;
7. database migration dan risiko data loss;
8. deployment, observability, dan rollback;
9. debugging ketika AI berulang kali salah;
10. checklist dari ide sampai production;
11. studi kasus aplikasi sederhana;
12. template prompt builder dan reviewer.

Artefak pembaca:

- requirement template;
- implementation checklist;
- security review checklist;
- test plan;
- deployment checklist;
- postmortem template.

#### E-book 2 — AI Praktis untuk Pekerjaan dan Bisnis

**Janji hasil:** pembaca dapat merancang workflow AI yang membantu pekerjaan tanpa membocorkan data atau mempercayai hasil mentah.

Outline:

1. pemetaan pekerjaan yang cocok dibantu AI;
2. drafting, summarization, extraction, dan classification;
3. penggunaan dokumen internal secara aman;
4. verifikasi sumber dan angka;
5. reusable prompt dan SOP;
6. otomatisasi sederhana;
7. human approval dan audit trail;
8. evaluasi kualitas dan penghematan waktu;
9. risiko privasi, bias, hallucination, dan vendor lock-in;
10. rencana pilot 30 hari.

### 6.3 Pelatihan publik

Produk awal:

#### AI Builder — Dari Ide sampai Aplikasi Siap Demo

Pilihan format:

- 2 hari tatap muka; atau
- 4 sesi daring langsung × 2 jam.

Outcome peserta:

- requirement satu halaman;
- prototype aplikasi;
- source code;
- test dasar;
- checklist keamanan;
- dokumentasi penggunaan;
- presentasi singkat mengenai batas dan risiko.

Tidak ada video course pada MVP. Peserta menerima e-book, workbook, template, contoh, dan materi referensi.

---

## 7. Produk Pelatihan AI Korporat

### 7.1 Nilai utama

Pelatihan korporat bukan kelas “cara memakai chatbot”. Produk dirancang berdasarkan pekerjaan, risiko, data, dan outcome unit bisnis.

Alur nilai:

```text
Discovery → baseline → customization → delivery → assessment → action plan → follow-up
```

### 7.2 Paket pelatihan korporat

#### Paket A — AI Literacy & Responsible Use

**Target:** seluruh karyawan atau kelompok lintas fungsi.  
**Durasi:** 3–4 jam atau 1 hari.  
**Outcome:** peserta memahami kemampuan, batasan, privasi, verifikasi, dan kebijakan penggunaan AI.

Modul:

1. AI generatif dalam bahasa kerja;
2. use case yang tepat dan tidak tepat;
3. prompt sebagai instruksi kerja;
4. hallucination dan pemeriksaan hasil;
5. data pribadi, rahasia, dan intellectual property;
6. human review dan accountability;
7. latihan berbasis pekerjaan peserta.

Artefak:

- safe-use checklist;
- prompt worksheet;
- review checklist;
- draft aturan penggunaan tim.

#### Paket B — AI Productivity for Teams

**Target:** administrasi, marketing, HR, customer service, sales support, operations, dan knowledge worker.  
**Durasi:** 1–2 hari.  
**Outcome:** peserta membuat workflow AI yang dapat digunakan untuk pekerjaan berulang.

Contoh use case:

- merangkum dokumen;
- mengekstrak tugas dan deadline;
- menyusun draft komunikasi;
- membuat FAQ berbasis dokumen;
- analisis tabel dummy;
- membuat SOP dan checklist;
- quality review sebelum publikasi.

Artefak:

- satu workflow per kelompok;
- prompt/SOP reusable;
- risk and review checklist;
- estimasi baseline waktu sebelum/sesudah;
- rencana pilot 30 hari.

#### Paket C — Secure AI-assisted Software Development

**Target:** developer, QA, tech lead, product engineer, dan engineering manager.  
**Durasi:** 2 hari atau 4 sesi.  
**Outcome:** tim mampu memakai coding agent dengan proses requirement, test, security, review, dan deployment yang aman.

Modul:

1. requirement dan acceptance criteria;
2. task decomposition untuk coding agent;
3. context management;
4. TDD dan non-vacuous test;
5. secure secret handling;
6. authentication, authorization, input validation, dan IDOR;
7. database safety dan migration;
8. independent review terhadap klaim agent;
9. CI/CD, rollback, dan runtime verification;
10. team policy untuk AI-generated code.

Artefak:

- aplikasi/prototype tim;
- test suite;
- security checklist;
- agent instruction template;
- AI coding policy draft;
- deployment evidence checklist.

#### Paket D — AI Workflow & Automation Discovery Workshop

**Target:** pimpinan fungsi, transformation team, dan process owner.  
**Durasi:** 1 hari discovery + optional implementation sprint.  
**Outcome:** organisasi memiliki backlog use case yang dinilai berdasarkan value, risk, effort, dan data readiness.

Artefak:

- workflow map;
- use-case inventory;
- prioritization matrix;
- risk register;
- pilot recommendation;
- success metric;
- 30/60/90-day roadmap.

#### Paket E — Custom Corporate Program

Program kustom dapat mencakup:

- kebutuhan sektor tertentu;
- data dan kebijakan organisasi;
- cohort beberapa level;
- train-the-trainer;
- office hours;
- assessment proyek;
- pendampingan pilot.

Proposal dibuat setelah discovery dan tidak menjanjikan outcome sebelum baseline diketahui.

### 7.3 Add-on korporat

- pre-training assessment;
- executive briefing;
- custom case study;
- workbook co-branded;
- policy review;
- post-training clinic;
- assessment proyek;
- implementation sprint;
- laporan hasil dan rekomendasi;
- train-the-trainer.

### 7.4 Data dan privasi pelatihan korporat

Default:

- gunakan data sintetis;
- jangan meminta credential atau secret;
- jangan mengunggah production database;
- jangan memasukkan data pelanggan/karyawan tanpa persetujuan dan kontrol;
- alat yang digunakan harus disepakati organisasi;
- materi custom dan data organisasi dipisahkan dari materi publik;
- retention dan penghapusan file dijelaskan sebelum delivery;
- recording tidak dilakukan secara default.

Jika organisasi mengizinkan data internal:

- klasifikasi data harus ditetapkan;
- akses dibatasi;
- purpose dan retention dicatat;
- vendor/tool harus disetujui;
- contoh publik harus dianonimkan atau dilarang;
- kesepakatan kerahasiaan dapat digunakan bila diperlukan.

---

## 8. User Journey

### 8.1 Pembaca gratis

```text
Search/social/referral
→ landing artikel
→ membaca materi
→ mengunduh e-book gratis atau melihat e-book berbayar
→ memberi persetujuan email opsional
→ menerima materi
→ diarahkan ke produk relevan
```

### 8.2 Pembeli e-book

```text
Product page
→ melihat outcome, outline, sample, author, FAQ, harga
→ checkout
→ pembayaran terkonfirmasi
→ akun/magic link
→ akses halaman baca dan PDF terpersonalisasi
→ mengunduh worksheet
→ menerima pembaruan versi jika kebijakan produk mengizinkan
```

### 8.3 Corporate inquiry

```text
Corporate landing page
→ pilih kebutuhan
→ isi inquiry form
→ acknowledgement otomatis
→ qualification oleh admin
→ discovery call
→ needs assessment
→ proposal dan scope
→ persetujuan
→ pre-assessment
→ delivery
→ post-assessment dan laporan
→ follow-up/pilot
```

### 8.4 Admin content workflow

```text
Draft
→ editorial review
→ technical/factual review
→ publish
→ version update
→ changelog
→ archive/deprecate
```

---

## 9. Informasi Arsitektur Website

### Navigasi utama

- Beranda
- Belajar Gratis
- E-book
- Pelatihan
- Untuk Perusahaan
- Tentang Trainer
- Studi Kasus
- Kontak

### Struktur halaman

#### Beranda

- positioning singkat;
- jalur individu dan perusahaan;
- e-book unggulan;
- pelatihan unggulan;
- bukti pengalaman nyata;
- artikel terbaru;
- CTA utama.

#### Belajar Gratis

- kategori;
- tingkat kesulitan;
- estimasi waktu baca;
- pencarian;
- filter topik;
- learning path;
- artikel dan e-book gratis.

#### Detail e-book

- judul dan outcome;
- target pembaca;
- prasyarat;
- masalah yang diselesaikan;
- outline;
- artefak yang diperoleh;
- sample chapter;
- versi dan tanggal pembaruan;
- format;
- harga;
- FAQ;
- CTA.

#### Halaman korporat

- masalah yang diselesaikan;
- daftar paket;
- outcome dan artefak;
- format delivery;
- proses engagement;
- keamanan dan privasi;
- profil trainer;
- FAQ;
- inquiry form.

#### Studi kasus

Hanya menampilkan klaim yang memiliki izin dan bukti. Struktur:

- konteks;
- masalah;
- peserta;
- pendekatan;
- artefak;
- hasil terukur;
- batasan;
- testimonial dengan izin.

---

## 10. Functional Requirements

### 10.1 Public content

- `FR-CONTENT-001` Pengunjung dapat melihat daftar artikel publik.
- `FR-CONTENT-002` Pengunjung dapat memfilter berdasarkan topik, level, dan jenis materi.
- `FR-CONTENT-003` Halaman menampilkan author, tanggal, versi, estimasi waktu baca, dan status pembaruan.
- `FR-CONTENT-004` Artikel mendukung heading, code block, diagram/image, callout, checklist, dan file download.
- `FR-CONTENT-005` Materi dapat ditandai deprecated dan diarahkan ke versi baru.
- `FR-CONTENT-006` Draft tidak dapat diakses publik hanya dengan mengetahui slug.

### 10.2 E-book gratis

- `FR-FREE-001` Admin dapat menerbitkan e-book gratis.
- `FR-FREE-002` Pengunjung dapat membaca versi web atau mengunduh PDF.
- `FR-FREE-003` Jika email diminta, consent marketing harus terpisah dari kebutuhan pengiriman file.
- `FR-FREE-004` Sistem mencatat download secara agregat tanpa tracking berlebihan.
- `FR-FREE-005` Link download dapat memiliki expiration atau rate limit untuk mencegah abuse.

### 10.3 E-book berbayar

- `FR-PAID-001` Pengguna dapat melihat preview sebelum membeli.
- `FR-PAID-002` Checkout menunjukkan harga final, isi produk, dan kebijakan akses.
- `FR-PAID-003` Akses hanya aktif setelah pembayaran terverifikasi server-side.
- `FR-PAID-004` Webhook pembayaran harus diverifikasi dan idempoten.
- `FR-PAID-005` Pembayaran retry tidak boleh membuat order atau entitlement ganda.
- `FR-PAID-006` Pengguna dapat membaca e-book dalam web dan mengunduh PDF sesuai hak akses.
- `FR-PAID-007` PDF dapat diberi watermark identitas pembeli secara terbatas, tanpa data sensitif berlebihan.
- `FR-PAID-008` Pengguna dapat mengunduh workbook/template terkait.
- `FR-PAID-009` Admin dapat mengubah harga tanpa mengubah transaksi historis.
- `FR-PAID-010` Refund dan pencabutan akses memiliki audit trail.

### 10.4 Akun dan akses

- `FR-AUTH-001` Pengguna dapat masuk dengan magic link atau metode aman yang sederhana.
- `FR-AUTH-002` Password, bila digunakan, wajib di-hash dengan mekanisme framework yang aman.
- `FR-AUTH-003` Rate limit diterapkan pada login dan magic link.
- `FR-AUTH-004` Semua entitlement dicek server-side.
- `FR-AUTH-005` User tidak dapat mengakses order, invoice, atau library pengguna lain.
- `FR-AUTH-006` Admin role dipisahkan dari user role.

### 10.5 Corporate inquiry dan CRM ringan

- `FR-CORP-001` Pengunjung dapat mengisi nama, organisasi, email kerja, jabatan, kebutuhan, jumlah peserta, mode, perkiraan waktu, dan catatan.
- `FR-CORP-002` Field sensitif yang tidak diperlukan dilarang.
- `FR-CORP-003` Sistem mengirim acknowledgement tanpa menjanjikan jadwal atau harga final.
- `FR-CORP-004` Admin dapat memberi status `NEW`, `QUALIFIED`, `DISCOVERY`, `PROPOSAL`, `WON`, `LOST`, atau `ARCHIVED`.
- `FR-CORP-005` Admin dapat menulis catatan internal dan next action.
- `FR-CORP-006` Inquiry memiliki owner dan audit trail.
- `FR-CORP-007` File organisasi tidak dapat diakses publik.
- `FR-CORP-008` Proposal dapat dibuat dari template, tetapi harga dan scope harus direview manusia.

### 10.6 Cohort dan delivery

- `FR-TRAIN-001` Admin dapat membuat program, cohort, jadwal, kapasitas, dan mode delivery.
- `FR-TRAIN-002` Peserta dapat menerima pre-read, workbook, dan agenda.
- `FR-TRAIN-003` Admin dapat mencatat kehadiran.
- `FR-TRAIN-004` Pre-test dan post-test dapat diaktifkan per program.
- `FR-TRAIN-005` Project rubric dapat digunakan untuk assessment.
- `FR-TRAIN-006` Sertifikat membedakan kehadiran dan penyelesaian assessment.
- `FR-TRAIN-007` Sertifikat tidak menyatakan sertifikasi profesi resmi.
- `FR-TRAIN-008` Trainer dapat mengekspor laporan cohort tanpa membocorkan data cohort lain.

### 10.7 Admin CMS

- `FR-ADMIN-001` Admin dapat membuat dan mengubah artikel, e-book, halaman produk, program, dan FAQ.
- `FR-ADMIN-002` Konten memiliki state `DRAFT`, `IN_REVIEW`, `PUBLISHED`, `DEPRECATED`, `ARCHIVED`.
- `FR-ADMIN-003` Perubahan penting memiliki version dan changelog.
- `FR-ADMIN-004` Technical claims dapat diberi reviewer dan review date.
- `FR-ADMIN-005` Publish memerlukan validasi title, slug, description, author, level, outcome, dan disclosure.
- `FR-ADMIN-006` File upload dibatasi berdasarkan tipe, ukuran, malware scan, dan authorization.

### 10.8 Analytics

- `FR-ANALYTICS-001` Admin dapat melihat page view agregat, download, checkout started, purchase, inquiry, dan conversion.
- `FR-ANALYTICS-002` Analytics memisahkan free reader, buyer, training lead, dan corporate lead tanpa fingerprinting invasif.
- `FR-ANALYTICS-003` UTM source/campaign dapat direkam.
- `FR-ANALYTICS-004` Corporate funnel dapat dilihat berdasarkan status.
- `FR-ANALYTICS-005` Learning outcome disimpan terpisah dari marketing analytics.

---

## 11. Model Konten dan Data Konseptual

Entitas utama:

### User

- id;
- name;
- email;
- emailVerifiedAt;
- role;
- consent flags;
- createdAt;
- updatedAt.

### Content

- id;
- type (`ARTICLE`, `FREE_EBOOK`, `PAID_EBOOK`, `PAGE`);
- title;
- slug;
- summary;
- body/source path;
- status;
- level;
- topics;
- authorId;
- reviewerId;
- publishedAt;
- updatedAt;
- version;
- disclosure;
- SEO metadata.

### Product

- id;
- productType;
- title;
- description;
- price;
- currency;
- status;
- accessPolicy;
- currentContentVersion.

### Order

- id;
- userId;
- productId;
- amount;
- currency;
- paymentProvider;
- externalReference;
- status;
- paidAt;
- refundedAt;
- immutable price snapshot.

### Entitlement

- id;
- userId;
- productId;
- orderId;
- status;
- grantedAt;
- revokedAt;
- reason.

### CorporateInquiry

- id;
- organization;
- contactName;
- workEmail;
- role;
- participantEstimate;
- audienceProfile;
- desiredOutcome;
- deliveryMode;
- preferredWindow;
- status;
- ownerId;
- nextActionAt;
- createdAt.

### TrainingProgram

- id;
- name;
- type;
- targetAudience;
- outcomes;
- duration;
- deliveryModes;
- modules;
- requiredAssets;
- status;
- version.

### Cohort

- id;
- programVersion;
- client/institution;
- startAt;
- endAt;
- timezone;
- mode;
- capacity;
- status.

### Participant

- id;
- cohortId;
- userId/email;
- attendance;
- preAssessment;
- postAssessment;
- projectScore;
- certificateType.

### AuditLog

- actor;
- action;
- entityType;
- entityId;
- prior state metadata;
- new state metadata;
- timestamp.

---

## 12. Content Governance

### Review levels

1. **Editorial review:** struktur, bahasa, keterbacaan.
2. **Technical review:** kode, formula, keamanan, dan reproduksibilitas.
3. **Source review:** klaim legal, kebijakan, statistik, pricing tool, dan standar.
4. **Training validation:** dry run, estimasi waktu, latihan, dan expected output.

### Versioning

- Minor typo tidak memerlukan versi produk baru.
- Perubahan konsep, tool, API, atau rekomendasi keamanan harus menaikkan versi/changelog.
- Pembeli melihat versi yang sedang dibaca dan tanggal pembaruan.
- Perubahan besar tidak boleh diam-diam menghilangkan akses yang sudah dibeli.

### AI-assisted authorship

Jika AI digunakan dalam drafting:

- manusia tetap menjadi author/editor yang bertanggung jawab;
- fakta dan contoh teknis diverifikasi;
- source eksternal diberi atribusi;
- materi tidak boleh menyalin karya pihak lain secara substansial;
- confidential client material tidak digunakan untuk melatih atau membuat materi publik.

---

## 13. Assessment dan Bukti Belajar

### Untuk pembaca e-book

Assessment bersifat opsional dan self-check:

- checkpoint per bab;
- latihan;
- rubric mandiri;
- final project checklist.

### Untuk pelatihan publik/korporat

Evidence minimum:

- pre-test baseline;
- artefak praktik;
- review menggunakan rubric;
- post-test;
- action plan.

Indikator keberhasilan bukan hanya skor kuis. Contoh:

- peserta dapat membedakan data aman dan tidak aman untuk AI;
- peserta dapat membuat workflow dengan human review;
- developer dapat menunjukkan test yang gagal lalu lulus;
- tim dapat mengidentifikasi risiko dan owner keputusan;
- process owner dapat menyusun pilot yang memiliki baseline dan metric.

### Sertifikat

Jenis:

- Certificate of Attendance;
- Certificate of Completion;
- Assessed Project Completion, bila benar-benar ada rubric dan penilaian.

Sertifikat tidak boleh memakai klaim “certified expert” atau kompetensi resmi tanpa otoritas yang sah.

---

## 14. Monetisasi

### Revenue stream

1. E-book berbayar.
2. Pelatihan publik per peserta.
3. Pelatihan korporat per engagement.
4. Customization fee.
5. Assessment/report add-on.
6. Implementation sprint atau advisory.
7. Lisensi materi internal berdasarkan kontrak.

### Prinsip pricing

- Harga e-book mengikuti kedalaman, artefak, dan update policy.
- Harga korporat mengikuti discovery, jumlah peserta, durasi, customization, travel, assessment, dan follow-up.
- Jangan memublikasikan harga corporate final jika scope sangat variatif; tampilkan “mulai dari” hanya jika ada paket standar yang benar-benar dapat dibeli pada harga itu.
- Proposal harus menyebut apa yang termasuk dan tidak termasuk.

### Free-to-paid conversion

```text
Artikel gratis
→ e-book gratis
→ e-book berbayar atau webinar
→ pelatihan publik
→ corporate inquiry / advisory
```

CTA harus relevan terhadap materi, bukan pop-up agresif di setiap halaman.

---

## 15. Arsitektur Teknis Rekomendasi

### MVP stack

Disarankan menggunakan stack yang sudah dikuasai:

- **Frontend/full stack:** Next.js;
- **Database:** PostgreSQL;
- **ORM:** Prisma;
- **Authentication:** magic link/OAuth melalui library auth yang teruji;
- **Content:** MDX atau Markdown di repository untuk versioning;
- **File storage:** S3-compatible object storage;
- **Payment:** payment gateway Indonesia yang dipilih setelah validasi fee dan settlement;
- **Email:** transactional email provider;
- **Deployment:** container/standalone dengan CI/CD;
- **Analytics:** privacy-conscious first-party analytics;
- **Error monitoring:** structured logs + error tracker.

Alternatif Laravel layak jika ingin menyatukan admin, payment, queue, dan reporting dalam pola yang lebih familiar. Keputusan final harus mempertimbangkan repository yang akan digunakan dan kemampuan operasional, bukan tren framework.

### Arsitektur konseptual

```text
Browser
  ↓
Web Application
  ├── Public content renderer
  ├── Authentication
  ├── Store & checkout
  ├── Entitlement service
  ├── Corporate lead management
  ├── Training/cohort management
  └── Admin CMS
        ↓
PostgreSQL
Object Storage
Payment Gateway
Email Provider
Observability
```

### YAGNI untuk MVP

Tidak perlu pada awal:

- microservices;
- event streaming;
- AI recommendation engine;
- native app;
- SCORM/xAPI;
- multi-tenant corporate portal penuh;
- DRM berat yang menyulitkan pembeli legal.

---

## 16. Security, Privacy, dan Compliance Requirements

### Authentication dan authorization

- server-side authorization untuk content premium, order, invoice, participant, dan corporate files;
- deny-by-default untuk admin route;
- CSRF protection pada state-changing request;
- session cookie aman;
- rate limit pada authentication dan download.

### Payment

- webhook signature diverifikasi;
- nominal, currency, product, dan merchant reference diverifikasi server-side;
- webhook idempotent;
- status client tidak boleh mengaktifkan entitlement;
- refund/reversal ditangani eksplisit;
- jangan menyimpan card data.

### File dan e-book

- signed URL dengan expiry;
- authorization sebelum URL dibuat;
- validasi MIME dan extension;
- malware scan untuk upload;
- private bucket untuk produk berbayar dan corporate assets;
- hindari predictable public URL.

### Personal data

- kumpulkan hanya data yang diperlukan;
- privacy notice jelas;
- consent marketing terpisah;
- retention policy;
- mekanisme koreksi dan penghapusan bila berlaku;
- jangan memublikasikan nama organisasi/testimonial tanpa izin.

### Corporate confidentiality

- tenant/client boundary pada setiap query;
- file dan report per organisasi;
- audit akses admin;
- export dibatasi;
- tidak menggunakan data klien sebagai contoh publik tanpa persetujuan tertulis.

### AI-specific safety

- tidak meminta secret, credential, atau production dataset;
- prompt latihan menggunakan data dummy;
- output AI penting wajib direview;
- tidak menjanjikan real-time/factual accuracy tanpa sumber;
- tool/vendor disclosure bila relevan;
- kebijakan untuk copyrighted/confidential material.

---

## 17. Non-Functional Requirements

### Performance

- LCP halaman publik target ≤2,5 detik pada koneksi seluler wajar.
- Artikel/e-book web bersifat cacheable tanpa membocorkan konten premium.
- Download besar memakai object storage/CDN.

### Availability

- Halaman publik dan library pembeli memiliki target availability yang realistis.
- Kegagalan analytics/email tidak boleh menggagalkan pembacaan materi atau pembayaran yang telah terverifikasi.
- Payment webhook memiliki retry-safe processing.

### Accessibility

- navigasi keyboard;
- contrast memadai;
- semantic heading;
- alt text;
- label form;
- error message tidak hanya berdasarkan warna;
- PDF memiliki struktur yang dapat dibaca sejauh tool memungkinkan.

### SEO

- canonical URL;
- metadata unik;
- sitemap;
- structured data yang tidak melebih-lebihkan review/course claim;
- crawlable article content;
- noindex untuk account, checkout, draft, dan private pages.

### Observability

- structured logs;
- correlation ID;
- audit trail untuk payment dan entitlement;
- alert untuk webhook failure, repeated login abuse, storage error, dan email failure;
- dashboard funnel tanpa mengekspos PII.

### Backup dan recovery

- backup database otomatis;
- restore drill;
- versioned content repository;
- object storage versioning/backup sesuai biaya;
- documented RPO/RTO sebelum transaksi riil.

---

## 18. Analytics dan KPI

### Acquisition

- organic visits;
- referral/social visits;
- landing-to-reader conversion;
- free e-book download;
- opt-in rate.

### Commerce

- product page → checkout;
- checkout → paid;
- payment failure rate;
- refund rate;
- repeat purchase.

### Learning

- completion self-report atau checkpoint;
- pre/post improvement;
- project completion;
- artifact quality berdasarkan rubric;
- application after 30 days.

### Corporate funnel

- inquiry count;
- qualified leads;
- discovery completed;
- proposal sent;
- win/loss;
- time to close;
- repeat engagement;
- participant outcome;
- pilot adoption.

### Guardrail metrics

- complaint/refund;
- material correction rate;
- privacy/security incident;
- certificate dispute;
- unsupported claim detected;
- participant data deletion request.

---

## 19. MVP Scope

### Included

- marketing website;
- article library;
- free and paid e-book catalog;
- web reader;
- PDF download;
- authentication;
- checkout/payment integration;
- entitlement;
- personal library;
- corporate landing page;
- corporate inquiry form;
- lightweight admin inquiry pipeline;
- program/cohort records sederhana;
- content CMS berbasis Markdown/MDX + metadata;
- transactional email;
- analytics dasar;
- audit log dasar;
- legal pages.

### Excluded

- video hosting;
- livestream platform;
- discussion forum;
- marketplace;
- multi-instructor payout;
- advanced LMS;
- proctored exam;
- AI tutor;
- corporate SSO;
- white-label tenant portal;
- mobile app.

---

## 20. Roadmap

### Phase 0 — Discovery dan validasi (1–2 minggu)

- tetapkan nama/brand final;
- wawancara 5–10 calon pembaca;
- wawancara 3–5 decision maker perusahaan;
- pilih e-book gratis pertama;
- pilih e-book berbayar pertama;
- pilih satu paket corporate utama;
- validasi metode pembayaran;
- validasi legal/privacy baseline;
- inventaris materi lama.

**Exit criteria:** masalah, audiens, outcome, dan produk pertama disetujui.

### Phase 1 — Content-led MVP (3–5 minggu)

- landing page;
- profile trainer;
- article system;
- corporate page;
- inquiry form;
- free e-book delivery;
- 3–5 artikel awal;
- analytics dasar;
- legal pages.

**Exit criteria:** pengunjung dapat membaca, mengunduh materi gratis, dan mengirim inquiry.

### Phase 2 — Paid e-book (3–4 minggu)

- authentication;
- catalog dan detail product;
- checkout;
- verified payment webhook;
- entitlement;
- web reader/private download;
- order history;
- admin order view.

**Exit criteria:** satu transaksi sandbox dan satu transaksi nominal kecil production melewati payment → entitlement → access → receipt tanpa duplikasi.

### Phase 3 — Training operations (2–4 minggu)

- program/cohort;
- participant import;
- pre/post assessment;
- attendance;
- workbook distribution;
- certificate rules;
- corporate reporting template.

**Exit criteria:** satu pilot cohort selesai dengan artefak, assessment, dan laporan.

### Phase 4 — Optimization

- conversion improvement;
- product bundle;
- licensing;
- follow-up automation;
- organization portal jika permintaan nyata membuktikan kebutuhan;
- additional e-books dan corporate tracks.

---

## 21. Launch Content Plan

### Free content pertama

1. Apa Itu Vibe Coding dan Apa Risikonya?
2. Cara Meminta AI Menulis Kode Tanpa Kehilangan Kendali.
3. Checklist Sebelum Deploy Kode dari AI.
4. Cara Memeriksa Jawaban AI yang Terlihat Meyakinkan.
5. Data yang Tidak Boleh Dimasukkan ke AI Publik.
6. Dari Prompt ke SOP: Membuat Hasil AI Konsisten.
7. Laravel/Next.js: Memilih Stack untuk Produk Pertama.
8. Kenapa Test Hijau Belum Tentu Membuktikan Fitur Benar.

### Lead magnet

**Checklist Aman Memakai AI untuk Pekerjaan**

### Paid product pertama

**Vibe Coding yang Bertanggung Jawab**

### Corporate flagship pertama

**Secure AI-assisted Software Development** untuk tim engineering, karena paling kuat terhubung dengan pengalaman dan portofolio Syahrizal.

Paket kedua setelah pilot:

**AI Productivity for Teams** untuk audiens nonteknis.

---

## 22. Acceptance Criteria MVP

### Public content

- Pengunjung dapat menemukan dan membaca artikel pada mobile dan desktop.
- Draft/private content tidak muncul di sitemap, API publik, HTML, atau client bundle.
- Metadata, canonical, dan structured data valid.

### Free e-book

- Pengunjung dapat memperoleh e-book dan worksheet.
- Persetujuan marketing tidak dipaksakan untuk memenuhi pengiriman transaksional bila model bisnis tidak mensyaratkannya.
- Download event tercatat secara agregat.

### Paid e-book

- Pembayaran terverifikasi membuat tepat satu order dan entitlement.
- Webhook duplikat tidak membuat akses ganda.
- Pengguna A tidak dapat mengakses e-book/order pengguna B.
- Refund/reversal menghasilkan state yang sesuai kebijakan.
- Konten premium tidak bocor ke payload halaman publik atau bundle client.

### Corporate inquiry

- Inquiry valid tersimpan dan menghasilkan acknowledgement.
- Spam/rate abuse dibatasi.
- Admin dapat mengubah status dan mencatat next action.
- Corporate file tidak memiliki public URL.

### Training

- Program menyebut audience, prerequisite, outcome, agenda, artifact, assessment, dan fallback.
- Satu pilot menjalani pre-test, praktik, post-test, dan menghasilkan laporan.
- Sertifikat tidak melebihi bukti yang dinilai.

### Operations

- Backup dan restore diuji.
- Error monitoring aktif.
- Payment dan entitlement memiliki audit trail.
- Production deploy memiliki rollback.
- Tidak ada secret di repository atau client bundle.

---

## 23. Testing Strategy

### Unit tests

- pricing snapshot;
- entitlement state;
- content publication predicate;
- inquiry status transition;
- certificate eligibility;
- consent handling.

### Integration tests

- payment webhook signature dan idempotency;
- payment → entitlement;
- refund → access policy;
- signed download authorization;
- inquiry creation;
- participant import;
- tenant/client boundary.

### Security tests

- IDOR order/library/download;
- admin authorization;
- rate limiting;
- malicious upload;
- XSS dalam Markdown/MDX;
- CSRF;
- webhook replay;
- session fixation;
- premium content leakage melalui RSC/API/client chunks.

### Content QA

- broken link;
- source validity;
- code sample reproducibility;
- claim review;
- reading time;
- mobile rendering;
- PDF accessibility;
- workbook completeness.

### Training dry run

- login/setup time;
- internet failure fallback;
- tool quota;
- participant device compatibility;
- example reproducibility;
- practice/review time;
- no confidential data.

---

## 24. Operational Workflows

### Publishing

```text
Author draft
→ editorial review
→ technical/source review
→ preview
→ publish
→ monitor corrections
→ version/changelog
```

### Payment incident

```text
Alert
→ identify provider event
→ check signature/reference/idempotency
→ compare order and entitlement
→ apply safe reconciliation
→ notify affected user
→ document incident
```

### Corporate delivery

```text
Qualification
→ discovery
→ confirmed scope
→ data/tool approval
→ pre-assessment
→ customization
→ dry run
→ delivery
→ assessment
→ report
→ follow-up
```

### Material correction

```text
Issue reported
→ severity classification
→ verify source
→ correct web and PDF
→ increment version when material
→ notify affected buyers if consequential
→ record changelog
```

---

## 25. Risks dan Mitigasi

### Risiko: terlalu banyak topik

**Mitigasi:** mulai dengan satu flagship e-book dan satu flagship corporate program.

### Risiko: membangun LMS sebelum pasar terbukti

**Mitigasi:** gunakan Markdown/MDX, simple entitlement, dan operasi ringan.

### Risiko: materi AI cepat usang

**Mitigasi:** ajarkan prinsip dan workflow, gunakan version/changelog, hindari ketergantungan pada screenshot tool.

### Risiko: klaim pelatihan terlalu besar

**Mitigasi:** outcome harus berupa artefak observable; jangan menyamakan attendance dengan competence.

### Risiko: data perusahaan bocor

**Mitigasi:** data sintetis default, approval tool, access control, retention, dan confidentiality rules.

### Risiko: piracy e-book

**Mitigasi:** friction ringan seperti personalized watermark dan signed link; fokus pada update, template, dan support value—bukan DRM agresif.

### Risiko: payment mismatch

**Mitigasi:** server-side verified webhook, idempotency, immutable order snapshot, dan reconciliation tool.

### Risiko: ketergantungan pada Syahrizal

**Mitigasi:** facilitator guide, trainer notes, rubric, template, dan versioned curriculum.

### Risiko: materi gratis mengkanibal produk berbayar

**Mitigasi:** gratis menyelesaikan masalah kecil; berbayar memberikan jalur utuh, latihan, template, dan konteks mendalam.

---

## 26. Open Questions

Keputusan berikut perlu dikonfirmasi sebelum implementasi:

1. Apakah brand final memakai **SyntaxDev Academy**, nama pribadi, atau brand baru?
2. Apakah website berdiri sendiri atau berada di domain/subdomain SyntaxDev?
3. Framework final: Next.js atau Laravel?
4. Payment gateway mana yang tersedia dan sesuai biaya?
5. Apakah free e-book wajib login atau dapat diunduh dengan link?
6. Apakah pembeli mendapat pembaruan seumur hidup atau per major version?
7. Apakah PDF download dibatasi jumlah/perangkat?
8. Siapa reviewer teknis/editorial selain Syahrizal?
9. Apakah pelatihan korporat tersedia onsite seluruh Indonesia atau area tertentu?
10. Apakah harga corporate ditampilkan atau hanya melalui proposal?
11. Apakah sertifikat diperlukan pada MVP?
12. Bahasa pertama Indonesia saja atau bilingual?
13. Apakah diperlukan invoice/faktur pajak dari badan usaha tertentu?
14. Apa status legal/brand operator yang akan dipakai dalam kontrak?

Open questions ini bukan blocker untuk validasi konten, tetapi blocker untuk checkout production, kontrak, invoicing, dan launch komersial penuh.

---

## 27. Definition of Done Produk Pertama

Produk pertama dinyatakan selesai jika:

1. E-book memiliki target pembaca, outcome, outline, latihan, template, dan review checklist.
2. Semua contoh teknis dapat direproduksi.
3. Klaim faktual penting memiliki sumber atau catatan verifikasi.
4. PDF dan versi web konsisten.
5. Product page menjelaskan isi dan batas produk.
6. Checkout sandbox dan production nominal kecil berhasil.
7. Entitlement tidak dapat dibypass.
8. Pembeli dapat membaca dan mengunduh produk.
9. Refund/retry diuji.
10. Backup, logs, dan alert tersedia.
11. Minimum tiga pembaca pilot memberi feedback terstruktur.
12. Minimal satu pembaca dapat menghasilkan artefak yang dijanjikan tanpa bantuan langsung dari author.

## 28. Definition of Done Corporate Pilot

Corporate pilot dinyatakan berhasil jika:

1. audience, baseline, durasi, fasilitas, dan outcome dikonfirmasi;
2. organisasi menyetujui tool dan aturan data;
3. materi menjalani dry run;
4. peserta menyelesaikan pre-assessment;
5. setiap blok menghasilkan artefak;
6. hasil dinilai dengan rubric;
7. post-assessment selesai;
8. laporan memisahkan attendance, satisfaction, knowledge gain, dan applied artifact;
9. rekomendasi tindak lanjut memiliki owner dan metric;
10. materi/data organisasi dihapus atau disimpan sesuai kesepakatan;
11. testimonial/studi kasus hanya diterbitkan setelah izin.

---

## 29. Rekomendasi Keputusan Awal

1. Gunakan **SyntaxDev Academy** sebagai nama kerja dan **Syahrizal Alisadikin** sebagai trainer utama.
2. Mulai dari text-first, tanpa video.
3. Luncurkan free e-book **Checklist Aman Memakai AI untuk Pekerjaan**.
4. Jadikan **Vibe Coding yang Bertanggung Jawab** sebagai paid flagship.
5. Jadikan **Secure AI-assisted Software Development** sebagai corporate flagship pertama.
6. Gunakan **AI Productivity for Teams** sebagai paket korporat kedua.
7. Validasi permintaan sebelum membangun fitur LMS lanjutan.
8. Gunakan website sebagai pusat trust, penjualan, inquiry, dan library—bukan sebagai proyek teknologi yang terlalu besar.

---

## 30. Next Actions

1. Konfirmasi brand dan domain.
2. Pilih flagship e-book dan corporate program.
3. Inventaris materi lama.
4. Wawancara calon pembaca dan tiga decision maker korporat.
5. Susun outline detail free e-book.
6. Susun outline detail paid e-book.
7. Buat facilitator-ready package untuk corporate flagship.
8. Validasi payment, invoice, dan badan usaha.
9. Buat wireframe website.
10. Setelah requirement final, buat implementation plan teknis terpisah sebelum coding.
