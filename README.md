# Deteksi Sintesis IndoT5 Menggunakan mDeBERTa v3

Repository ini berisi keseluruhan pipeline eksperimen untuk mendeteksi teks buatan AI (AI-generated text) pada abstrak jurnal ilmiah berbahasa Indonesia. Fokus utama penelitian ini adalah menguji kemampuan model `mDeBERTa-v3` dalam mendeteksi teks sintesis yang di-generate oleh model `IndoT5-base-paraphrase`.

## Latar Belakang Proyek
Meningkatnya penggunaan AI generatif dalam penulisan akademis membutuhkan sistem deteksi yang andal. Proyek ini mengekstraksi abstrak tulisan manusia dari portal jurnal SINTA 3, kemudian menyintesis data ekuivalen menggunakan model `IndoT5-base-paraphrase` untuk membuat dataset klasifikasi yang seimbang. Kemampuan deteksi kemudian dievaluasi menggunakan pendekatan Machine Learning tradisional (Random Forest) sebagai baseline, dan model pre-trained `mDeBERTa-v3` sebagai eksperimen utama.

## Alur Kerja (Pipeline)
1. **Data Acquisition:** Scraping data mentah abstrak jurnal via OAI-PMH.
2. **Data Synthesis (IndoT5):** Pembuatan dataset AI menggunakan teknik parafrase dengan `Wikidepia/IndoT5-base-paraphrase`.
3. **Data Cleaning & Preprocessing:** Pembersihan artefak mesin, case folding, dan penyeragaman panjang teks (truncation maksimal 100 kata).
4. **Linguistic Analysis:** Uji statistik Mann-Whitney U terhadap 7 fitur linguistik untuk melihat anomali teks sintesis.
5. **Baseline Model:** Pelatihan model Random Forest Classifier berbasis ekstraksi fitur linguistik.
6. **Advanced Inference (mDeBERTa v3):** Pengujian Zero-Shot Classification menggunakan `MoritzLaurer/mDeBERTa-v3-base-mnli-xnli` dengan berbagai skenario (1 aspek, 3 aspek, dan 5 aspek) untuk mendeteksi teks IndoT5.

## Struktur Direktori
* `/data` : Folder untuk menyimpan dataset mentah (raw), setengah jadi (interim), dan final (processed). *(Diabaikan oleh gitignore)*
* `/notebooks` : Kumpulan Jupyter Notebook yang berisi eksperimen berurutan dari scraping hingga evaluasi model.
* `requirements.txt` : Daftar dependensi library Python.

## Teknologi yang Digunakan
* **Hugging Face Transformers** (IndoT5 & mDeBERTa v3)
* **Python 3.x**
* **Pandas, NumPy, Scikit-Learn** (Data processing & Baseline ML)
* **BeautifulSoup & Requests** (Web Scraping OAI-PMH)
* **Matplotlib & Seaborn** (Visualisasi Data)

## Cara Menjalankan
1. Clone repository ini.
2. Install dependensi dengan menjalankan `pip install -r requirements.txt`.
3. Jalankan notebook di dalam folder `/notebooks` secara berurutan mulai dari `01_data_scraping.ipynb`.