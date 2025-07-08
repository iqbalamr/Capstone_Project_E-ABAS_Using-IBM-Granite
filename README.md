# Capstone_Project_E-ABAS_Using-IBM-Granite

<p align="center">
  <img src="https://img.shields.io/badge/AI_Model-IBM_Granite-blue.svg" alt="Model AI">
  <img src="https://img.shields.io/badge/Platform-Replicate-lightgrey.svg" alt="Platform">
  <img src="https://img.shields.io/badge/Language-Python-yellow.svg" alt="Bahasa">
  <img src="https://img.shields.io/badge/Project-Capstone-success.svg" alt="Proyek">
</p>

# Analisis Emosi-Aspek pada Ulasan E-commerce Menggunakan AI

### 🚀 Sebuah Sistem Analisis untuk Mengungkap Insight Operasional dari Suara Pelanggan

Proyek ini mendemonstrasikan pembangunan sistem **E-ABAS (Emotion-Aspect Based Analysis System)** untuk menganalisis ulasan pelanggan e-commerce secara mendalam, melampaui analisis sentimen konvensional.

---

### ✨ Insight Kunci: Peta Masalah Operasional

Salah satu temuan utama dari 400 ulasan yang dianalisis adalah korelasi kuat antara emosi pelanggan dengan aspek layanan tertentu, yang divisualisasikan dalam *heatmap* di bawah ini.

![Heatmap Korelasi Emosi vs Aspek](https://github.com/iqbalamr/Capstone_Project_E-ABAS_Using-IBM-Granite/blob/main/Visualisasi/heatmap_emosi_vs_aspek.png)
*Visualisasi ini menunjukkan bahwa keluhan **pengiriman** adalah pemicu **kemarahan** terbesar, sementara isu **kualitas produk** lebih sering menimbulkan **kekecewaan (sedih)**.*

---

### 📋 Daftar Isi
1.  [Project Overview](#project-overview)
2.  [Sumber Dataset](#sumber-dataset)
3.  [Temuan & Visualisasi](#temuan--visualisasi)
4.  [Rekomendasi Bisnis](#rekomendasi-bisnis)
5.  [Penjelasan Dukungan AI](#penjelasan-dukungan-ai)
6.  [Teknologi yang Digunakan](#teknologi-yang-digunakan)

---

## 1. Project Overview

**🎯 Tujuan Proyek:** Merancang sistem untuk mengklasifikasikan **emosi spesifik** (marah, senang, dll.) dan **aspek layanan** (pengiriman, kualitas produk, dll.) dari ulasan pelanggan, guna memberikan *insight* yang presisi untuk pengambilan keputusan bisnis.

**❗ Masalah Bisnis:** Analisis sentimen konvensional ('Positif'/'Negatif') tidak cukup untuk mengidentifikasi akar masalah. Ulasan "kurir lambat" dan "produk cacat" sama-sama negatif, namun memerlukan solusi dari departemen yang berbeda. Proyek ini memecahkan masalah kesenjangan informasi tersebut.

**💡 Pendekatan:** Solusi dikembangkan menggunakan **IBM Granite Models** via API **Replicate**. Pendekatan teknisnya adalah **"Prompt Mikro"**, di mana satu tugas kompleks dipecah menjadi tiga panggilan API yang lebih sederhana (untuk sentimen, emosi, dan aspek secara terpisah) untuk meningkatkan akurasi dan keandalan.

---

## 2. Sumber Dataset

Proyek ini menggunakan dataset **PRDECT-ID** yang tersedia secara publik dan telah divalidasi secara akademis, memastikan kualitas dan kredibilitas analisis.

* **Link Sumber:** [PRDECT-ID (Indonesian product reviews dataset for emotions classification tasks)]([https://raw.githubusercontent.com/rizalespe/Dataset-Sentimen-Analisis-Bahasa-Indonesia/master/data/PRDECT-ID/PRDECT-ID%20(train).csv](https://github.com/rhiosutoyo/PRDECT-ID-Indonesian-Product-Reviews-Dataset/tree/main/Dataset))

---

## 3. Temuan & Visualisasi

### Distribusi Emosi Pelanggan
Analisis menunjukkan bahwa emosi **'Happy'** dan **'Sadness'** (yang merepresentasikan kekecewaan) adalah dua emosi yang paling dominan dalam ulasan. Ini menandakan bahwa pelanggan paling vokal saat mereka sangat puas atau sangat kecewa.

![Distribusi Emosi](https://github.com/iqbalamr/Capstone_Project_E-ABAS_Using-IBM-Granite/blob/main/Visualisasi/distribusi_emosi.png)

### Konsistensi Logika Model AI
*Heatmap* Emosi vs. Sentimen membuktikan bahwa model berpikir secara logis. Emosi negatif seperti 'Anger' dan 'Sadness' secara konsisten diklasifikasikan dengan sentimen 'Negative', yang memvalidasi keandalan model.

![Heatmap Emosi vs Sentimen](https://github.com/iqbalamr/Capstone_Project_E-ABAS_Using-IBM-Granite/blob/main/Visualisasi/heatmap_emosi_vs_sentimen.png)

---

## 4. Rekomendasi Bisnis

Berdasarkan *insight* yang didapat, berikut adalah tiga rekomendasi konkret yang dapat ditindaklanjuti:

1.  **🚨 Untuk Tim Logistik: Buat *Early Warning System***
    * **Aksi:** Implementasikan dasbor yang memantau metrik "Jumlah Ulasan 'Anger' pada Aspek 'shipping'". Jika naik >20% dari rata-rata, kirim notifikasi otomatis ke kepala logistik.
    * **Dampak:** Memungkinkan intervensi cepat pada masalah kurir atau hub sebelum masalah meluas.

2.  **⭐ Untuk Tim Kategori: Buat *Vendor Health Score***
    * **Aksi:** Gunakan data korelasi "Sadness" & "product_quality" untuk menilai vendor. Vendor dengan tingkat keluhan kualitas yang tinggi perlu diaudit atau diberi pelatihan.
    * **Dampak:** Meningkatkan kualitas produk secara keseluruhan dan mengurangi tingkat pengembalian barang.

3.  **📣 Untuk Tim Pemasaran: Manfaatkan Keunggulan Operasional**
    * **Aksi:** Selain perang harga, jalankan kampanye pemasaran yang menonjolkan "Jaminan Pengiriman Cepat & Aman".
    * **Dampak:** Menarik pelanggan yang memprioritaskan keandalan layanan, bukan hanya harga murah.

---

## 5. Penjelasan Dukungan AI

> Kecerdasan Buatan (AI) adalah inti dari proyek ini, diimplementasikan dengan strategi matang untuk memastikan akurasi. Model yang digunakan adalah **IBM Granite** yang diakses melalui **Replicate**. Kunci keberhasilan proyek ini adalah pendekatan **"Prompt Mikro"**, yaitu memecah satu masalah kompleks menjadi tiga tugas klasifikasi sederhana yang terpisah. Parameter `temperature` diatur ke **0** untuk output yang deterministik dan konsisten. Pendekatan berlapis ini terbukti mampu menghasilkan analisis yang andal dari teks ulasan yang kompleks dan penuh bahasa gaul.

---

## 6. Teknologi yang Digunakan

* **Bahasa Pemrograman:** Python
* **Library Utama:** Pandas, Matplotlib, Seaborn, Scikit-learn
* **Model AI:** IBM Granite (`ibm/granite-3.3-8b-instruct`)
* **Platform Eksekusi:** Google Colab
* **Platform API:** Replicate

---
