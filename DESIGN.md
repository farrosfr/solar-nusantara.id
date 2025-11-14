# Design

## Rute (Routes)

Rute utama adalah halaman index. Berdasarkan navigasi, siapkan juga rute-rute berikut (bisa sebagai *stubs* awal):

```md
/
/tentang
/layanan
/produk
/pintar
/berita
/kontak
```

Astro akan menangani rute-rute ini berdasarkan file di dalam `src/pages/`. Contoh:

* `src/pages/index.astro` (Halaman ini)
* `src/pages/about.astro` (Untuk `/tentang`)
* `src/pages/news/index.astro` (Untuk `/berita`)
* `src/pages/news/[...slug].astro` (Untuk detail artikel berita)

-----

## Komponen (Components)

Berikut adalah pemecahan komponen yang bisa dibuat di `src/components/` untuk membangun halaman `index.astro`:

### 1\. Layout Global

* **`Layout.astro`**: Komponen layout utama. Isinya mencakup tag `<head>` (dengan SEO, font, dan metadata), serta memanggil komponen `Header` dan `Footer`.
* **`Header.astro`**: Komponen *wrapper* untuk navigasi.
  * **`HeaderTop.astro`**: Bagian atas header (Logo, Search, Info Kontak, Tombol "SonusHUB").
  * **`Navbar.astro`**: Menu navigasi utama (Beranda, Tentang Kami, Layanan, Produk, dll.) termasuk logika *dropdown*.
  * **`MobileHeader.astro`**: Versi *mobile* dari header (Logo, Ikon Search, Ikon Menu "Hamburger").
* **`Footer.astro`**: Komponen footer lengkap.
  * Isinya: Logo, info kontak (Telepon, Alamat, Email), gambar ISO, ikon media sosial, dan menu navigasi footer.
  * **`Copyright.astro`**: Baris teks *copyright* dan kredit developer di bagian paling bawah.

### 2\. Komponen Halaman (Page Components)

Ini adalah komponen-komponen spesifik yang akan dipanggil di dalam `src/pages/index.astro`:

* **`HeroSlider.astro`**:

  * **Deskripsi**: *Slideshow* utama di bagian atas halaman.
  * **Konten**: Gambar *background*, judul (e.g., "Solar Nusantara"), deskripsi (e.g., "ENERGI BARU INDONESIA"), dan tombol *call-to-action* (e.g., "About Us").

* **`AboutIntro.astro`**:

  * **Deskripsi**: Sesi perkenalan singkat "Tentang kami".
  * **Konten**: Judul (e.g., "Solar-Nusantara.ID - Mewujudkan Energi Terbarukan...") dan paragraf deskripsi.

* **`StatsGrid.astro`**:

  * **Deskripsi**: Menampilkan data/statistik dalam bentuk grid. Dibagi per kategori (Energi Terbarukan, Manajemen Energi, Energi Biomassa).
  * **Konten**: Menggunakan *sub-komponen* `StatItem.astro` (ikon, angka *counter*, dan judul statistik seperti "Proyek yang sedang Berjalan", "Perkiraan kWh").

* **`NewsSection.astro`**:

  * **Deskripsi**: Menampilkan "informasi terbaru".
  * **Konten**: Judul seksi dan grid/list dari `NewsItem.astro`.
  * **`NewsItem.astro`**: Komponen *card* untuk satu artikel (Gambar, Judul, Tanggal, Deskripsi singkat, Tombol "Baca Selengkapnya").

* **`Benefits.astro`**:

  * **Deskripsi**: Sesi "Mari kita bicarakan tentang manfaatnya."
  * **Konten**: Grid yang berisi *icon box* (Ikon, Judul, Deskripsi singkat) seperti "Membantu Lingkungan", "Lebih Menghemat Uang Anda".

* **`ServiceHighlight.astro`**:

  * **Deskripsi**: Sesi khusus untuk "Platform SonusHUB".
  * **Konten**: Layout 2 kolom (Gambar di kiri, Teks di kanan: Judul, Deskripsi, Tombol).

* **`ServiceCarousel.astro`**:

  * **Deskripsi**: *Carousel* untuk "Layanan Kami".
  * **Konten**: *Slider* yang berisi *card* layanan (e.g., "Solar PV EPC", "Manajemen Energi", "PINTAR") dengan deskripsi dan tombol.

* **`ProductCarousel.astro`**:

  * **Deskripsi**: *Carousel* untuk "Produk Kami".
  * **Konten**: *Slider* yang berisi *card* produk (e.g., "Impor Panel", "Panel TKDN", "SPKL") dengan deskripsi dan tombol.

* **`VideoSection.astro`**:

  * **Deskripsi**: Sesi untuk menampilkan video YouTube.
  * **Konten**: *Player* video dengan gambar *overlay* dan tombol *play*.

* **`FlipBoxGrid.astro`**:

  * **Deskripsi**: Grid berisi 3 kotak yang bisa di-*flip*.
  * **Konten**: Komponen *flip box* (Sisi depan: Ikon, Judul, Deskripsi singkat. Sisi belakang: Tombol *link*).
