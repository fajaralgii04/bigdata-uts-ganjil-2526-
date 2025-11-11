# 📁 data/raw

Berisi **dataset hasil scraping Steam** yang digunakan untuk proyek *Big Data UTS Ganjil 25/26*.

### 🧾 File:
- `steam_reviews_realtime_11cols.csv` — hasil scraping 4 game (Dota 2, Apex Legends, PUBG, GTA V) menggunakan **Steam API**.

### 📊 Struktur Kolom:
`appid`, `review`, `word_count`, `voted_up`, `votes_up`, `votes_funny`,  
`timestamp_created`, `author_playtime_forever`, `name`, `price`, `release_date`

### 💡 Keterangan:
- Data masih mentah (belum cleaning).
- `price` disimpan dalam **cent** (contoh: 5999 = $59.99).
- Digunakan sebagai **30% data hasil scraping** sebelum digabung dengan dataset Kaggle (`/data/external/`).

