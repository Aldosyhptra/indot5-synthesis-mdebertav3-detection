# IndoT5 Synthesis Detection Using mDeBERTa v3 

## Publication / Citation
The complete methodology, experiments, and findings of this repository are published in the **International Journal of Data Science (IJODAS)** (SINTA 2). 

**Read the full paper here:** [Zero-Shot Detection of IndoT5-Synthesized Indonesian Scientific Abstracts Using mDeBERTa v3](https://jurnal.yoctobrain.org/index.php/ijodas/article/view/457)

---

## Pipeline
1. **Data Acquisition:** Scraping raw journal abstracts via OAI-PMH.
2. **Pre-processing Stage 1:** Initial cleaning of human texts (removing HTML entities, encoding anomalies, introductory words) and document length filtering.
3. **Data Synthesis (IndoT5):** Creating an AI dataset using paraphrasing techniques with `Wikidepia/IndoT5-base-paraphrase`.
4. **Pre-processing Stage 2:** Removing machine artifacts from AI generation, case folding, standardizing text length (truncating to a maximum of 100 words), and class balancing (undersampling).
5. **Linguistic Analysis:** Applying the Mann-Whitney U statistical test on 7 linguistic features to identify anomalies in synthesized texts.
6. **Baseline Model:** Training a Random Forest Classifier based on the extracted linguistic features.
7. **Advanced Inference (mDeBERTa v3):** Testing Zero-Shot Classification using `MoritzLaurer/mDeBERTa-v3-base-mnli-xnli` under various scenarios (1-aspect, 3-aspect, and 5-aspect) to detect IndoT5 texts.

## Directory Structure
* `/data` : Folder for storing raw, interim, and processed datasets. *(Ignored by gitignore)*
* `/notebooks` : A collection of Jupyter Notebooks containing sequential experiments from scraping to model evaluation.
* `requirements.txt` : List of Python library dependencies.

## Technologies Used
* **Hugging Face Transformers** (IndoT5 & mDeBERTa v3)
* **Python 3.12.13**
* **Pandas, NumPy, Scikit-Learn** (Data processing & Baseline ML)
* **BeautifulSoup & Requests** (Web Scraping OAI-PMH)
* **Matplotlib & Seaborn** (Data Visualization)

## How to Run
1. Clone this repository.
2. Install the dependencies by running `pip install -r requirements.txt`.
3. Execute the notebooks in the `/notebooks` folder sequentially, starting from `01_data_scraping.ipynb`.

<br>

---

<br>

# Deteksi Sintesis IndoT5 Menggunakan mDeBERTa v3 

## Publikasi / Sitasi
Metodologi, eksperimen, dan temuan lengkap dari repositori ini telah dipublikasikan pada **International Journal of Data Science (IJODAS)** (SINTA 2).

**Baca naskah lengkapnya di sini:** [Zero-Shot Detection of IndoT5-Synthesized Indonesian Scientific Abstracts Using mDeBERTa v3](https://jurnal.yoctobrain.org/index.php/ijodas/article/view/457)

---

## Alur Kerja (Pipeline)
1. **Data Acquisition:** Scraping data mentah abstrak jurnal via OAI-PMH.
2. **Pre-processing Tahap 1:** Pembersihan awal teks manusia (penghapusan entitas HTML, anomali encoding, kata pengantar) dan penyaringan panjang dokumen.
3. **Data Synthesis (IndoT5):** Pembuatan dataset AI menggunakan teknik parafrase dengan `Wikidepia/IndoT5-base-paraphrase`.
4. **Pre-processing Tahap 2:** Pembersihan artefak mesin hasil generasi AI, *case folding*, penyeragaman panjang teks (*truncation* maksimal 100 kata), dan penyeimbangan kelas (*undersampling*).
5. **Linguistic Analysis:** Uji statistik Mann-Whitney U terhadap 7 fitur linguistik untuk melihat anomali teks sintesis.
6. **Baseline Model:** Pelatihan model Random Forest Classifier berbasis ekstraksi fitur linguistik.
7. **Advanced Inference (mDeBERTa v3):** Pengujian Zero-Shot Classification menggunakan `MoritzLaurer/mDeBERTa-v3-base-mnli-xnli` dengan berbagai skenario (1 aspek, 3 aspek, dan 5 aspek) untuk mendeteksi teks IndoT5.

## Struktur Direktori
* `/data` : Folder untuk menyimpan dataset mentah (raw), setengah jadi (interim), dan final (processed). *(Diabaikan oleh gitignore)*
* `/notebooks` : Kumpulan Jupyter Notebook yang berisi eksperimen berurutan dari scraping hingga evaluasi model.
* `requirements.txt` : Daftar dependensi library Python.

## Teknologi yang Digunakan
* **Hugging Face Transformers** (IndoT5 & mDeBERTa v3)
* **Python 3.12.13**
* **Pandas, NumPy, Scikit-Learn** (Data processing & Baseline ML)
* **BeautifulSoup & Requests** (Web Scraping OAI-PMH)
* **Matplotlib & Seaborn** (Visualisasi Data)

## Cara Menjalankan
1. Clone repository ini.
2. Install dependensi dengan menjalankan `pip install -r requirements.txt`.
3. Jalankan notebook di dalam folder `/notebooks` secara berurutan mulai dari `01_data_scraping.ipynb`.