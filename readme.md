<div align="center">

# Auth Backend

Aplikasi ini dirancang untuk menangani proses autentikasi termasuk login, registrasi, dan pengecekan middleware autentikasi. Pengguna harus login untuk melihat dan memperbarui profil mereka.

</div>

# Getting Started
### Install Dependencies
```bash
  npm install
```

### Run Development
```bash
  npm run dev
```

### Run Server 
```bash
  npm start
```


<br>
<br>
<br>

## List API

### Autentikasi
- **POST /api/auth/register**: Mendaftarkan pengguna baru.
- **POST /api/auth/login**: Login pengguna yang sudah ada.
- **POST /api/auth/logout**: Logout pengguna saat ini.

### Profil Pengguna
- **GET /api/user/**: Mengambil profil pengguna yang sudah login.
- **PUT /api/user/**: Memperbarui profil pengguna yang sudah login.

### Middleware
- **authMiddleware**: Memastikan bahwa pengguna sudah diautentikasi sebelum mengakses rute tertentu.

## JWT Authentication

Aplikasi ini menggunakan JWT (JSON Web Token) untuk autentikasi. JWT adalah standar terbuka yang memungkinkan informasi aman dikirimkan sebagai objek JSON.

### Mengapa Menggunakan JWT?
- **Keamanan**: Data yang dikirimkan aman dan tidak dapat diubah oleh pihak ketiga.
- **Stateless**: Tidak memerlukan penyimpanan sesi di server, mengurangi beban server.
- **Fleksibilitas**: Dapat digunakan di berbagai platform dan bahasa pemrograman.

### Public Key dan Secret Key
JWT ditandatangani menggunakan public key dan secret key. Public key untuk memverifikasi token, secret key untuk menandatangani token. Kunci-kunci ini harus disimpan dengan aman.

Contoh kunci yang digunakan:
- **SECRET_PRIVATE**: Kunci privat untuk menandatangani token.
- **SECRET_PUBLIC**: Kunci publik untuk memverifikasi token.

Dengan JWT, hanya pengguna terautentikasi yang dapat mengakses sumber daya yang dilindungi.





<br>

## Automigration

Aplikasi ini menggunakan automigration untuk membuat tabel di database secara otomatis jika belum ada. Berikut adalah contoh kode untuk membuat tabel `users`:

```javascript
(async () => {
  try {
    db.execute(`
      CREATE TABLE IF NOT EXISTS users (
        id INT AUTO_INCREMENT PRIMARY KEY,
        username VARCHAR(255) UNIQUE,
        email VARCHAR(255) UNIQUE,
        password VARCHAR(255),
        created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
        updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
      );
    `);

    console.log('Tables created successfully!');
  } catch (err) {
    console.error('Error creating tables:', err.message);
  }
})();
```

Kode di atas akan membuat tabel `users` dengan kolom `id`, `username`, `email`, `password`, `created_at`, dan `updated_at`. Jika tabel sudah ada, maka kode ini tidak akan membuat tabel baru.

<br>
<br>


# List Modules

### 1. Api
    Melakukan request api ke service lain
    - contoh penamaan file:  `transaction.api.js`

### 2. Config
    Untuk konfigurasi seperti konfigurasi koneksi ke database

### 3. Controllers
    Mengelola HTTP request dan response
    - contoh penamaan file:  `user.controller.js`

### 4. Helpers
    Function-function pembantu untuk digunakan di berbagai file

### 5. Models
    Berisi logika langsung ke database yang nantinya bisa digunakan di berbagai file
    - contoh penamaan file:  `user.model.js`

### 6. Routers
    Mengarahkan routing HTTP ke controller. Memiliki index untuk mengarahkan ke router yang lebih spesifik
    - contoh penamaan file:  `user.router.js`

### 7. Service
    Logika bisnis utama untuk mengelola request dan data dari database
    - contoh penamaan file:  `user.service.js`

### 8. Validators
    Validasi request body menggunakan zod yang nantinya bisa digunakan di beberapa file controller
    - contoh penamaan file:  `user.validator.js`

<br>
<br>
<br>

# List Rules
  - Menggunakan single-quote
  - Prefer penggunaan const apabila varibel tersebut tidak di ubah lagi
  - .env tanpa menggunakan quote '' / "" 
  - Untuk kode menggunakan `camelCase` dan untuk request, response dan route url menggunakan `snake_case`

<br>
<br>
<br>

# Extensions VS-Code
### 1. Prettier
    Atur untuk penggunaan prettier dengan auto-save dan pengaturan yang sudah ada

### 2. Better Align
    Untuk meratakan titik dua atau samadengan
  - cara  kombinasi dengan prettir => `Ctrl + A`, `Ctrl + S`, `Alt + A`

### 3. Eslint
    Membuat standard code

