# Tugas-kelompok5
# Proyek Komputer Grafik : kelompok 5
Proyek ini dibuat untuk memenuhi komponen penilaian Tugas Kelompok (Bobot 40%) pada mata kuliah Komputer Grafik. Kami memilih untuk membuat Game 2D yang bergenre "Endless Runner" yang menerapkan 3 materi utama yaitu, tranformasi, clipping, dan Anti aliasing.

---

## 👥 Anggota Kelompok 
- Muhammad alif septian
- Muhammad Rifki
- Muhammad Dimas Rizky Awaludin
- Rio reyfandi
- Ruli sulistiana
- Samiza Kautsar


---

## 📝 Latar Belakang Pemilihan Game

Kami memilih game bergenre **Endless Runner** karna terinspirasi dari *Dino Chrome*  karena game ini memiliki struktur logika yang dinamis namun tetap sederhana untuk diimplementasikan dari nol (*scratch*) tanpa menggunakan *game engine* atau bahasa pemrogramanan yang kompleks. 

Selain itu, mekanik dari *Endless Runner* sangat ideal dan relevan untuk mendemonstrasikan 3  materi utama dalam mata kuliah Komputer grafik, yaitu:
1. **Transformasi Objek:** Manipulasi posisi elemen game secara *real-time*.
2. **Clipping Efektif:** Manajemen memori terhadap objek yang keluar dari ruang pandang (*viewport*).
3. **Anti-Aliasing:** Pengaturan kualitas visual objek geometris agar terlihat halus pada layar digital.

---

## 🚀 Penerapan Bab Materi

Game ini secara murni mengimplementasikan 3 bab materi perkuliahan, yaitu:

### 1. Transformasi (2D Transformation)
* **Translasi:** Digunakan pada rintangan (*obstacles*) dan koin untuk menggeser posisinya secara konstan dari koordinat kanan layar menuju kiri layar ($X_{\text{baru}} = X_{\text{lama}} - \text{kecepatan}$).
* **Rotasi:** Diterapkan pada objek koin melayang menggunakan matriks perputaran sudut ($\theta$) lokal dengan memanfaatkan fungsi `ctx.rotate()`, sehingga koin terlihat berputar pada porosnya saat game berjalan.

### 2. Clipping/Viewing (Otomatis)
* Proyek ini menerapkan **Screen Bounding Box Clipping**. Setiap objek rintangan atau koin yang bergerak melewati batas koordinat kiri layar ($X < 0$) akan otomatis dipotong dan dihapus dari *array* memori utama menggunakan fungsi `.splice()`. 
* Hal ini mencegah terjadinya kebocoran memori (*memory leak*) sehingga performa *rendering* aplikasi tetap stabil dan ringan.

### 3. Anti-Aliasing
* Objek karakter utama dan koin digambar menggunakan bentuk lingkaran sempurna (`ctx.arc()`) yang memanfaatkan fitur *sub-pixel smoothing* bawaan browser. 
* Kami juga menambahkan efek *Soft Glow/Blur* pada tepi objek untuk mematikan efek piksel berundak (*jaggies*), sehingga menghasilkan visual lekukan yang halus dan nyaman dilihat.

---

## 🎮 Cara Menjalankan Game

Game ini dibuat menggunakan teknologi **HTML5 Canvas dan JavaScript **, sehingga tidak memerlukan proses instalasi atau *library* tambahan yang berat.

1. **Unduh/Clone Repository:** Download seluruh berkas kode proyek ini.
2. **Buka File:** Cari file bernama `game.html` (atau `index.html`).
3. **Jalankan:** Klik dua kali file tersebut untuk membukanya di browser pilihan Anda (direkomendasikan menggunakan Google Chrome, Mozilla Firefox, atau Microsoft Edge versi terbaru).
4. **Kontrol Permainan:** * Tekan tombol **SPASI (Spacebar)** pada keyboard untuk membuat karakter melompat menghindari rintangan.
   * Jika game over, tekan kembali tombol **SPASI** untuk mengulang permainan.

----
## 🧑‍💻Penjelasan Source Code

Berikut adalah penjelasan source code yang terkait dengan 3 materi perkuliahan

1. `<canvas id="gameCanvas" width="700" height="300"></canvas>`
code ini digunakan untuk membuat canvas yang digunakan untuk tampilan game

2. `let score = 0;
let isGameOver = false;
let gameSpeed = 5;
let obstacles = [];
let coins = [];`
code ini berfungsi sebagai menyimpan data pada game, dalam game ini terdapat score, jika pada saat permainan itu mendapatkan score makan score itu akan tersimpan kedalam data secara otomatis.

3. `window.addEventListener("keydown", (e) => {`digunakan sebagai interaksi antara game dan controller, ketika kita klik spasi maka game akan otomatis memulai

4. `obstacles.push({
    x: canvas.width + 20,` digunakan untuk membuat obstacle, rintangan yang muncul di luar sisi kanan canvas.

5. `function spawnCoin()` Membuat coin yang akan muncul pada sisi canvas yang berfungsi sebagai score

6. `ctx.shadowBlur = 15;`ini adalah anti aliasing yang digunakan untuk memperhalus objek yang bergerigi

7. `obs.x -= gameSpeed;` ini adalah transformasi, yang digunakan untuk memindahkan objek di setiap frame

8. `if (obs.x + obs.width < 0)` `obstacles.splice(i,1);`ini adalah clipping, yang digunakan menghapus obstcale keluar dari layar sebelah kiri
