# Tokosaya — Proyek Berjalan Bab 1–8

Implementasi referensi proyek **Tokosaya** untuk mata kuliah *Frontend Development &
Web Design*, semester III.

> **Belanja Tepat, Kirim Cepat** — toko online UMKM peralatan kerja digital.

Folder ini adalah teman-jalan `tokosaya-css/` yang disebut sepanjang Bab 1–7 di
bahan ajar `../buku/`. Ia berisi kode yang **sudah dijalankan dan diukur**, bukan
potongan contoh di dalam teks — sesuatu yang `../REVISI-CASUAL.md` catat belum ada
di repo ini.

## Batasan proyek

| | |
|---|---|
| Teknologi | HTML5 + CSS3 murni |
| JavaScript | **tidak ada sama sekali** |
| Framework | **tidak ada** (Bootstrap baru masuk Bab 9, di proyek lain) |
| Dependensi runtime | nol — hanya Google Fonts via HTTPS |
| Berkas | 6 halaman HTML, 2 berkas CSS, 10 berkas SVG |

## Cara membuka

Klik dua kali `index.html`. Tidak perlu server: semua tautan relatif dan font
diambil dari HTTPS, jadi membukanya lewat `file://` sudah cukup.

Kalau kamu ingin menyajikannya lewat HTTP (misalnya untuk mengukur di DevTools
atau berbagi ke perangkat lain di jaringan lokal):

```bash
cd tokosaya-css
python3 -m http.server 8765
# lalu buka http://127.0.0.1:8765/index.html
```

## Peta berkas ke bab asal

Setiap berkas bisa ditelusuri balik ke bab yang membangunnya.

