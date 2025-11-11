# 🎮 Analisis Perilaku Pemain Berdasarkan Ulasan Gim di Platform Steam Menggunakan Pendekatan Big Data Analytics

> **Tugas Besar UTS Big Data (Semester Ganjil 2025/2026)**  
> Proyek ini menganalisis perilaku pemain berdasarkan ulasan pengguna (*user reviews*) di platform **Steam**, dengan menerapkan konsep **Big Data Analytics** untuk memahami hubungan antara durasi bermain, kepuasan pemain, dan keterlibatan komunitas.  
>  
> 📍 *Telkom University — Fakultas Teknik Elektro, S1 Teknik Komputer*  
> 👥 *Kelompok 5: Muhammad Fajar Algifari & Auldy Ranayu Sanny Prahasty Rachman*

---

## 🧠 Ringkasan Proyek

Perkembangan industri gim digital menghasilkan jutaan data ulasan yang kaya akan informasi perilaku pengguna.  
Penelitian ini menggabungkan **data open-source dari Kaggle** (21.000 ulasan dari 10 gim populer) dan **data hasil scraping API Steam** (8.000 ulasan dari 4 gim populer), menghasilkan total ±24.900 data dengan 11 kolom utama seperti `appid`, `review`, `voted_up`, `votes_up`, `votes_funny`, `author_playtime_forever`, dan `price`.

Pendekatan **Big Data Analytics** digunakan untuk:
- Menemukan korelasi antara durasi bermain dan kepuasan pemain.  
- Menganalisis tren sentimen mingguan dan bulanan.  
- Mengelompokkan perilaku pemain berdasarkan pola interaksi dan waktu bermain.  
- Membangun model klasifikasi, regresi, dan clustering berbasis data numerik.

---

## 🧩 Struktur Folder

bigdata-uts-ganjil-2526-/

├─ data/

│ ├─ raw/ # Hasil scraping Steam API (8k ulasan)

│ ├─ external/ # Dataset Kaggle (21k ulasan)

│ ├─ processed/ # Hasil cleaning & preprocessing

│ └─ semua csv (gabungan)

│

├─ notebooks/

│ ├─ 00_scraping.ipynb # Pengambilan data dari Steam API

│ ├─ 01_cleaning_eda.ipynb # Data cleaning & EDA (SMART)

│ ├─ 02_preprocessing.ipynb # Normalisasi & encoding

│ ├─ 03_model_classification.ipynb # SVM & Random Forest

│ ├─ 04_model_regression.ipynb # Linear Regression & XGBoost

│ └─ 05_model_clustering.ipynb # K-Means & DBSCAN

│ └─ combine scrap dan kaggle.ipynb

├─ reports/

│ ├─ figures/ # Grafik hasil analisis

│ └─ Kelompok5_TugasBesarBigData.pdf # Laporan akhir lengkap

│

├─ src/ # Script modular (scraping, cleaning, modeling)

│

├─ Kelompok5_Code.ipynb # Notebook utama (reproducible)

└─ README.md


## ⚙️ Alur Analisis

### 1️⃣ Pengumpulan Data
- **Kaggle dataset:** Steam Game Reviews of 743 Games (oleh *akashunikaggle*).  
  Diambil subset top 10 gim dengan total 21.000 ulasan.
- **Scraping Steam API:**  
  Endpoint: `https://store.steampowered.com/appreviews/{appid}`  
  Gim: Dota 2 (570), Apex Legends (1172470), PUBG (578080), GTA V (271590).  
  Menggunakan Python `requests`, retry logic, dan jeda antar request.  
- Hasil digabung menjadi satu dataset dengan **11 kolom identik**:


---

### 2️⃣ Data Cleaning
- Menghapus *missing values* dan *duplicate reviews*.  
- Mengonversi tipe data:  
`timestamp_created → datetime`, `voted_up → bool`, `word_count & price → int`.  
- Menghapus *outlier* dengan rentang kuantil (1%–99%) untuk waktu bermain.  
- Hasil akhir: `steam_reviews_clean.csv` (≈24.000 baris, 11 kolom).  

---

### 3️⃣ Data Preprocessing
- Menghapus kolom non-prediktif (`appid`, `name`, `review`, `release_date`).  
- Membuat fitur kategorikal `review_length_cat` (Short, Medium, Long).  
- Menormalisasi fitur numerik (`StandardScaler`).  
- Split data: 80% *train* / 20% *test*.  
- Disimpan sebagai:


