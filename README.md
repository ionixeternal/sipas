<img alt="Screenshoot" src="https://github.com/ionixeternal/sipas/blob/master/docs/image/thumbnails.jpg">

## Aplikasi SIPAS - Sistem Infomasi Pengelolaan Arsip Surat

Aplikasi SIPAS merupakan kependekan dari Sistem Informasi Pengelolaan Arsip Surat yang bertujuan untuk mengelola Kearsipan Surat atau Dokumen lainnya. Fitur aplikasi ini cukup lengkap hingga memuat Notifikasi, Disposisi dan Upload File lebih dari satu, dengan tampilan GUI yang Modern serta kemudahaan dalam penggunaannya, aplikasi ini sangat cocok untuk Perusahaan ataupun Pribadi (Perseorangan).

_This needs **PHP 7.x, MySQL**_

## Instalasi Lokal

#### Dependensi
Anda mungkin membutuhkan Webserver seperti `XAMPP, AMPPS dan sejenisnya`. Buka aplikasi melalu Firefox, Chrome, Edge, Safari dan lainnya.

#### Lokal Webserver
- Buka file `sipas [app version].zip` dengan WinRAR atau ZIP
- Letakan folder `SIPAS dan .htacces` ke direktori htdocs atau www (Tergantung folder root Webserver)
- Buka `localhost/phpmyadmin` kemudian buat database dengan nama db_sipas dengan format char `utf8mb4_general_ci`
- Pilih IMPORT kemudian browse Databasenya di direktori` WEBSERVER ROOT FOLDER PATH.sipas/database/db_sipas.sql`, klik Go
- Buka url localhost / IP LAN Server untuk login kedalam Aplikasi

#### Hosting
- Buka file `sipas [app version].zip` dengan WinRAR atau ZIP kemudan masuk ke folder sipas/database. Ekstrak `db_sipas.sql` keluar dari ZIP
- Login CPanel lalu buka Database dan buat Database baru (Nama disesuaikan saja)
- Pilih Usernya dan `grant all access` ke Database yang baru dibuat
- Buka File Manajer kemudian masuk ke folder public_html (untuk base domain) atau ke subdomain (untuk sub domain)
- Pilih Upload lalu pilih `app.zip` tunggu hingga selesai mengupload
- Kembali kefolder tadi kemudian klik kanan `app.zip` dan ekstrak ke folder tersebut
- Setelah terekstrak masuk ke folder `sipas/application/config/database.php`
```
<?php
defined('BASEPATH') OR exit('No direct script access allowed');

$active_group = 'default';
$query_builder = TRUE;

$db['default'] = array(
	'dsn'	=> '',
	'hostname' => 'localhost',
	'username' => 'root',
	'password' => '',
	'database' => 'db_sipas',
	'dbdriver' => 'mysqli',
	'dbprefix' => '',
	'pconnect' => FALSE,
	'db_debug' => (ENVIRONMENT !== 'production'),
	'cache_on' => FALSE,
	'cachedir' => '',
	'char_set' => 'utf8',
	'dbcollat' => 'utf8_general_ci',
	'swap_pre' => '',
	'encrypt' => FALSE,
	'compress' => FALSE,
	'stricton' => FALSE,
	'failover' => array(),
	'save_queries' => TRUE
);
```
- Sesuaikan domain, nama database dan usernya lalu Simpan
- Buka url Base Domain / Sub Domain untuk login kedalam Aplikasi

## Fitur Aplikasi

#### Fitur
    - Dashboard
    - Kotak Masuk
    - Indeks Surat dan Klasifikasi Jabatan
    - Registrasi Surat Masuk dan Keluar
    - Disposisi Surat Masuk
    - Laporan Surat Masuk dan Keluar
    - Manajemen Hak Akses dan Pengguna
    - Pengaturan Aplikasi dan Backup Database

