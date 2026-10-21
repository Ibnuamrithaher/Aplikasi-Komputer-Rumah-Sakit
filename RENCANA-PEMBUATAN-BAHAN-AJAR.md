# RENCANA PEMBUATAN BAHAN AJAR INTERAKTIF — KOMPUTER RUMAH SAKIT

Dokumen ini adalah instruksi kerja untuk model AI (Haiku 4.5). Baca seluruhnya sebelum mengerjakan. Kerjakan SATU pertemuan per sesi. Jangan melompat.

## 0. Tujuan

Membuat 14 file HTML interaktif (satu file per pertemuan, CSS dan JS di dalam file yang sama) untuk mata kuliah Komputer Rumah Sakit, Prodi Administrasi RS, Semester 1. Dosen: Ibnu Amri Thaher. Setiap file harus mengisi 90 menit tatap muka dan bisa dioperasikan langsung oleh mahasiswa.

Bahasa konten: Bahasa Indonesia, baku, ramah mahasiswa. Semua data pasien/pegawai WAJIB fiktif (nama karangan, NIK/No. RM palsu). Jangan pernah memakai data pasien nyata.

## 1. Daftar file keluaran

Nama file mengikuti nomor minggu pada RPS. Minggu 8 (UTS) dan 16 (UAS) tidak dibuat.

| File | Minggu | Topik |
| --- | --- | --- |
| pertemuan-01.html | 1 | Pengenalan & kontrak kuliah |
| pertemuan-02.html | 2 | Perangkat keras (hardware) medis & perkantoran |
| pertemuan-03.html | 3 | Perangkat lunak (software) & pemetaan aplikasi |
| pertemuan-04.html | 4 | MS Word untuk administrasi RS |
| pertemuan-05.html | 5 | Word lanjutan & Mail Merge |
| pertemuan-06.html | 6 | Excel dasar |
| pertemuan-07.html | 7 | Excel lanjutan (grafik & statistik) |
| pertemuan-09.html | 9 | PowerPoint dasar |
| pertemuan-10.html | 10 | PowerPoint lanjutan (data storytelling, dasbor) |
| pertemuan-11.html | 11 | Integrasi Office bagian 1 (OLE, Word-Excel) |
| pertemuan-12.html | 12 | Integrasi Office bagian 2 (Excel-PowerPoint) |
| pertemuan-13.html | 13 | Email resmi RS |
| pertemuan-14.html | 14 | Cloud storage & kolaborasi dokumen |
| pertemuan-15.html | 15 | Mini project terpadu |

Tambahan: `index.html` (menu daftar 14 pertemuan, dibuat terakhir) dan `_template.html` (lihat Fase 0).

## 2. Aturan teknis WAJIB

1. Satu file = HTML + `<style>` + `<script>` inline. Tidak ada file CSS/JS terpisah.
2. Tanpa library eksternal, tanpa CDN, tanpa Google Fonts, tanpa gambar eksternal. Laboratorium bisa offline. Gunakan font sistem (`system-ui, "Segoe UI", sans-serif`), ikon berupa emoji atau SVG inline.
3. JavaScript vanilla saja. Dilarang `eval()` dan `innerHTML` dengan input mahasiswa mentah (pakai `textContent` atau escape).
4. Grafik digambar manual dengan SVG atau `<canvas>`.
5. Responsif (layar proyektor 1280x720 dan laptop 1366x768 harus nyaman). Teks isi minimal 18px agar terbaca dari belakang kelas.
6. Aksesibel: kontras warna WCAG AA, tombol bisa dipakai keyboard, `lang="id"`.
7. Progres mahasiswa disimpan di `localStorage` dengan kunci `krs-p{NN}-...` dan dibungkus `try/catch` (halaman tetap jalan bila storage diblokir).
8. Ada tombol "Cetak / Simpan PDF" (`window.print()`) dengan CSS `@media print` yang rapi.
9. Satu file target 900–1800 baris. Jika file lebih panjang dari yang bisa ditulis sekali jalan, tulis bertahap (lihat bagian 6).
10. Jangan menambah fitur di luar spesifikasi pertemuan. Jangan mengubah isi RPS.