---

### 4️⃣ Exploratory Data Analysis (EDA) — Konsep SMART
Terdapat enam pertanyaan analitik berbasis SMART (Specific, Measurable, Achievable, Relevant, Time-bound):

| No | Fokus Analisis | Metode & Visualisasi |
|----|----------------|----------------------|
| 1 | Korelasi durasi bermain ↔ review positif | Pearson correlation per game (bar chart) |
| 2 | Tren mingguan sentimen pemain | Line chart per minggu per game |
| 3 | Engagement score ↔ positivity | Korelasi + bar chart top 10 |
| 4 | Panjang review ↔ proporsi positif | Bar chart 3 kategori panjang teks |
| 5 | Game dengan engagement tertinggi | Bar chart rata-rata `votes_up` dan `votes_funny` |
| 6 | Tren aktivitas bulanan | Line chart jumlah review bulanan |

---

### 5️⃣ Modeling dan Evaluasi

#### 🔸 Klasifikasi — *Sentiment Prediction*
| Algoritma | Tujuan | Hasil |
|------------|--------|-------|
| **SVM** | Memprediksi review positif/negatif | Akurasi moderat, cenderung bias ke kelas positif |
| **Random Forest** | Ensemble untuk klasifikasi sentimen | Akurasi & F1-Score tertinggi, hasil paling seimbang |

**Model terbaik:** `RandomForestClassifier`  
**Faktor dominan:** waktu bermain dan jumlah votes_up.

---

#### 🔸 Regresi — *Upvote Prediction*
| Algoritma | Tujuan | Hasil |
|------------|--------|-------|
| **Linear Regression** | Model dasar linier | Kurang akurat untuk nilai ekstrem |
| **XGBoost Regressor** | Model boosting non-linear | R² = 0.956, MSE = 0.056 (terbaik) |

**Model terbaik:** `XGBRegressor`  
Menangkap hubungan kompleks antar fitur numerik.

---

#### 🔸 Clustering — *Player Segmentation*
| Algoritma | Hasil |
|------------|-------|
| **K-Means (k=3)** | 3 segmen utama: Casual, Active, Hardcore players |
| **DBSCAN** | Mengidentifikasi outlier & pemain unik |

**Cluster Interpretasi:**
- **C1 – Pemain Kasual:** waktu bermain pendek, review singkat.  
- **C2 – Pemain Aktif:** review panjang, sering memberi vote lucu.  
- **C3 – Pemain Intensif:** waktu bermain lama, ulasan positif tinggi.

---

## 📊 Hasil Utama

| Analisis | Temuan |
|-----------|---------|
| Korelasi Playtime–Positivity | Korelasi positif kuat, semakin lama bermain → semakin puas |
| Engagement Score | Votes_up & funny memengaruhi kecenderungan review positif |
| Aktivitas Bulanan | Lonjakan ulasan tertinggi pada Maret 2025 |
| Panjang Review | Review panjang cenderung lebih positif |
| Model Terbaik | Random Forest (klasifikasi), XGBoost (regresi), K-Means (clustering) |

---

## 🧾 Reproduksi Analisis

pengguna dapat langsung menjalankan seluruh pipeline tanpa Google Drive:

```bash
git clone https://github.com/fajaralgii04/bigdata-uts-ganjil-2526-.git
cd bigdata-uts-ganjil-2526-
pip install -r requirements.txt
jupyter notebook Kelompok5_Code.ipynb

Dataset diambil otomatis dari folder:

https://github.com/fajaralgii04/bigdata-uts-ganjil-2526-/tree/main/data/semua%20csv%20(gabungan)

🧩 Teknologi yang Digunakan

Python 3.10+

pandas, numpy, matplotlib, seaborn

scikit-learn, xgboost

requests, urllib3, tqdm

StandardScaler, LabelEncoder

Google Colab / Jupyter Notebook

🏁 Kesimpulan

Analisis ini membuktikan bahwa pendekatan Big Data Analytics mampu:

Mengungkap pola perilaku pemain berdasarkan data ulasan publik.

Mengklasifikasikan kepuasan dan engagement secara kuantitatif.

Membangun model prediktif yang akurat untuk mendukung pengambilan keputusan.
