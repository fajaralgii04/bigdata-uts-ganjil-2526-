🕹️ Analisis Data Game di Platform Steam

🎯 Deskripsi Singkat
Proyek ini merupakan Tugas Besar UTS Mata Kuliah Big Data yang berfokus pada analisis data game di platform Steam.
Tujuan proyek ini adalah untuk memahami faktor-faktor yang memengaruhi popularitas game, seperti harga, rating, genre, dan waktu bermain pengguna.
Data diperoleh dari Steam Store (Kaggle) sebagai open data dan Steam Community Reviews sebagai hasil scraping.

🎯 Tujuan Proyek
Melakukan analisis eksploratif (EDA) untuk menemukan pola dan tren dalam data game di Steam.
Menganalisis hubungan antara harga, ulasan positif, dan waktu bermain.
Mengelompokkan game berdasarkan karakteristiknya seperti genre, rating, dan popularitas.
Mengembangkan model prediktif untuk memperkirakan rating atau sentimen ulasan pengguna.

Muhammad Fajar Algifari	1103223119 >> Data Engineer & Machine Learning Engineer 

Auldy Ranayu Sanny Prahasty Rachman	1103223216 >>	Data Analyst

Cara Menjalankan Notebook

Clone repository ini ke lokal atau buka di Google Colab:

git clone https://github.com/fajaralgii04/bigdata-uts-ganjil-2526- 

cd bigdata-uts-steam-analysis

Jalankan notebook sesuai urutan berikut:
00_scraping.ipynb → Mengambil data ulasan dari Steam (scraping)

01_cleaning_eda.ipynb → Membersihkan data dan melakukan EDA

02_preprocessing.ipynb → Menyiapkan data sebelum modeling 

03_model_classification.ipynb → Klasifikasi sentimen ulasan 

04_model_regression.ipynb → Prediksi rating atau popularitas 

05_model_clustering.ipynb → Pengelompokan game berdasarkan karakteristik 

Hasil visualisasi dan grafik otomatis disimpan ke folder /reports/figures/. 


# bigdata-uts-ganjil-2526

Struktur folder proyek:
├─ data/
│  ├─ raw/           # hasil scraping mentah (CSV/JSON)
│  └─ external/      # dataset open-source
├─ notebooks/
│  ├─ 00_scraping.ipynb
│  ├─ 01_cleaning_eda.ipynb
│  ├─ 02_preprocessing.ipynb
│  ├─ 03_model_classification.ipynb
│  ├─ 04_model_regression.ipynb
│  └─ 05_model_clustering.ipynb
├─ src/               # fungsi bantu (py)
│  ├─ scraping/
│  ├─ cleaning/
│  └─ modeling/
├─ reports/
│  ├─ figures/
│  └─ KelompokX_TugasBesarBigData.pdf
├─ KelompokX_Code.ipynb
└─ README.md
