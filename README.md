# WeTV App Reviews Multi-Class Sentiment Analysis

Proyek analisis sentimen multi-kelas (Positif, Netral, Negatif) pada ulasan aplikasi **WeTV** di Google Play Store Indonesia. Proyek ini membandingkan kinerja model _Machine Learning_ klasik dengan arsitektur _Deep Learning_ sekuensial (BiLSTM) menggunakan skema pelabelan berbasis leksikon (_lexicon-based labeling_).

---

## Ringkasan Proyek

- **Sumber Data:** Google Play Store ulasan aplikasi WeTV (`com.tencent.qqlivei18n`)
- **Skala Data:** 11.001 ulasan bersih (setelah deduping & pembersihan teks)
- **Kelas Target:** 3 Kelas (`positif`, `netral`, `negatif`)
- **Metode Pelabelan:** _InSet Lexicon Polarity Scoring_ (Kamus Leksikon Bahasa Indonesia)
- **Strategi Pemisahan Data:** 80% Data Latih, 20% Data Uji (_Stratified Split_)
- **Skema Pemodelan:**
  - **Skema 1:** TF-IDF (Unigram + Bigram) + Multinomial Naive Bayes (Baseline)
  - **Skema 2:** TF-IDF + Random Forest Classifier (GridSearchCV & Class Weighting)
  - **Skema 3:** Keras Tokenizer + Word Embedding (128-dim) + Bidirectional LSTM (BiLSTM)

---

## Ringkasan Kinerja Model

| Skema Pemodelan             | Fitur Input    | Akurasi Uji | F1-Score (Macro) | F1-Score (Weighted) | Keterangan                                      |
| :-------------------------- | :------------- | :---------: | :--------------: | :-----------------: | :---------------------------------------------- |
| **Skema 1: Multinomial NB** | TF-IDF         |   71.83%    |      0.4521      |       0.6428        | Model baseline probabilistik                    |
| **Skema 2: Random Forest**  | TF-IDF         |   86.07%    |      0.8070      |       0.8606        | Optimasi _balanced class weights_               |
| **Skema 3: BiLSTM**         | Word Embedding | **89.37%**  |    **0.8426**    |     **0.8961**      | **Model Terbaik** (Konteks sekuensial & negasi) |

---

## Alur Pipeline Prapemrosesan Teks

1. **Text Cleaning:** Menghapus mention, tagar, URL, angka, dan karakter simbol/tanda baca.
2. **Case Folding:** Menyeragamkan seluruh karakter teks menjadi huruf kecil (_lowercase_).
3. **Slang Normalization:** Memperbaiki singkatan/bahasa gaul menggunakan kamus slang terkurasi dari korpus ulasan WeTV.
4. **Tokenization:** Pemecahan kalimat menjadi token kata individual.
5. **Selective Stopword Removal:** Penyaringan kata umum dengan tetap mempertahankan kata negasi (_tidak_, _bukan_, _jangan_, _belum_, _kurang_, _tanpa_).

---

## Struktur Direktori

```text
├── wetv-scraping.ipynb               # Notebook scraping ulasan Google Play Store
├── wetv-sentiment-analysis.ipynb     # Notebook utama
├── requirements.txt                  # Dokumentasi dependensi pustaka environment
└── README.md                         # Dokumentasi resmi proyek
```
