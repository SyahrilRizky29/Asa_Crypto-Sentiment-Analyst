# 🚀 Asa Crypto Sentiment Analyst (n8n Automation)

Sistem otomasi cerdas berbasis **n8n** yang dirancang untuk memantau sentimen pasar cryptocurrency ($BTC & $ETH) secara real-time. Proyek ini mengintegrasikan AI untuk analisis teks, Google Sheets sebagai database historis, dan Telegram sebagai media pelaporan otomatis.

## 📊 Alur Kerja Sistem

1.  **Data Collection:** Mengambil data mention crypto setiap 15 menit menggunakan mekanisme simulasi/RSS.
2.  **AI Sentiment Processing:** Menggunakan model **Mimo-v2-flash** (via OpenRouter) untuk menentukan label sentimen (*Positive, Negative, Neutral*) dan skor kekuatan sentimen.
3.  **Database Management:** Menyimpan data terstruktur (Timestamp, ID, Teks, Score, Label) ke **Google Sheets** menggunakan logika JavaScript `split()` untuk pemisahan data.
4.  **Daily Analytics:** Setiap jam 07:00 pagi, sistem menarik seluruh data harian, menghitung persentase dominasi sentimen menggunakan **JavaScript**.
5.  **Smart Reporting:** AI merangkum statistik harian menjadi narasi pasar (Bullish/Bearish) dan mengirimkannya ke **Telegram**.

## 🛠️ Tech Stack

* **Automation:** [n8n](https://n8n.io/)
* **Artificial Intelligence:** OpenRouter (Mimo-v2-flash)
* **Database:** Google Sheets API
* **Messaging:** Telegram Bot API
* **Scripting:** JavaScript (Node.js)

## 📂 Struktur Repositori

* `Asa_Crypto_Sentiment_Analyst.json`: File workflow n8n yang dapat di-import langsung.
* `crypto_rss_sentiment.ipynb`: Script Python (Google Colab) untuk penyedia data RSS awal.

## 🚀 Cara Instalasi

1.  **n8n Setup:**
    * Import file `Asa_Crypto_Sentiment_Analyst.json` ke kanvas n8n Anda.
    * Konfigurasikan kredensial: Google Sheets OAuth2, Telegram Bot API, dan OpenRouter API.
2.  **Spreadsheet Setup:**
    * Buat Google Sheets dengan header: `Timestamp`, `Tweet_ID`, `Tweet_Text`, `Hasil_Analisis_AI`, `Score`.
    * Masukkan `Document ID` Sheets tersebut ke dalam node Google Sheets di n8n.
3.  **Activation:**
    * Klik **Save** dan nyalakan tombol **Active** untuk menjalankan sistem secara otomatis.
---
