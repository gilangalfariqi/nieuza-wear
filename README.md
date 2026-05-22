# Nieuza Wear – Women’s Fashion Catalog

Sebuah web katalog fashion wanita modern berbasis **React + Vite** yang terhubung ke **Supabase** untuk menampilkan produk, mendukung pencarian & filter kategori, serta fitur cart/CTA melalui komponen UI.

> Nama aplikasi sesuai halaman utama: **“Nieuza Wear – Women’s Fashion Catalog”**.

---

## Fitur Utama

- **Catalog Produk** dengan layout responsive
- **Kategori & filter** (termasuk opsi **All** untuk menampilkan seluruh koleksi)
- **Pencarian** produk berdasarkan kata kunci
- **Product detail modal** (jika digunakan pada flow UI)
- **Cart / CTA** terintegrasi lewat context (mis. `CartContext`)
- **Arsitektur layered** (Domain / Use Case / Infrastructure / Presentation)
- **Tailwind CSS** untuk styling cepat dan konsisten

---

## Demo Preview (opsional)
Jika proyek ini dideploy, tuliskan URL demo di sini.

---

## Tech Stack

- **Frontend**: React 19, Vite
- **Styling**: Tailwind CSS
- **Data**: Supabase (`@supabase/supabase-js`)
- **State Management**: React Context
- **Tooling**: ESLint, PostCSS

---

## Struktur Proyek

Ringkasan folder utama:

- `src/components/` – komponen UI (Navbar, Footer, ProductCard, ProductGrid, modal, dll.)
- `src/pages/` – halaman (mis. `CatalogPage`)
- `src/context/` – state global (mis. `CartContext`, `ToastContext`)
- `src/domain/` – model, repository interface, dan use case
- `src/infrastructure/` – implementasi repository & client Supabase
- `src/presentation/` – hooks dan layer presentasi untuk akses use case
- `src/utils/` – utility (mis. integrasi WhatsApp)

---

## Prasyarat

- Node.js versi terbaru (disarankan LTS)
- Akun Supabase dan project database

---

## Setup Lokal

1) Install dependency

```bash
npm install
```

2) Jalankan development server

```bash
npm run dev
```

3) Build production

```bash
npm run build
```

4) Linting

```bash
npm run lint
```

---

## Environment Variables (Supabase)

Buat file **`.env`** di root project.

> Catatan: prefix yang biasanya dipakai untuk Vite adalah `VITE_`. Gunakan nama variabel sesuai implementasi di `src/infrastructure/api/supabaseClient.js`.

Contoh template:

```bash
# Supabase
VITE_SUPABASE_URL="https://YOUR_PROJECT_REF.supabase.co"
VITE_SUPABASE_ANON_KEY="YOUR_SUPABASE_ANON_KEY"
```

Jika project Anda memakai nama env lain, sesuaikan.

---

## Cara Kerja Fitur Katalog (Ringkas)

- Data produk diambil melalui repository Supabase.
- Use case mengatur logika akses data (mis. kategori `All` dan pencarian kosong).
- Hook presentasi mengirim data ke komponen UI.
- UI merender layout dan interaksi (filter, search, modal, CTA/cart).

Untuk detail debugging terkait “Semua Koleksi” dan memastikan tidak ada hidden limit, lihat dokumen:
- `.debug-product-fetching.md`

---

## Troubleshooting

### 1) “Semua Koleksi” tidak menampilkan seluruh produk
- Pastikan di Supabase semua produk yang diharapkan berstatus aktif/visible (sesuai filter yang dipakai query).
- Cek apakah repository melakukan `limit()`/`range()` (idealnya tidak untuk kasus “All”).
- Gunakan referensi log debug pada `.debug-product-fetching.md`.

### 2) Filter kategori “All” tidak konsisten
- Pastikan use case menangani input `All` / `all` dengan benar.
- Verifikasi bahwa filter kategori tidak memodifikasi query untuk kasus `All`.

---

## Deployment

Proyek ini cocok untuk deploy ke platform static/web hosting seperti Vercel.

Langkah umum:
1. Set environment variables sesuai bagian **Environment Variables**.
2. Gunakan command build standar:

```bash
npm run build
```

---

## Kontribusi

- Buat branch dari `main`
- Kirim PR dengan deskripsi singkat
- Jelaskan perubahan terkait UI, use case, atau query Supabase

---

## License

Proyek ini dirilis di bawah **MIT License**.

Lihat file: `LICENSE`.

---

## Catatan Aset

Pastikan aset gambar/icons (mis. di `public/` atau `src/assets/`) memiliki hak pakai yang sesuai. Jika menggunakan aset pihak ketiga, sertakan attribution/license yang relevan bila diperlukan.

