# 066 — Catatan Kerja: Tahap 1 – Pemicu (dua modul) dan Rencana Tahap 3 – Aksi

> Disimpan: 15-11-2026 17:10 WIB (+07).
> Branch kerja: `arena/aedbcd0d-codeshark-qwen3-8max2` (dari `main` @ `51d13de`).
> Isi: rekap apa yang sudah dikerjakan pada 13–15 November 2026, di mana hasilnya
> berada, dan apa yang masih terbuka. Dokumen ini hanya merangkum; rincian tetap
> di dokumen 052–065 yang dirujuk.

---

## 1. Ringkasan

Dalam tiga hari dikerjakan empat hal, semuanya sudah digabung ke `main`:

1. **Simulasi Krisis Produksi** (AI-Trap Simulator), modul pertama Tahap 1 – Pemicu.
2. **Gerbang masuk CodeShark** untuk simulasi itu.
3. **Dokumen perencanaan**: PRD, requirement, design, dan tasklist untuk
   kelanjutan Tahap 1 dan untuk Tahap 3 – Aksi. Tahap 3 **belum dibangun**.
4. **Blind Live-Coding Challenge** dengan Rapor Kegagapan Sintaksis, modul kedua
   Tahap 1 – Pemicu.

Hasil akhirnya untuk murid kelompok Mahasiswa/Umum: dua langkah wajib, masing-masing
satu kali, sebelum latihan reguler. Pertama simulasi krisis (memperbaiki kode
"buatan AI" yang rusak), lalu blind challenge (menulis kode dari halaman kosong).

---

## 2. Kronologi

Waktu dalam WIB.

| Kapan | Pekerjaan | PR | Commit gabung | Ukuran |
|---|---|---|---|---|
| 13-11, 21:45 | Rencana Blind Live-Coding Challenge (dok. 052) | — | — | — |
| 13-11, 21:50 | Rencana AI-Trap Simulator (dok. 053); 052 ditandai "digantikan" | — | — | — |
| 14-11, 14:14 | Simulasi Krisis Produksi, MVP | #15 | `11c10c1` | 21 berkas, +4.215 / −4 |
| 14-11, 14:30 | Gerbang masuk CodeShark | #16 | `c6bc695` | 6 berkas, +185 / −20 |
| 14-11, 18:17–21:10 | Dokumen 056–064 ditulis | — | — | — |
| 15-11, 12:26 | Dokumen 056–064 digabung | #17 | `d52c04e` | 12 berkas, +3.015 / −4 |
| 15-11, 16:49 | Blind Live-Coding Challenge (052 dibangun) | #18 | `51d13de` | 17 berkas, +3.138 / −10 |
| 15-11, 17:07 | `main` fork digabung ke repo induk oleh pemilik repo induk | #37 (repo induk) | `31fab4e` | 28 berkas, +6.153 / −14 |

PR #15–#18 ada di fork `rozanhaisyam/codeshark-qwen3.8max2`. PR #37 ada di repo
induk `haisyamalawwab/codeshark-qwen3.8max2` dan bukan bagian dari pekerjaan ini;
dicatat karena sejak itu `main` di kedua repo menunjuk commit yang sama
(`31fab4e`). Isi berkas `31fab4e` sama persis dengan `51d13de`.

---

## 3. Yang dibangun

### 3.1 Simulasi Krisis Produksi (PR #15)

Rancangan: 053. Catatan implementasi: 054.

- **Babak 1, Jebakan (3 menit):** satu berkas HTML + CSS + JS berisi empat cacat
  yang ditanam. Editor polos tanpa autocomplete; tempel ditolak. Tombol Jalankan
  mengeksekusi kode di iframe ter-sandbox dan menampilkan error asli browser.
- **Babak 2, Cermin:** putar ulang ketikan, pembanding waktu dan biaya dengan AI,
  peta panas keyboard, angka pendukung, lalu pembongkaran keempat cacat.
- **Keputusan pemilik:** skenario mencampur HTML, CSS, dan JS; nada faktual dan
  semua angka murid adalah hasil ukur; angka AI hanya di
  `src/data/aiBenchmark.ts`; telemetri dan 10 percobaan terakhir disimpan;
  pembongkaran jebakan wajib tampil.
- **Berkas inti:** `src/lib/trapLint.ts`, `trapMetrics.ts`, `trapRunner.ts`,
  `src/data/aiTrapScenarios.ts`, `aiBenchmark.ts`, `src/ui/AiTrapModule.tsx`,
  `AiTrapDiagnostic.tsx`, `AiTrapCard.tsx`, `KeyboardHeatmap.tsx`,
  `tests/ai-trap.test.mjs`.

### 3.2 Gerbang masuk CodeShark (PR #16)

Catatan: 055.

