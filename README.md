# DompetKu - Aplikasi Catatan Keuangan Pribadi & Scan Struk Belanja

DompetKu adalah aplikasi web modern pencatat keuangan pribadi (arus kas masuk & keluar) dengan nuansa **Clean Light Dashboard** beraksen kontras Pink Magenta & Cyan Teal (mengadopsi desain visual dashboard analitik profesional dengan latar belakang terang dan kartu putih bersih).

Aplikasi ini dapat di-deploy 100% gratis ke **GitHub Pages**, terhubung langsung dengan **Google Sheets** (sebagai database transaksi) dan **Google Drive** (sebagai tempat penyimpanan arsip foto struk belanjaan via pemindai OCR kamera HP).

---

## 🌟 Fitur Utama DompetKu

1. **Dashboard Visual Interaktif (Clean Light Theme):**
   - 4 Kartu Metrik KPI: Total Pemasukan, Total Pengeluaran, Saldo Bersih, dan Tingkat Tabungan (Savings Rate %).
   - Filter Periode Cepat: Harian, Mingguan, Bulanan (Pill Button Jan–Des), dan Tahunan.
   - Double Bar Chart arus kas bulanan/mingguan (Teal `#00b4d8` vs Pink `#ff3b69`).
   - Donut Chart komposisi pengeluaran per kategori.
   - Donut Chart metode pembayaran per rekening (**BRI, BJB 1, BJB 2, Cash**).
   - Horizontal Bar Chart 5 pengeluaran terbesar.
2. **Scan Struk Belanja & Catatan (Kamera HP + OCR):**
   - Ambil foto langsung melalui kamera HP (`capture="camera"`).
   - Membaca nominal total dan tanggal transaksi secara otomatis menggunakan Tesseract OCR.
   - Foto bukti struk otomatis tersimpan rapi di Google Drive.
3. **Multi-Rekening (BRI, BJB 1, BJB 2, Cash):**
   - Memantau saldo terpisah untuk masing-masing rekening dan kas tunai.
   - Fitur transfer antar-rekening (misal: Transfer dari BRI ke Cash).
4. **Kelola Jadwal Rutin Bulanan:**
   - Tambah, atur, dan hapus jadwal rutin bulanan (Gaji, Tagihan Listrik/WiFi, Sewa) langsung dari antarmuka aplikasi.
   - Tombol eksekusi 1-klik untuk langsung mencatat ke pembukuan.
5. **Keamanan Akses PIN:**
   - Dilindungi kunci PIN 4 digit saat aplikasi dibuka (Default: `1234`, dapat diganti di menu Pengaturan).
6. **Ekspor & Cetak Laporan:**
   - Download data riwayat ke format file Excel (.csv / .xlsx).
   - Mode Cetak / Simpan ke PDF.
   - Fitur Backup instan ke Google Drive.
7. **Bebas Autofill:**
   - Kolom pencarian dilindungi atribut anti-autofill sehingga tidak akan otomatis terisi nama profil Google Chrome.

---

## 📁 Struktur Berkas

- `index.html`: Antarmuka frontend Single Page Application (Tailwind CSS, Chart.js, Tesseract.js). Berkas ini yang di-upload ke GitHub Pages.
- `code.gs`: Script backend Google Apps Script (Controller API RESTful untuk CRUD transaksi, upload foto ke Drive, kelola jadwal rutin, dan backup).
- `setup.gs`: Skrip inisialisasi database idempoten (Safe Migration) untuk membuat 5 sheet utama: `Transaksi`, `Dompet`, `Kategori`, `TransaksiRutin`, dan `Pengaturan` tanpa karakter underscore.
- `prd.md`: Dokumen arsitektur sistem dan spesifikasi kebutuhan produk (PRD 2-Zona).
- `ZettBOT.md`: Berkas sakelar lisensi dan pedoman rekayasa sistem ZettBOT by Zettbos.

---

## 🚀 Panduan Pemasangan & Deployment ke GitHub Pages

### 1. Perbarui Google Apps Script (Jika Belum)
Salin berkas [setup.gs](setup.gs) dan [code.gs](code.gs) ke editor Apps Script Google Spreadsheet Anda, lalu pastikan fungsi `initDatabase()` telah dijalankan.

### 2. Unggah ke GitHub Pages
1. Unggah berkas `index.html` ke repositori GitHub Anda.
2. Buka **Settings > Pages > Branch main** lalu klik **Save**.
3. Buka link GitHub Pages Anda di Google Chrome HP atau Laptop.
4. Masukkan PIN awal: `1234`.
5. Status otomatis **🟢 Terhubung ke Google Sheets** karena URL API Anda sudah tertanam langsung di dalamnya!

Selamat mencatat keuangan Anda dengan **DompetKu**! 🎉
