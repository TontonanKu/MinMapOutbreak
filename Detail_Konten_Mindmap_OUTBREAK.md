# PANDUAN DETAIL KONTEN INTERAKTIF MIND MAP PROYEK "OUTBREAK"
**Game Title:** OUTBREAK (2D Zombie Survival Shooter)  
**Dokumen Referensi:** Konten Detail Tiap Node Mind Map (Siap Salin / Klik)  
**Target Penggunaan:** Mind Map Interaktif (Miro / Whimsical / GitMind / Presentasi Dosen)

---

## 🧭 PUSAT (CORE NODE): OUTBREAK
- **Judul Game:** OUTBREAK
- **Genre:** 2D Top-Down / Isometric-feel Action Survival Shooter
- **Game Engine:** Unity 6 LTS (6000.3.24f1)
- **Bahasa Pemrograman:** C# (.NET Framework)
- **Platform:** PC Standalone (Windows) & Siap Porting ke Mobile (Android)
- **Resolusi Acuan:** 1920 x 1080 (Full HD, 16:9 Widescreen)
- **Status Proyek:** **Feature-Complete** (Loop permainan utuh dari Main Menu $\rightarrow$ Misi $\rightarrow$ Gameplay $\rightarrow$ Victory/Game Over $\rightarrow$ Reward Cash).

---

## 🟦 SISI KIRI 1: FASE 1 - FONDASI SISTEM

### 1. Node: Struktur Folder [6]
*Isi Pop-up / Penjelasan:*
Direktori game distandarisasi di bawah `Assets/_Project/` yang terbagi ke dalam **6 pilar utama** untuk memudahkan kolaborasi dan skalabilitas:
1. `Art/`: Seluruh aset visual 2D (Karakter, Senjata, Lingkungan kota, Background, Icon UI).
2. `Prefabs/`: Prefab siap pakai (Player hero, jenis Zombie, Proyektil Peluru, Drop Obat Darah).
3. `Scenes/`: `MainMenu.unity` (antarmuka awal & toko) dan `Gameplay.unity` (arena pertempuran).
4. `Scripts/`: Kode program C# terbagi modular (`Core/`, `Player/`, `Enemies/`, `Weapons/`, `Gameplay/`, `UI/`).
5. `Resources/`: Folder bawaan Unity untuk aset dinamis yang dijamin terbawa saat diexport ke APK/EXE (`Resources/UI/htp_heal.png`).
6. `Editor/`: Skrip utilitas internal Unity Editor (`GameDevHubWindow.cs`).

---

### 2. Node: Canvas 1920x1080 [16:9]
*Isi Pop-up / Penjelasan:*
- **Canvas Render Mode:** `Screen Space - Overlay`.
- **Canvas Scaler:** `Scale With Screen Size`.
- **Reference Resolution:** `1920 x 1080` piksel.
- **Screen Match Mode:** `Match Width Or Height` dengan slider **Match = 0.5** (memberikan proporsi seimbang saat aspect ratio layar bervariasi).
- **Keunggulan:** Menghilangkan bug UI gepeng, tombol meleset, atau elemen terpotong saat layar dimainkan pada monitor laptop, PC, maupun layar HP modern.

---

### 3. Node: Font Inter-Black SDF [SDF]
*Isi Pop-up / Penjelasan:*
- **Teknologi Font:** TextMeshPro (TMP) berbasis *Signed Distance Field (SDF)* yang digenerate dari `Inter-Black.ttf`.
- **Keunggulan SDF:** Teks tetap tajam (*ultra-crisp*) dan tidak pecah meski dizoom dari resolusi 720p hingga 4K UHD.
- **Hierarki & Standar Ukuran Font (Font Size Hierarchy):**
  - **Title / Header Layar:** `48 - 60 pt` (Contoh: "OUTBREAK", Judul Popup)
  - **Sub-Header / Tab:** `24 - 32 pt` (Contoh: "HEROES", "GUNS", "DAILY")
  - **Nama Misi & Tombol Utama:** `20 - 24 pt` (Contoh: "MISSION 1 - EASY", "RESUME", "RETRY")
  - **Statistik & Nilai Koin:** `16 - 18 pt` (Contoh: Saldo Cash "+100", Damage "25", HP "100")
  - **Teks Deskripsi / Tutorial:** `14 - 16 pt` (Contoh: Teks bantuan How To Play)
  - **Status Badge:** `11 - 12 pt` (Contoh: "[LOCKED]", "[EQUIPPED]")

