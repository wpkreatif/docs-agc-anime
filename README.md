# 📦 Panduan Instalasi AGC Anime v1.0.0

## 📋 Persyaratan Sistem

| Komponen | Versi Minimum              |
| -------- | -------------------------- |
| PHP      | 8.4                       |
| Composer | 2.x                        |
| Node.js  | 18+                        |
| NPM      | 9+                         |
| SQLite   | 3.x (default) / MySQL 8.0+ |

### Ekstensi PHP yang diperlukan:

- `php-mbstring`
- `php-xml`
- `php-curl`
- `php-zip`
- `php-bcmath`
- `php-fileinfo`

---

## 🚀 Download File

```bash
Silahkan Login ke Member Area di https://akses.toko.im
Masuk Menu Access
Download file yang tersedia
```

## 🌐 Deploy di Shared Hosting (cPanel/Plesk)

### 1. Upload File

Upload semua file ke folder di luar `public_html`, contoh: `/home/user/agc-anime/`

### 2. Storage Link (Tanpa Terminal)

Jika tidak ada akses terminal, akses URL berikut di browser:

```
https://domain-anda.com/setup/storage-link
```

### 3. Optimasi (Tanpa Terminal)

Akses URL berikut di browser:

```
https://domain-anda.com/setup/optimize
```

---

## ⚙️ Konfigurasi .env

Buka file `.env` dan sesuaikan pengaturan berikut:

---

### 🔧 Pengaturan Aplikasi Utama

```env
APP_NAME=Otakudesu                          # Nama website
APP_ENV=production                          # Mode: local / production
APP_KEY=base64:xxxxxxx                      # Auto-generated (jangan diubah manual)
APP_DEBUG=false                             # true = tampilkan error detail (dev only)
APP_URL=https://domain-anda.com             # URL lengkap website
```

| Variable    | Deskripsi                     | Nilai                               |
| ----------- | ----------------------------- | ----------------------------------- |
| `APP_NAME`  | Nama website yang ditampilkan | Bebas, contoh: `Otakudesu`          |
| `APP_ENV`   | Mode aplikasi                 | `local` (dev) / `production` (live) |
| `APP_DEBUG` | Tampilkan error detail        | `true` (dev) / `false` (live)       |
| `APP_URL`   | URL lengkap website           | `https://domain-anda.com`           |

> ⚠️ **PENTING:** Set `APP_DEBUG=false` dan `APP_ENV=production` saat deploy ke server live!

---

### 🔍 Webmaster / Search Console Verification

```env
GOOGLE_WEBMASTER=                           # Kode verifikasi Google Search Console
BING_WEBMASTER=                             # Kode verifikasi Bing Webmaster
YANDEX_WEBMASTER=                           # Kode verifikasi Yandex Webmaster
```