## 3. Sistem desain (dipakai sama di semua file)

Tema: bersih, klinis, hangat. Bukan tampilan generik/template.

Token warna di `:root`:
- `--bg: #f6faf9`, `--surface: #ffffff`, `--ink: #12303a`, `--muted: #5b7480`
- `--primary: #0b7285` (teal RS), `--primary-soft: #d3f0f4`
- `--accent: #e8590c` (oranye untuk aksi/penting), `--ok: #2b8a3e`, `--warn: #e67700`, `--bad: #c92a2a`
- Mode gelap lewat `@media (prefers-color-scheme: dark)` dengan token yang sama dibalik.

Tata letak: header tetap berisi judul + penghitung waktu; sidebar kiri berisi agenda 90 menit (klik untuk lompat, bagian yang selesai diberi centang); konten utama berupa kartu per segmen. Sudut membulat 12px, bayangan tipis, jarak lega.

## 4. Struktur baku 90 menit (semua pertemuan)

Setiap file berisi segmen berikut, masing-masing dengan lencana durasi:

| Menit | Segmen | Isi |
| --- | --- | --- |
| 0–5 | Pembuka | Tujuan pertemuan, kaitan CPMK, skenario RS singkat (cerita pemantik) |
| 5–15 | Pre-test | 5 soal pilihan ganda, skor langsung tampil, jawaban tidak mengunci |
| 15–55 | Inti teori interaktif | 3–4 blok konsep, tiap blok 8–12 menit, masing-masing PUNYA widget interaktif (lihat spesifikasi per pertemuan) |
| 55–80 | Praktik / simulasi / studi kasus | Aktivitas utama yang dikerjakan mahasiswa di halaman, dengan umpan balik otomatis |
| 80–87 | Post-test | 5 soal (berbeda dari pre-test), tampilkan skor pre vs post |
| 87–90 | Penutup | Ringkasan 5 poin, refleksi 1 pertanyaan (kotak teks), tugas/tindak lanjut |

Catatan: RPS minggu 1–3 dan 15 hanya 45 menit teori. Karena target 90 menit, segmen 55–80 diisi diskusi + simulasi berbasis halaman, bukan praktik di aplikasi Office.
Untuk minggu 4–7, 9–14: teori 45 menit (segmen 5–55 + pre-test) dan praktik 55 menit (55–80 simulasi di halaman + instruksi tugas praktik di Word/Excel/PPT sungguhan yang dikerjakan di lab). Pada segmen praktik, sediakan kartu "Tugas Lab" berisi langkah bernomor, data contoh yang bisa di-copy atau diunduh (lihat bagian 5), dan kriteria penilaian dari RPS.

## 5. Komponen interaktif yang boleh dipakai

Semua dibuat di Fase 0 pada `_template.html` lalu disalin ke tiap file. Haiku tidak perlu menulis ulang dari nol, cukup memakai dan mengisi data.

1. `quiz` — pilihan ganda, umpan balik benar/salah + penjelasan, skor.
2. `flashcard` — kartu bolak-balik.
3. `dragmatch` — seret-pasangkan (pakai klik-pilih sebagai alternatif keyboard).
4. `sortlist` — urutkan langkah (tombol naik/turun).
5. `accordion` dan `tabs`.
6. `hotspot` — gambar SVG dengan titik klik yang menampilkan penjelasan.
7. `checklist` — dengan progres bar.
8. `slider-sim` — slider/input yang mengubah pratinjau langsung.
9. `minisheet` — mini spreadsheet (kolom A–H, baris 1–15), mendukung `+ - * /`, referensi sel, `SUM`, `AVERAGE`, `COUNT`, `MAX`, `MIN`. Parser ditulis manual (tokenizer + rekursif), TANPA `eval`/`Function`.
10. `chart` — bar, line, pie dari array angka (SVG).
11. `downloadCSV` — tombol mengunduh data contoh sebagai `.csv` lewat `Blob`.
12. `timer` — hitung mundur per segmen, tombol mulai/jeda.
13. `reflect` — kotak teks refleksi, tersimpan di localStorage.

