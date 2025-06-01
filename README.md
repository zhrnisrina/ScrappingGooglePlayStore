# Proyek Scraping Data Aplikasi Google Play Store

## 🔍 Deskripsi Proyek

Proyek ini bertujuan untuk mengumpulkan data aplikasi dari **Google Play Store** secara **otomatis dan sistematis**, berdasarkan kata kunci kategori aplikasi. Data yang diperoleh mencakup informasi penting seperti nama aplikasi, developer, kategori, rating, jumlah unduhan, harga, dan deskripsi.

---

Berikut adalah versi README yang sudah disesuaikan dengan penjelasan bahwa proses scraping dilakukan di R dengan memanfaatkan modul Python:

---

## 🧰 Tools & Teknologi

* **R**: Platform utama untuk integrasi, pengolahan, dan analisis data.
* **Python (via Reticulate)**: Digunakan untuk scraping data Google Play Store dengan modul `google-play-scraper`. Modul Python ini dipanggil langsung dari R menggunakan package `reticulate`.
* **MongoDB**: Digunakan sebagai penyimpanan data hasil scraping.

---

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

---

## 🎯 Tujuan Proyek

Tujuan utama proyek ini adalah untuk mengumpulkan data aplikasi Google Play secara otomatis dan sistematis, termasuk informasi penting seperti nama aplikasi, developer, kategori, rating, jumlah unduhan, harga, dan deskripsi. Data ini nantinya digunakan untuk:

* Menganalisis distribusi aplikasi berdasarkan kategori dan developer.
* Menilai kualitas dan popularitas aplikasi berdasarkan rating dan jumlah unduhan.
* Mengidentifikasi potensi risiko melalui aplikasi populer yang memiliki rating rendah.
* Memberikan insight bermanfaat bagi developer, analis pasar, investor, dan peneliti.

---

## 🛠️ Metode Scraping

Scraping dilakukan menggunakan kombinasi Python dan R:

