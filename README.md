# Rahmad HandyCraft — Business Management App

> A comprehensive cross-platform business management application for handicraft businesses — featuring financial tracking, inventory management, employee payroll, and customer/supplier relationship management.

---

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Configuration](#configuration)
- [Screenshots & Modules](#screenshots--modules)
- [License](#license)

---

## Overview

**Rahmad HandyCraft** is a Flutter-based mobile and desktop business management system designed specifically for small-to-medium handicraft businesses. The app provides a complete financial and operational management solution, including income and expense tracking, product and raw material inventory, employee compensation management, and stakeholder (customer and supplier) databases.

The application is backed by **Firebase Realtime Database**, uses **Flutter Riverpod** for reactive state management, and supports multiple platforms: Android, iOS, Web, Windows, macOS, and Linux — with a fully responsive UI adapting to any screen size.

---

## Features

### Dashboard
- Real-time financial overview showing total income, total expenses, and net profit
- Monthly and yearly date filtering with a month-picker dialog
- Recent transaction timeline grouped by date
- Summary cards with animated data loading (shimmer effect)

### Penerimaan (Revenue / Income)
- Record product sales to customers with quantity, unit, price, and total
- Record miscellaneous income (penerimaan lainnya) for non-product revenue
- Full CRUD: add, view detail, edit, and delete revenue records
- Streams data in real time from Firebase

### Pengeluaran (Expenses)
- Record supplier purchases (raw material procurement) with item, quantity, unit, price, and supplier reference
- Record employee salary disbursements (pengeluaran gaji) with employee reference and payment amount
- Record miscellaneous expenses (pengeluaran lainnya)
- Full CRUD on all expense types

### Produk (Product & Material Inventory)
- Manage finished product catalog with name, unit, and selling price
- Manage raw material (bahan) catalog
- Edit or remove existing products and materials

### Pelanggan (Customer Management)
- Maintain a customer database with name, phone, address, and description
- View individual customer transaction history
- Add, edit, and delete customer records

### Supplier Management
- Maintain a supplier database with contact and address information
- View per-supplier purchase history
- Add, edit, and delete supplier records

### Karyawan (Employee Management)
- Manage employee roster with name, phone, address, and employment status
- Record honor/compensation per employee with flexible payment methods (daily, hourly, per-piece)
- View per-employee honor history and payment tracking

### Settings
- PIN-based security lock (enable/disable toggle, default PIN: 123456)
- Light / Dark theme switching persisted via Shared Preferences

---

## Tech Stack

| Layer | Technology |
|---|---|
| Framework | Flutter (Dart SDK ^3.8.1) |
| State Management | Flutter Riverpod 2.6.1 |
| Backend / Database | Firebase Realtime Database 11.3.9 |
| Local Storage | Shared Preferences 2.5.3 |
| Charts | FL Chart 1.0.0 |
| HTTP Client | Dio 5.8.0 / HTTP 1.4.0 |
| Internationalization | Intl 0.20.2 (id_ID locale) |
| UI Animations | Flutter Animate 4.5.2 / Shimmer 3.0.0 |
| Navigation | Persistent Bottom Nav Bar 6.2.1 |
| Fonts & Icons | Google Fonts 6.2.1 / Iconsax |
| Export | Excel 4.0.6 |
| Encryption | Encrypt 5.0.3 |

---

## Project Structure

```
handycraft-app/
├── lib/
│   ├── main.dart                         # App entry point, Firebase initialization
│   ├── firebase_options.dart             # Firebase project configuration
│   ├── core/
│   │   ├── constants/
│   │   │   └── app_constant.dart         # App-wide constants, breakpoints
│   │   ├── models/                       # Data models (10 models)
│   │   │   ├── penerimaan_model.dart
│   │   │   ├── pengeluaran_model.dart
│   │   │   ├── product_model.dart
│   │   │   ├── karyawan_model.dart
│   │   │   ├── honor_model.dart
│   │   │   ├── supplier_model.dart
│   │   │   ├── pelanggan_model.dart
│   │   │   ├── transaction_model.dart
│   │   │   ├── recent_transaction_model.dart
│   │   │   └── settings_model.dart
│   │   ├── providers/                    # Riverpod providers (12 providers)
│   │   │   ├── dashboard_provider.dart
│   │   │   ├── penerimaan_provider.dart
│   │   │   ├── pengeluaran_provider.dart
│   │   │   ├── product_provider.dart
│   │   │   ├── karyawan_provider.dart
│   │   │   ├── honor_provider.dart
│   │   │   ├── supplier_provider.dart
│   │   │   ├── pelanggan_provider.dart
│   │   │   ├── pin_provider.dart
│   │   │   ├── settings_provider.dart
│   │   │   ├── summary_total_provider.dart
│   │   │   └── theme_provider.dart
│   │   ├── repository/                   # Firebase CRUD repositories (8 repos)
│   │   │   ├── dashboard_repository.dart
│   │   │   ├── penerimaan_repository.dart
│   │   │   ├── pengeluaran_repository.dart
│   │   │   ├── product_repository.dart
│   │   │   ├── karyawan_repository.dart
│   │   │   ├── honor_repository.dart
│   │   │   ├── supplier_repository.dart
│   │   │   └── pelanggan_repository.dart
│   │   ├── extensions/                   # Dart extension helpers
│   │   │   ├── date_helper_extension.dart
│   │   │   ├── penerimaan_extension.dart
│   │   │   └── pengeluaran_extension.dart
│   │   └── routes/
│   │       └── app_routes.dart           # Named route definitions
│   ├── screens/                          # 34+ UI screens
│   │   ├── splash_screen.dart
│   │   ├── pin_screen.dart
│   │   ├── dashboard/
│   │   ├── product/
│   │   ├── supplier/
│   │   ├── pelanggan/
│   │   ├── karyawan/
│   │   └── settings/
│   ├── widgets/
│   │   ├── navbottom.dart
│   │   └── button_widgets.dart
│   └── mocks/
│       └── recent_transaction_mock.dart
├── assets/
│   ├── logo-app.png
│   └── icon/
│       └── icon_app.png
├── android/
├── ios/
├── web/
├── windows/
├── macos/
├── linux/
├── pubspec.yaml
└── firebase.json
```

---

## Getting Started

### Prerequisites

- Flutter SDK >= 3.8.1
- Dart SDK ^3.8.1
- A Firebase project with Realtime Database enabled
- Android Studio / VS Code with Flutter plugin

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/handycraft-app.git
   cd handycraft-app
   ```

2. **Install dependencies**
   ```bash
   flutter pub get
   ```

3. **Configure Firebase**
   - Create a Firebase project at [console.firebase.google.com](https://console.firebase.google.com)
   - Enable **Realtime Database**
   - Use the FlutterFire CLI to generate `firebase_options.dart`:
     ```bash
     dart pub global activate flutterfire_cli
     flutterfire configure
     ```

4. **Run the app**
   ```bash
   flutter run
   ```

---

## Configuration

### Firebase Database Rules

Make sure your Firebase Realtime Database rules allow read/write for authenticated or test use:

```json
{
  "rules": {
    ".read": true,
    ".write": true
  }
}
```

> For production, replace with proper authentication rules.

### Locale

The app is configured for **Indonesian locale (id_ID)**. Date and currency formatting follows Indonesian conventions. To change locale, update `initializeDateFormatting` in `main.dart`.

### PIN Security

- Default PIN: `123456`
- PIN can be enabled or disabled from the Settings screen
- PIN state is persisted using Shared Preferences

---

## Application Flow

```
App Launch
    └── Splash Screen (2s delay)
            └── PIN Screen (if PIN is enabled)
                    └── Main App (Bottom Navigation)
                            ├── Dashboard
                            │     ├── Add Penerimaan (product sale)
                            │     ├── Add Penerimaan Lainnya (misc income)
                            │     ├── Add Pengeluaran (supplier purchase)
                            │     ├── Add Pengeluaran Gaji (employee salary)
                            │     └── Add Pengeluaran Lainnya (misc expense)
                            ├── Produk
                            │     ├── Add / Edit Product
                            │     └── Add / Edit Bahan (raw material)
                            ├── Supplier
                            │     ├── Add / Edit Supplier
                            │     └── Supplier Detail + Purchase History
                            ├── Pelanggan
                            │     ├── Add / Edit Pelanggan
                            │     └── Pelanggan Detail + Transaction History
                            ├── Karyawan
                            │     ├── Add / Edit Karyawan
                            │     ├── Add Honor (compensation)
                            │     └── Karyawan Detail + Honor History
                            └── Settings
                                  ├── Toggle PIN Security
                                  └── Toggle Light / Dark Theme
```

---

## License

This project is private and proprietary. All rights reserved by **Rahmad HandyCraft**.

---

---

# Rahmad HandyCraft — Aplikasi Manajemen Bisnis

> Aplikasi manajemen bisnis lintas platform yang komprehensif untuk usaha kerajinan tangan — mencakup pelacakan keuangan, manajemen inventaris, penggajian karyawan, serta pengelolaan data pelanggan dan supplier.

---

## Daftar Isi

- [Gambaran Umum](#gambaran-umum)
- [Fitur Utama](#fitur-utama)
- [Teknologi yang Digunakan](#teknologi-yang-digunakan)
- [Struktur Proyek](#struktur-proyek)
- [Cara Memulai](#cara-memulai)
- [Konfigurasi](#konfigurasi)
- [Alur Aplikasi](#alur-aplikasi)

---

## Gambaran Umum

**Rahmad HandyCraft** adalah aplikasi manajemen bisnis berbasis Flutter yang dirancang khusus untuk usaha kerajinan tangan skala kecil hingga menengah. Aplikasi ini menyediakan solusi manajemen operasional dan keuangan yang lengkap, mencakup pencatatan pemasukan dan pengeluaran, manajemen inventaris produk dan bahan baku, pengelolaan honor karyawan, serta database pelanggan dan supplier.

Aplikasi ini didukung oleh **Firebase Realtime Database**, menggunakan **Flutter Riverpod** untuk state management yang reaktif, dan mendukung berbagai platform: Android, iOS, Web, Windows, macOS, dan Linux — dengan UI responsif yang menyesuaikan ukuran layar secara otomatis.

---

## Fitur Utama

### Dashboard
- Ringkasan keuangan real-time yang menampilkan total pemasukan, total pengeluaran, dan laba bersih
- Filter berdasarkan bulan dan tahun menggunakan dialog pemilih bulan
- Timeline transaksi terkini yang dikelompokkan berdasarkan tanggal
- Kartu ringkasan dengan animasi loading shimmer

### Penerimaan (Pemasukan)
- Catat penjualan produk ke pelanggan beserta kuantitas, satuan, harga, dan total
- Catat pemasukan lainnya (non-produk) untuk pendapatan di luar penjualan produk
- Operasi lengkap: tambah, lihat detail, edit, dan hapus catatan pemasukan
- Data diperbarui secara real-time dari Firebase

### Pengeluaran
- Catat pembelian bahan baku dari supplier beserta item, kuantitas, satuan, harga, dan referensi supplier
- Catat pembayaran gaji/honor karyawan dengan referensi karyawan dan jumlah yang dibayarkan
- Catat pengeluaran lainnya untuk biaya operasional di luar pembelian dan gaji
- Operasi lengkap pada semua jenis pengeluaran

### Produk & Bahan Baku (Inventaris)
- Kelola katalog produk jadi dengan nama, satuan, dan harga jual
- Kelola katalog bahan baku
- Edit atau hapus produk dan bahan yang sudah ada

### Pelanggan
- Kelola database pelanggan beserta nama, nomor telepon, alamat, dan keterangan
- Lihat riwayat transaksi per pelanggan
- Tambah, edit, dan hapus data pelanggan

### Supplier
- Kelola database supplier beserta informasi kontak dan alamat
- Lihat riwayat pembelian per supplier
- Tambah, edit, dan hapus data supplier

### Karyawan
- Kelola daftar karyawan beserta nama, telepon, alamat, dan status pekerjaan
- Catat honor/kompensasi per karyawan dengan metode pembayaran fleksibel (harian, per jam, per item)
- Lihat riwayat honor dan rekap pembayaran per karyawan

### Pengaturan
- Keamanan berbasis PIN (aktifkan/nonaktifkan, PIN default: 123456)
- Pergantian tema Terang / Gelap yang tersimpan secara permanen

---

## Teknologi yang Digunakan

| Lapisan | Teknologi |
|---|---|
| Framework | Flutter (Dart SDK ^3.8.1) |
| State Management | Flutter Riverpod 2.6.1 |
| Backend / Database | Firebase Realtime Database 11.3.9 |
| Penyimpanan Lokal | Shared Preferences 2.5.3 |
| Grafik | FL Chart 1.0.0 |
| HTTP Client | Dio 5.8.0 / HTTP 1.4.0 |
| Internasionalisasi | Intl 0.20.2 (locale id_ID) |
| Animasi UI | Flutter Animate 4.5.2 / Shimmer 3.0.0 |
| Navigasi | Persistent Bottom Nav Bar 6.2.1 |
| Font & Ikon | Google Fonts 6.2.1 / Iconsax |
| Ekspor | Excel 4.0.6 |
| Enkripsi | Encrypt 5.0.3 |

---

## Struktur Proyek

```
handycraft-app/
├── lib/
│   ├── main.dart                         # Titik masuk aplikasi, inisialisasi Firebase
│   ├── firebase_options.dart             # Konfigurasi proyek Firebase
│   ├── core/
│   │   ├── constants/                    # Konstanta global aplikasi
│   │   ├── models/                       # Model data (10 model)
│   │   ├── providers/                    # Riverpod providers (12 provider)
│   │   ├── repository/                   # Repository CRUD Firebase (8 repo)
│   │   ├── extensions/                   # Ekstensi Dart helper
│   │   └── routes/                       # Definisi rute navigasi
│   ├── screens/                          # Lebih dari 34 layar UI
│   │   ├── splash_screen.dart
│   │   ├── pin_screen.dart
│   │   ├── dashboard/
│   │   ├── product/
│   │   ├── supplier/
│   │   ├── pelanggan/
│   │   ├── karyawan/
│   │   └── settings/
│   ├── widgets/                          # Widget kustom yang dapat digunakan ulang
│   └── mocks/                            # Data mock untuk pengembangan
├── assets/                               # Aset gambar dan ikon
├── android/ ios/ web/ windows/ macos/ linux/
├── pubspec.yaml
└── firebase.json
```

---

## Cara Memulai

### Prasyarat

- Flutter SDK >= 3.8.1
- Dart SDK ^3.8.1
- Proyek Firebase dengan Realtime Database yang sudah diaktifkan
- Android Studio / VS Code dengan plugin Flutter

### Instalasi

1. **Clone repositori**
   ```bash
   git clone https://github.com/your-username/handycraft-app.git
   cd handycraft-app
   ```

2. **Install dependensi**
   ```bash
   flutter pub get
   ```

3. **Konfigurasi Firebase**
   - Buat proyek Firebase di [console.firebase.google.com](https://console.firebase.google.com)
   - Aktifkan **Realtime Database**
   - Gunakan FlutterFire CLI untuk membuat `firebase_options.dart`:
     ```bash
     dart pub global activate flutterfire_cli
     flutterfire configure
     ```

4. **Jalankan aplikasi**
   ```bash
   flutter run
   ```

---

## Konfigurasi

### Aturan Firebase Database

Pastikan aturan Firebase Realtime Database mengizinkan operasi baca/tulis:

```json
{
  "rules": {
    ".read": true,
    ".write": true
  }
}
```

> Untuk produksi, ganti dengan aturan autentikasi yang sesuai.

### Locale

Aplikasi dikonfigurasi untuk **locale Indonesia (id_ID)**. Format tanggal dan mata uang mengikuti konvensi Indonesia. Untuk mengubah locale, perbarui `initializeDateFormatting` di `main.dart`.

### Keamanan PIN

- PIN default: `123456`
- PIN dapat diaktifkan atau dinonaktifkan dari layar Pengaturan
- Status PIN tersimpan menggunakan Shared Preferences

---

## Alur Aplikasi

```
Buka Aplikasi
    └── Splash Screen (jeda 2 detik)
            └── Layar PIN (jika PIN aktif)
                    └── Aplikasi Utama (Navigasi Bawah)
                            ├── Dashboard
                            │     ├── Tambah Penerimaan (penjualan produk)
                            │     ├── Tambah Penerimaan Lainnya (pemasukan lain)
                            │     ├── Tambah Pengeluaran (pembelian supplier)
                            │     ├── Tambah Pengeluaran Gaji (gaji karyawan)
                            │     └── Tambah Pengeluaran Lainnya (biaya lain)
                            ├── Produk
                            │     ├── Tambah / Edit Produk
                            │     └── Tambah / Edit Bahan Baku
                            ├── Supplier
                            │     ├── Tambah / Edit Supplier
                            │     └── Detail Supplier + Riwayat Pembelian
                            ├── Pelanggan
                            │     ├── Tambah / Edit Pelanggan
                            │     └── Detail Pelanggan + Riwayat Transaksi
                            ├── Karyawan
                            │     ├── Tambah / Edit Karyawan
                            │     ├── Tambah Honor (kompensasi)
                            │     └── Detail Karyawan + Riwayat Honor
                            └── Pengaturan
                                  ├── Aktifkan / Nonaktifkan PIN
                                  └── Ganti Tema Terang / Gelap
```
