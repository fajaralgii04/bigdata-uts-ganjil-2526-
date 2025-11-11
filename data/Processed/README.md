# 📁 data/processed

Folder ini berisi **dataset hasil akhir** dari seluruh proses pengolahan data (gabungan, cleaning, dan preprocessing).

### 🧾 File
- `steam_reviews_combined.csv` — hasil penggabungan dataset Kaggle & scraping  
- `steam_reviews_clean.csv` — hasil *data cleaning*  
- `steam_reviews_preprocessed.csv` — hasil *data preprocessing* yang siap digunakan untuk modeling  
- `steam_reviews_final.xlsx` — versi Excel dari hasil akhir untuk dokumentasi

### 📊 Struktur Kolom
`appid`, `review`, `word_count`, `voted_up`, `votes_up`, `votes_funny`,  
`timestamp_created`, `author_playtime_forever`, `name`, `price`, `release_date`

### 💡 Keterangan
- Data di folder ini adalah hasil akhir yang **siap untuk tahap modeling dan evaluasi**  
- Semua kolom sudah distandardisasi, bebas duplikasi, dan memiliki format konsisten  
- File `steam_reviews_final.xlsx` dapat digunakan sebagai *final deliverable* proyek
