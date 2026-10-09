# Benchmark Tren Website Cafe Modern & Standar UX 2026

Dokumen ini merangkum pola desain, perilaku interaksi pengguna (UX), dan arsitektur visual yang menjadi pembeda antara website cafe kelas dunia vs website cafe generik.

---

## 1. Komponen UX Wajib (*High-Converting Patterns*)

### A. The "WFC Ready" Matrix
Pengunjung cafe di kota besar (Jakarta, Bali, Tokyo, dsb.) sering mencari cafe spesifik untuk *Work From Cafe*. Website modern tidak menyembunyikan fasilitas di paragraf panjang, melainkan menampilkan panel ringkas di bawah tiap outlet:
* Badge Wi-Fi terverifikasi (`150 Mbps`).
* Rasio soket daya (`Tersedia di 85% meja`).
* Indikator area merokok vs AC hening.
* Keberadaan musholla / ruang sholat.

### B. Flavor Wheel & Radar Chart Interaktif
Specialty coffee memiliki jargon teknis yang membingungkan orang awam (anaerobic, acidity, body). Website cafe top dunia mengonversi metrik ini ke visual:
* Grafik radar 4 sumbu: **Acidity**, **Sweetness**, **Body**, **Aroma**.
* Badge tasting notes dengan warna asosiasi (misal: *Strawberry* warna merah muda, *Bergamot* warna jingga cerah).

### C. Direct-to-WhatsApp Checkout Link Generator
Daripada memaksa pengguna checkout via cart e-commerce yang rumit untuk pesanan takeaway lokal, website cafe sukses menyediakan tombol:
> **"Pesan via WhatsApp (Pilih Outlet)"**

Formula encoding string URL WhatsApp:
```
https://wa.me/6281234567890?text=Halo%20Kroma%20Coffee%2C%20saya%20mau%20pesan%3A%0A-%201x%20Gayo%20Anaerobic%20Filter%20(Iced)%0A-%201x%20French%20Butter%20Croissant%0AAmbil%20di%20cabang%3A%20Senopati
```

---

## 2. Pola Visual & Animasi (Modern Front-End)
* **Hero Ambient Loop**: Video latar micro-loop (slow pour V60 atau crema espresso mengalir) dengan overlay gelap 30-40% untuk menjaga keterbacaan teks.
* **Sticky Category Navigation**: Header kategori menu (`Espresso`, `Filter`, `Signature`, `Pastry`) yang menempel di bagian atas saat scrolling dengan efek scrollspy.
* **Image Micro-zoom on Hover**: Card makanan dengan transisi gambar halus (`transition-transform duration-500 ease-out hover:scale-105`).