---

## 🟩 SISI KIRI 2: FASE 2 - PLAYER & SENJATA

### 4. Node: Gerak 8 Arah [8]
*Isi Pop-up / Penjelasan:*
- **Input:** Unity New Input System (`Keyboard WASD / Arrow Keys`).
- **Kecepatan Gerak:** `3.5 - 4.5 unit/detik` (disesuaikan dengan atribut masing-masing hero).
- **Sumbu Isometrik 2.5D:** Pergerakan vertikal dikalikan faktor `0.4f` pada sumbu Y untuk menciptakan ilusi kedalaman ruang jalanan kota.
- **Rotasi Hadap (Sprite Flip):** Hero otomatis membalikkan arah badan (*Flip X*) secara instan berdasarkan arah gerak horizontal.
- **5 State Animasi:** `Idle`, `Walk`, `Attack`, `Hurt`, `Dead`.
- **Invulnerability Period:** Efek kebal selama `1.0 detik` dengan kedip merah 3 kali setelah terkena cakar zombie untuk mencegah kematian instan.

---

### 5. Node: Tembak Presisi [R]
*Isi Pop-up / Penjelasan:*
- **Sistem Bidik:** Arah moncong peluru melacak posisi mouse (`Camera.main.ScreenToWorldPoint`).
- **Muzzle Offset Presisi:** Posisi spawn peluru diatur tepat di ujung laras senjata hero (`x: ±0.95f, y: 1.15f`) relatif terhadap kaki hero, menjamin peluru keluar tepat dari moncong senjata di setiap arah hadap.
- **Mekanik Reload:**
  - Tombol manual: Tekan tombol **`R`**.
  - Reload otomatis: Aktif seketika saat peluru di magazen habis (`CurrentAmmo == 0`).
  - Durasi reload: `1.2 detik` jeda animasi sebelum amunisi terisi penuh kembali.

---

### 6. Node: 5 Jenis Senjata [5]
*Isi Pop-up / Penjelasan:*
Perbandingan statistik lengkap 5 senjata:

| Senjata | Damage | Kapasitas Peluru | Fire Rate | Harga Cash | Status Awal |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **Revolver** | 25 | 12 | 0.35s (Sedang) | **FREE** | Terbuka (Default) |
| **SMG** | 18 | 45 | 0.12s (Sangat Cepat) | 350 | Terkunci |
| **Shotgun** | 55 | 8 | 0.65s (Lambat/Area) | 700 | Terkunci |
| **Assault Rifle** | 32 | 35 | 0.18s (Cepat/Sakit) | 1,200 | Terkunci |
| **Sniper Rifle** | 95 | 8 | 0.90s (Sangat Fatal) | 2,000 | Terkunci |

---

## 🟧 SISI KIRI 3: FASE 3 - MUSUH & DROP

### 7. Node: AI Zombie [3]
*Isi Pop-up / Penjelasan:*
Menggunakan arsitektur Finite State Machine (FSM) 3 status:
1. **Chasing State:** AI melacak posisi hero di koordinat 2D dan bergerak mengejar (`MoveSpeed = 1.8 - 2.8f`).
2. **Attacking State:** Terpicu saat jarak dengan hero $\le 0.8\text{ unit}$, memicu animasi cakar dan mengurangi HP hero (Cooldown serang: `1.0 detik`, Damage: `15 - 25 HP`).
3. **Hurt & Death State:** Terpicu saat peluru mengenai hitbox zombie; zombie memutar animasi terkena hit dan mati saat HP habis.

---

### 8. Node: Spawner Gelombang [$\infty$]
*Isi Pop-up / Penjelasan:*
- **Radius Spawn Aman:** Zombie dimunculkan secara dinamis di luar area pandang kamera pemain (radius minimal $8\text{ unit}$, maksimal $14\text{ unit}$).
- **Skalabilitas:** Laju spawn bertambah cepat seiring banyaknya zombie yang dieliminasi, menciptakan tensi permainan yang semakin menegangkan.

---