Di `/codingshark/` simulasi tampil **sebelum** Dashboard, bukan baru saat latihan
pertama ditekan. Di Coding Tower gerbangnya tetap di latihan pertama. Perangkat
tanpa keyboard fisik tidak digerbang.

### 3.3 Blind Live-Coding Challenge (PR #18)

Rancangan: 052. Catatan implementasi, selisih dari rancangan, dan batasnya: 065.

- **Sesi 3 menit:** menulis HTML + `<style>` + `<script>` dari halaman kosong.
  Tanpa contoh, pewarnaan, pratinjau, autocomplete, tempel, atau jeda. Tiga varian
  soal: Tombol Penghitung, Kartu Sapaan, Daftar Tugas Mini.
- **Rapor Kegagapan Sintaksis:** jeda panjang sebelum `{ }` dan `;`, jumlah
  *syntax error* pada kode akhir, garis waktu, waktu beku, salah tombol simbol,
  tuntutan soal yang terpenuhi, keyakinan diri berbanding hasil. Tingkat (Lancar,
  Tersendat, Gagap berat) ditentukan aturan yang ditampilkan di rapor.
- **Keputusan pemilik:** 052 dibangun sebagai modul kedua, bukan pengganti 053;
  gerbang wajib satu kali sebelum latihan pertama (D3), termasuk untuk pengguna
  lama.
- **Berkas inti:** `src/lib/blindMetrics.ts`, `blindLint.ts`, `blindAttempt.ts`,
  `src/data/blindChallenges.ts`, `src/ui/BlindChallenge.tsx`,
  `BlindReportCard.tsx`, `BlindCard.tsx`, `tests/blind-lint.test.mjs`,
  `tests/blind-metrics.test.mjs`.

### 3.4 Aturan yang sama untuk kedua modul

| Hal | Berlaku |
|---|---|
| Wajib satu kali | kelompok `academy` (Mahasiswa/Umum) |
| Opsional lewat kartu Dashboard | kelompok `senior` (16–19 tahun) |
| Tidak ditampilkan | kelompok `junior` dan `teen` (10–15 tahun) |
| Tanpa keyboard fisik | ditunda; latihan tetap terbuka |
| Hadiah | 30 XP per modul, sekali, berapa pun hasilnya |
| Dampak ke nilai | tidak ada: rank dan koin tidak berubah |
| Penyimpanan | di `SaveData` (`aiTrap`, `blind`); ikut sinkron sebagai `save_data`; tanpa migrasi skema |
| Jalan keluar | tautan aksesibilitas melepas gerbang tanpa hasil dan tanpa XP |

Urutan gerbang untuk `academy`:

```
CodeShark   : buka /codingshark/ → Simulasi Krisis → Dashboard → tombol latihan → Blind Challenge → arena
Coding Tower: Dashboard → tombol latihan → Simulasi Krisis → Blind Challenge → arena
```

---

## 4. Dokumen yang ditulis

| No. | Isi | Status |
|---|---|---|
| 052 | Rencana Blind Live-Coding Challenge | dibangun (lihat 065) |
| 053 | Rencana AI-Trap & Production Crisis Simulator | dibangun (lihat 054) |
| 054 | Catatan implementasi Simulasi Krisis Produksi | — |
| 055 | Gerbang masuk CodeShark | — |
| 056 | PRD Tahap 1 lanjutan | rencana |
| 057 | Requirement Tahap 1 lanjutan | rencana |
| 058 | Design Tahap 1 lanjutan | rencana |
| 059 | Tasklist Tahap 1 lanjutan | belum dikerjakan |
| 060 | Naskah modul Tahap 3 – Aksi | rencana; koreksi di §12 |
| 061 | PRD Tahap 3 | rencana |
| 062 | Requirement Tahap 3 (55 butir) | rencana |
| 063 | Design Tahap 3 | rencana |
| 064 | Tasklist Tahap 3 (36 tugas) | belum dikerjakan |
| 065 | Catatan implementasi Blind Live-Coding Challenge | — |
| 066 | Dokumen ini | — |

README mendapat dua bagian: "Simulasi Krisis Produksi" dan "Blind Live-Coding
Challenge".

---

## 5. Hasil uji

Angka di bawah adalah hasil saat tiap pekerjaan selesai. Tidak dijalankan ulang
untuk dokumen ini.

