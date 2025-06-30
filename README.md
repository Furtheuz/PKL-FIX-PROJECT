# 📘 Sistem Magang - PHP Native

Sistem informasi pengelolaan peserta magang untuk institusi/instansi. Dibangun menggunakan **PHP Native** dan **MySQL**, dengan **Bootstrap** sebagai tampilan dasar.

---

## 👨‍💻 Tim Pengembang

| Nama    | Role     |
|---------|----------|
| Tristan | Backend  |
| Dimas   | Frontend |

---

## 📁 Struktur Folder

```
sistem_magang/
├── assets/ # File statis (js, css, img)
│ ├── css/
│ └── js/
├── config/ # Konfigurasi koneksi & auth
│ ├── db.php
│ └── auth.php
├── modules/ # Modul tambahan (contoh: cetak ID Card)
│ └── print_idcard.php
├── sql/
│ └── database.sql # Struktur & data awal
├── uploads/ # Dokumen peserta
├── index.php # Redirect awal
├── login.php # Login & Register user
├── logout.php
├── dashboard.php # Dashboard multi-role
├── peserta.php # Data peserta magang
├── institusi.php # Data institusi
├── jadwal.php # Jadwal pembimbingan
├── laporan.php # Input + validasi laporan
├── arsip.php # Riwayat & alumni
├── profile.php # Profil user + ganti password + cetak ID Card
├── settings.php # Pengaturan sistem
├── uploads.php # Upload file
└── idcard.php # Cetak ID Card massal
```
