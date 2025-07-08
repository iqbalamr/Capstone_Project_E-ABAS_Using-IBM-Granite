# Capstone_Project_E-ABAS_Using-IBM-Granite

Analisis Emosi-Aspek pada Ulasan E-commerce Menggunakan AI

Analisis mendalam terhadap ulasan pelanggan e-commerce untuk mengidentifikasi masalah operasional spesifik menggunakan IBM Granite dan pendekatan "Prompt Mikro".

---

## Project Overview

**Tujuan Proyek:** Proyek ini bertujuan untuk merancang dan mengimplementasikan sebuah sistem analisis bernama **E-ABAS (Emotion-Aspect Based Analysis System)**. Sistem ini secara spesifik mengklasifikasikan **emosi** (misalnya, marah, senang) dan **aspek layanan** (misalnya, pengiriman, kualitas produk) dari ulasan pelanggan untuk menghasilkan *insight* operasional yang presisi, melampaui analisis sentimen konvensional.

**Masalah Bisnis:** Di pasar e-commerce yang sangat kompetitif, memahami umpan balik pelanggan adalah kunci retensi. Namun, analisis sentimen standar (positif/negatif) tidak cukup. Sebuah ulasan negatif tentang "kurir yang lambat" dan "produk yang cacat" sama-sama dikategorikan 'negatif', padahal memerlukan tindakan perbaikan dari departemen yang berbeda (Logistik vs. Manajemen Produk). Proyek ini memecahkan masalah kesenjangan informasi tersebut.

**Pendekatan:** Solusi dikembangkan menggunakan **IBM Granite Models** yang diakses melalui API **Replicate**. Pendekatan teknis yang digunakan adalah **"Prompt Mikro"**, di mana satu tugas analisis yang kompleks dipecah menjadi tiga panggilan API yang lebih sederhana dan fokus (untuk sentimen, emosi, dan aspek secara terpisah). Hal ini terbukti secara signifikan meningkatkan akurasi dan keandalan output AI.

---

## Raw Dataset Link

Proyek ini secara eksklusif menggunakan dataset **PRDECT-ID** yang tersedia secara publik dan telah divalidasi secara akademis.

* **Sumber:** [PRDECT-ID (Indonesian product reviews dataset for emotions classification tasks)] https://github.com/rhiosutoyo/PRDECT-ID-Indonesian-Product-Reviews-Dataset/tree/main
* **Lisensi:** Data ini tersedia untuk tujuan riset dan edukasi.

---

## Insight & Findings

Analisis terhadap 400 ulasan pelanggan menghasilkan beberapa temuan kunci yang dapat ditindaklanjuti:

* **Insight 1: Logistik adalah Pemicu Emosi Negatif Terkuat.**
    Visualisasi *heatmap* menunjukkan korelasi yang sangat kuat antara **emosi "Marah" (Anger)** dengan **aspek "Pengiriman" (shipping)**. Ini membuktikan secara kuantitatif bahwa masalah keterlambatan dan penanganan paket adalah sumber frustrasi terbesar bagi pelanggan, melebihi masalah harga atau bahkan kualitas produk.

* **Insight 2: Kualitas Produk Memicu Kekecewaan.**
    Emosi **"Sedih" (Sadness)**, yang merepresentasikan kekecewaan, paling sering berpasangan dengan aspek **"Kualitas Produk" (product_quality)**. Ini mengindikasikan adanya kesenjangan antara ekspektasi pelanggan (dari foto/deskripsi) dengan produk fisik yang diterima.

* **Insight 3: Konsistensi Logika AI Terbukti.**
    *Heatmap* korelasi Sentimen vs. Emosi menunjukkan bahwa model AI berpikir secara logis. Emosi seperti 'Anger' dan 'Sadness' hampir selalu diklasifikasikan dengan sentimen 'Negative', sementara 'Happy' dan 'Love' diklasifikasikan sebagai 'Positive', yang memvalidasi keandalan model.

* **Insight 4: Deteksi Multi-Aspek dalam Satu Ulasan.**
    Pendekatan "Prompt Mikro" berhasil mengidentifikasi beberapa aspek dalam satu ulasan. Contohnya, pada ulasan *"Pelayanannya ramah, tapi pengirimannya lama"*, sistem berhasil mendeteksi aspek `['customer_service', 'shipping']`, memberikan gambaran yang lebih utuh kepada bisnis.

---

## AI Support Explanation

Kecerdasan Buatan (AI) adalah inti dari proyek ini, diimplementasikan dengan strategi yang matang untuk memastikan akurasi dan keandalan.

* **Model yang Digunakan:** **IBM Granite (`ibm/granite-3.3-8b-instruct`)** diakses melalui platform API **Replicate**.
* **Cara Penggunaan:** AI tidak diberi satu perintah kompleks, melainkan tiga perintah sederhana yang terpisah (**Prompt Mikro**) untuk melakukan tugas-tugas berikut:
    1.  **Klasifikasi Sentimen:** Menentukan sentimen (Positive, Negative, Neutral).
    2.  **Klasifikasi Emosi:** Menentukan emosi (Happy, Sadness, Anger, dll).
    3.  **Ekstraksi Aspek:** Mengidentifikasi semua aspek relevan yang dibahas dalam ulasan.
* **Optimalisasi:** Parameter `temperature` diatur ke **0** untuk memastikan output yang **deterministik** (konsisten dan tidak acak). Kode *parser* juga dibuat secara "defensif" untuk dapat mengekstrak informasi inti bahkan jika output AI sedikit tidak sempurna. Pendekatan ini terbukti mampu mengatasi masalah ketidakstabilan output dan menghasilkan analisis yang akurat.