## 6. Cara kerja Haiku (alur eksekusi)

### Fase 0 — Template (dikerjakan DULU, idealnya oleh model lebih kuat / ditinjau dosen)
Buat `_template.html`: kerangka halaman (header, sidebar agenda, segmen, tema, cetak) + 13 komponen di bagian 5, lengkap dengan contoh pemakaian dan komentar singkat. Uji di browser sampai semua komponen jalan. Dosen menyetujui tampilan sebelum Fase 1.

### Fase 1 — Per pertemuan (ulangi 14 kali, satu sesi per pertemuan)
Untuk pertemuan N:
1. Baca bagian 0–5 dokumen ini dan spesifikasi pertemuan N (bagian 7).
2. Salin `_template.html` menjadi `pertemuan-NN.html`.
3. Isi dalam 3 langkah terpisah (edit bertahap, jangan tulis ulang seluruh file):
   - Langkah A: metadata (judul, CPMK, tujuan), segmen pembuka, pre-test, post-test, penutup.
   - Langkah B: segmen inti teori + widget.
   - Langkah C: segmen praktik/simulasi + kartu Tugas Lab + data contoh.
4. Hapus komponen template yang tidak dipakai agar file ringan.
5. Jalankan checklist QA (bagian 8). Perbaiki sampai semua lolos.
6. Laporkan singkat: file selesai, total baris, menit per segmen, hal yang belum beres.

### Fase 2 — Penutup
Buat `index.html` (kartu 14 pertemuan, status progres dari localStorage). Tinjau konsistensi tampilan antar-file.

## 7. Spesifikasi per pertemuan

Setiap spesifikasi memuat: segmen inti (widget) dan segmen praktik. Pre/post-test dibuat dari materi pokok bahasan RPS.

### P01 — Pengenalan & Kontrak Kuliah
- Pembuka: cerita "hari pertama jadi staf administrasi RS tanpa bisa komputer".
- Inti 1: Peta 16 minggu (timeline interaktif, klik minggu tampil topik, UTS minggu 8 dan UAS minggu 16 ditandai).
- Inti 2: Kalkulator nilai: Tugas 40%, UTS 30%, UAS 30%; mahasiswa memasukkan nilai simulasi dan melihat nilai akhir.
- Inti 3: Aturan main (accordion): tata tertib, keterlambatan, toleransi absensi (dosen mengisi angka di variabel konfigurasi di atas file, beri nilai bawaan yang jelas bertanda "ATUR OLEH DOSEN").
- Inti 4: Peran komputer di RS (hotspot alur pasien: pendaftaran, poli, farmasi, kasir, rekam medis).
- Praktik: Kontrak belajar digital (centang kesepakatan, isi nama, tampil pratinjau "berita acara" yang bisa dicetak) + Peta ekspektasi (mahasiswa mengetik 3 harapan, tersimpan) + diskusi.

### P02 — Perangkat Keras
- Inti 1: Komponen komputer (hotspot SVG: CPU, RAM, storage, monitor, keyboard, mouse; klasifikasi Input/Process/Output/Storage dengan `dragmatch`).
- Inti 2: Satuan penyimpanan (konverter KB-MB-GB-TB; berapa foto/rontgen muat di 1 TB).
- Inti 3: Hardware khusus RS (flashcard: barcode scanner pasien, printer gelang, scanner dokumen RM, kartu pembaca, UPS).
- Inti 4: Infrastruktur jaringan (diagram server-LAN-WiFi medis, tombol "putuskan koneksi" memperlihatkan dampak ke unit mana).
- Praktik: Studi kasus "Rancang loket pendaftaran RS baru": pilih perangkat dari daftar berharga fiktif dengan batas anggaran, skor otomatis berdasarkan kelengkapan fungsi vs anggaran.