| Variable           | Deskripsi                    | Cara Mendapatkan                                                  |
| ------------------ | ---------------------------- | ----------------------------------------------------------------- |
| `GOOGLE_WEBMASTER` | Meta tag verification Google | [Google Search Console](https://search.google.com/search-console) |
| `BING_WEBMASTER`   | Meta tag verification Bing   | [Bing Webmaster Tools](https://www.bing.com/webmasters)           |
| `YANDEX_WEBMASTER` | Meta tag verification Yandex | [Yandex Webmaster](https://webmaster.yandex.com)                  |

---

### 🎬 Pengaturan API Anime

```env
ANIME_CACHE_TTL=360                         # Durasi cache dalam menit (default: 6 jam)
```

| Variable          | Deskripsi                          | Default       |
| ----------------- | ---------------------------------- | ------------- |
| `ANIME_CACHE_TTL` | Durasi cache data (menit)          | `360` (6 jam) |

---

### 🖼️ Pengaturan Logo & Favicon

```env
LOGO_LIGHT=/assets/images/logo-light.png    # Logo untuk mode terang
LOGO_DARK=/assets/images/logo-dark.png      # Logo untuk mode gelap
FAVICON=/assets/images/favicon.png          # Favicon website
OG_IMAGE=                                   # Gambar Open Graph (untuk share sosmed)
```

| Variable     | Deskripsi                      | Format                |
| ------------ | ------------------------------ | --------------------- |
| `LOGO_LIGHT` | Logo mode terang               | Path relatif atau URL |
| `LOGO_DARK`  | Logo mode gelap                | Path relatif atau URL |
| `FAVICON`    | Favicon website                | Path relatif atau URL |
| `OG_IMAGE`   | Gambar saat di-share ke sosmed | URL lengkap           |

---

### 💬 Pengaturan Komentar (Disqus)

```env
DISQUS_NAME=nama-disqus-anda               # Shortname Disqus
```

Daftar di [Disqus](https://disqus.com/) dan dapatkan shortname website Anda.

---

### ⚡ HTML Minification

```env
MINIFY_HTML=false                           # true = aktifkan minify HTML output
```

---

### 📢 Pengaturan Iklan (Ads)

#### Iklan Samping Kiri

```env
ADS_LEFT_ON=false                           # Aktifkan iklan kiri (true/false)
ADS_LEFT_IMG=https://url-gambar-iklan.jpg   # URL gambar iklan
ADS_LEFT_LINK=https://url-tujuan.com        # URL tujuan saat diklik
```

#### Iklan Samping Kanan

```env
ADS_RIGHT_ON=false
ADS_RIGHT_IMG=https://url-gambar-iklan.jpg
ADS_RIGHT_LINK=https://url-tujuan.com
```

#### Iklan Bawah

```env
ADS_BOTTOM_ON=false
ADS_BOTTOM_IMG=https://url-gambar-iklan.jpg
ADS_BOTTOM_LINK=https://url-tujuan.com
```

| Variable     | Deskripsi                    | Nilai            |
| ------------ | ---------------------------- | ---------------- |
| `ADS_*_ON`   | Toggle aktif/nonaktif iklan  | `true` / `false` |
| `ADS_*_IMG`  | URL gambar banner iklan      | URL gambar       |
| `ADS_*_LINK` | URL tujuan saat iklan diklik | URL lengkap      |

---

### 🏷️ Pengaturan Banner

Banner tersedia di beberapa lokasi:

| Lokasi         | Variable Prefix                                         | Deskripsi                             |
| -------------- | ------------------------------------------------------- | ------------------------------------- |
| Halaman Home   | `BANNER_HOME_1_*`, `BANNER_HOME_2_*`, `BANNER_HOME_3_*` | 3 slot banner di halaman utama        |
| Halaman Detail | `BANNER_DETAIL_1_*`, `BANNER_DETAIL_2_*`                | 2 slot banner di halaman detail anime |
| Halaman Watch  | `BANNER_WATCH_1_*`, `BANNER_WATCH_2_*`                  | 2 slot banner di halaman nonton       |
| Global         | `BANNER_GLOBAL_*`                                       | 1 banner yang tampil di semua halaman |

Setiap banner memiliki 3 variable:

```env
BANNER_HOME_1_ON=false                      # Aktifkan banner (true/false)
BANNER_HOME_1_IMG=https://url-gambar.jpg    # URL gambar banner
BANNER_HOME_1_LINK=https://url-tujuan.com   # URL tujuan saat diklik
```

---

### 📜 Footer Ads Script

```env
FOOTER_ADS_SCRIPT=                          # Script iklan di footer (harus di-encode base64)
```

> **Cara encode:** Encode script HTML iklan Anda ke format Base64. Bisa menggunakan [base64encode.org](https://www.base64encode.org/).

---

### 📊 Pengaturan Analytics

```env
HISTATS_SID=                                # Session ID dari Histats
GOOLE_ANALYTICS_ID=                         # Google Analytics Measurement ID (G-XXXXXXXXXX)
```

| Variable             | Deskripsi             | Cara Mendapatkan                                  |
| -------------------- | --------------------- | ------------------------------------------------- |
| `HISTATS_SID`        | ID statistik Histats  | [Histats.com](https://www.histats.com/)           |
| `GOOLE_ANALYTICS_ID` | ID Google Analytics 4 | [Google Analytics](https://analytics.google.com/) |

---

### 🗄️ Pengaturan Database

#### SQLite (Default - Direkomendasikan)

```env
DB_CONNECTION=sqlite
```

Tidak perlu konfigurasi tambahan. File database otomatis di `database/database.sqlite`.

---

### 🔐 Pengaturan Session & Cache

```env
SESSION_DRIVER=database                     # Driver session: file / database / redis
SESSION_LIFETIME=120                        # Durasi session (menit)
CACHE_STORE=file                            # Driver cache: file / database / redis
```

---

## 🗑️ Membersihkan Cache

Setelah mengubah `.env`, jalankan perintah berikut:

```bash
php artisan config:clear
php artisan cache:clear
php artisan view:clear
php artisan route:clear
```

Atau akses URL berikut di browser (jika tanpa terminal):

| URL Route             | Fungsi                                 |
| --------------------- | -------------------------------------- |
| `/clear/optimize`     | Bersihkan semua cache (optimize:clear) |
| `/clear/cache`        | Bersihkan cache aplikasi               |
| `/clear/config`       | Bersihkan cache konfigurasi            |
| `/clear/route`        | Bersihkan cache route                  |
| `/clear/view`         | Bersihkan cache view                   |
| `/setup/storage-link` | Buat symlink storage                   |
| `/setup/optimize`     | Optimasi aplikasi untuk production     |

Contoh penggunaan:

```
https://domain-anda.com/clear/optimize
https://domain-anda.com/clear/cache
https://domain-anda.com/clear/config
https://domain-anda.com/setup/storage-link
https://domain-anda.com/setup/optimize
```

---

## 🔄 Generate Sitemap

### Manual (via Terminal)

```bash
php artisan sitemap:generate
```

Output sitemap akan disimpan ke `public/sitemap.xml` dan cache di-update otomatis.

### Otomatis via Cron Job (Direkomendasikan)

Sitemap sudah di-schedule otomatis setiap hari **jam 03:00 pagi**. Cukup tambahkan **1 baris cron** di server:

#### Setup di Linux/VPS:

```bash
# Buka crontab editor
crontab -e

# Tambahkan baris ini (sesuaikan path project):
* * * * * cd /var/www/agc-anime && php artisan schedule:run >> /dev/null 2>&1
```

#### Setup di cPanel:

1. Login ke **cPanel** → **Cron Jobs**
2. Set interval ke **Every Minute** (`* * * * *`)
3. Masukkan command:

```
cd /home/username/agc-anime && php artisan schedule:run >> /dev/null 2>&1
```

> **Catatan:** Sesuaikan `/home/username/agc-anime` dengan path project Anda di server.

#### Cek Log Sitemap:

```bash
cat storage/logs/sitemap.log
```

### Akses Sitemap di Browser

```
https://domain-anda.com/sitemap.xml
```

---

## 🗂️ Struktur File / File Tree

```
agc-anime-v1.0.0/
├── 📄 .editorconfig
├── 📄 .env                        # ⚙️ File konfigurasi utama
├── 📄 .env.example                # Template konfigurasi
├── 📄 .gitattributes
├── 📄 .gitignore
├── 📄 .htaccess                   # Konfigurasi Apache root
├── 📄 404.html                    # Halaman 404 statis
├── 📄 README.md
├── 📄 install.md                  # 📖 Panduan instalasi (file ini)
├── 📄 artisan                     # CLI Laravel
├── 📄 composer.json               # Dependency PHP
├── 📄 composer.lock
├── 📄 package.json                # Dependency Node.js
├── 📄 phpunit.xml                 # Konfigurasi testing
├── 📄 vite.config.js              # Konfigurasi Vite bundler
│
├── 📂 app/                        # 🏗️ Kode Aplikasi Utama
│   ├── 📂 Http/
│   │   ├── 📂 Controllers/
│   │   │   ├── 📄 Controller.php           # Base controller
│   │   │   ├── 📄 AnimeController.php      # Controller utama anime
│   │   │   └── 📄 SitemapController.php    # Controller sitemap
│   │   └── 📂 Middleware/
│   │       └── 📄 (middleware files)
│   ├── 📂 Models/
│   │   └── 📄 (model files)
│   ├── 📂 Providers/
│   │   └── 📄 (service provider files)
│   └── 📂 Services/
│       └── 📄 AnimeService.php             # Service layer API anime
│
├── 📂 bootstrap/                  # 🔌 Bootstrap Laravel
│   ├── 📄 app.php
│   ├── 📄 providers.php
│   └── 📂 cache/
│
├── 📂 config/                     # ⚙️ File Konfigurasi
│   ├── 📄 ads.php                 # Konfigurasi iklan
│   ├── 📄 analytics.php           # Konfigurasi analytics
│   ├── 📄 app.php                 # Konfigurasi aplikasi
│   ├── 📄 auth.php                # Konfigurasi autentikasi
│   ├── 📄 banner.php              # Konfigurasi banner
│   ├── 📄 cache.php               # Konfigurasi cache
│   ├── 📄 database.php            # Konfigurasi database
│   ├── 📄 filesystems.php         # Konfigurasi filesystem
│   ├── 📄 logging.php             # Konfigurasi logging
│   ├── 📄 mail.php                # Konfigurasi email
│   ├── 📄 minify.php              # Konfigurasi HTML minify
│   ├── 📄 queue.php               # Konfigurasi antrian
│   ├── 📄 services.php            # Konfigurasi services
│   └── 📄 session.php             # Konfigurasi session
│
├── 📂 database/                   # 🗄️ Database
│   ├── 📄 .gitignore
│   ├── 📄 database.sqlite         # File database SQLite
│   ├── 📂 factories/
│   ├── 📂 migrations/             # File migrasi database
│   └── 📂 seeders/
│
├── 📂 public/                     # 🌐 File Publik (Document Root)
│   ├── 📄 .htaccess               # Konfigurasi Apache
│   ├── 📄 index.php               # Entry point aplikasi
│   ├── 📄 favicon.ico
│   ├── 📄 robots.txt
│   ├── 📂 .well-known/
│   ├── 📂 assets/
│   │   ├── 📂 css/                # File CSS
│   │   ├── 📂 js/                 # File JavaScript
│   │   └── 📂 images/             # Gambar (logo, favicon, dll)
│   └── 📂 vendor/                 # Asset vendor publik
│
├── 📂 resources/                  # 🎨 Resource Frontend
│   ├── 📂 css/
│   │   └── 📄 app.css
│   ├── 📂 js/
│   │   └── 📄 (JavaScript files)
│   └── 📂 views/                  # Blade Templates
│       ├── 📂 anime/
│       │   ├── 📄 details.blade.php        # Halaman detail anime
│       │   └── 📄 watch.blade.php          # Halaman nonton/streaming
│       ├── 📂 components/
│       │   ├── 📄 analytics.blade.php      # Komponen analytics
│       │   ├── 📄 banner.blade.php         # Komponen banner
│       │   └── 📄 pagination.blade.php     # Komponen pagination
│       ├── 📂 errors/
│       │   ├── 📄 401.blade.php
│       │   ├── 📄 403.blade.php
│       │   ├── 📄 404.blade.php
│       │   └── 📄 500.blade.php
│       ├── 📂 layout/
│       │   ├── 📄 main.blade.php           # Layout utama
│       │   ├── 📄 ads.blade.php            # Layout iklan
│       │   ├── 📄 sidebar.blade.php        # Sidebar
│       │   └── 📄 sidebar_watch.blade.php  # Sidebar halaman nonton
│       ├── 📂 pages/
│       │   ├── 📄 disclaimer.blade.php
│       │   ├── 📄 privacy.blade.php
│       │   └── 📄 terms.blade.php
│       ├── 📄 home.blade.php               # Halaman utama
│       ├── 📄 animelist.blade.php          # Daftar anime A-Z
│       ├── 📄 bookmark.blade.php           # Halaman bookmark
│       ├── 📄 complete.blade.php           # Anime completed
│       ├── 📄 genre-list.blade.php         # Daftar genre
│       ├── 📄 genres.blade.php             # Halaman per genre
│       ├── 📄 history.blade.php            # Riwayat nonton
│       ├── 📄 ongoing.blade.php            # Anime ongoing
│       ├── 📄 schedule.blade.php           # Jadwal anime
│       ├── 📄 search.blade.php             # Halaman pencarian
│       ├── 📄 sitemap.blade.php            # Template sitemap
│       └── 📄 welcome.blade.php            # Halaman welcome
│
├── 📂 routes/                     # 🛣️ Routing
│   ├── 📄 web.php                 # Route web utama
│   └── 📄 console.php             # Route console/artisan
│
├── 📂 storage/                    # 💾 Storage
│   ├── 📂 app/                    # File yang diupload
│   ├── 📂 framework/              # Cache, session, views compiled
│   └── 📂 logs/                   # File log aplikasi
│
└── 📂 tests/                      # 🧪 Testing
    └── 📄 (test files)
```

---

## ❓ Troubleshooting

### Error: Permission Denied

```bash
sudo chmod -R 775 storage bootstrap/cache
sudo chown -R www-data:www-data .
```

### Error: 500 Internal Server Error

1. Cek `APP_DEBUG=true` untuk melihat detail error
2. Cek log di `storage/logs/laravel.log`
3. Pastikan semua ekstensi PHP sudah terinstall

### Halaman Blank / Tidak Muncul

```bash
php artisan config:clear
php artisan cache:clear
php artisan view:clear
```

### Error: API Key Invalid

Pastikan `ANIME_API_KEY` di `.env` sudah benar dan valid.

### Perubahan .env Tidak Berlaku

```bash
php artisan config:clear
php artisan config:cache
```

---

## 📞 Catatan Penting

- Selalu backup file `.env` dan `database/database.sqlite` sebelum update
- Jangan pernah share file `.env` ke publik (berisi API key & kredensial)
- Set `APP_DEBUG=false` di production untuk keamanan
- Gunakan HTTPS di production untuk keamanan data