| Berkas | Bab asal | Catatan |
|---|---|---|
| `index.html` | Bab 6 (struktur final) + Bab 2 (semantik) | hero + 8 kartu `flex-wrap`; hero dipindah ke dalam `<main>` |
| `katalog.html` | Bab 7 (`.katalog-grid`) + Bab 2 | 8 kartu `grid`, 1/2/3/4 kolom pada <576/576/992/1200 px |
| `produk.html` | **tanpa rujukan bab** | dijanjikan Bab 4, disebut Bab 7 & Bab 15.1, tapi tak pernah dispesifikasikan |
| `tentang.html` | Bab 2 (isi) + Bab 6 (kerangka `site-nav`) | profil, visi-misi, nilai (`dl`), kunjungi |
| `kontak.html` | Bab 2 (form 3 kolom) + Bab 6 (kerangka nav) | ditambah `required` + `autocomplete` |
| `admin.html` | Bab 7 (disalin apa adanya) | `.dasbor` grid 4 area, 4 stat card, tabel 5 pesanan |
| `css/style.css` | Bab 4 · Bab 3–5 · Bab 6 · Bab 7 | token → dasar → komponen → katalog → responsif |
| `css/admin.css` | Bab 7 (disalin apa adanya) | hanya aturan panel admin; satu tambahan perbaikan cacat |
| `img/logo-tokosaya.svg` | Bab 2 | dipakai sebagai favicon seluruh halaman |
| `img/hero-tokosaya.svg` | Bab 2 | digambar ulang (lihat "Penyimpangan" #6) |
| `img/produk-*.svg` (8 berkas) | Bab 5–6 (konvensi nama) | siluet digambar sendiri, palet token Bab 4 |

Di dalam `css/style.css` dan `css/admin.css`, setiap blok diberi penanda babnya —
`/* ===== Bab 6 — KARTU PRODUK ===== */` — jadi kamu bisa membaca CSS-nya berdampingan
dengan bahan ajarnya. Blok yang tidak berasal dari bab mana pun ditandai
`tanpa rujukan bab` supaya tidak ada CSS yang lahir tanpa jejak.

## Delapan produk baku

Data di bawah disalin dari Bab 5 dan dipakai konsisten di seluruh halaman.
Jumlahnya cocok dengan kartu "Produk Aktif = 8" pada dashboard admin.

| Kode | Nama | Kategori | Harga | Badge |
|---|---|---|---|---|
| KX-210 | Keyboard Mekanis KX-210 | Aksesori Input | Rp650.000 | Best Seller |
| MW-88 | Mouse Wireless MW-88 | Aksesori Input | Rp185.000 | Tersedia |
| HS-15 | Headphone Studio HS-15 | Audio | Rp425.000 | Tersedia |
| MR-241 | Monitor IPS 24&#8243; MR-241 | Layar | Rp1.899.000 | Best Seller |
| FD-64 | Flash Drive 64GB FD-64 | Penyimpanan | Rp95.000 | Tersedia |
| CP-30 | Charger Cepat 30W CP-30 | Daya | Rp120.000 | Tersedia |
| BT-5 | Speaker Bluetooth BT-5 | Audio | Rp285.000 | Stok Terbatas |
| WC-720 | Webcam HD WC-720 | Video | Rp310.000 | Baru |

Rekap: **8 produk**, **6 kategori**, **2 Best Seller** (KX-210, MR-241),
**1 Stok Terbatas** (BT-5), **1 Baru** (WC-720).

> Catatan: tugas Bab 5 menyebut "Kategori **7**". Data aktualnya hanya **6**
> kategori berbeda. Angka lain pada tugas yang sama (8 produk, 2 Best Seller,
> 1 Stok Terbatas) cocok persis — jadi hanya angka kategori itu yang menyimpang.

## Token desain

Blok `:root` di `css/style.css` disalin persis dari Bab 4. Jangan menambah warna
kedua yang mirip; ubah di sini dan seluruh antarmuka ikut berubah.

```css
:root {
  --clr-primary: #4F46E5;      /* indigo — tombol & link utama */
  --clr-primary-dark: #4338CA;
  --clr-accent: #F59E0B;       /* amber — badge & sorotan */
  --clr-dark: #1E293B;         /* heading & teks tegas */
  --clr-body: #334155;         /* teks paragraf */
  --clr-bg: #F8FAFC;           /* latar halaman */
  --clr-surface: #FFFFFF;      /* kartu & panel */
  --clr-border: #E2E8F0;
  --clr-success: #16A34A;
  --clr-danger: #DC2626;
  --font-heading: 'Poppins', sans-serif;
  --font-body: 'Inter', sans-serif;
  --radius: 12px;
  --shadow-card: 0 8px 24px rgba(15, 23, 42, 0.08);
  --space-unit: 8px;           /* basis skala jarak 8/16/24/32/48/64 */
}
```

Breakpoint yang dipakai konsisten: **576 / 768 / 992 / 1200 px**, semuanya
`min-width` (mobile-first) mengikuti Bab 7.

## Konvensi penamaan kelas

Pola `blok-elemen`, kebab-case, huruf kecil — sesuai Bab 15.3.

| Kelompok | Contoh |
|---|---|
| Navigasi situs | `site-header`, `site-nav`, `site-nav-brand`, `site-nav-toggle`, `site-nav-burger`, `site-nav-menu`, `site-nav-link-aktif`, `site-nav-keranjang` |
| Hero | `hero`, `hero-title`, `hero-subtitle`, `hero-cta`, `hero-gambar` |
| Kartu produk | `produk-card`, `produk-gambar`, `produk-flag` + `produk-flag-best/tersedia/stok/baru`, `produk-card-nama/kategori/harga/deskripsi`, `produk-card-tautan` |
| Katalog | `katalog`, `katalog-judul`, `katalog-intro`, `katalog-grid` |
| Halaman dalam | `seksi`, `seksi-tajuk`, `blok`, `breadcrumb` |
| Detail produk | `produk-detail`, `produk-detail-media/info/nama/kategori/harga`, `produk-beli`, `spesifikasi` |
| Form & tombol | `form-kontak`, `kolom-form`, `label-form`, `input-form`, `tombol`, `tombol-primer` |
| Panel admin | `dasbor`, `dasbor-header/nav/main/footer`, `dasbor-tautan`, `stat-kartu`, `tabel-scroll`, `status-lunas/diproses/dikirim` |

## Navigasi responsif

Nav punya breakpoint sendiri, **768 px**, terpisah dari breakpoint konten
(576/992/1200). Alasannya terukur, bukan selera: satu baris nav butuh **~644 px**
— merek 101 + menu 310 + keranjang 137 + dua celah 48 + padding 48. Di bawah itu
nav melipat dan tombol keranjang terlempar sendirian ke baris berikutnya.

| | < 768 px | >= 768 px |
|---|---|---|
| Tombol buka-tutup | tampil (hamburger) | sembunyi |
| Menu | panel melayang di bawah header | mendatar, selalu tampil |
| Tinggi header | **73 px** — sama saat tertutup maupun terbuka | 75 px |
| Baris nav | 1 | 1 |

Mekanismenya murni CSS, tanpa JavaScript:

1. `<input type="checkbox" class="site-nav-toggle" id="nav-toggle">` yang
disembunyikan secara visual tetapi **tetap bisa difokus keyboard**.
2. `<label class="site-nav-burger" for="nav-toggle">` yang jadi tombolnya. Ikon
tiga garisnya digambar dengan satu `::before` + `box-shadow`, jadi tidak perlu
berkas ikon atau font ikon.
3. Panel dikendalikan pemilih saudara `.site-nav-toggle:checked ~ .site-nav-menu`.

Tiga keputusan yang membuatnya tidak sekadar jalan:

- **Panel diposisikan `absolute`** (`top: 100%`, `left: 0`, `right: 0`) sehingga
  keluar dari alur flex. Kalau panel dibiarkan ikut alur, ia mendorong tombol
  keranjang — yang ada sesudahnya di DOM — ke baris ketiga dan header melonjak
  dari 73 px ke **325 px** setiap kali dibuka. Sebagai panel melayang, tinggi
  header tidak berubah: nol pergeseran tata letak.
- **Urutan DOM: merek → toggle → burger → menu → keranjang.** Urutan ini membuat
  urutan fokus keyboard sama dengan urutan visual, *dan* membuat desktop tampil
  persis seperti rancangan Bab 6 (menu dulu, keranjang di ujung kanan). Tidak ada
  properti `order` di mana pun.
- **Menu tertutup memakai `display: none`**, bukan sekadar disembunyikan. Itu
  sekaligus mengeluarkan keempat tautan dari urutan fokus, sehingga pengguna
  keyboard tidak tersesat ke tautan yang tak terlihat.

Tidak ada `aria-expanded`: CSS murni tidak bisa menyinkronkan nilainya, sementara
status `checked` kotak centang selalu benar dan diumumkan sendiri oleh pembaca
layar. Kotak centangnya diberi `aria-label="Menu navigasi"`, dan cincin fokusnya
digambar di label lewat `.site-nav-toggle:focus-visible ~ .site-nav-burger`.

## Ketika isi buku saling bertentangan

Buku kadang memberi dua atau tiga versi untuk komponen yang sama. Aturan yang
dipakai di sini: **bab terakhir yang membahas topik itu menang** (bab berikutnya
memang sengaja menimpa bab sebelumnya — prinsip kaskade Bab 3).

| Topik | Versi bab awal | Versi bab akhir | Yang dipakai |
|---|---|---|---|
| Komponen kartu produk | Bab 5 (`.produk-media` + badge absolute + `.produk-body`) | Bab 6 (`img.produk-gambar` + `.produk-flag` pill, kartu ber-`padding`) | Kartu **Bab 6** |
| Nama kelas field kartu | Bab 5 (`.produk-nama`, `.produk-harga`) | Bab 7 (`.produk-card-nama`, `.produk-card-harga`) | Nama **Bab 7** |
| Gambar di dalam kartu | Bab 6 (`height: 140px; object-fit: cover` — memotong gambar) | Bab 7 (`width: 100%; height: auto`) | **Bab 7** |
| Tautan tombol keranjang | Bab 2 (`href="index.html"` + komentar) | Bab 6 (`href="#"`) | **`index.html`** + komentar (# gagal uji "nol tautan mati") |
| Badge "Best Seller" | Bab 5 (amber + teks `--clr-dark`) | Bab 6 (amber + teks putih) | Teks **Bab 5** (putih di atas amber hanya 2,2:1) |
| Posisi hero terhadap `<main>` | Bab 5 ("`main` berisi dua `section`: hero dan produk") | Bab 6 (hero di luar `main`) | Hero **di dalam `<main>`** |

## Penyimpangan yang disengaja

Sebelas butir di bawah ini keluar dari salinan apa adanya. Semuanya tercatat di
komentar kode, dan tidak satu pun mengubah tampilan tanpa alasan yang bisa diukur.

1. **Nama kelas field kartu memakai Bab 7**, sementara struktur kartunya tetap
   Bab 6 — dua bab itu menamai empat field yang sama dengan nama berbeda.
2. **`width: 100%; height: auto`** pada gambar kartu (Bab 7) menggantikan
   `height: 140px; object-fit: cover` (Bab 6) yang memotong siluet produk; makin
   lebar sel grid, makin dalam potongannya.
3. **Hero dipindah ke dalam `<main>`** mengikuti Bab 2 (main = isi utama) dan
   Bab 5 ("main berisi dua section: hero dan produk"). Bab 6 menaruhnya di luar.
4. **Judul seksi beranda "Produk Unggulan"** (label Bab 5) bukan "Katalog Produk"
   (label Bab 6) — supaya tidak sama persis dengan judul halaman katalog.
5. **Tautan keranjang `href="index.html"` disertai komentar**, bukan `href="#"`.
   `#` adalah tautan tanpa tujuan dan akan gagal pada uji "nol tautan mati".
6. **`img/hero-tokosaya.svg` digambar ulang tanpa teks.** Versi Bab 2 adalah panel
   berisi tulisan "Peralatan Kerja Digital" dan "Keyboard · Mouse · Monitor" —
   yang persis mengulang `h1` dan `hero-subtitle`, jadi hanya akan jadi duplikat.
7. **Logo dan ilustrasi hero benar-benar dipakai.** Bab 6 mengganti merek nav jadi
   teks dan hero-nya tanpa gambar, sehingga kedua aset Bab 2 jadi tak terpakai.
   Di sini logo dipakai sebagai favicon dan ilustrasi hero diletakkan di dalam
   `.hero` (yang sudah `flex-direction: column`, jadi nol perubahan struktur).
8. **`.produk-flag-best` memakai teks `--clr-dark` di atas amber** (pasangan
   Bab 5), bukan putih. Putih di atas amber hanya 2,2:1 — jauh di bawah WCAG AA.
9. **Lapisan responsif mobile-first** (jarak dan padding dikecilkan di bawah
   576 px) ditambahkan di akhir `style.css`. Bab 6 dan 7 menulis nilai penuh;
   tanpa lapisan ini kartu di 375 px hanya selebar 250 px dan menyisakan ruang
   kosong di kanannya.
10. **`min-height: 40px` pada tautan nav** supaya kriteria terukur Bab 7 ("area
    sentuh paling kurang 40 piksel") benar-benar terpenuhi.
11. **`.dasbor > * { min-width: 0 }` di `admin.css`** — perbaikan cacat nyata,
    lihat temuan F-01 di bawah.
12. **Navigasi berganti ke hamburger CSS-only di bawah 768 px**, menyimpang dari
    Bab 6 yang menganjurkan `flex-wrap` dan dari Bab 10:115 yang justru menolak
    trik kotak centang. Alasannya terukur, bukan estetika: `flex-wrap` apa adanya
    menempatkan nav di **3 baris / 195 px** pada 375 px dan **4 baris / 259 px**
    pada 320 px, dengan tombol keranjang menggantung sendirian — sebab satu baris
    nav butuh ~644 px. Lihat temuan F-11.
13. **`.site-nav-kanan` dihapus** dari markup dan CSS. Pembungkus itu ada di Bab 6
    untuk mengelompokkan menu + keranjang dengan jarak 24 px. Supaya hamburger
    bisa menaruh keranjang di baris pertama sementara menu turun ke panel, menu
    dan keranjang harus jadi anak langsung `.site-nav`; jarak 24 px di layar lebar
    sekarang dijaga `column-gap` pada `.site-nav`.

Kelas yang **tidak berasal dari bab mana pun** dan murni tambahan proyek:
`.seksi`, `.seksi-tajuk`, `.blok`, `.breadcrumb`, seluruh kelompok `.produk-detail*`,
`.spesifikasi`, `.produk-beli`, `.input-jumlah`, `.hero-gambar`, `.produk-card-tautan`,
`.form-kontak`, `.kolom-form`, `.label-form`, `.input-form`, `.tombol`,
`.tombol-primer`. Semuanya ditandai di dalam CSS.

## Hasil verifikasi

Diukur pada Chromium headless lewat Playwright. Dua matriks: **6 halaman × 10 lebar
uji** (320 / 360 / 375 / 414 / 480 / 576 / 640 / 768 / 992 / 1200 px) = 60
kombinasi, dan **5 halaman × 8 lebar mobile** (320–767 px) dengan menu nav
**terbuka** = 40 kombinasi.

| Pemeriksaan | Kriteria | Hasil |
|---|---|---|
| Gulir horizontal, nav tertutup | `scrollWidth <= clientWidth` (Bab 7) | **60/60 lulus** |
| Gulir horizontal, menu **terbuka** | idem | **40/40 lulus** |
| Tinggi header & jumlah baris nav | tidak ada item menggantung di baris sendiri | **73 px konstan** di 320–767 px (tertutup *dan* terbuka); 75 px di >= 768 px. Satu baris di semua lebar |
| Menu tertutup & urutan fokus | tautan tersembunyi di luar urutan Tab | **0/4 terjangkau Tab** saat tertutup, **4/4** saat terbuka |
| Buka-tutup tanpa JavaScript | klik label **dan** tombol spasi | **lulus** di kelima halaman, kedua arah |
| Cincin fokus hamburger | terlihat saat kotak centang difokus | `solid 3px rgb(79, 70, 229)` |
| Tautan internal | setiap `href` menunjuk berkas yang ada | **6 tujuan unik, nol tautan mati** |
| Tautan `#` tanpa tujuan | tidak ada | **nol** |
| Area sentuh tautan nav | >= 40 px (Bab 7) | **lulus** — minimum 40 px (hamburger 40 px, admin 44 px) |
| Gambar termuat | `naturalWidth > 0` | **21/21 termuat** (index 9, katalog 8, produk 4), nol `alt` hilang |
| Tinggi kartu per baris | selisih <= satu baris teks (Bab 7) | **selisih 0 px** di setiap baris |
| Kolom grid katalog | 1 / 2 / 3 / 4 pada <576/576/992/1200 | **lulus**; 1200 px = 4 kolom × 2 baris |
| Urutan heading | satu `h1`, tidak melompat | **6/6 lulus** |
| Font web termuat | Poppins + Inter aktif | **lulus** (`document.fonts.check`) |
| Teks terpotong | `scrollWidth <= clientWidth` per elemen | **nol** di 375 px dan 1200 px |
| Validasi HTML | `html-validate` v8 | **0 galat** |
| Kontras WCAG AA | 4,5:1 normal / 3:1 teks besar | **14 gagal** — lihat F-02 |

### Temuan

| ID | Halaman | Temuan | Severitas | Status |
|---|---|---|---|---|
| F-01 | `admin.html` | Gulir horizontal di 375/576/768 px. Keempat area `.dasbor` adalah grid item dengan `min-width: auto`, jadi kolom `1fr` tidak bisa menyusut di bawah min-content isinya: tabel (`min-width: 640px` + padding 48 = 690 px) lalu baris chip nav (642 px) memaksa `<body>` menggulir. **Bab 7 justru mengklaim cacat ini tidak ada.** | Kritis | Diperbaiki (`.dasbor > * { min-width: 0 }`) |
| F-11 | semua halaman | Navigasi utama **tidak responsif**: dengan `flex-wrap` Bab 6 apa adanya, nav menempati **3 baris / 195 px** pada 375 px dan **4 baris / 259 px** pada 320 px — tombol keranjang menggantung sendirian di baris terakhir, dan header memakan ~26% tinggi layar. Sebabnya satu baris nav butuh ~644 px, sedangkan 375 px hanya menyediakan 343 px. **Verifikasi saya yang pertama melewatkannya**: yang diukur hanya `scrollWidth` dan tinggi tautan (>= 40 px), dan keduanya lulus meski nav berantakan. | Kritis | Diperbaiki (hamburger CSS-only + panel melayang; header kini 73 px konstan) |
| F-02 | index, katalog, produk, admin | Teks badge di atas `--clr-success` = **3,30:1** (10 kemunculan); `.status-diproses` amber di atas putih = **2,15:1**, `.status-lunas` = 3,30:1 (4 kemunculan). Semuanya pasangan warna dari Bab 5/6/7 sendiri. | Mayor | **Terbuka** |
| F-03 | `produk.html` | Halaman ini dijanjikan Bab 4, disebut Bab 7 sebagai output UTS, dan dideskripsikan Bab 15.1 — tetapi tidak pernah dibangun di Bab 1–7, sehingga tautan "Lihat Detail" tidak punya tujuan. | Mayor | Diperbaiki (halaman dibangun) |
| F-04 | semua kartu produk | Buku memberi **tiga dialek kelas** untuk komponen kartu yang sama (Bab 5, Bab 6, Bab 7), dan Bab 7 membatalkan namanya sendiri di komentar ("kelas `produk-card`, badge, dan harga tetap dari Bab 4-6"). | Mayor | Diselesaikan (aturan bab terakhir menang) |
| F-05 | `kontak.html` | Form Bab 2 tidak memuat `required` maupun `autocomplete`, padahal checklist Form Bab 15.1 menuntut keduanya. | Minor | Diperbaiki |
| F-06 | `tentang.html`, `kontak.html` | Nomor telepon memakai spasi dan tanda hubung biasa, sehingga bisa patah baris (aturan `tel-non-breaking`). | Minor | Diperbaiki (`&nbsp;` + `&#8209;`) |
| F-07 | `admin.html` | Tautan nav "Pesanan" menunjuk `admin.html` sendiri. Bukan tautan rusak, tetapi tidak menuju ke apa pun yang berbeda. | Minor | **Dibiarkan** sesuai kode buku |
| F-08 | `admin.html` | Ketidakcocokan tanggal: header data "6 Oktober 2025" sementara footer "© 2026". | Minor | **Dibiarkan** sesuai kode buku |
| F-09 | tugas Bab 5 | Menyebut "Kategori 7" padahal data produk hanya punya 6 kategori berbeda. | Minor | Dilaporkan, tidak diubah |
| F-10 | `index.html` | Bab 6 menaruh `.hero` — termasuk satu-satunya `h1` — di luar `<main>`, sehingga konten utama berada di luar landmark main. | Minor | Diperbaiki |

**F-02 sengaja dibiarkan terbuka.** Memperbaikinya menuntut warna di luar token
Bab 4: teks putih di atas `--clr-success` (3,30:1) dan teks `--clr-dark` di atasnya
(4,44:1) **dua-duanya** gagal ambang 4,5:1, jadi tidak ada pasangan yang sudah ada
di buku yang lulus. Ini justru bahan latihan yang tepat untuk Bab 13 (aksesibilitas)
dan Bab 15 (audit QA): temuan ini bisa langsung disalin ke `laporan-temuan.html`.

### Catatan cakupan verifikasi

- Verifikasi bersifat **terukur (geometri DOM, kaskade, dan kontras terhitung)**,
  bukan berbasis piksel. Tangkapan layar diambil sebagai bukti untuk diperiksa
  manusia, tetapi **belum diperiksa secara visual**.
- **Pelajaran dari temuan F-11:** matriks uji pertama hanya mengukur `scrollWidth`
  dan tinggi tautan. Keduanya lulus sementara nav tetap berantakan 3 baris, karena
  tidak ada satu pun pemeriksaan yang mengukur *jumlah baris nav* atau *tinggi
  header*. Kedua ukuran itu kini masuk matriks. Pelajaran umumnya: menguji sifat
  yang mudah diukur (lebar, tinggi elemen) tidak sama dengan menguji perilaku yang
  dimaksud.
- Peramban yang diuji: **Chromium** (mesin Playwright). Uji lintas-peramban di
  Firefox dan WebKit belum dijalankan.
- Pembaca layar belum diuji langsung; penilaian aksesibilitas terbatas pada
  struktur (heading, `alt`, `label for`/`id`, area sentuh, urutan fokus, status
  kotak centang) dan kontras terhitung.
- `admin.html` memakai nav panel sendiri (`.dasbor-nav`, chip mendatar yang bisa
  digulir) sesuai spesifikasi Bab 7 — bukan hamburger. Belum diukur terhadap
  matriks baris nav di atas karena memang pola yang berbeda.