### P03 — Perangkat Lunak & Pemetaan Aplikasi
- Inti 1: OS vs aplikasi vs utilitas (`dragmatch` 12 contoh software).
- Inti 2: Simulasi kompresi ZIP (pilih file, slider tingkat kompresi, tampil ukuran sebelum/sesudah dan rasio; jelaskan kapan perlu ZIP untuk email).
- Inti 3: PDF reader/editor (tabs: baca, gabung, pisah, ubah ke PDF; penjelasan kapan pakai masing-masing; simulasi gabung dua dokumen dengan urutan).
- Inti 4: Kapan Word, Excel, PowerPoint? Matriks fungsi.
- Praktik: Game "Pilih Aplikasi": 15 kasus dokumen RS (surat, rekap kunjungan, laporan rapat, billing, dll.), mahasiswa memilih Word/Excel/PPT, skor dan penjelasan per kasus.

### P04 — MS Word Administrasi RS
- Inti 1: Anatomi surat dinas RS (surat contoh, arahkan kursor ke bagian: kop, nomor, lampiran, perihal, alamat, salam, isi, penutup, tanda tangan, tembusan).
- Inti 2: Pemformat langsung: halaman A4 pratinjau + kontrol margin, jenis font, ukuran, line spacing; mahasiswa melihat dampaknya; tantangan "buat sesuai standar" (Times New Roman/Arial 12, margin 3-2.5-2.5-2.5 cm, spasi 1,5; ATUR OLEH DOSEN di konfigurasi).
- Inti 3: Pembuat kop surat (form nama RS, alamat, telepon, email; pratinjau kop + garis).
- Praktik: "Temukan 8 kesalahan format" pada surat contoh (klik bagian yang salah, skor), lalu Tugas Lab: ketik surat rujukan pasien fiktif di Word dengan kriteria RPS (kerapian format, struktur surat). Sediakan teks surat contoh yang bisa disalin.

### P05 — Word Lanjutan & Mail Merge
- Inti 1: Tabel di Word (konsep sisip, gabung sel, header baris; simulasi pembuat tabel baris x kolom).
- Inti 2: Konsep Mail Merge (diagram animasi: master surat + sumber data = banyak surat).
- Inti 3: `sortlist` 6 langkah Mail Merge (Mailings > Start Mail Merge > Select Recipients > Insert Merge Field > Preview > Finish & Merge).
- Praktik: Simulator Mail Merge: tabel data pasien kontrol fiktif (10 baris, bisa diedit), master surat dengan kolom bertanda «Nama», «Poli», «Tanggal», tombol pratinjau panah kiri/kanan antar penerima, tombol "Gabungkan semua" memperlihatkan semua surat. Lalu Tugas Lab: Mail Merge undangan kontrol di Word dengan CSV yang bisa diunduh dari halaman.

### P06 — Excel Dasar
- Inti 1: Anatomi lembar kerja (hotspot: cell, row, column, nama sel, formula bar; latihan klik sel lalu sebut alamatnya).
- Inti 2: Tipe data (teks, angka, tanggal, persen) dengan `dragmatch` dan contoh dampak salah tipe.
- Inti 3: Operator + - * / dan urutan operasi dalam `minisheet`.
- Inti 4: SUM, AVERAGE, COUNT dalam `minisheet` dengan data stok obat fiktif.
- Praktik: 5 tantangan bertingkat di `minisheet` (hitung total, rata-rata, jumlah data, total biaya = harga x jumlah, kombinasi), pengecekan jawaban otomatis. Lalu Tugas Lab di Excel: dataset kunjungan poli yang diunduh dari halaman.