### 9. Node: Health Drop Magnet [+]
*Isi Pop-up / Penjelasan:*
- **Drop Rate:** 25% peluang muncul saat zombie dieliminasi.
- **Efek Pemulihan:** Menambah `+25 HP` hero seketika saat disentuh.
- **Animasi Hovering:** Melayang lembut naik-turun menggunakan fungsi sinus matematika $\sin(t \times 3) \times 0.12\text{ unit}$.
- **Fitur Magnetis:** Jika HP hero belum penuh dan berada dalam radius $2.8\text{ unit}$, item obat otomatis tersedot dan meluncur ke arah hero dengan kecepatan $9\text{ unit/detik}$.
- **Proteksi Standalone Build:** Aset ikon tersimpan di `Assets/_Project/Resources/UI/htp_heal.png` sehingga tidak akan pernah hilang atau menjadi kotak putih saat game di-export.

---

## 🟪 SISI KANAN 1: FASE 4 - MENU UTAMA

### 10. Node: 5 Misi Berjenjang [5]
*Isi Pop-up / Penjelasan:*
Detail konfigurasi dan objektif 5 misi permainan:

| Misi | Tingkat | Objektif Utama | Durasi Waktu | Hadiah Cash | Status |
| :--- | :--- | :--- | :---: | :---: | :---: |
| **Misi 1** | EASY | Eliminasi 25 Zombie | Tanpa Batas | **+150 Cash** | Terbuka |
| **Misi 2** | NORMAL | Eliminasi 35 Zombie | Bertahan 60s | **+300 Cash** | Buka via Misi 1 |
| **Misi 3** | HARD | Eliminasi 50 Zombie | Bertahan 90s | **+500 Cash** | Buka via Misi 2 |
| **Misi 4** | EXPERT | Eliminasi 75 Zombie | Bertahan 120s | **+800 Cash** | Buka via Misi 3 |
| **Misi 5** | NIGHTMARE | Eliminasi 100 Zombie | Bertahan 180s | **+1,500 Cash** | Buka via Misi 4 |

*Sistem Kunci:* Misi 2 sampai 5 terkunci secara otomatis (`[LOCKED]`), dan baru terbuka secara bertahap saat pemain berhasil memenangkan misi sebelumnya.

---

### 11. Node: Heroes & Guns [3]
*Isi Pop-up / Penjelasan:*
- **3 Karakter Penyintas (Heroes):**
  1. **ALEKK:** HP 100, ATK 50, SPD 70 | Status: **Gratis (Default Hero)** | All-rounder.
  2. **ERIKA:** HP 120, ATK 75, SPD 60 | Harga: **500 Cash** | Penyerang Kuat.
  3. **HANK:** HP 160, ATK 90, SPD 45 | Harga: **1,000 Cash** | Tank Bertahan.
- **Proteksi Garis Bawah (`RectMask2D`):** Tinggi kartu hero dihitung matematis (`246px` per kartu) dan dikunci dengan komponen `RectMask2D` agar pas di dalam batas bingkai tanpa meluap keluar garis hitam bawah.

---

### 12. Node: Settings & Daily [7]
*Isi Pop-up / Penjelasan:*
- **Menu Settings:**
  - **Sound Switch:** On/Off efek suara tembakan, damage, dan klik UI.
  - **Music Switch:** On/Off alunan melodi latar belakang (BGM).
  - **HD Graphic Switch:** Mengubah profil render (`QualitySettings`) antara mode grafis tinggi (**60 FPS & VSync**) vs hemat daya (**30 FPS**).
  - **Vibration Switch:** Toggle efek getar.
- **Menu Daily (7 Hari Hadiah):**
  - Hari 1 s/d Hari 6: `+100 Cash` per hari.
  - Hari 7: `+1,000 Mega Cash Reward`.
  - Dilengkapi tombol **Back** yang menutup popup dan mensinkronisasi saldo cash secara real-time.

---

## 🟩 SISI KANAN 2: FASE 5 - HUD & PAUSE

### 13. Node: HUD In-Game [2]
*Isi Pop-up / Penjelasan:*
1. **HUD Status Pemain:** Health bar dinamis warna merah-hitam, teks sisa peluru / magazen maksimal, dan ikon senjata aktif yang berganti otomatis sesuai senjata yang dipilih.
2. **HUD Status Misi:** Badge misi di bagian atas layar (Kill counter untuk Misi 1, atau Timer mundur + Kill counter untuk Misi 2).