| Pemeriksaan | Simulasi Krisis + gerbang masuk | Blind Challenge (di `e77ba04`) |
|---|---|---|
| `npx tsc --noEmit` | bersih | bersih |
| `npm run build` | berhasil | berhasil |
| `npm run test:trap` | 27 dari 27 | 27 dari 27 |
| `npm run test:blind` | — | 50 dari 50 |
| Uji lain | `test:local-mode`, `test:profile`, `test:boot-loading`: 6, 13, 3 lulus | seluruh `tests/*.test.mjs`: 187 dari 188; satu yang gagal juga gagal sebelum perubahan |
| Chromium headless, server dev | 42 dari 42 pada pengecekan terakhir (`79a66c6`); skenarionya di 054 dan 055 | 100 dari 100 (A 57, B–H 43); skenarionya di 065 §6 |
| Chromium headless, build produksi | tidak dijalankan | 3 dari 3 (uji asap) |
| Netlify deploy preview pada PR | lulus | lulus |

Dokumen 056–064 (PR #17) tidak mengubah kode; setelahnya `tsc` bersih dan
`test:trap` 27 dari 27.

---

## 6. Yang masih terbuka

### 6.1 Cacat yang diketahui dan belum diperbaiki

- **V-09 (P0), Simulasi Krisis:** kode murid bisa memalsukan putusan sandbox
  ("produksi pulih" tanpa memperbaiki apa pun). Sudah direproduksi di browser
  headless. Rancangan perbaikan: 058 §8.1; tugas: 059 T2.1. **Belum dikerjakan.**
- **Blind Challenge bisa dilewati dalam beberapa detik** dengan menekan "Saya
  selesai" dua kali. Rapornya tercatat apa adanya dan menjadi rapor pertama yang
  tidak bisa diganti. Ini mengikuti 052; belum ada keputusan apakah perlu dikunci.

### 6.2 Belum dibangun

- **Tahap 3 – Aksi** (Cetak Motorik, Perancah Memudar, Hiu Boss, Ritual Pra-Lab):
  hanya dokumen 060–064. Keputusan **K1–K12 di 061 §10 belum dijawab**; tiga tugas
  bisa dimulai tanpa keputusan itu: W7.2, W1.1, W1.2.
- **Tahap 1 lanjutan** (056–059): butir terbuka O1–O7 belum dijawab.
- **Tahap 2** tidak didefinisikan di dokumen mana pun.
- **Untuk dosen:** rekap per kelas, ekspor CSV, dan sakelar di panel admin belum ada
  untuk kedua modul.

### 6.3 Belum diuji

- Murid sungguhan, untuk kedua modul. Belum ada bukti bahwa modul ini memicu
  refleksi seperti yang dimaksud.
- Firefox dan Safari; tata letak keyboard selain QWERTY-US; pembaca layar.
- Sinkron cloud dengan irisan `aiTrap` dan `blind`; login akun.
- Situs produksi setelah `main` berubah. Yang diperiksa hanya deploy preview PR.

### 6.4 Angka yang masih sementara

- Semua ambang rapor Blind Challenge (1,5 detik, 4×, 5 detik, 3 error, 5 jeda,
  40%, 15%, 40 karakter) belum dikalibrasi dengan data kelas.
- Angka pembanding AI di `src/data/aiBenchmark.ts` adalah perkiraan kasar, bukan
  tarif resmi.

### 6.5 Dampak yang perlu diketahui sebelum dipakai di kelas

- Pengguna Mahasiswa/Umum yang **sudah punya progres** terkena kedua modul satu kali.
- Pengguna baru Mahasiswa/Umum menjalani dua sesi 3 menit ditambah dua layar hasil
  sebelum latihan pertama.
- Browser tidak bisa mencegah murid bertanya ke AI lewat perangkat kedua. Kedua
  modul adalah alat penyadaran, bukan ujian terawasi.

---

## 7. Cara memeriksa dan mengubah

```bash
npm ci --no-audit --no-fund
npx tsc --noEmit
npm run test:trap     # Simulasi Krisis Produksi
npm run test:blind    # Blind Live-Coding Challenge
npm run build
npm run dev           # port 3000; buka /codingshark/ atau /codingtower/
```

| Ingin | Ubah |
|---|---|
| Mematikan gerbang Blind Challenge | `BLIND_GATE_ENABLED = false` di `src/data/blindChallenges.ts` |
| Mengubah siapa yang terkena | `TRAP_REQUIRED_AGES` / `TRAP_OPTIONAL_AGES` di `src/data/aiTrapScenarios.ts`; `BLIND_REQUIRED_AGES` / `BLIND_OPTIONAL_AGES` di `src/data/blindChallenges.ts` |
| Mengubah ambang rapor | konstanta di awal `src/lib/blindMetrics.ts` |
| Menambah skenario krisis | objek `TrapScenario` di `src/data/aiTrapScenarios.ts`, lalu `npm run test:trap` |
| Menambah soal blind | objek `BlindBrief` di `src/data/blindChallenges.ts`, lalu `npm run test:blind` |

Untuk mencoba sebagai murid: buat profil kelompok Mahasiswa/Umum di perangkat
dengan keyboard fisik, buka `/codingshark/`, lalu tekan tombol latihan apa pun.
