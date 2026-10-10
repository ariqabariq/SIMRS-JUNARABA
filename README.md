# 🏥 SIMRS JUNARABA
**Sistem Informasi Manajemen Rumah Sakit Terpadu**

![React](https://img.shields.io/badge/React-19.2-61DAFB?logo=react&logoColor=black)
![Vite](https://img.shields.io/badge/Vite-8.3-646CFF?logo=vite&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-4.3-38B2AC?logo=tailwind-css&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-Express-339933?logo=node.js&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-Database-4479A1?logo=mysql&logoColor=white)
![Status](https://img.shields.io/badge/Status-Development-orange)

SIMRS Junaraba adalah platform berbasis web modern untuk digitalisasi dan otomasi operasional rumah sakit. Dirancang dengan antarmuka yang intuitif dan responsif untuk mendukung alur kerja tenaga medis, administrasi, hingga farmasi secara efisien dan terintegrasi.

---

## ✨ Fitur Utama

### 1. 🌐 Portal Publik & Pasien
- **Landing Page Interaktif**: Beranda informasi rumah sakit, layanan darurat 24 jam (*Emergency Call*), dan pencarian dokter/spesialis.
- **Autentikasi Pengguna**: Login, Registrasi Mandiri, dan Pemulihan Akun (*Forgot Password*).

### 2. 📋 Pelayanan Pasien & Operasional
- **Manajemen Antrian**: Pemanggilan nomor antrean poliklinik dan loket secara terstruktur.
- **Pendaftaran Pasien & Poli**: Registrasi pasien baru/lama, verifikasi NIK/No. RM, serta penjadwalan kunjungan poli.
- **Pemeriksaan Dokter (Rekam Medis)**: Formulir pencatatan anamnesis, diagnosis (ICD-10), tindakan medis, dan e-resep dokter.
- **Apotek & Farmasi**: Pengelolaan resep masuk, penyiapan obat, dan distribusi farmasi.
- **Rawat Inap**: Manajemen keterisian bangsal/kamar tidur pasien secara *real-time*.

### 3. 📊 Master Data & Administrasi
- **Data Pasien**: Riwayat lengkap pasien dengan kemampuan sinkronisasi offline (Local Storage & Server Sync).
- **Data Tenaga Medis (Dokter)**: Manajemen direktori dokter spesialis, SIP, dan jadwal praktik.
- **Departemen & Poliklinik**: Pengaturan poli spesialis dan unit pelayanan.
- **Manajemen Pengguna & Pengaturan**: Pembagian hak akses dan pengaturan profil akun.

---

## 🛠️ Arsitektur & Teknologi

| Bagian | Teknologi | Keterangan |
| :--- | :--- | :--- |
| **Frontend** | React 19, Vite 8 | UI framework & modern build tool dengan performa tinggi |
| **Styling** | Tailwind CSS v4, PostCSS | Utility-first styling modern & responsive |
| **Ikon** | Lucide React | Icon set minimalis & konsisten |
| **Routing** | React Router v7 | Manajemen navigasi Single Page Application (SPA) |
| **Backend** | Node.js, Express.js | REST API server untuk integrasi data |
| **Database** | MySQL | Penyimpanan data relasional sistem rumah sakit |

---

## 📁 Struktur Direktori

```text
SIMRS-Junaraba/
├── backend-simrs/              # Server API (Express.js)
│   ├── config/
│   │   └── database.js         # Koneksi database MySQL
│   ├── routes/
│   │   └── apiRoutes.js        # Endpoint REST API (sinkronisasi data)
│   ├── .env.example            # Template konfigurasi environment backend
│   ├── package.json
│   └── server.js               # Titik masuk server Express
│
├── frontend-simrs/             # Client Web Application (React + Vite)
│   ├── public/                 # Aset statis publik
│   ├── src/
│   │   ├── assets/             # Gambar & ikon visual
│   │   ├── components/         # Komponen bersama (Layout, Sidebar)
│   │   ├── pages/              # Halaman aplikasi (Poli, Antrian, Apotek, dll.)
│   │   ├── App.jsx             # Konfigurasi routing utama
│   │   └── main.jsx            # Entry point React
│   ├── package.json
│   ├── tailwind.config.js
│   └── vite.config.js
│
├── .gitignore                  # Konfigurasi file yang diabaikan Git
└── README.md                   # Dokumentasi proyek
```

---

## 🚀 Panduan Instalasi & Menjalankan

### Prasyarat
- [Node.js](https://nodejs.org/) (versi 18.x atau yang lebih baru disarankan)
- [MySQL Database Server](https://www.mysql.com/) (atau MariaDB / XAMPP)
- [Git](https://git-scm.com/)

---

### 1. Kloning Repository
```bash
git clone https://github.com/ariqabariq/SIMRS-JUNARABA.git
cd SIMRS-JUNARABA
```

---

### 2. Konfigurasi & Jalankan Backend

1. Masuk ke direktori backend:
   ```bash
   cd backend-simrs
   ```

2. Pasang dependensi:
   ```bash
   npm install
   ```

3. Siapkan file `.env`:
   Salin `.env.example` menjadi `.env`:
   ```bash
   cp .env.example .env
   ```
   Sesuaikan parameter database di file `.env`:
   ```env
   PORT=5000
   DB_HOST=localhost
   DB_USER=root
   DB_PASSWORD=
   DB_NAME=db_sim_rs_junaraba
   ```

4. Buat Database MySQL & Tabel:
   Buat database di MySQL (`db_sim_rs_junaraba`), contoh skema tabel pasien:
   ```sql
   CREATE DATABASE IF NOT EXISTS db_sim_rs_junaraba;
   USE db_sim_rs_junaraba;

   CREATE TABLE IF NOT EXISTS patients (
       id INT AUTO_INCREMENT PRIMARY KEY,
       noRm VARCHAR(50) UNIQUE,
       nik VARCHAR(20),
       nama VARCHAR(150),
       jk ENUM('L', 'P'),
       tglLahir DATE,
       penjamin VARCHAR(50),
       kontak VARCHAR(30),
       created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
   );
   ```

5. Jalankan server backend:
   ```bash
   # Mode pengembangan (live reload)
   npm run dev

   # Atau mode produksi
   npm start
   ```
   Backend akan aktif di `http://localhost:5000`.

---

### 3. Konfigurasi & Jalankan Frontend

1. Buka terminal baru dan masuk ke direktori frontend:
   ```bash
   cd frontend-simrs
   ```

2. Pasang dependensi:
   ```bash
   npm install
   ```

3. Jalankan server development:
   ```bash
   npm run dev
   ```
   Buka URL yang ditampilkan di terminal (biasanya `http://localhost:5173`) di browser Anda.

---

## 🔒 Catatan Keamanan
- File `.env` yang memuat kredensial database **tidak boleh di-commit** ke repositori publik.
- Selalu gunakan `.env.example` sebagai referensi struktur variabel lingkungan.

---

## 👨‍💻 Pengembang
- **Pengembang**: Ariq Abariq ([@ariqabariq](https://github.com/ariqabariq))
- **Lisensi**: Proyek ini dikembangkan untuk kebutuhan internal / operasional SIMRS Junaraba.