---

### 14. Node: Menu Pause [3]
*Isi Pop-up / Penjelasan:*
- Menjeda waktu permainan (`Time.timeScale = 0`).
- **Tata Letak 3 Tombol Simetris:**
  - **Kiri (`x: -115`):** `Btn_MainMenu` (Ikon Rumah $\rightarrow$ Kembali ke Menu Utama).
  - **Tengah (`x: 0`):** `Btn_Restart` (Ikon Repeat $\rightarrow$ Mengulang Misi Saat Ini).
  - **Kanan (`x: 115`):** `Btn_Resume` (Ikon Play $\rightarrow$ Melanjutkan Permainan).

---

### 15. Node: Victory & Game Over [2]
*Isi Pop-up / Penjelasan:*
1. **Victory Panel:** Muncul ketika syarat misi tercapai; menghitung koin hadiah, menyimpan pembukaan misi berikutnya di `PlayerPrefs`, dan menyediakan tombol lanjut misi berikutnya.
2. **Game Over Panel:** Muncul ketika hero kehabisan darah; menampilkan skor akhir dan tombol coba lagi (*Retry*).

---

## 🟥 SISI KANAN 3: FASE 6 - MESIN AUDIO

### 16. Node: AudioManager [1]
*Isi Pop-up / Penjelasan:*
- Arsitektur berbasis **Singleton Persistent** (`DontDestroyOnLoad`).
- Menangani 2 saluran audio independen: `bgmSource` (musik looping) dan `sfxSource` (suara tembakan/klik).
- Suara tidak terputus saat transisi perpindahan scene antar `MainMenu` dan `Gameplay`.

---

### 17. Node: Synth Prosedural [4]
*Isi Pop-up / Penjelasan:*
Menghasilkan suara jernih secara matematis via kode C# tanpa bergantung file eksternal yang rawan hilang:
1. **Click SFX:** Gelombang sinus frekuensi 950 Hz berdurasi 60ms (suara klik renyah).
2. **Gunshot SFX:** Perpaduan frequency sweep (750 Hz $\rightarrow$ 100 Hz) dan white noise berdurasi 180ms (suara tembakan bertenaga).
3. **Hurt & Death SFX:** Gelombang bass 220 Hz $\rightarrow$ 60 Hz dengan soft distortion (suara benturan kena cakar) dan melodi kekalahan.
4. **BGM Menu:** Melodi synth ambient 4-akord (C - Am - F - G) berdurasi 8 detik per loop yang menenangkan.

---

### 18. Node: Volume Dinormalisasi [.95]
*Isi Pop-up / Penjelasan:*
- Amplitudo dinaikkan ke level optimal: **0.95 pada efek suara (SFX)** dan **0.75 pada musik latar (BGM)**.
- Mengatasi bug suara terlalu pelan sehingga game terdengar tegas, jelas, dan seimbang pada volume normal komputer/laptop (20% - 30%).

---

## 🟨 KOTAK BAWAH (METADATA & ROADMAP)

### 19. Node: Teknologi
- Unity 6 LTS (6000.3.24f1)
- C# / .NET SDK
- Unity New Input System
- Unity UI (UGUI) & TextMeshPro (SDF)
- Singleton Pattern & PlayerPrefs Data Persistence
- Cross-Platform Ready (PC & Mobile Android)

### 20. Node: Hasil Pengujian
- **Build C# Assembly:** 0 Error (100% Sukses)
- **Build Editor Assembly:** 0 Error (100% Sukses)
- **Navigasi UI:** Transisi mulus antar 6 popup tanpa bug tumpang-tindih
- **Data Tersimpan:** Saldo koin dan misi terbuka tersimpan permanen
- **Rasio Layar:** Terkunci di Full HD 1920x1080 (16:9), bebas distorsi
- **Audio Sistem:** SFX & BGM berbunyi normal dan responsif terhadap switch settings

### 21. Node: Rencana Lanjutan
- Mekanisme klaim koin harian aktif (*Daily Claim System*)
- Partikel visual *Muzzle Flash* pada ujung senjata
- Teks angka damage melayang (*Floating Damage Numbers*)
- Kontrol sentuh *Virtual Joystick* untuk rilis Android
- Variasi musuh: *Fast Runner Zombie* dan *Tank/Boss Zombie*