### P07 — Excel Lanjutan
- Inti 1: MAX dan MIN dalam `minisheet` (kunjungan tertinggi/terendah per bulan).
- Inti 2: Memilih jenis grafik (Bar untuk perbandingan, Line untuk tren, Pie untuk proporsi) dengan `quiz` kasus.
- Inti 3: Pembuat grafik: tabel data editable memperbarui bar/line/pie langsung.
- Praktik: Studi kasus kunjungan 12 bulan: hitung MAX/MIN/AVERAGE, pilih grafik yang tepat, tulis satu kalimat interpretasi. Tugas Lab: laporan ringkasan biaya operasional dengan grafik di Excel.

### P09 — PowerPoint Dasar
- Inti 1: Prinsip desain slide formal (geser "sebelum/sesudah" slide jelek vs baik).
- Inti 2: Pemeriksa kontras warna (pilih warna teks/latar, hitung rasio kontras, beri label Lulus/Gagal AA).
- Inti 3: Aturan teks (maksimal poin, ukuran font minimum, 1 pesan per slide; slider ukuran font dengan pratinjau slide).
- Inti 4: Penyisipan tabel/gambar dan transisi/animasi fungsional (quiz "animasi mana yang membantu").
- Praktik: Editor slide mini: pilih layout, isi judul dan poin, pratinjau 16:9, penilai otomatis (jumlah kata, kontras). Tugas Lab: slide profil/laporan kinerja RS di PowerPoint.

### P10 — PowerPoint Lanjutan
- Inti 1: Data storytelling (tombol "angka mentah" ↔ "cerita": data BOR, LOS, TOI, BTO, NDR, GDR yang sama ditampilkan dua cara).
- Inti 2: Kalkulator indikator RS (BOR, LOS, TOI, BTO dengan rumus dan data fiktif; tampil rumus + hasil).
- Inti 3: Interaktivitas (hyperlink, action button, slide zoom) lewat demo presentasi mini di halaman dengan menu navigasi non-linear.
- Inti 4: Record Slide Show dan Rehearse Timings (simulasi timer latihan).
- Praktik: Dasbor indikator mutu: mahasiswa memilih 4 indikator dan tipe visual, melihat pratinjau dasbor. Tugas Lab: dasbor presentasi interaktif capaian indikator mutu RS di PowerPoint.

### P11 — Integrasi Office Bagian 1 (OLE)
- Inti 1: Konsep OLE (analogi "salin" vs "tautan" vs "tanam").
- Inti 2: Simulator Link vs Embed vs Paste: panel kiri tabel Excel editable, panel kanan dokumen Word; ubah data lalu lihat mana yang ikut berubah (Link ya, Embed tidak, Paste biasa tidak).
- Inti 3: `sortlist` langkah Paste Special → Paste Link.
- Praktik: Permainan pemecahan masalah "link putus" (file dipindah/diganti nama, pilih solusi benar). Tugas Lab: laporan bulanan RS di Word dengan tabel dan grafik tertaut ke Excel; uji dengan mengubah data.

### P12 — Integrasi Office Bagian 2
- Inti 1: Menyisipkan grafik Excel ke slide (dua cara: embed vs link) dengan simulator mirip P11 tapi bergrafik.
- Inti 2: Strategi penyajian data kuantitatif di rapat (kuis: pesan apa → grafik apa).
- Inti 3: Simulasi pembaruan data saat rapat (ubah angka, grafik di slide ikut berubah, tombol "Update Link").
- Praktik: Skenario rapat kerja RS: mahasiswa menyusun 3 slide dengan grafik pilihan, penilai otomatis, lalu Tugas Lab di PowerPoint-Excel nyata.

