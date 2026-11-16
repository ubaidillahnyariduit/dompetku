# FinTrack Pro - Aplikasi Catatan Keuangan Pribadi & Scan Struk Belanja

FinTrack Pro adalah aplikasi web modern pencatat keuangan pribadi (arus kas masuk & keluar) dengan nuansa **Dark Charcoal Elegance** beraksen kontras Pink Magenta & Cyan Teal (mengadopsi desain visual dashboard analitik profesional).

Aplikasi ini dapat di-deploy 100% gratis ke **GitHub Pages**, terhubung langsung dengan **Google Sheets** (sebagai database transaksi) dan **Google Drive** (sebagai tempat penyimpanan arsip foto struk belanjaan via pemindai OCR kamera HP).

---

## 🌟 Fitur Utama

1. **Dashboard Visual Interaktif (Chart.js):**
   - 4 Kartu Metrik KPI: Total Pemasukan, Total Pengeluaran, Saldo Bersih, dan Tingkat Tabungan (Savings Rate %).
   - Filter Periode Fleksibel: Harian, Mingguan, Bulanan (Pill Button Jan–Des), dan Tahunan.
   - Double Bar Chart arus kas bulanan/mingguan.
   - Donut Chart komposisi pengeluaran per kategori.
   - Donut Chart metode pembayaran (Cash, Bank BCA, GoPay, OVO).
   - Horizontal Bar Chart 5 pengeluaran terbesar.
2. **Scan Struk Belanja & Catatan (Kamera HP + OCR):**
   - Ambil foto langsung melalui kamera HP (`capture="camera"`).
   - Membaca nominal total dan tanggal transaksi secara otomatis menggunakan Tesseract OCR.
   - Foto bukti struk otomatis tersimpan rapi di Google Drive.
3. **Multi-Dompet & Transfer Saldo:**
   - Memantau saldo terpisah untuk Bank, E-Wallet, dan Kas Tunai.
   - Fitur transfer antar-dompet (misal: Top-Up GoPay dari BCA).
4. **Transaksi Rutin (Bulanan):**
   - Daftar transaksi berkala seperti Gaji Bulanan, Tagihan Listrik/WiFi, Sewa Kos/Rumah dengan tombol eksekusi 1-klik.
5. **Keamanan Akses PIN:**
   - Dilindungi kunci PIN 4 digit saat aplikasi dibuka (Default: `1234`, dapat diganti di menu Pengaturan).
6. **Ekspor & Cetak Laporan:**
   - Download data riwayat ke format file Excel (.csv / .xlsx).
   - Mode Cetak / Simpan ke PDF.
   - Fitur Backup instan ke Google Drive.
7. **100% Responsif & Mobile-Friendly:**
   - Dilengkapi Mobile Thumb Bar di bagian bawah layar HP dan tombol aksi cepat (+).

---

## 📁 Struktur Berkas

- `index.html`: Antarmuka frontend Single Page Application (Tailwind CSS, Chart.js, Tesseract.js). Berkas ini yang di-upload ke GitHub Pages.
- `code.gs`: Script backend Google Apps Script (Controller API RESTful untuk CRUD transaksi, upload foto ke Drive, dan backup).
- `setup.gs`: Skrip inisialisasi database idempoten (Safe Migration) untuk membuat 5 sheet utama: `Transaksi`, `Dompet`, `Kategori`, `TransaksiRutin`, dan `Pengaturan`.
- `prd.md`: Dokumen arsitektur sistem dan spesifikasi kebutuhan produk (PRD 2-Zona).
- `ZettBOT.md`: Berkas sakelar lisensi dan pedoman rekayasa sistem ZettBOT by Zettbos.

---

## 🚀 Panduan Pemasangan & Deployment (Step-by-Step)

### LANGKAH 1: Persiapan Google Sheets & Google Apps Script
1. Buka [Google Sheets](https://sheets.new) di browser Anda dan buat spreadsheet baru (misal beri judul: `Database FinTrack Pro`).
2. Pada menu atas, klik **Extensions (Ekstensi)** > **Apps Script**.
3. Di dalam editor Apps Script:
   - Buat file script baru bernama `setup.gs`, lalu salin seluruh isi berkas [setup.gs](setup.gs) ke dalamnya.
   - Pada file `Code.gs` (atau buat file `code.gs`), salin seluruh isi berkas [code.gs](code.gs) ke dalamnya.
4. Pada dropdown fungsi di bagian atas editor Apps Script, pilih fungsi `initDatabase`, lalu klik tombol **Run (Jalankan)**.
   - Berikan izin akses (*Grant Permissions*) saat Google meminta konfirmasi.
   - Buka kembali spreadsheet Anda: 5 tab sheet (`Transaksi`, `Dompet`, `Kategori`, `TransaksiRutin`, `Pengaturan`) sudah otomatis terbuat dengan rapi dan terisi data contoh awal!

---

### LANGKAH 2: Deploy Web App Google Apps Script
1. Di halaman editor Apps Script, klik tombol biru **Deploy (Terapkan)** di pojok kanan atas > pilih **New deployment (Penerapan baru)**.
2. Klik ikon gerigi (Select type) > pilih **Web app**.
3. Atur konfigurasi berikut:
   - **Description:** `FinTrack Pro API v1`
   - **Execute as:** `Me (email Anda)`
   - **Who has access:** `Anyone (Siapa saja)` *(Penting agar aplikasi web di GitHub Pages dapat membaca/menyimpan data)*.
4. Klik **Deploy**. Salin **Web app URL** yang dihasilkan (format: `https://script.google.com/macros/s/.../exec`).

---

### LANGKAH 3: Deploy ke GitHub Pages
1. Buat repositori baru di [GitHub](https://github.com/new) (misal: `fintrack-pro`).
2. Unggah berkas `index.html` dan `README.md` ke dalam repositori tersebut.
3. Buka tab **Settings** di repositori GitHub Anda > pilih menu **Pages** di bilah kiri.
4. Pada bagian **Build and deployment**:
   - Source: pilih **Deploy from a branch**.
   - Branch: pilih **main** / root (`/`), lalu klik **Save**.
5. Tunggu sekitar 1–2 menit, GitHub akan memberikan link website Anda (contoh: `https://username.github.io/fintrack-pro/`).

---

### LANGKAH 4: Langsung Pakai Secara Online di Chrome (Sudah Terhubung Otomatis!)
1. Buka link GitHub Pages Anda (misal: `https://username.github.io/fintrack-pro/`) di browser Google Chrome (HP maupun PC).
2. Masukkan PIN awal: `1234`.
3. URL backend Google Apps Script Anda (`.../AKfycbyM8LZucxjFymD6wLGO6U82AbYHg0mFwTivPnmeF5U_1L2Js_vw_F4ElvR0Jg3hzuXs/exec`) **sudah tertanam secara otomatis di dalam `index.html`**.
4. Indikator status di pojok kiri atas langsung berwarna hijau: **🟢 Terhubung ke Google Sheets**.
5. Seluruh pencatatan kas, mutasi dompet, scan struk ke Google Drive, dan laporan analitik sudah 100% online dan tersinkronisasi secara real-time! 🎉

---

## 🔒 Catatan Keamanan
- Kunci PIN tersimpan di `localStorage` peramban dan tersinkronisasi dengan tab `Pengaturan` di Google Sheets.
- Pastikan tidak membagikan link Web App URL Anda kepada orang yang tidak berhak.
