<div align="center">
  <a href="https://github.com/Srjeff27/api-quran-indonesia">
    <img src="./src/assets/logo.png" alt="Quran API ID Logo" width="200">
  </a>
  
  <h1>🕌 Quran API Indonesia</h1>
  
  <p>
    <strong>REST API Al-Quran Bahasa Indonesia - Lengkap, Gratis, dan Mudah Digunakan!</strong>
  </p>
  
  <p>
    Menyediakan terjemahan, tafsir (Kemenag, Quraish Shihab, Al-Jalalain), audio murottal dari 6 qori terkenal, dan fitur ayat random.
  </p>

  <p>
    <a href="https://apiquran.jesio.cyou"><strong>🌐 Demo Live</strong></a> · 
    <a href="https://github.com/Srjeff27/api-quran-indonesia/issues"><strong>🐛 Lapor Bug</strong></a> · 
    <a href="https://github.com/Srjeff27/api-quran-indonesia/issues"><strong>💡 Request Fitur</strong></a>
  </p>

  <p>
    <a href="https://github.com/Srjeff27/api-quran-indonesia/graphs/contributors">
      <img alt="GitHub contributors" src="https://img.shields.io/github/contributors/Srjeff27/api-quran-indonesia?style=flat-square">
    </a>
    <a href="https://github.com/Srjeff27/api-quran-indonesia/network/members">
      <img alt="GitHub forks" src="https://img.shields.io/github/forks/Srjeff27/api-quran-indonesia?style=flat-square">
    </a>
    <a href="https://github.com/Srjeff27/api-quran-indonesia/stargazers">
      <img alt="GitHub Repo stars" src="https://img.shields.io/github/stars/Srjeff27/api-quran-indonesia?style=flat-square">
    </a>
    <a href="https://github.com/Srjeff27/api-quran-indonesia/issues">
      <img alt="GitHub issues" src="https://img.shields.io/github/issues/Srjeff27/api-quran-indonesia?style=flat-square">
    </a>
    <a href="https://github.com/Srjeff27/api-quran-indonesia/blob/main/LICENSE">
      <img alt="GitHub license" src="https://img.shields.io/github/license/Srjeff27/api-quran-indonesia?style=flat-square">
    </a>
  </p>
</div>

---

## ✨ Fitur Unggulan

**Quran API Indonesia** adalah REST API Al-Quran yang komprehensif, dirancang khusus untuk kebutuhan pengembang aplikasi Islami di Indonesia. Data digabungkan dari berbagai sumber terpercaya dengan struktur JSON yang modern dan optimal.

### 🎯 Keunggulan Utama:

- **🎧 6 Audio Murottal**: Pilihan lantunan indah dari Qori internasional:
  - *Shaykh Mishari Alafasy*
  - *Ahmed ibn Ali al-Ajamy*
  - *Husary (Mujawwad)*
  - *Minshawi*
  - *Muhammad Ayyoub*
  - *Muhammad Jibreel*
  
- **📖 3 Varian Tafsir**: Pendalaman makna ayat yang variatif:
  - Kementerian Agama RI (Ringkas & Lengkap)
  - Tafsir Quraish Shihab
  - Tafsir Al-Jalalain

- **🛠️ Utilitas Lengkap**:
  - **Ayat Random**: Generator ayat untuk fitur "Quote of the Day"
  - **Metadata Detail**: Info Juz, Manzil, Ruku, Sajda, dan penomoran
  - **Visualisasi**: Aset gambar per ayat untuk kemudahan berbagi

