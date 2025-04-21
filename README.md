
# Hosting CodeIgniter 3 di Vercel

Panduan sederhana untuk menjalankan project **CodeIgniter 3** di platform **Vercel** menggunakan build pack `vercel-php`.

### 👁️ Preview
[https://codeigniter3-vercel.vercel.app/](https://codeigniter3-vercel.vercel.app/)

## 📁 Struktur Folder

```
.
├── api
│   └── index.php
├── application
├── system
├── user_guide
├── index.php
├── .htaccess
└── vercel.json

```

## 🔧 Konfigurasi

### 1. Buat Folder `api` dan File `api/index.php`

Isi file `api/index.php` dengan kode berikut:

```php
<?php 

// Forward vercel request to normal index.php
require __DIR__.'/../index.php';

```

### 2. Buat file `vercel.json`

Isi file `vercel.json` dengan kode berikut:

```json
{
	"version": 2,
	"builds": [
		{ "src": "/api/index.php", "use": "vercel-php@0.3.1" },
		{ "src": "/user_guide/**", "use": "@vercel/static" }
	],
    "routes": [
		{ "src": "/user_guide/(.*)", "dest": "/user_guide/$1/$2/" },
		{ "src": "/(.*)", "dest": "/api/index.php" }
	]
}

```

## 🚀 Deploy ke Vercel

   ### 1. Open `vercel.com`.
   ### 2. Create New Project.
   ### 3. `Deploy` Project.
   ### 4. Change Node js to version `18.x.x`.
   ### 4. `Redeploy` Project.

Kamu bisa memilih versi PHP dengan menyesuaikan versi `vercel-php` di file `vercel.json`. Berikut referensi versi:

`https://www.npmjs.com/package/vercel-php`

Build Pack       | Versi PHP |
| :-:            | :-:       |  
vercel-php@0.7.3 | PHP 8.3.x | 
vercel-php@0.6.2 | PHP 8.2.x |
vercel-php@0.5.5 | PHP 8.1.x | 
vercel-php@0.4.4 | PHP 8.0.x | 
vercel-php@0.3.6 | PHP 7.4.x | 

## 📚 Referensi
- **[CodeIgniter 3 Documentation](https://codeigniter.com/userguide3/)** 
- **[Vercel PHP](https://github.com/vercel-community/vercel-php)**
- **[Vercel Docs](https://vercel.com/docs)**
