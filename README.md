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

Tujuan utama proyek ini adalah untuk mengumpulkan data aplikasi Google Play secara otomatis dan sistematis, termasuk informasi penting seperti nama aplikasi, developer, kategori, rating, jumlah unduhan, harga, dan deskripsi. Data ini nantinya digunakan untuk:

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


## 📊 Insight Menarik dari Proyek

* 📌 **Kategori dengan jumlah aplikasi terbanyak** → Mengindikasikan area dengan persaingan tinggi.
* 🏆 **Developer dengan total unduhan terbesar** → Pemain utama di ekosistem aplikasi.
* 📈 **Hubungan antara rating dan jumlah unduhan** → Mengukur pengaruh kualitas terhadap popularitas.
* ⚠️ **Aplikasi dengan unduhan tinggi tapi rating rendah** → Sinyal risiko buruknya pengalaman pengguna.
* 🧭 **Perbandingan rating & popularitas antar kategori** → Mengetahui kategori yang paling disukai pengguna.

## 📂 Struktur Data yang Dikumpulkan

| Field                 | Tipe Data     | Deskripsi                                                                   |
| --------------------- | ------------- | --------------------------------------------------------------------------- |
| `_id`                 | `ObjectId`    | ID unik dokumen (otomatis oleh MongoDB)                                     |
| `app_name`            | `string`      | Nama aplikasi                                                               |
| `developer`           | `string`      | Nama pengembang aplikasi                                                    |
| `category`            | `string`      | Kategori aplikasi                                                           |
| `rating`              | `float`       | Nilai rating aplikasi (misalnya 3.77)                                       |
| `number_of_reviews`   | `integer`     | Jumlah ulasan dari pengguna                                                 |
| `number_of_downloads` | `string`      | Jumlah unduhan aplikasi (perlu parsing lebih lanjut bila ingin kuantitatif) |
| `price`               | `float`       | Harga aplikasi (0 berarti gratis)                                           |
| `size`                | `string/null` | Ukuran file aplikasi (jika tersedia, contoh: "25M")                         |
| `description`         | `string`      | Deskripsi aplikasi (bisa mengandung HTML tag)                               |
| `app_id`              | `string`      | ID unik aplikasi di Play Store (misalnya: "com.tinder")                     |
| `source_keyword`      | `string`      | Kata kunci yang digunakan saat scraping aplikasi ini                        |

## 🧰 Tools & Teknologi

* **Python**: Scraping data
* **R**: Integrasi & analisis data
* **MongoDB**: Penyimpanan data
