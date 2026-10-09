# ☕ Cafe Website Production-Grade Dataset & Design Architecture

[![License: MIT](https://img.shields.io/badge/License-MIT-amber.svg)](https://opensource.org/licenses/MIT)
[![Schema: JSON Schema Draft-07](https://img.shields.io/badge/Schema-Draft--07-blue.svg)](http://json-schema.org/draft-07/schema#)
[![Next.js & Tailwind Ready](https://img.shields.io/badge/Ready-Next.js%20%26%20Tailwind%20v4-black.svg)](https://nextjs.org/)

Kumpulan dataset terstruktur, JSON schema tervalidasi, design token, dan dokumentasi benchmark untuk membangun website cafe / specialty coffee kelas dunia. Siap dikonsumsi langsung oleh aplikasi **Next.js**, **React**, **Tailwind CSS v4**, maupun agen AI (**Antigravity**, **Hermes**, dsb.) tanpa perlu membuat mock data manual.

---

## 📂 Struktur Direktori

```text
cafe-website-data/
├── PRD.md                            # Product Requirements Document & arsitektur sistem
├── README.md                         # Dokumentasi & panduan integrasi
├── schemas/                          # Definisi JSON Schema (Draft-07)
│   ├── menu.schema.json              # Validasi katalog menu & coffee profile
│   ├── outlet.schema.json            # Validasi lokasi outlet & fasilitas WFC
│   └── design-tokens.schema.json     # Validasi tema warna & tipografi
├── datasets/                         # Data riil siap pakai (JSON)
│   ├── menu-items.json               # 11+ item menu terperinci (Espresso, Filter, Pastry, Mains)
│   ├── outlets-facilities.json       # 3 cabang flagship (Jakarta, BSD, Bali) + metadata WFC
│   └── design-tokens.json            # 3 preset tema warna & typography pairings
└── benchmarks/                       # Studi kasus & riset UI/UX
    ├── visual-trends-2026.md         # Standar komponen web cafe modern
    └── brand-case-studies.md         # Analisis Blue Bottle, % Arabica, Fore Coffee
```

---

## ⚡ Cara Pakai di Project Next.js (App Router)

### 1. Import Langsung Dataset JSON
```typescript
// app/menu/page.tsx
import menuData from '@/datasets/menu-items.json';

export default function MenuPage() {
  return (
    <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
      {menuData.items.map((item) => (
        <div key={item.id} className="p-4 rounded-xl border border-stone-200">
          <img src={item.image_url} alt={item.name} className="w-full h-48 object-cover rounded-lg" />
          <h3 className="text-xl font-bold mt-3">{item.name}</h3>
          <p className="text-stone-600 text-sm">{item.description}</p>
          <div className="mt-4 flex justify-between items-center font-semibold">
            <span>Rp {item.price.toLocaleString('id-ID')}</span>
            {item.coffee_profile && (
              <span className="text-xs bg-amber-100 text-amber-800 px-2 py-1 rounded">
                {item.coffee_profile.roast_level.toUpperCase()}
              </span>
            )}
          </div>
        </div>
      ))}
    </div>
  );
}
```

### 2. Gunakan Design Tokens di Tailwind CSS v4
Theme tokens di `datasets/design-tokens.json` dapat langsung dipetakan ke variabel CSS:
```css
/* app/globals.css */
@import "tailwindcss";

:root {
  --color-primary: #3E2723;
  --color-secondary: #8D6E63;
  --color-background: #FDFBF7;
  --color-surface: #F4EFEA;
  --color-accent: #C47C35;
}
```

---

## 🎯 Mengapa Dataset Ini Berbeda?
1. **Specialty Coffee Authenticity**: Menyertakan detail origin biji kopi, metode proses pasca-panen (anaerobic, washed), elevasi tanam (masl), tasting notes, dan metrik radar (acidity, sweetness, body, aroma).
2. **Kebutuhan Komunitas & WFC**: Metadata cabang memuat kecepatan Wi-Fi teruji (Mbps), ketersediaan colokan per meja, musholla AC, dan jenis tempat duduk.
3. **Konversi Bisnis Terpadu**: Dilengkapi format link direct order WhatsApp per cabang dan link delivery online (GoFood & GrabFood).

---

## 👤 Maintainer
Dikembangkan dan dimaintain oleh **[@anonimjra](https://github.com/anonimjra)**.