#### Fitur Unggulan
    - Realtime Notifikasi, Uploads dan Komentar (Layaknya sebuah Chatting)
    - Penggungahan Berkas lebih dari satu pada setiap Surat (Tansaksi)
    - Batasan Hak Akses dan Menu Dinamis [Tidak memiliki Akses = DENIED]
    - JQuery Validation
    - CRUD AJAX Serverside No Reload Page
    - Custom Bootstrap (Boostrap 3.x digabung dengan beberapa modul dari Bootstrap 4.x)
    - Custom Datatables (Tampilan Datatable dirubah menjadi halus dan responsif)

## Konfigurasi Aplikasi
- Login menggunakan akun `admin`
- Pilih menu Instansi / Badan usaha
```
Pada halaman Instansi / Badan usaha kami menyediakan pengaturan gambar yang akan digunakan dalam aplikasi beserta penjelasan penempatan gambar-gambar tersebut
```
- Pilih menu `Klasifikasi` dan tambahkan klasifikasi baru berdasarkan jabatan pada perusahaan
```
Klasifikasi ini merupakan pengelompokan jabatan, devisi atau bagian yang ada dalam perusahaan yang akan menjadi salah satu master data pada aplikasi
```
- Pilih menu `Kelola Hak Akses dan Pengguna`
```
Kelola hak akses dinamis dan pengguna aplikasi pada halaman ini, kami telah menyediakan 4 hak akses, yaitu pengguna, operator, pimpinan dan admin. anda juga dapat membuat pengguna baru
```
- Pilih menu `Indeks`
```
Mengindeks yaitu memberi kode atau kategori pada surat, biasanya indeks diambil berdasarkan perihal surat, hal ini berguna dalam pengelompokan surat untuk kepentingan arsip
```

## Alur Aplikasi

#### Surat Masuk
- Login menggunakan akun ber hak akses `Operator` atau `Administrator` kemudian pilih menu Registrasi `Surat Masuk` dan buat data baru
- Pada bagian `Aksi` pilih `Lihat Rincian` lalu Upload surat yang sudah di scan/gambar/word dan berikan komentar (Opsional)
- Kembali dan pada bagian `Aksi` lalu pilih `Teruskan`
- Login menggunakan akun ber hak akses `pimpinan` kemudian pilih menu Disposisi `Surat Masuk` dan ke bagian `Aksi` pilih `Lihat Rincian` untuk melihat deskripsi Surat, File dan menambahkan Komentar
- Kembali dan pada bagian `Aksi` lalu pilih `Disposisi`, setelah teredirect silakan klik `Tambah Disposisi` dan masukkan `Pengguna` yang akan menerima surat tersebut
- Login menggunakan akun ber hak akses `Pengguna` kemudian pilih menu `Kotak Masuk` klik pada surat yang belum terbaca untuk melihat deskripsi surat, File dan menambahkan komentar

#### Surat Keluar
- Login menggunakan akun ber hak akses `Operator` atau `Administrator` kemudian pilih menu Registrasi `Surat Keluar` dan buat data baru
- Pada bagian `Aksi` pilih `Lihat Rincian` lalu Upload surat yang sudah di scan/gambar/word dan berikan komentar (Opsional)

#### Mencetak Laporan
- Login menggunakan akun ber hak akses `Administrator` atau `Pimpinan` kemudian pilih menu Laporan `Surat Masuk` atau `Surat Keluar`
- Atur tanggal awal dan tanggal akhir lalu klik tampilkan, setelah muncul anda bisa mengklik tombol print

## Demo Aplikasi
Link Demo bisa anda buka di [SIPAS - Ionix Eternal Studio (Official Web)](http://sipas.ionixeternal.co.id/)

## Changelog
- SIPAS [v1.3](https://github.com/ionixeternal/sipas/blob/master/CHANGELOG.md) - (STABLE)
- SIPAS v1.2 - (Release Candidate)
- SIPAS v1.1 - (BETA)
- SIPAS v1.0 - (BETA)
