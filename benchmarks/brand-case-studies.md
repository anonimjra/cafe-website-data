# Studi Kasus Arsitektur Brand Cafe Terkemuka

Analisis komparatif terhadap strategi digital brand coffee terdepan global & regional.

---

## 1. Blue Bottle Coffee (USA / Japan)
* **Filosofi Desain**: *Ultra-minimalist, San Francisco tech meets Japanese kissaten.*
* **Karakteristik Visual**: Background putih bersih (`#FFFFFF`), aksen biru pastel ikonik (`#00A3E0`), font sans-serif presisi tinggi.
* **Fitur Kunci**:
  * Coffee Match Quiz (kuis interaktif memandu pemula memilih biji kopi sesuai preferensi rasa).
  * Roasting schedule real-time ("Roasted within 48 hours").
* **Insight untuk Dataset**: Wajib memiliki atribut `roast_level`, `process`, dan `tasting_notes`.

---

## 2. % Arabica (Kyoto / Global)
* **Filosofi Desain**: *"See the World Through Coffee" — Architectural & Global.*
* **Karakteristik Visual**: Monokromatik putih, marmer, dan kayu terang. Fotografi arsitektur toko menjadi elemen hero utama.
* **Fitur Kunci**:
  * Peta interaktif toko global yang menampilkan interior toko di Paris, Kyoto, New York, Bali, hingga Jakarta.
  * Navigasi super ringkas tanpa menu dropdown bertingkat.
* **Insight untuk Dataset**: Data outlet harus mencakup arsitektur & foto toko beresolusi tinggi, bukan sekadar peta pin Google Maps biasa.

---

## 3. Fore Coffee & Kopi Kenangan (Indonesia - App-First Model)
* **Filosofi Desain**: *Fast, frictionless, pick-up & delivery oriented.*
* **Fitur Kunci**:
  * Integrasi store nearest locator berbasis geolokasi browser.
  * Estimasi waktu penyiapan minuman (5-10 menit).
* **Insight untuk Dataset**: Diperlukan koordinat geolokasi akurat (`latitude`, `longitude`) dan integrasi multi-channel delivery (GoFood, GrabFood, WhatsApp).
