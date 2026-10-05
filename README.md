# WeTV App Reviews Multi-Class Sentiment Analysis

Proyek analisis sentimen multi-kelas (Positif, Netral, Negatif) pada ulasan aplikasi **WeTV** di Google Play Store Indonesia. Proyek ini membandingkan algoritma *Machine Learning* klasik dengan pendekatan *Deep Learning* sekuensial (BiLSTM) menggunakan skema pelabelan berbasis leksikon (*lexicon-based labeling*).

---

## Ringkasan Project

- **Sumber Data:** Google Play Store ulasan aplikasi WeTV (`com.tencent.qqlivei18n`)
- **Skala Data:** $\ge$ 10.000 sampel ulasan bahasa Indonesia
- **Kelas Target:** 3 Kelas (`Positif`, `Netral`, `Negatif`)
- **Metode Pelabelan:** *Lexicon-Based Polarity Scoring* (InSet / VADER Bahasa Indonesia)
- **Arsitektur Model:**
  - **Skema 1:** TF-IDF + Support Vector Machine (Linear SVM)
  - **Skema 2:** TF-IDF (N-gram) + Logistic Regression / Random Forest
  - **Skema 3:** Tokenizer + Embedding Layer + Bidirectional LSTM (BiLSTM)

---

## Target & Metrik Evaluasi

- **Akurasi Minimum Submission:** $\ge$ 85%
- **Target Model Unggulan (BiLSTM):** $\ge$ 92% (Train & Test)
- **Metrik Evaluasi:** Accuracy, Precision, Recall, F1-Score, dan Confusion Matrix.

---

## 📂 Struktur Direktori

```text
├── data/
│   ├── raw/                 # Dataset mentah hasil scraping
│   └── processed/           # Dataset bersih yang telah dilabeli leksikon
├── notebooks/
│   └── wetv_sentiment_analysis.ipynb   # Notebook pengerjaan utama
├── scripts/
│   ├── scrape_playstore.py  # Script scraping Python mandiri
│   └── lexicon_labeler.py   # Modul pelabelan polaritas teks
├── requirements.txt         # Daftar dependensi pustaka
└── README.md                # Dokumentasi proyek
