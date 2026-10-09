# Product Requirements Document (PRD)
## Project: Cafe Website Production-Grade Dataset & Design Architecture

**Version**: 1.0.0  
**Target Organization**: `anonimjra/cafe-website-data`  
**Architect**: Chief Systems Architect & Master Prompt Engineer  
**Status**: Ready for Production / Agent Integration  

---

## 1. Executive Summary & Problem Statement
Membangun website cafe modern sering kali terhambat oleh ketiadaan data riil yang terstruktur. Kebanyakan template website cafe hanya menyediakan data dummy dangkal ("Coffee 1", "Cake 1") tanpa memperhitungkan:
1. **Spesifikasi Specialty Coffee**: Tasting notes, beans origin, altitude, wash process, dan flavor wheels.
2. **Kebutuhan Pengunjung Nyata (WFC Culture)**: Indikator colokan listrik per meja, kecepatan Wi-Fi terverifikasi, ruangan ber-AC vs outdoor smoking, dan ketersediaan musholla.
3. **Konversi Bisnis**: Integrasi direct order WhatsApp dengan format pre-filled order string, link aggregator pesan antar (GoFood/GrabFood), dan sistem reservasi meja.

Dataset ini dirancang sebagai **Single Source of Truth (SSOT)** standar industri yang siap dikonsumsi langsung oleh Next.js, Tailwind CSS v4, mobile apps, atau agen AI (seperti Antigravity/Hermes) saat meng-generate website cafe komplit tanpa perlu mock data manual.

---

## 2. Goals & Success Metrics
* **G1 - 100% Type-Safe**: Semua dataset memiliki JSON Schema valid yang kompatibel dengan generator TypeScript types (`zod` atau `quicktype`).
* **G2 - Production-Ready Mocking**: Menyediakan katalog menu multi-kategori komplit, data outlet multi-cabang dengan atribut WFC, dan design token siap pakai.
* **G3 - Zero-Friction AI Consumption**: Format data berbasis `.json` dan `.md` bersih sehingga token-efficient saat dibaca oleh LLM/Agentic pair programmers.

---

## 3. Data Architecture & Specifications

### 3.1. Menu & Catalog Engine (`datasets/menu-items.json`)
Setiap item menu wajib memenuhi kriteria berikut:
* `id`: Slug unik URL-safe (e.g. `gayo-anaerobic-filter`).
* `category`: Kategori terdefinisi (`espresso`, `manual_brew`, `signature_coffee`, `artisan_tea`, `non_coffee`, `pastry_bakery`, `main_course`).
* `name`: Nama resmi produk.
* `description`: Copywriting deskriptif yang menjual.
* `price`: Harga dasar integer IDR.
* `tags`: Array tag (`best_seller`, `new_arrival`, `barista_pick`, `seasonal`).
* `dietary`: Object flags (`is_vegan`, `is_gluten_free`, `is_halal`, `allergens: []`).
* `customizations`: Varian suhu (`hot`/`iced`), opsi susu (`regular`, `oat`, `almond`, `soy`), sweetness level, extra espresso shot.
* `coffee_profile` *(Optional untuk kopi)*:
  * `beans_origin`: Asal daerah biji kopi.
  * `process`: Metode pasca panen (`washed`, `natural`, `honey`, `anaerobic`).
  * `roast_level`: `light`, `light_medium`, `medium`, `dark`.
  * `tasting_notes`: Array rasa (e.g. `["Bergamot", "Peach", "Black Tea"]`).
  * `radar_metrics`: Skor 1-5 untuk `acidity`, `sweetness`, `body`, `aroma`.

### 3.2. Outlets & Store Locator (`datasets/outlets-facilities.json`)
Data multi-cabang dengan fokus pengunjung WFC dan kumpul komunitas:
* `id`: Slug outlet (e.g. `senopati-flagship`).
* `name`: Nama cabang.
* `address`: Alamat lengkap + kota + kode pos.
* `coordinates`: Latitude dan Longitude akurat untuk mapping (Leaflet / Google Maps / Mapbox).
* `google_maps_url`: Direct URL ke pin lokasi.
* `operating_hours`: Jadwal buka/tutup harian (`monday_to_friday`, `saturday_to_sunday`) beserta status peak hours.
* `wfc_amenities`:
  * `wifi_speed_mbps`: Kecepatan download/upload teruji.
  * `power_sockets_ratio`: Estimasi soket listrik (e.g., `"High (Available at 80% tables)"`).
  * `seating_capacity`: Total kapasitas kursi.
  * `areas`: Daftar area (`indoor_ac_no_smoking`, `indoor_smoking_mezzanine`, `outdoor_garden`, `private_meeting_room`).
  * `prayer_room`: Ketersediaan musholla (`boolean` + detail fasilitas).
  * `parking`: Fasilitas parkir mobil & motor.
* `contact`: Nomor WhatsApp order khusus cabang & link delivery online.

### 3.3. Design Tokens & Visual Benchmarks (`datasets/design-tokens.json` & `benchmarks/`)
Preset visual untuk styling instan frontend:
* Tiga preset tema warna:
  1. *Artisan Minimalist (Earthy / Warm Oat & Espresso)*
  2. *Nordic Brutalist (Monochrome High Contrast)*
  3. *Japanese Modern Zen (Muted Sage & Sand)*
* Tipografi terkurasi: Heading serif editorial + body sans-serif geometris.
* Analisis benchmark dari website cafe kelas dunia: Blue Bottle Coffee, % Arabica, Fore Coffee, dan Ralph's Coffee.

---

## 4. Non-Functional Requirements
1. **Schema Validation**: Semua file JSON tervalidasi terhadap skema di folder `schemas/`.
2. **Git Version Control**: Terpusat pada branch `main` di repo `anonimjra/cafe-website-data`.
3. **No External Asset Broken Links**: URL gambar menggunakan CDN placeholder berkualitas tinggi (Unsplash curated coffee collections) dengan fallback.
