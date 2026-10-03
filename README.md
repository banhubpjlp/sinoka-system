# SINOKA - Sistem Informasi Nota Dinas dan Kwitansi

## Deskripsi
SINOKA adalah sistem informasi berbasis web untuk mengelola Nota Dinas dan Kwitansi di kantor/instansi pemerintah maupun swasta. Dilengkapi dengan fitur workflow approval, multi-user dengan role berbeda, dan cetak dokumen format resmi.

## Fitur Utama
- ✅ Manajemen Nota Dinas dengan status workflow
- ✅ Manajemen Kwitansi dengan perhitungan otomatis
- ✅ Sistem approval multi-level
- ✅ Role-based access control (Admin, Pejabat, Operator)
- ✅ Dashboard statistik
- ✅ Cetak PDF & Print
- ✅ Manajemen user dan unit kerja
- ✅ Lampiran file
- ✅ Riwayat perubahan
- ✅ Export laporan

## Tech Stack
- **Backend**: Node.js + Express
- **Database**: PostgreSQL
- **Frontend**: EJS Templates + Bootstrap 5
- **Security**: bcryptjs, express-session
- **PDF**: PDFKit

## Instalasi

### 1. Clone Repository
```bash
git clone https://github.com/banhubpjlp/sinoka-system.git
cd sinoka-system
```

### 2. Install Dependencies
```bash
npm install
```

### 3. Setup Database
Buat database PostgreSQL terlebih dahulu:
```sql
CREATE DATABASE sinoka_db;
```

### 4. Konfigurasi Environment
```bash
cp .env.example .env
```
Edit file `.env` sesuai konfigurasi database Anda.

### 5. Jalankan Migrasi Database
```bash
npm run migrate
```

### 6. Jalankan Aplikasi
```bash
# Development
npm run dev

# Production
npm start
```

Aplikasi akan berjalan di `http://localhost:3000`

## Login Default
- **Username**: admin@sinoka.com
- **Password**: Admin@123

## Struktur Folder
```
sinoka-system/
├── config/           # Konfigurasi database
├── migrations/       # Database migrations
├── models/           # Database models & queries
├── routes/           # Route handlers
├── middleware/       # Middleware (auth, validation)
├── controllers/      # Business logic
├── views/            # EJS templates
├── public/           # Static files (CSS, JS, images)
├── utils/            # Helper functions
├── uploads/          # Folder untuk upload file
└── server.js         # Entry point
```

## Panduan Penggunaan

### Admin
- Kelola user dan role
- Kelola unit kerja
- Lihat semua nota dinas dan kwitansi
- Dashboard statistik global

### Pejabat/Atasan
- Approve/reject nota dinas
- Lihat laporan
- Verifikasi kwitansi

### Operator/Staff
- Buat nota dinas baru
- Buat kwitansi baru
- Upload lampiran
- Lihat status dokumen

## Database Schema

### Table: users
- id, email, nama_lengkap, password, role, unit_kerja_id, is_active, created_at, updated_at

### Table: unit_kerja
- id, nama, kode, deskripsi, created_at

### Table: notas
- id, nomor, judul, tujuan, perihal, isi, dibuat_oleh, status, unit_kerja_id, created_at, updated_at

### Table: kwitansi
- id, nomor, nama_penerima, keperluan, jumlah, terbilang, status, bukti_file, dibuat_oleh, created_at, updated_at

### Table: approval_history
- id, dokumen_id, dokumen_type, disetujui_oleh, komentar, status, created_at

## API Endpoints

### Auth
- `POST /auth/login`
- `POST /auth/logout`
- `POST /auth/register` (Admin only)

### Dashboard
- `GET /dashboard`

### Nota Dinas
- `GET /nota` - List semua nota
- `GET /nota/create` - Form buat nota
- `POST /nota/store` - Simpan nota baru
- `GET /nota/:id/edit` - Edit nota
- `POST /nota/:id/update` - Update nota
- `GET /nota/:id/preview` - Preview nota
- `GET /nota/:id/print` - Print nota
- `POST /nota/:id/approve` - Approve nota
- `POST /nota/:id/reject` - Reject nota

### Kwitansi
- `GET /kwitansi` - List semua kwitansi
- `GET /kwitansi/create` - Form buat kwitansi
- `POST /kwitansi/store` - Simpan kwitansi baru
- `GET /kwitansi/:id/preview` - Preview kwitansi
- `GET /kwitansi/:id/print` - Print kwitansi

## Kontribusi
Silakan buat pull request untuk improvement atau lapor bug di issues.

## Lisensi
MIT License - Bebas digunakan untuk keperluan komersial dan non-komersial.

## Support
Untuk bantuan dan pertanyaan, silakan buat issue di repository ini.
