# Proyek Analisis Sentimen Ulasan Aplikasi Play Store

![Image](https://github.com/user-attachments/assets/c80c7b7b-1440-4399-9099-3dff66214c43)

## 📋 Deskripsi Proyek

Proyek ini bertujuan untuk melakukan analisis sentimen terhadap ulasan aplikasi Google Play Store dengan menggunakan teknik Natural Language Processing (NLP) dan Machine Learning. Proyek ini mengumpulkan data ulasan secara mandiri melalui proses web scraping, melakukan preprocessing data, ekstraksi fitur, dan melatih berbagai model machine learning hingga deep learning untuk mengklasifikasikan sentimen ulasan ke dalam kategori positif, netral, dan negatif.

## 🎯 Tujuan

- Mengumpulkan minimal 3.000 ulasan dari Google Play Store menggunakan teknik web scraping
- Melakukan preprocessing dan ekstraksi fitur pada data teks ulasan
- Melatih model machine learning dengan akurasi minimal 85% pada data testing
- Membandingkan beberapa pendekatan algoritma dan metode ekstraksi fitur
- Membuat fungsi inferensi untuk memprediksi sentimen dari teks baru

## 📊 Dataset

Dataset terdiri dari ulasan pengguna yang dikumpulkan dari 10 aplikasi populer di Google Play Store Indonesia:
- Gojek
- Tokopedia
- Shopee
- Instagram
- WhatsApp
- Netflix
- Spotify
- Bukalapak
- Traveloka
- Grab

Setiap ulasan memiliki atribut:
- `content`: teks ulasan
- `score`: nilai rating (1-5)
- `app_name`: nama aplikasi
- `at`: waktu ulasan ditulis
- dan atribut lainnya

## 🛠️ Alur Kerja

### 1. Web Scraping
Data dikumpulkan menggunakan library `google-play-scraper` untuk mengambil ulasan dari aplikasi-aplikasi terpilih. Script scraping (`scraping_playstore.py`) secara otomatis mengambil dan menyimpan data ulasan dalam format CSV dan JSON.

### 2. Preprocessing Data
Preprocessing data meliputi:
- Konversi teks ke lowercase
- Penghapusan URL dan HTML tags
- Penghapusan angka dan tanda baca
- Penghapusan stopwords Bahasa Indonesia
- Tokenisasi dan stemming

### 3. Ekstraksi Fitur
Dua metode ekstraksi fitur utama yang digunakan:
- **TF-IDF (Term Frequency-Inverse Document Frequency)**: Mengubah teks menjadi vektor numerik berdasarkan frekuensi kata
- **Word2Vec**: Mengubah kata-kata menjadi vektor embedding dengan mempertahankan hubungan semantik

### 4. Pelabelan Data
Data diberi label berdasarkan rating:
- Rating 1-2: Sentimen Negatif
- Rating 3: Sentimen Netral
- Rating 4-5: Sentimen Positif

### 5. Pemodelan
Tiga skema pelatihan yang berbeda diimplementasikan:
1. **SVM dengan TF-IDF (80/20 split)**
2. **Random Forest dengan Word2Vec (80/20 split)**
3. **Random Forest dengan TF-IDF (70/30 split)**

Selain itu, model Deep Learning berbasis **Bidirectional LSTM** juga diimplementasikan untuk mencapai akurasi yang lebih tinggi.

## 📈 Hasil

| Model | Ekstraksi Fitur | Split Data | Akurasi Training | Akurasi Testing |
|-------|----------------|------------|-----------------|-----------------|
| SVM | TF-IDF | 80/20 | 95.2% | 88.7% |
| Random Forest | Word2Vec | 80/20 | 97.1% | 86.5% |
| Random Forest | TF-IDF | 70/30 | 94.8% | 87.3% |
| BiLSTM | Embedding | 80/20 | 96.3% | 93.1% |

Model Bidirectional LSTM mencapai akurasi tertinggi sebesar 93.1% pada data testing.

## 🚀 Penggunaan

### Persyaratan
Instal semua dependencies yang diperlukan:

```bash
pip install -r requirements.txt
```

### Scraping Data
Untuk mengumpulkan data ulasan baru:

```bash
python scraping_playstore.py
```

### Pelatihan Model
Model dilatih melalui Jupyter Notebook `analisis_sentimen.ipynb`. Notebook ini berisi semua langkah dari load data hingga evaluasi model.

### Inferensi
Fungsi `predict_sentiment()` dapat digunakan untuk memprediksi sentimen dari teks baru:

```python
text = "Aplikasi ini sangat membantu dan mudah digunakan!"
sentiment = predict_sentiment(text, model_type='deep_learning')
print(f"Sentimen: {sentiment}")
```

## 📁 Struktur Proyek

```
.
├── scraping_playstore.py           # Script scraping data
├── analisis_sentimen.ipynb         # Notebook analisis dan pelatihan model
├── playstore_reviews.csv           # Dataset hasil scraping
├── requirements.txt                # Daftar package yang dibutuhkan
└── README.md                       # Dokumentasi proyek
```

## 🔮 Pengembangan Selanjutnya

Beberapa ide untuk pengembangan proyek di masa depan:
- Implementasi analisis sentimen multi-bahasa
- Penambahan deteksi aspek (aspect-based sentiment analysis)
- Pengembangan dashboard interaktif untuk visualisasi hasil
- Implementasi model yang lebih ringan untuk deployment
- Perluasan dataset dengan lebih banyak ulasan dan kategori aplikasi

## 📚 Referensi

- [Natural Language Processing with Python](https://www.nltk.org/book/)
- [Hands-On Machine Learning with Scikit-Learn, Keras, and TensorFlow](https://www.oreilly.com/library/view/hands-on-machine-learning/9781492032632/)
- [Deep Learning for Natural Language Processing](https://www.tensorflow.org/tutorials/text/text_classification_rnn)
- [Sentiment Analysis for Indonesian Language](https://www.researchgate.net/publication/337099858_Sentiment_Analysis_for_Indonesian_Language_A_Systematic_Literature_Review)

## 📝 Lisensi

Proyek ini dilisensikan di bawah MIT License - lihat file [LICENSE](LICENSE) untuk detail.

## 👨‍💻 Pengembang

Dikembangkan sebagai proyek submission untuk kursus Analisis Sentimen.
