Nama : Alif Titan Maulana
NIM : 41257178

# Sistem Informasi Pengaduan Lingkungan Kampus (SIP-Kampus)

![Laravel](https://img.shields.io/badge/Laravel-9.52-red.svg)
![PHP](https://img.shields.io/badge/PHP-%3E%3D8.0-blue.svg)
![Bootstrap](https://img.shields.io/badge/Bootstrap-5.3-purple.svg)
![Database](https://img.shields.io/badge/Database-MySQL-orange.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)

**SIP-Kampus** adalah portal web layanan pengaduan dan whistleblowing terpadu di lingkungan perguruan tinggi. Sistem ini dibangun menggunakan arsitektur **Laravel MVC** dengan antarmuka berbahasa Indonesia yang responsif, modern, dan aman.

Sistem dirancang untuk menerima, memverifikasi, mendisposisikan, serta menindaklanjuti laporan dari:
- **Mahasiswa** (Sarjana, Vokasi, Pascasarjana)
- **Dosen** (Tenaga Pengajar Tetap & Tidak Tetap)
- **Tenaga Kependidikan (Tendik)** (Staf Administrasi, Laboran, Teknisi)
- **Alumni**
- **Masyarakat Umum & Mitra Kampus**

---

## Cakupan 7 Kategori Pengaduan

Sesuai Product Requirements Document (PRD), laporan diklasifikasikan ke dalam 7 kategori utama dan didisposisikan ke unit kerja berwenang:

1. **Kekerasan & Pelanggaran Etika** &rarr; Disposisi: *Satgas PPKS & Komisi Etik*
2. **Akademik & Pelayanan** &rarr; Disposisi: *Biro Administrasi Akademik & Kemahasiswaan (BAAK)*
3. **Integritas & Keuangan** &rarr; Disposisi: *Satuan Pengawas Internal (SPI)*
4. **Hukum & Tata Kelola** &rarr; Disposisi: *Bagian Hukum & Tata Kelola*
5. **Sarana & Prasarana** &rarr; Disposisi: *Biro Sarana, Prasarana & Logistik*
6. **Keamanan Kampus** &rarr; Disposisi: *Satuan Pengamanan (Satpam 24 Jam)*
7. **Aspirasi & Layanan Umum** &rarr; Disposisi: *Humas & Layanan Terpadu*

---

## Arsitektur & Teknologi

- **Backend:** PHP 8.0+ dengan Laravel Framework 9.x (MVC, Eloquent ORM, Request Validation, Service Layer).
- **Database:** MySQL / MariaDB (XAMPP).
- **Frontend:** Blade Template Engine, HTML5, Vanilla CSS3 (SIP Design System Tokens), JavaScript ES6, dan Bootstrap 5.3 + Bootstrap Icons.
- **Tipografi:** Google Fonts *Plus Jakarta Sans*.

---

## Struktur Direktori Proyek

```text
Sistem Pengaduan/
├── app/
│   ├── Http/
│   │   ├── Controllers/
│   │   │   ├── Controller.php
│   │   │   ├── HomeController.php          # Controller landing page publik
│   │   │   ├── PengaduanController.php     # Controller form, lacak, tiket, arsip
│   │   │   ├── DashboardController.php     # Controller panel operasional unit
│   │   │   ├── UnitController.php          # Controller direktori unit kerja
│   │   │   ├── NotifikasiController.php    # Controller notifikasi masuk
│   │   │   └── LaporanController.php       # Controller rekapitulasi statistik
│   │   └── Requests/
│   │       └── PengaduanRequest.php        # Form request validation bahasa Indonesia
│   ├── Models/
│   │   ├── User.php                        # Model akun admin/petugas
│   │   ├── UnitKerja.php                   # Model unit kerja penerima disposisi
│   │   ├── KategoriPengaduan.php           # Model 7 kategori pengaduan
│   │   ├── Pengaduan.php                   # Model utama entitas pengaduan
│   │   └── TanggapanPengaduan.php          # Model riwayat tracking/progres
│   └── Services/
│       └── PengaduanService.php            # Business logic tiket & transaksi DB
├── database/
│   ├── migrations/
│   │   ├── 2014_10_12_000000_create_users_table.php
│   │   ├── 2026_10_13_000001_create_unit_kerjas_table.php
│   │   ├── 2026_10_13_000002_create_kategori_pengaduans_table.php
│   │   ├── 2026_10_13_000003_create_pengaduans_table.php
│   │   └── 2026_10_13_000004_create_tanggapan_pengaduans_table.php
│   └── seeders/
│       ├── DatabaseSeeder.php
│       ├── UnitKerjaSeeder.php
│       ├── KategoriPengaduanSeeder.php
│       └── PengaduanSeeder.php
├── resources/
│   └── views/
│       ├── layouts/
│       │   ├── app.blade.php               # Layout publik
│       │   ├── dashboard.blade.php         # Layout dashboard internal
│       │   └── partials/                   # Navbar, footer, sidebar
│       ├── components/                     # Blade component (alert, badge, stat-card)
│       ├── public/                         # Halaman beranda (home.blade.php)
│       ├── pengaduan/                      # create.blade.php, lacak.blade.php, show.blade.php, index.blade.php
│       ├── dashboard/                      # index.blade.php
│       ├── unit/                           # index.blade.php
│       ├── notifikasi/                     # index.blade.php
│       ├── laporan/                        # index.blade.php
│       └── errors/                         # 404.blade.php, 500.blade.php
└── routes/
    └── web.php                             # Rute web terstruktur dengan nama rute
```

---

## Persyaratan Sistem

- PHP versi **>= 8.0.2** (ekstensi: `pdo_mysql`, `mbstring`, `openssl`, `tokenizer`, `xml`, `ctype`, `json`, `fileinfo`)
- MySQL Server versi **>= 5.7** atau MariaDB **>= 10.3** (tersedia di XAMPP)
- Composer versi **>= 2.0**
- Web browser modern (Chrome, Edge, Firefox, Safari)

---

## Panduan Instalasi & Konfigurasi

### 1. Masuk ke Direktori Proyek
Buka PowerShell atau Terminal di direktori proyek:
```bash
cd "C:\xampp\htdocs\Sistem Pengaduan"
```

### 2. Salin & Sesuaikan File Konfigurasi `.env`
Pastikan file `.env` telah disalin dari `.env.example`:
```bash
copy .env.example .env
```

Sesuaikan parameter koneksi database MySQL pada file `.env` (jangan menyimpan kredensial sensitif di source code repository):
```dotenv
APP_NAME="SIP-Kampus"
APP_ENV=local
APP_KEY=base64:ZjfnZrpahoVBSLGlY6gr4bUryiUw5CDz0q0xOadry/g=
APP_DEBUG=true
APP_URL=http://localhost:8000

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=db_pengaduan_kampus
DB_USERNAME=root
DB_PASSWORD=
```

### 3. Buat Database MySQL
Pastikan service MySQL di XAMPP Control Panel telah aktif (Running). Jika database `db_pengaduan_kampus` belum ada, buat melalui phpMyAdmin atau terminal MySQL:
```sql
CREATE DATABASE IF NOT EXISTS db_pengaduan_kampus CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

### 4. Generate Kunci Aplikasi (Jika Belum Ada)
```bash
php artisan key:generate
```
*(Catatan: Jika `php` belum masuk PATH Windows, gunakan path binary XAMPP: `C:\xampp\php\php.exe artisan key:generate`)*

### 5. Jalankan Migrasi & Seeding Data Awal
Eksekusi migrasi tabel dan seeding master data (unit kerja, 7 kategori, akun admin, serta tiket contoh):
```bash
php artisan migrate --seed
```
atau dengan PHP XAMPP:
```bash
C:\xampp\php\php.exe artisan migrate --seed
```

---

## Cara Menjalankan Aplikasi

### Metode 1: Menggunakan Laravel Development Server (Direkomendasikan)
Jalankan perintah berikut:
```bash
C:\xampp\php\php.exe artisan serve
```
Buka browser dan akses alamat:
```
http://localhost:8000
```

### Metode 2: Menggunakan Apache XAMPP
Pastikan Apache pada XAMPP Control Panel dalam status **Running**. Akses melalui URL:
```
http://localhost/Sistem Pengaduan/public
```

---

## Rute Utama Aplikasi

| Metode | URL | Nama Rute | Deskripsi |
| :--- | :--- | :--- | :--- |
| `GET` | `/` | `home` | Halaman utama / landing page publik |
| `GET` | `/pengaduan/buat` | `pengaduan.create` | Formulir pembuatan pengaduan baru (Anonim / Terbuka) |
| `POST` | `/pengaduan` | `pengaduan.store` | Proses penyimpanan laporan pengaduan & upload lampiran |
| `GET` | `/pengaduan/lacak` | `pengaduan.lacak` | Halaman pelacakan status laporan berbasis nomor tiket |
| `GET` | `/pengaduan/tiket/{ticket}` | `pengaduan.show` | Bukti penerimaan pengaduan (dapat dicetak) |
| `GET` | `/pengaduan` | `pengaduan.index` | Daftar arsip seluruh laporan pengaduan |
| `GET` | `/dashboard` | `dashboard.index` | Panel dashboard operasional petugas unit & admin |
| `GET` | `/unit-kerja` | `unit.index` | Direktori unit kerja penanganan kampus |
| `GET` | `/notifikasi` | `notifikasi.index` | Pusat notifikasi laporan baru & disposisi |
| `GET` | `/laporan` | `laporan.index` | Rekapitulasi laporan & statistik penanganan |

---

## Data Pengujian (Testing Samples)

Aplikasi telah dilengkapi data awal sehingga dapat langsung diuji tanpa perlu input manual:

### 1. Akun Masuk Petugas / Administrator
- **Email:** `admin@kampus.ac.id`
- **Kata Sandi:** `password123`

### 2. Nomor Tiket Siap Uji Pelacakan
Masukkan salah satu nomor tiket di bawah ini pada kolom **"Lacak Pengaduan"** di halaman awal:
- `SIP-202610-001` &rarr; Kasus Sarana & Prasarana *(Status: Selesai)*
- `SIP-202610-002` &rarr; Kasus Akademik & Pelayanan *(Status: Sedang Diproses)*
- `SIP-202610-003` &rarr; Kasus Keamanan Kampus *(Status: Diajukan / Baru)*
- `SIP-202610-0004` &rarr; Kasus Uji Etik *(Status: Diajukan)*

---

## Konfigurasi Notifikasi Email (SMTP)

Sistem menggunakan **Laravel Mail** dengan antrian (*queue*) untuk mengirim notifikasi email ke pelapor dan petugas. Email dirancang untuk **tidak memuat** kronologi lengkap, nama pihak terlapor, catatan investigasi, atau informasi sensitif lainnya.

### 1. Variabel `.env` untuk Pengiriman Email

Tambahkan atau sesuaikan variabel berikut di file `.env` (**jangan gunakan kredensial nyata di repository**):

```dotenv
# Driver email: smtp | log | array | mailgun | ses
MAIL_MAILER=smtp

# Konfigurasi SMTP (ganti dengan data SMTP institusi)
MAIL_HOST=smtp.institusi.ac.id
MAIL_PORT=587
MAIL_USERNAME=no-reply@institusi.ac.id
MAIL_PASSWORD=ganti_dengan_kata_sandi_smtp
MAIL_ENCRYPTION=tls

# Identitas pengirim yang tampil di kotak masuk penerima
MAIL_FROM_ADDRESS=no-reply@institusi.ac.id
MAIL_FROM_NAME="SIP-Kampus Pengaduan"
```

> **Keamanan:** Jangan pernah menyimpan password SMTP nyata di dalam source code atau di-commit ke version control. Gunakan variabel environment atau *secrets manager* institusi.

### 2. Mode Pengujian Lokal (Tanpa SMTP Asli)

Untuk pengembangan lokal tanpa server SMTP, ubah driver ke `log` agar email tercatat di `storage/logs/laravel.log`:

```dotenv
MAIL_MAILER=log
```

Atau gunakan layanan sandbox seperti **Mailtrap**:
```dotenv
MAIL_MAILER=smtp
MAIL_HOST=sandbox.smtp.mailtrap.io
MAIL_PORT=2525
MAIL_USERNAME=username_mailtrap_anda
MAIL_PASSWORD=password_mailtrap_anda
MAIL_ENCRYPTION=tls
```

### 3. Konfigurasi Antrian (Queue)

`PengaduanNotificationMail` mengimplementasikan `ShouldQueue` sehingga pengiriman dilakukan secara asinkron. Untuk lingkungan pengembangan, cukup jalankan:

```bash
C:\xampp\php\php.exe artisan queue:work --stop-when-empty
```

Untuk produksi, konfigurasikan `QUEUE_CONNECTION` di `.env` (disarankan: `redis` atau `database`):

```dotenv
QUEUE_CONNECTION=database
```

Kemudian jalankan tabel antrian:

```bash
C:\xampp\php\php.exe artisan queue:table
C:\xampp\php\php.exe artisan migrate
```

---

## Konfigurasi Scheduler SLA

Modul SLA menggunakan **Laravel Task Scheduler** untuk:
- Memeriksa laporan yang mendekati batas waktu → kirim **pengingat** ke petugas & koordinator
- Memicu **eskalasi otomatis** bila batas waktu terlewati
- **Tidak menutup laporan secara otomatis** — laporan tetap dibuka untuk tindak lanjut

### Perintah Artisan

```bash
# Periksa secara manual (cocok untuk debugging)
C:\xampp\php\php.exe artisan sla:check-escalation

# Jalankan semua jadwal Laravel yang terdaftar
C:\xampp\php\php.exe artisan schedule:run
```

### Penjadwalan di Windows (Task Scheduler)

1. Buka **Task Scheduler** Windows.
2. Buat task baru dengan **Basic Task Wizard**.
3. Atur trigger ke **Setiap 1 menit** (*minutely*).
4. Atur Action ke **Start a Program** dengan nilai:
   - Program: `C:\xampp\php\php.exe`
   - Arguments: `artisan schedule:run`
   - Start in: `C:\xampp\htdocs\Sistem Pengaduan`

### Penjadwalan di Linux / macOS (Cron)

Tambahkan baris berikut ke `crontab -e`:

```cron
* * * * * cd /var/www/html/sistem-pengaduan && php artisan schedule:run >> /dev/null 2>&1
```

### Jadwal yang Terdaftar di Kernel

| Perintah | Frekuensi | Tujuan |
|:---|:---|:---|
| `sla:check-escalation` | Setiap 5 menit | Cek pengingat & eskalasi SLA aktif |

---

## Menjalankan Test Suite (84 Passed)

Semua 84 pengujian unit dan feature Laravel dapat dijalankan dengan:

```bash
C:\xampp\php\php.exe artisan test
```

Atau jalankan per suite pengujian:

```bash
# 1. Pengujian End-to-End Pelaporan & Lacak (30 Tests)
C:\xampp\php\php.exe artisan test --filter PengaduanEndToEndTest

# 2. Pengujian Notifikasi, Email Queue & SLA (15 Tests)
C:\xampp\php\php.exe artisan test --filter NotifikasiDanSlaTest

# 3. Pengujian Workflow Multiunit & State Machine (13 Tests)
C:\xampp\php\php.exe artisan test --filter WorkflowMultiunitTest

# 4. Pengujian Keamanan & Negatif Audit (10 Tests)
C:\xampp\php\php.exe artisan test --filter SecurityNegativeAuditTest

# 5. Pengujian Dashboard Statistik & Ekspor Anti-Formula (7 Tests)
C:\xampp\php\php.exe artisan test --filter DashboardStatistikTest

# 6. Pengujian Fitur Utama & RBAC (7 Tests)
C:\xampp\php\php.exe artisan test --filter SipKampusFeatureTest
```

---

## Dokumentasi Teknis & Serah Terima

Dokumentasi arsitektur lengkap, diagram state machine penanganan kasus, matriks kontrol akses per peran, spesifikasi perlindungan identitas anonim/rahasia, panduan scheduler SLA, dan laporan audit pengujian keamanan tersedia di file:

📄 **[DOKUMENTASI_SERAH_TERIMA.md](file:///c:/xampp/htdocs/Sistem%20Pengaduan/DOKUMENTASI_SERAH_TERIMA.md)**

---

## Lisensi
Aplikasi ini dikembangkan untuk kepentingan institusi pendidikan dengan lisensi terbuka [MIT License](https://opensource.org/licenses/MIT).