* **Modul**: [`google_play_scraper`](https://github.com/JoMingyu/google-play-scraper) (Python)
* **Integrasi**: Paket `reticulate` di R
* **Database**: MongoDB (untuk penyimpanan dan pengolahan data)

---

### Tahapan Scraping:

1. **Pencarian aplikasi** berdasarkan kata kunci kategori, dengan batas maksimal **50 aplikasi per kategori** untuk menjaga efisiensi.
2. **Pengambilan detail aplikasi** seperti rating, jumlah review, ukuran, harga, dan deskripsi.
3. **Pembersihan data** dari nilai kosong dan standarisasi format data.
4. **Penyimpanan ke database MongoDB**.

---

### Target Audiens

* **Developer & Product Manager** yang ingin memahami posisi dan performa aplikasi mereka di pasar.
* **Investor & Analis Pasar** yang mencari informasi tentang tren pasar aplikasi, pangsa pasar developer, dan potensi risiko aplikasi.
* **Akademisi & Peneliti** yang tertarik pada studi kuantitatif tentang ekosistem aplikasi mobile dan faktor-faktor yang mempengaruhi kesuksesan aplikasi.
* **Tim Pemasaran dan Strategi Bisnis** yang membutuhkan insight tentang kategori aplikasi populer dan perilaku pengguna.

---

## 📂 Struktur Data yang Dikumpulkan

<div align="center">
  
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

</div>

Penyimpanan pada MongoDB:
![image](https://github.com/user-attachments/assets/2c7a1339-ce1c-4b03-bc65-792510de45ef)

---

## 📊 Agregasi

**1. Top 10 Categories berdasarkan jumlah aplikasi**

<div align="center">
  
  ![image](https://github.com/user-attachments/assets/ffa426b5-0262-4481-b1a5-0b95ecb854f5)
  
</div>


  Gambar tersebut menampilkan diagram batang horizontal yang menunjukkan **10 kategori aplikasi teratas di Google Play Store berdasarkan jumlah aplikasi yang berhasil dikumpulkan melalui proses scraping**. Kategori **"Sports"** mendominasi dengan jumlah aplikasi terbanyak, disusul oleh kategori **"Strategy"** dan **"Entertainment"**. Kategori lain yang juga menempati peringkat atas adalah **Shopping**, **Simulation**, **Finance**, hingga **Parenting**. Hal ini mengindikasikan bahwa kategori-kategori tersebut menunjukkan area persaingan pasar yang paling padat, memiliki tingkat popularitas atau tingkat pengembangan aplikasi yang tinggi, dan bisa menjadi area fokus utama dalam analisis lebih lanjut atau pengembangan aplikasi baru.

**2. Rata-rata Download vs Rating per Kategori**

<div align="center">
  
![image](https://github.com/user-attachments/assets/18413c13-d5a7-4d79-bec5-db53c93a7958)


</div>

  Gambar tersebut merupakan diagram **scatter plot** yang menunjukkan hubungan antara **rata-rata jumlah download (dalam juta)** dengan **rata-rata rating** untuk setiap kategori aplikasi di Google Play Store. Setiap titik mewakili satu kategori. Terlihat bahwa kategori seperti **Communication** dan **Tools** memiliki jumlah download rata-rata yang sangat tinggi (mencapai lebih dari 1000 juta), namun ratingnya berada pada kisaran rata-rata (sekitar 4.0–4.2). Sebaliknya, beberapa kategori seperti **Casino**, **Medical**, dan **Arcade** memiliki rating tinggi mendekati 4.5 meskipun jumlah downloadnya relatif rendah. Kategori **Auto & Vehicles** tampak menyimpang dengan rating yang sangat rendah. Secara umum, grafik ini menunjukkan bahwa **tingginya jumlah download tidak selalu berkorelasi dengan rating tinggi**, yang bisa menjadi pertimbangan penting bagi pengembang dalam memilih kategori dan fokus pengembangan aplikasi.

**3. Developer dengan Total Download Terbesar (Top 10)**

<div align="center">
  
  ![image](https://github.com/user-attachments/assets/27fb8529-0b46-44b6-9463-4b9e84f93728)

</div>

  Gambar tersebut menunjukkan **diagram batang horizontal** yang mengilustrasikan **10 developer teratas berdasarkan total jumlah download aplikasi di Google Play Store**. Terlihat bahwa **Google LLC** mendominasi secara signifikan dengan total download mendekati **150.000 juta (150 miliar)**, jauh melampaui developer lain. Posisi berikutnya ditempati oleh **Meta Platforms, Inc.**, **WhatsApp LLC**, dan **Microsoft Corporation**, yang masing-masing juga mencatatkan angka download yang tinggi, namun masih sangat kecil dibandingkan Google. Developer lain seperti **Instagram**, **Samsung Electronics**, **Outfit7 Limited**, dan **Garena International** memiliki kontribusi download yang relatif lebih rendah. Visualisasi ini menegaskan bahwa beberapa perusahaan besar menguasai distribusi aplikasi dengan volume unduhan sangat tinggi, mencerminkan dominasi mereka dalam pasar aplikasi global.

**4. Aplikasi dengan Download Tinggi tapi Rating Rendah (Risiko UX)**

<div align="center">

| No | Nama Aplikasi                        | Rating   | Jumlah Unduhan |
|----|--------------------------------------|----------|----------------|
| 1  | Google Maps                          | 3.30     | 10,000,000,000 |
| 2  | Flipboard: Your Social Magazine      | 3.47     | 500,000,000    |
| 3  | happn: Dating, Chat & Meet           | 3.33     | 100,000,000    |
| 4  | Google Classroom                     | 2.54     | 100,000,000    |
| 5  | Shelf                                | 2.68     | 100,000,000    |
| 6  | VSCO: Photo & Video Editor           | 3.45     | 100,000,000    |
| 7  | NFL                                  | 3.01     | 100,000,000    |
| 8  | AccuWeather: Weather Radar           | 3.48     | 100,000,000    |
| 9  | Genshin Impact                       | 3.27     | 100,000,000    |
| 10 | Top War: Battle Game                 | 3.22     | 50,000,000     |

</div>

  Tabel tersebut menunjukkan bahwa beberapa aplikasi dengan jumlah unduhan sangat tinggi justru memiliki rating pengguna yang rendah, yang mengindikasikan potensi masalah dalam pengalaman pengguna (UX). Contohnya, **Google Maps** meskipun sangat populer, hanya meraih rating 3,30, kemungkinan karena perubahan fitur atau bug yang mengganggu. **Google Classroom** bahkan memiliki rating lebih rendah lagi (2,54), yang mungkin disebabkan oleh antarmuka yang kurang intuitif atau performa buruk selama penggunaan daring massal. Aplikasi lain seperti **Shelf**, **Genshin Impact**, dan **Top War: Battle Game** juga menunjukkan pola serupa, di mana popularitas tidak menjamin kepuasan pengguna—bisa jadi karena desain UI yang buruk, sistem monetisasi agresif, iklan yang mengganggu, atau ekspektasi pengguna yang tidak terpenuhi. Hal ini menjadi peringatan penting bagi pengembang untuk lebih fokus pada kualitas UX, bukan hanya target unduhan.

**5. Korelasi Rating dan Download**

<div align="center">
  
  ![image](https://github.com/user-attachments/assets/07c0ab57-1409-4f5f-bcf9-f1582428896e)
  
</div>

Gambar tersebut menampilkan **analisis korelasi antara rating dan jumlah download aplikasi** di Google Play Store. Nilai korelasi Pearson (r) adalah **0**, yang berarti **tidak ada hubungan linear yang signifikan antara jumlah download dan rating aplikasi**. Hal ini divisualisasikan dalam scatter plot dengan sumbu X sebagai jumlah download (dalam skala logaritmik) dan sumbu Y sebagai rating aplikasi.
Meskipun garis tren (regresi linier) sedikit menanjak, persebaran data sangat tersebar dan tidak menunjukkan pola korelasi yang kuat. Ini mengindikasikan bahwa **aplikasi yang banyak diunduh belum tentu memiliki rating tinggi**, dan sebaliknya, rating tinggi tidak menjamin popularitas dalam bentuk jumlah download. Temuan ini penting untuk pengembang dan analis produk karena menegaskan bahwa **kuantitas pengguna dan kualitas pengalaman pengguna bisa berjalan secara independen**.

**6. Aplikasi dengan Rating Tertinggi per Kategori**

<div align="center">
  
| No | Kategori          | Nama Aplikasi                              | Rating   | Jumlah Unduhan     |
|----|-------------------|---------------------------------------------|----------|---------------------|
| 1  | Action            | Endurance: dead space Premium               | 4.83     | 50,000              |
| 2  | Adventure         | Animals & Coins Adventure Game              | 4.85     | 10,000,000          |
| 3  | Arcade            | Streets of Rage 4                           | 4.82     | 50,000              |
| 4  | Art & Design      | Canva: AI Photo & Video Editor              | 4.80     | 500,000,000         |
| 5  | Auto & Vehicles   | Edmunds - Shop Cars For Sale                | 4.27     | 1,000,000           |
| 6  | Beauty            | Booksy Biz: For Businesses                  | 4.61     | 1,000,000           |
| 7  | Board             | Vita Mahjong                                | 4.89     | 50,000,000          |
| 8  | Books & Reference | ReadEra – book reader pdf epub              | 4.85     | 10,000,000          |
| 9  | Business          | Cvent Events                                | 4.87     | 500,000             |
| 10 | Card              | Solitaire for Seniors Game                  | 4.89     | 1,000,000           |

</div>

  Tabel ini menunjukkan aplikasi dengan rating tertinggi di berbagai kategori yang mencerminkan kepuasan pengguna yang sangat baik, mulai dari niche dengan unduhan lebih kecil seperti **Endurance: dead space Premium** (50 ribu unduhan, rating 4.83) hingga aplikasi populer seperti **Canva** dengan 500 juta unduhan dan rating 4.80. Beberapa aplikasi seperti **Vita Mahjong** dan **Solitaire for Seniors Game** tidak hanya mendapat rating tinggi di atas 4.8 tetapi juga berhasil mengumpulkan puluhan juta unduhan, menandakan kombinasi antara kualitas dan popularitas. Meski ada kategori dengan jumlah unduhan yang relatif rendah, semua aplikasi di tabel ini berhasil memberikan pengalaman pengguna yang memuaskan, menegaskan bahwa rating tinggi tidak selalu bergantung pada jumlah unduhan besar, tetapi pada kualitas dan relevansi aplikasi di kategorinya masing-masing.

**7. Aplikasi dengan Download Tertinggi per Kategori**

<div align="center">
  
| No | Kategori          | Nama Aplikasi                      | Jumlah Unduhan     | Rating  |
|-----|-------------------|----------------------------------|--------------------|---------|
| 1   | Action            | Free Fire                        | 1,000,000,000      | 4.22    |
| 2   | Adventure         | Roblox                          | 1,000,000,000      | 4.46    |
| 3   | Arcade            | Subway Surfers                  | 1,000,000,000      | 4.56    |
| 4   | Art & Design      | Canva: AI Photo & Video Editor  | 500,000,000        | 4.80    |
| 5   | Auto & Vehicles   | Edmunds - Shop Cars For Sale     | 1,000,000          | 4.27    |
| 6   | Beauty            | Ulta Beauty: Makeup & Skincare  | 5,000,000          | 4.59    |
| 7   | Board             | Ludo King®                      | 1,000,000,000      | 4.22    |
| 8   | Books & Reference | Google Play Books & Audiobooks   | 1,000,000,000      | 4.68    |
| 9   | Business          | Zoom Workplace                  | 1,000,000,000      | 4.15    |
| 10  | Card              | UNO!™                          | 100,000,000        | 4.41    |

</div>

  Tabel ini menampilkan aplikasi dengan jumlah unduhan tertinggi di berbagai kategori, menunjukkan popularitas besar sekaligus memberikan gambaran tentang pengalaman pengguna melalui rating mereka. Beberapa aplikasi seperti Free Fire, Roblox, Subway Surfers, dan Ludo King® berhasil mencapai 1 miliar unduhan, menandakan dominasi pasar yang signifikan di kategori masing-masing, meskipun ratingnya berkisar antara 4.15 hingga 4.56, yang masih cukup baik. Sementara itu, aplikasi seperti Canva dan Google Play Books & Audiobooks menunjukkan keseimbangan antara popularitas tinggi dan rating pengguna yang sangat baik (4.80 dan 4.68), mengindikasikan kualitas yang konsisten. Aplikasi dengan unduhan lebih rendah seperti Edmunds dan Ulta Beauty tetap mempertahankan rating yang bagus, menegaskan bahwa walaupun skalanya lebih kecil, kepuasan pengguna tetap terjaga. Secara keseluruhan, tabel ini menegaskan bahwa aplikasi dengan unduhan tertinggi tetap bisa menawarkan pengalaman pengguna yang memuaskan di berbagai kategori.

**8. Volatilitas Rating antar Aplikasi dalam Satu Kategori**

<div align="center">
  
  ![image](https://github.com/user-attachments/assets/4e6b0eb8-d5e4-4559-a934-8122d40405f5)
  
</div>

 Grafik ini menampilkan volatilitas rating antar aplikasi dalam masing-masing kategori, yang diukur menggunakan standar deviasi (SD) rating. Kategori *Libraries & Demo* menunjukkan volatilitas tertinggi, dengan nilai SD rating melebihi 2, yang mengindikasikan adanya variasi besar dalam penilaian pengguna terhadap aplikasi-aplikasi dalam kategori tersebut. Sebaliknya, kategori seperti *Food & Drink*, *Art & Design*, dan *Education* memiliki standar deviasi rendah, menunjukkan bahwa aplikasi dalam kategori ini cenderung memiliki konsistensi dalam penilaian pengguna. Informasi ini penting untuk menilai stabilitas persepsi kualitas aplikasi dalam setiap kategori — semakin tinggi volatilitas, semakin beragam pula pengalaman pengguna.
  
**9. Konsentrasi Developer Dominan per Kategori**

<div align="center">

![image](https://github.com/user-attachments/assets/b7763001-eb6b-4faf-9035-da4a7a8b37b5)

  
</div>

  Grafik ini menggambarkan konsentrasi developer dominan di tiap kategori aplikasi, yaitu developer yang memiliki jumlah aplikasi terbanyak dalam satu kategori. Terlihat bahwa pada kategori *Education*, terdapat satu developer yang sangat dominan dengan lebih dari 30 aplikasi, jauh melampaui kategori lain. Hal serupa meskipun dalam skala lebih kecil juga terlihat pada kategori *Entertainment*, *Books & Reference*, dan *Libraries & Demo*. Pola ini menunjukkan bahwa dalam beberapa kategori, distribusi aplikasi cenderung terpusat pada satu developer saja, yang dapat mengindikasikan dominasi pasar atau spesialisasi developer dalam topik tertentu. Sebaliknya, kategori lain memiliki konsentrasi yang lebih merata atau rendah, mengindikasikan persaingan yang lebih seimbang antar developer.

**10. Rasio Aplikasi Berbayar per Kategori**

<div align="center">
  
  ![image](https://github.com/user-attachments/assets/724a5d8d-15bd-4a70-8ff0-530fcef40a95)
  
</div>

  Visualisasi ini menunjukkan proporsi aplikasi berbayar di setiap kategori aplikasi. Kategori *Role Playing* menempati posisi teratas dengan rasio aplikasi berbayar tertinggi, diikuti oleh *Strategy* dan *Personalization*. Artinya, lebih dari separuh aplikasi dalam kategori *Role Playing* adalah aplikasi berbayar. Sebaliknya, banyak kategori seperti *Education*, *Communication*, dan *Books & Reference* memiliki proporsi aplikasi berbayar yang sangat rendah, menunjukkan bahwa mayoritas aplikasi dalam kategori tersebut tersedia secara gratis. Pola ini mengindikasikan perbedaan strategi monetisasi berdasarkan jenis aplikasi, di mana genre permainan dan personalisasi cenderung lebih banyak menawarkan konten berbayar.

**11. Aplikasi Rating Tinggi tapi Download Rendah (Hidden Gems)**

<div align="center">

  ![image](https://github.com/user-attachments/assets/4c9939d4-e535-4cfd-af50-d98e89fd49e2)

</div>

Visualisasi ini menampilkan sepuluh aplikasi dengan rating tinggi (≥ 4.5) namun jumlah unduhan rendah (< 100.000), yang dikategorikan sebagai *"hidden gems"*. Aplikasi seperti *Streets of Rage 4*, *ReadEra Premiun - ebook reader*, dan *Partiful: Fun Party Invites* menduduki peringkat teratas dengan rating mendekati sempurna, menunjukkan kualitas yang sangat baik dari perspektif pengguna. Namun, rendahnya angka unduhan mengindikasikan bahwa aplikasi-aplikasi ini kurang dikenal atau belum menjangkau audiens yang luas. Temuan ini menunjukkan adanya potensi besar untuk dikembangkan lebih lanjut melalui promosi atau strategi distribusi yang lebih baik.

