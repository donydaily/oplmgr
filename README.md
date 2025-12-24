# oplmgr

**oplmgr** adalah tool **CLI (Command Line Interface)** untuk Linux yang berfungsi sebagai **alternatif OPL Manager / USBUtil PS2** versi Windows.

Tool ini dibuat **native untuk Linux**, ringan, tanpa GUI, dan **100% kompatibel dengan OPL (Open PS2 Loader)** untuk penggunaan **USB / HDD eksternal**.

---

## ✨ Fitur Utama

* ✅ Convert **ISO → format OPL USB** (split otomatis)
* ✅ Deteksi **Game ID** akurat (SLUS / SLES / SCUS / SCES)
* ✅ Deteksi **CD / DVD otomatis**
* ✅ Generate, update & rebuild `ul.cfg`
* ✅ Rename judul game (metadata-safe)
* ✅ Download cover **ART otomatis**
* ✅ Verify game (cek part hilang / rusak)
* ✅ Extract / gabung ISO kembali
* ✅ Progress bar CLI (`pv`)
* ✅ Native OPL (tanpa USBUtil proprietary)

---

## 📂 Struktur Folder OPL

Setelah dikelola oleh `oplmgr`, struktur USB/HDD akan menjadi:

```
PS2USB/
├── DVD/
│   └── SLUS_203.12.Game_Name.iso.00
├── CD/
│   └── SCES_508.87.Game_Name.iso.00
├── ART/
│   └── SLUS_203.12.png
├── CFG/
├── VMC/
└── ul.cfg
```

Struktur ini **langsung terbaca oleh OPL** tanpa konfigurasi tambahan.

---

## 🧰 Dependency

### Wajib

* `bash`
* `coreutils`
* `util-linux`
* `awk`, `sed`, `grep`
* `pv` (progress bar)
* `p7zip` (deteksi Game ID dari ISO)
* `curl` (download ART)

### Install Dependency

#### Arch Linux / Manjaro

```bash
sudo pacman -S --needed bash coreutils util-linux awk sed grep pv p7zip curl
```

#### Ubuntu / Debian / Linux Mint

```bash
sudo apt update
sudo apt install -y bash coreutils util-linux gawk sed grep pv p7zip-full curl
```

#### Fedora

```bash
sudo dnf install -y bash coreutils util-linux gawk sed grep pv p7zip curl
```

---

## 🚀 Instalasi

### Manual

```bash
git clone https://github.com/USERNAME/oplmgr.git
cd oplmgr
chmod +x oplmgr.sh
sudo cp oplmgr.sh /usr/local/bin/oplmgr
```

Cek:

```bash
oplmgr --help
```

---

## 📖 Penggunaan

### 1️⃣ Scan USB / HDD

```bash
oplmgr scan
```

Menampilkan semua removable drive yang terdeteksi.

---

### 2️⃣ Inject ISO ke USB (Convert ISO → OPL)

```bash
oplmgr inject game.iso /run/media/$USER/PS2USB
```

✔ Split otomatis 1GB (FAT32 safe)
✔ Deteksi CD / DVD
✔ Update `ul.cfg`

---

### 3️⃣ List Game

```bash
oplmgr list /run/media/$USER/PS2USB
```

Output:

```
TYPE  GAME ID        SIZE     TITLE
DVD   SLUS_203.12    3.9G     God_of_War
```

---

### 4️⃣ Download Cover ART

```bash
oplmgr art /run/media/$USER/PS2USB
```

Cover akan tersimpan di folder `ART/`.

---

### 5️⃣ Rename Judul Game

```bash
oplmgr rename SLUS_203.12 "God of War II" /run/media/$USER/PS2USB
```

✔ Rename file
✔ Update `ul.cfg`
✔ Aman untuk OPL

---

### 6️⃣ Remove Game

```bash
oplmgr remove SLUS_203.12 /run/media/$USER/PS2USB
```

---

### 7️⃣ Verify Game

```bash
oplmgr verify /run/media/$USER/PS2USB
```

Mendeteksi:

* Part ISO hilang
* Split tidak lengkap

---

### 8️⃣ Extract ISO (Gabung kembali)

```bash
oplmgr extract SLUS_203.12 ~/ISO
```

---

### 9️⃣ Rebuild `ul.cfg`

```bash
oplmgr rebuild-ulcfg /run/media/$USER/PS2USB
```

Digunakan jika:

* Copy manual
* `ul.cfg` rusak

---

## 🎨 ART Source

Default source:

```
https://github.com/xlenore/ps2-covers
```

Bisa diganti di script:

```bash
ART_BASE_URL="https://server-kamu/ps2-art"
```

---

## ⚠️ Catatan Penting

* **Tidak perlu USBUtil Windows**
* OPL mendukung split ISO secara native
* Disarankan **FAT32** untuk USB
* Jangan jalankan sebagai `root`

---

## 🧪 Tested On

* Arch Linux (Hyprland)
* Linux Mint
* Ubuntu

---

## 🛣️ Roadmap

* [ ] FZF Interactive Menu (TUI)
* [ ] LAN / SMB OPL support
* [ ] PKGBUILD AUR
* [ ] Multiple ART type (ICON / BG / DISC)
* [ ] Config file (`oplmgr.conf`)

---

## 📜 Lisensi

MIT License

---

## 🙌 Credit

* Open PS2 Loader (OPL)
* xlenore – PS2 cover database

---

Happy gaming 🎮
