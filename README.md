# 🎮 GameState and UI Framework for Unity

`GameSttate & UI Framework` adalah pustaka antarmuka pengguna modular yang dirancang untuk mempercepat pengembangan *vertical slice* game 2D. Framework ini mengusung arsitektur **Event-Driven** yang bersih, memisahkan logika UI dari logika *gameplay*, serta menyertakan alat otomasi (*Editor Tools*) untuk mempercepat alur kerja di Unity.

---

## 🏗️ Fitur Utama

* **Editor Automation:** Tambahkan Main Menu dan HUD fungsional ke dalam *scene* kosong hanya dengan satu klik via *Custom Editor Menu*.
* **State-Driven UI:** Komponen UI bereaksi secara otomatis terhadap perubahan status game (`MainMenu`, `Playing`, `Paused`, `GameOver`) melalui sistem *Event Observer*.
* **Performance Focused:** Transisi panel menggunakan `CanvasGroup` untuk performa optimal (mencegah lonjakan *layout recalculation*).
* **Modular & Decoupled:** Logika UI sepenuhnya terpisah dari sistem data *gameplay* (Gems, Ammo, Health), sehingga framework ini bersifat universal untuk game apa pun.

---

## 🛠️ Alur Kerja Sistem (Under the Hood)

Sistem ini dirancang untuk menghindari *spaghetti code* dengan alur komunikasi satu arah.



1. **State Provider:** `GameManager` memancarkan ( *broadcast* ) event perubahan status (`GameState`) ke semua *listener*.
2. **UI Observer:** `GenericUIManager` menerima event tersebut dan secara otomatis mengaktifkan/menonaktifkan panel yang relevan (Pause/GameOver).
3. **Decoupled Logic:** `PlayerHUD` mengelola data spesifik game (Health/Ammo) secara terpisah, sehingga framework UI ini bisa kamu pindahkan ke proyek lain tanpa membawa skrip spesifik game jam-mu.

## 🚀 Cara Instalasi & Penggunaan

### Instalasi
1. Unduh paket `.unitypackage` dari repositori ini.
2. Impor ke dalam proyek Unity milikmu.
3. Pastikan `GameManager` (dengan sistem `GameState` berbasis `Action`) sudah ada di dalam *scene* atau sebagai *Global Singleton*.

### Penggunaan (Editor Tools)
Setelah diimpor, kamu akan melihat menu baru **"GameSeed Tools"** di deretan menu atas Unity:
* **Generate Main Menu:** Membuat *Canvas* Main Menu yang sudah terhubung dengan logika transisi dan tombol Start/Quit.
* **Generate In-Game UI:** Membuat *HUD* dan *Pause Panel* yang siap dipasang di *scene gameplay*.

### Struktur Pustaka
```text
Assets/GameStatePlugin/
├── Editor/              # Skrip otomasi (Custom Editor Tools)
├── Resources/           # Prefab UI siap pakai (Main Menu, HUD, Pause Panel)
├── Scripts/             # Logika UI Modular (GenericUIManager, PlayerHUD)
└── README.md            # Dokumentasi ini
