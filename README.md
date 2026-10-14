# Mind Map Interaktif & Laporan Proyek - OUTBREAK (2D Zombie Survival Shooter)

Repositori ini berisi visualisasi Mind Map interaktif berbasis web (HTML5, SVG, CSS, JS) dan dokumentasi laporan perkembangan untuk proyek game **OUTBREAK: 2D Zombie Survival Shooter** yang dikembangkan dengan Unity 6 LTS dan C#.

## 🌟 Fitur Utama Mind Map Web
- **⚡ Animasi Aliran Bio-Hazard (Flow Animation):** Jalur konektor SVG dengan efek aliran pulsa neon dinamis dan partikel energi bergerak dari node pusat *OUTBREAK* ke seluruh 6 fase dan 18 cabang node.
- **🖥️ Desktop Responsive & Centered:** Dilengkapi mesin *Pan & Zoom* interaktif (mouse drag & wheel scroll), *Fit to Screen* otomatis, tombol reset 1:1, dan *Mini-Map Radar HUD*.
- **📑 Detail 22 Node Interaktif:** Setiap node dapat diklik untuk menampilkan modal detail teknis, hierarki font TextMeshPro SDF, perbandingan statistik senjata, FSM AI zombie, dan hasil pengujian QA.
- **📖 Pembaca Laporan Lengkap:** Dokumen laporan resmi terintegrasi dengan 6 tab navigasi, diagram alur arsitektur game (SVG Flowchart), dan tombol cetak/ekspor PDF.
- **🔊 Procedural Audio SFX (Web Audio API):** Mensimulasikan efek suara synthesizer prosedural Unity C# game (950Hz UI click, 750Hz → 100Hz gunshot sweep).
- **🌓 Mode Tema & Pencarian Langsung:** Mendukung tema *Cyber Dark (Outbreak)* dan *Blueprint Light*, serta fitur pencarian instan (*live search*).

## 🚀 Cara Menjalankan
Cukup buka berkas [`index.html`](index.html) langsung di browser pilihan Anda (Google Chrome, Microsoft Edge, Mozilla Firefox, Opera, dll). Berkas bersifat *standalone* tanpa memerlukan dependensi server eksternal.

## 📂 Struktur Berkas
- `index.html`: Aplikasi web mind map interaktif utama dengan animasi, kontrol desktop, dan laporan lengkap.
- `Mind Map OUTBREAK – Mind Map OUTBREAK.html`: Berkas cadangan mind map versi standalone yang tersinkronisasi.
- `Detail_Konten_Mindmap_OUTBREAK.md`: Dokumentasi data konten teks untuk tiap node mind map.
- `Laporan_Perkembangan_Project_Game_2D_Zombie.md`: Laporan teknis lengkap arsitektur, siklus pengembangan, pengujian QA, dan roadmap game OUTBREAK.
