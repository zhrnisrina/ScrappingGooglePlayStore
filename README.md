# Proyek Scraping Data Aplikasi Google Play Store

## 🔍 Deskripsi Proyek

Proyek ini bertujuan untuk mengumpulkan data aplikasi dari **Google Play Store** secara **otomatis dan sistematis**, berdasarkan kata kunci kategori aplikasi. Data yang diperoleh mencakup informasi penting seperti nama aplikasi, developer, kategori, rating, jumlah unduhan, harga, dan deskripsi.

## 🗝️ Penentuan Kata Kunci

Scraping dilakukan berdasarkan kata kunci kategori aplikasi yang mencerminkan berbagai jenis aplikasi di Google Play Store. Contoh kata kunci yang digunakan meliputi:

* **Top Free**
* **Top Paid**
* **Game**
* **Health & Fitness**
* **Finance**
* **Game Puzzle**
* **Family**

Pemilihan kata kunci ini bertujuan untuk memperoleh **data yang representatif dan komprehensif** dari berbagai kategori aplikasi.

## 🎯 Tujuan Proyek

Data yang dikumpulkan digunakan untuk:

* Menganalisis distribusi aplikasi berdasarkan kategori dan developer.
* Menilai kualitas dan popularitas aplikasi berdasarkan rating dan jumlah unduhan.
* Mengidentifikasi potensi risiko melalui aplikasi populer yang memiliki rating rendah.
* Memberikan insight bermanfaat bagi developer, analis pasar, investor, dan peneliti.

## 🛠️ Metode Scraping

Scraping dilakukan menggunakan kombinasi Python dan R:

* **Modul**: [`google_play_scraper`](https://github.com/JoMingyu/google-play-scraper) (Python)
* **Integrasi**: Paket `reticulate` di R
* **Database**: MongoDB (untuk penyimpanan dan pengolahan data)

### Tahapan Scraping:

1. **Pencarian aplikasi** berdasarkan kata kunci kategori, dengan batas maksimal **50 aplikasi per kategori** untuk menjaga efisiensi.
2. **Pengambilan detail aplikasi** seperti rating, jumlah review, ukuran, harga, dan deskripsi.
3. **Pembersihan data** dari nilai kosong dan standarisasi format data.
4. **Penyimpanan ke database MongoDB**.

## 👥 Target Audiens

Proyek ini dirancang untuk memberikan manfaat bagi:

* **Developer & Product Manager**: Memahami posisi dan performa aplikasi mereka di pasar.
* **Investor & Analis Pasar**: Menilai tren aplikasi dan potensi risiko pasar.
* **Akademisi & Peneliti**: Melakukan studi kuantitatif tentang ekosistem aplikasi mobile.
* **Tim Pemasaran & Strategi Bisnis**: Mendapat insight perilaku pengguna dan kategori aplikasi populer.

## 📊 Insight Menarik dari Proyek

* 📌 **Kategori dengan jumlah aplikasi terbanyak** → Mengindikasikan area dengan persaingan tinggi.
* 🏆 **Developer dengan total unduhan terbesar** → Pemain utama di ekosistem aplikasi.
* 📈 **Hubungan antara rating dan jumlah unduhan** → Mengukur pengaruh kualitas terhadap popularitas.
* ⚠️ **Aplikasi dengan unduhan tinggi tapi rating rendah** → Sinyal risiko buruknya pengalaman pengguna.
* 🧭 **Perbandingan rating & popularitas antar kategori** → Mengetahui kategori yang paling disukai pengguna.

## 📂 Struktur Data yang Dikumpulkan

| Kolom         | Deskripsi                      |
| ------------- | ------------------------------ |
| `app_name`    | Nama aplikasi                  |
| `developer`   | Nama pengembang aplikasi       |
| `category`    | Kategori aplikasi              |
| `rating`      | Nilai rating (1-5)             |
| `installs`    | Jumlah unduhan                 |
| `price`       | Harga aplikasi (jika berbayar) |
| `description` | Deskripsi aplikasi             |
| `size`        | Ukuran file aplikasi           |
| `reviews`     | Jumlah ulasan pengguna         |

## 🧰 Tools & Teknologi

* **Python**: Scraping data
* **R**: Integrasi & analisis data
* **MongoDB**: Penyimpanan data
