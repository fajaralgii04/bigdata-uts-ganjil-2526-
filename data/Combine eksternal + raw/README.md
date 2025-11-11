# 📁 data/processed

Berisi **dataset gabungan** antara data hasil scraping (`/data/raw/`) dan dataset open-source dari Kaggle (`/data/external/`).

### 🧾 File:
- `steam_reviews_combined.csv` — hasil penggabungan dua sumber data:
  - `steam_reviews_realtime_11cols.csv` → hasil scraping Steam API (4 game)
  - `steam_game_reviews_top10_21000.csv` → dataset Kaggle (10 game)

### 📊 Struktur Kolom:
`appid`, `review`, `word_count`, `voted_up`, `votes_up`, `votes_funny`,  
`timestamp_created`, `author_playtime_forever`, `name`, `price`, `release_date`

### 💡 Keterangan:
- Total data: ±23.000–25.000 baris, 11 kolom.  
- Data sudah distandardisasi agar kedua sumber memiliki skema identik.  
- Digunakan sebagai input utama untuk tahap **cleaning**, **EDA (SMART)**, dan **modeling** di notebook berikutnya.

