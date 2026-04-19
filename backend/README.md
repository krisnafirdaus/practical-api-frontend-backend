# Practical API: React + Laravel

Project ini memakai arsitektur terpisah:
- Backend: Laravel API di folder `backend`
- Frontend: React (Vite) di folder `frontend`

## Fitur
- CRUD Product dari React ke Laravel API
- Auth API berbasis Laravel Sanctum (register, login, me, logout)
- Endpoint API REST:
  - GET `/api/products`
  - POST `/api/products` (perlu token)
  - GET `/api/products/{id}`
  - PUT `/api/products/{id}` (perlu token)
  - DELETE `/api/products/{id}` (perlu token)
  - POST `/api/register`
  - POST `/api/login`
  - GET `/api/me` (perlu token)
  - POST `/api/logout` (perlu token)

## Struktur
- `app/Http/Controllers/ProductController.php` logic CRUD API
- `app/Models/Product.php` model product
- `database/migrations/*create_products_table.php` schema product
- `routes/api.php` route API resource product
- `../frontend/` aplikasi React

## Menjalankan Backend (Laravel)
1. Install dependency:

```bash
composer install
```

2. Buat database SQLite (jika belum ada):

```bash
touch database/database.sqlite
```

3. Jalankan migrasi:

```bash
php artisan migrate
```

4. Jalankan server Laravel:

```bash
php artisan serve
```

Backend akan jalan di `http://127.0.0.1:8000`.

## Menjalankan Frontend (React)
1. Masuk ke folder frontend:

```bash
cd ../frontend
```

2. Install dependency:

```bash
npm install
```

3. Jalankan dev server:

```bash
npm run dev
```

Frontend akan jalan di `http://localhost:5173`.

Catatan: Vite proxy sudah dikonfigurasi di `../frontend/vite.config.js` supaya request `/api/*` diteruskan ke backend Laravel.

## Validasi yang sudah dijalankan
- Build frontend sukses: `npm run build`
- Lint frontend sukses: `npm run lint`
- API route Laravel terdaftar: `php artisan route:list --path=api`
- Test backend sukses: `php artisan test`