### P13 — Email Resmi RS
- Inti 1: Etika dan format email dinas (anatomi email: subjek, salam, isi, penutup, tanda tangan).
- Inti 2: To / CC / BCC (`dragmatch` skenario: siapa di kolom mana; peringatan kerahasiaan data pasien).
- Inti 3: Subjek efektif (quiz perbaiki subjek buruk; pencarian kotak masuk simulasi).
- Praktik: Penyusun email simulasi: form To/CC/BCC/Subjek/Isi/Lampiran, tombol Kirim memicu penilai otomatis (cek format, subjek, salam, lampiran disebut dalam isi, tidak ada data pasien terbuka). Tugas Lab: kirim surat rujukan resmi dari akun email simulasi.

### P14 — Cloud & Kolaborasi
- Inti 1: Cloud storage (Google Drive/OneDrive: apa, kelebihan, risiko).
- Inti 2: Hak akses (Viewer/Commenter/Editor) dengan simulator berbagi: tambah orang, pilih peran, atur "siapa yang punya tautan"; tampil siapa bisa apa.
- Inti 3: Struktur folder dan penamaan berkas (pembuat pohon folder; aturan penamaan).
- Inti 4: Kolaborasi real-time dan riwayat versi (simulasi dua pengguna mengedit teks, tombol pulihkan versi).
- Praktik: Kasus keamanan (10 skenario "aman atau berisiko?") + Tugas Lab: folder bersama kelompok, dokumen rekam operasional, tautan hanya internal.

### P15 — Mini Project Terpadu
- Inti 1: Pengarahan proyek (studi kasus Laporan Akhir Tahun Administrasi RS; peta tiga dokumen Word, Excel, PPT).
- Inti 2: Review kendala umum Office (accordion FAQ dari P4–P14).
- Inti 3: Kuis komprehensif 10 soal lintas pertemuan.
- Praktik: Perencana proyek (pembagian peran kelompok, linimasa), `checklist` kelengkapan deliverable, kalkulator rubrik penilaian diri (kriteria dari RPS minggu 15–16), data skenario unduhan CSV. Catatan: waktu kerja terbimbing dilakukan di lab.

## 8. Checklist QA (wajib lulus sebelum melapor selesai)

- [ ] File terbuka di browser tanpa error di console.
- [ ] Tidak ada URL eksternal (`http://`, `https://`) kecuali teks referensi biasa.
- [ ] Total durasi segmen = 90 menit; tiap segmen punya lencana waktu.
- [ ] Ada pre-test dan post-test yang berbeda, skor tampil.
- [ ] Setiap blok inti punya minimal 1 widget interaktif yang berfungsi (klik semua).
- [ ] Semua tombol bisa dipakai keyboard (Tab/Enter).
- [ ] Reload halaman: progres dari localStorage kembali; bila storage diblokir, halaman tetap jalan.
- [ ] Cetak ke PDF rapi (sidebar disembunyikan, tidak terpotong).
- [ ] Semua data pasien/pegawai fiktif.
- [ ] Teks isi minimal 18px, kontras terbaca.
- [ ] Kriteria/indikator penilaian RPS pertemuan tersebut muncul pada kartu Tugas Lab.
- [ ] `minisheet` (P06, P07): semua formula di bagian 5 menghasilkan angka benar; input tidak valid menampilkan `#ERROR`, tidak membuat halaman crash.

## 9. Hal yang JANGAN dilakukan

- Jangan memakai framework (React, Vue, Bootstrap, Tailwind).
- Jangan membuat file selain yang tercantum.
- Jangan mengarang aturan kampus; yang belum diketahui diberi nilai bawaan bertanda "ATUR OLEH DOSEN".
- Jangan memperpanjang materi di luar RPS.
- Jika ragu, berhenti dan tulis pertanyaan pada laporan, jangan menebak.

## 10. Urutan kerja yang disarankan

1. Fase 0 (template) → persetujuan dosen.
2. P01 → tinjau bersama dosen (menjadi acuan kualitas).
3. P02–P07, P09–P15 berurutan, satu sesi satu file.
4. `index.html`.
5. Uji keliling semua file dengan checklist bagian 8.