> 💡 **Punya ide menarik?** Jangan ragu untuk mengajukan [Feature Request](https://github.com/Srjeff27/api-quran-indonesia/issues) di GitHub!

---

## 🚀 Quick Start

### Base URL

```
https://apiquran.jesio.cyou
```

### Contoh Penggunaan

#### JavaScript (Fetch API)

```javascript
// 1. Mendapatkan daftar semua surah
fetch('https://apiquran.jesio.cyou/surahs')
  .then(res => res.json())
  .then(data => console.log(data));

// 2. Mendapatkan detail Surah Al-Ikhlas (112)
fetch('https://apiquran.jesio.cyou/surahs/112')
  .then(res => res.json())
  .then(data => console.log(data));
```

#### Python

```python
import requests

# Mendapatkan satu ayat random untuk renungan
response = requests.get('https://apiquran.jesio.cyou/random')
print(response.json())
```

#### cURL

```bash
# Mendapatkan semua ayat dalam Surah Al-Fatihah
curl https://apiquran.jesio.cyou/surahs/1/ayahs
```

---

## 📚 Dokumentasi API

### 1️⃣ Mendapatkan Daftar Surah

Mengembalikan daftar 114 surah dengan metadata dasar (nama, arti, jumlah ayat, dll).

**Endpoint:** `GET /surahs`

<details>
<summary>🔍 Lihat Contoh Response</summary>

```json
[
  {
    "number": 1,
    "sequence": 5,
    "numberOfVerses": 7,
    "name": {
      "short": "الفاتحة",
      "long": "سُورَةُ ٱلْفَاتِحَةِ",
      "transliteration": { "en": "Al-Faatiha", "id": "Al-Fatihah" },
      "translation": { "en": "The Opening", "id": "Pembukaan" }
    },
    "revelation": { "arab": "مكة", "en": "Meccan", "id": "Makkiyyah" },
    "tafsir": { "id": "Surat Al Faatihah..." }
  },
  ...
]
```

</details>

---

### 2️⃣ Mendapatkan Detail Surah

Mengembalikan satu surah lengkap beserta seluruh ayat, terjemahan, dan audionya.

**Endpoint:** `GET /surahs/{nomorSurah}`

**Parameter:**
- `nomorSurah` (integer, 1-114): Nomor urut surah dalam Al-Quran

**Contoh:** `https://apiquran.jesio.cyou/surahs/112`

<details>
<summary>🔍 Lihat Contoh Response</summary>

```json
{
  "number": 112,
  "name": { "short": "الإخلاص", "transliteration": { "id": "Al-Ikhlas" } },
  "preBismillah": {
    "text": { "arab": "بِسْمِ اللَّهِ الرَّحْمَٰنِ الرَّحِيمِ" },
    "audio": { "primary": "https://cdn.alquran.cloud/..." }
  },
  "verses": [
    {
      "number": { "inQuran": 6221, "inSurah": 1 },
      "text": { "arab": "قُلْ هُوَ ٱللَّهُ أَحَدٌ" },
      "translation": { "id": "Katakanlah (Muhammad), \"Dialah Allah, Yang Maha Esa." },
      "audio": { "primary": "https://cdn.alquran.cloud/..." }
    }
  ]
}
```

</details>

---

### 3️⃣ Mendapatkan Semua Ayat dari Surah

Mengembalikan array semua ayat dalam surah tertentu.

**Endpoint:** `GET /surahs/{nomorSurah}/ayahs`

**Parameter:**
- `nomorSurah` (integer, 1-114): Nomor urut surah dalam Al-Quran

**Contoh:** `https://apiquran.jesio.cyou/surahs/1/ayahs`

---

### 4️⃣ Mendapatkan Ayat Spesifik

Mengambil data satu ayat tertentu secara spesifik, sangat lengkap dengan metadata dan tafsir.

**Endpoint:** `GET /surahs/{nomorSurah}/ayahs/{nomorAyat}`

**Parameter:**
- `nomorSurah` (integer, 1-114): Nomor urut surah dalam Al-Quran
- `nomorAyat` (integer): Nomor ayat dalam surah tersebut

**Contoh:** `https://apiquran.jesio.cyou/surahs/112/ayahs/2`

<details>
<summary>🔍 Lihat Contoh Response</summary>

```json
{
  "number": { "inQuran": 6222, "inSurah": 2 },
  "meta": { "juz": 30, "page": 604, "manzil": 7 },
  "text": { "arab": "ٱللَّهُ ٱلصَّمَدُ" },
  "translation": { "id": "Allah tempat meminta segala sesuatu." },
  "tafsir": {
    "id": {
      "short": "Allah tempat meminta segala sesuatu.",
      "long": "Allah adalah Tuhan yang bergantung kepada-Nya segala sesuatu..."
    }
  }
}
```

</details>

---

### 5️⃣ Mendapatkan Ayat Random

Mengembalikan satu ayat acak dari 6.236 ayat Al-Quran. Sempurna untuk fitur "Ayat Hari Ini".

**Endpoint:** `GET /random`

**Contoh:** `https://apiquran.jesio.cyou/random`

---

## 🛠️ Instalasi & Pengembangan

Ingin menjalankan API ini di server lokal Anda sendiri? Ikuti langkah berikut.

### Prasyarat

- Node.js (v14+)
- Yarn atau NPM

### Langkah Instalasi

1. **Clone Repository**
   ```bash
   git clone https://github.com/Srjeff27/api-quran-indonesia.git
   cd api-quran-indonesia
   ```

2. **Install Dependencies**
   ```bash
   yarn install
   # atau
   npm install
   ```

3. **Konfigurasi Environment**
   
   Salin file contoh env menjadi file konfigurasi aktif:
   ```bash
   cp env.example .env
   ```

4. **Jalankan Server Development**
   ```bash
   yarn dev
   ```
   
   Server akan berjalan di `http://localhost:5000` 🚀

### Script Tersedia

| Perintah | Fungsi |
|----------|--------|
| `yarn start` | Menjalankan server produksi |
| `yarn dev` | Menjalankan server development dengan nodemon |
| `yarn build:quran` | Rebuild data JSON Quran utama |
| `yarn scrape:surah` | Update data surah dari Kemenag |
| `yarn scrape:tafsir` | Update data tafsir dari Kemenag |
| `yarn test` | Menjalankan unit testing |
| `yarn lint` | Memeriksa kode dengan ESLint |
| `yarn lint:fix` | Memperbaiki masalah ESLint otomatis |

---

## 💾 Sumber Data

Kredibilitas data adalah prioritas kami. Kami menggunakan sumber terpercaya:

| Sumber | Penggunaan |
|--------|------------|
| [Kemenag RI](https://quran.kemenag.go.id) | Sumber utama teks, terjemahan, dan tafsir |
| [Al Quran Cloud](https://alquran.cloud) | Metadata teknis, CDN audio, dan gambar ayat |
| [Tanzil.net](https://tanzil.net/docs/) | Referensi tafsir Quraish Shihab & Al-Jalalain |

Semua data disimpan di folder `data`. Data mentah ada di `data/tmp`, sedangkan `data/quran.json` adalah data final yang digunakan API.

---

## 🤝 Kontribusi

Kami sangat terbuka untuk kontribusi dari komunitas!

1. Fork repository ini
2. Buat branch fitur baru: `git checkout -b fitur-keren`
3. Commit perubahan: `git commit -m 'Menambahkan fitur keren'`
4. Push ke branch: `git push origin fitur-keren`
5. Submit Pull Request

Pastikan kode mengikuti style guide (ESLint) dan lulus semua test.

---

## 📄 Lisensi

Proyek ini dilisensikan di bawah [MIT License](https://opensource.org/licenses/MIT). 

Anda bebas:
- ✅ Menggunakan untuk keperluan komersial
- ✅ Memodifikasi
- ✅ Mendistribusikan
- ✅ Penggunaan pribadi

Dengan syarat:
- 📋 Menyertakan lisensi dan copyright notice

---

## 👨‍💻 Maintainer

**Srjeff27**

- GitHub: [@Srjeff27](https://github.com/Srjeff27)
- Website: [Jesio Technology](https://jesio.cyou)

---

## 💖 Support

Jika API ini bermanfaat untuk proyek Anda, pertimbangkan untuk:

- ⭐ Memberikan star di [GitHub](https://github.com/Srjeff27/api-quran-indonesia)
- 🐛 Melaporkan bug atau masalah
- 💡 Memberikan saran fitur baru
- 🤝 Berkontribusi dalam pengembangan

---

## 📞 Kontak & Informasi

- **Website**: [apiquran.jesio.cyou](https://apiquran.jesio.cyou)
- **Repository**: [github.com/Srjeff27/api-quran-indonesia](https://github.com/Srjeff27/api-quran-indonesia)
- **Issues**: [GitHub Issues](https://github.com/Srjeff27/api-quran-indonesia/issues)

---

<div align="center">
  <p>
    <strong>Dibuat dengan ❤️ untuk kemudahan akses Al-Quran digital di Indonesia</strong>
  </p>
  <p>
    <em>"Bacalah dengan (menyebut) nama Tuhanmu Yang menciptakan"</em><br>
    <strong>(QS. Al-Alaq: 1)</strong>
  </p>
</div>
