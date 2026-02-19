# Analisis Spasiotemporal Hotspot Provinsi Jambi (2010-2020)

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-Research-orange)

## Deskripsi Proyek

Repositori ini berisi *pipeline* pemrosesan data untuk menganalisis sebaran titik panas (*hotspot*) kebakaran hutan dan lahan di **Provinsi Jambi** selama satu dekade (2010-2020). Data bersumber dari satelit **MODIS (NASA FIRMS)**.

Script ini melakukan otomatisasi proses:
1.  **Filtering**: Menyaring titik panas berdasarkan tingkat kepercayaan (*Confidence Level* > 80%).
2.  **Spatial Clipping**: Memotong data titik panas global/regional agar pas dengan batas administrasi Provinsi Jambi.
3.  **Time Series Analysis**: Menganalisis tren kejadian kebakaran secara harian, bulanan (musiman), dan tahunan.
4.  **Visualization**: Menghasilkan grafik fluktuasi, pola musiman, dan *heatmap* intensitas kejadian.

## Metodologi

Alur kerja analisis data dalam script ini adalah sebagai berikut:

1.  **Input Data Mentah**: Shapefile Hotspot per tahun (2010-2020).
2.  **Preprocessing**:
    * Standardisasi CRS (Coordinate Reference System) ke `EPSG:4326`.
    * Seleksi atribut (`ACQ_DATE`, `CONFIDENCE`).
3.  **Pembersihan Data (*Cleaning*)**:
    * Hapus data dengan *low confidence*.
    * Hapus data di luar batas wilayah Jambi (menggunakan `geopandas.clip`).
4.  **Output**:
    * Shapefile bersih (`.shp`) per tahun.
    * Tabel rekapitulasi (`.csv`).
    * Grafik analisis (`.png` ditampilkan di notebook).

## Struktur Direktori Google Drive

Script ini dirancang untuk berjalan di **Google Colab** dan mengakses data melalui Google Drive. Agar script berjalan tanpa error, susun folder Drive Anda sebagai berikut:

```text
/My Drive/Colab Notebooks/Skripsi/
├── Batas Adm Jambi/
│   └── Adm_Jambi_Prov.shp      <-- Shapefile Batas Provinsi
├── NASA-FIRMS Fire (New2)/     <-- Folder Data Mentah
│   ├── DL_FIRE_M-C61_587963_2010/
│   │   └── fire_archive_M-C61_587963.shp
│   ├── DL_FIRE_M-C61_587964_2011/
│   └── ... (dst sampai 2020)
└── Hotspot Clean Jambi/        <-- (Output Folder: Dibuat Otomatis oleh Script)

```

## Prasyarat Instalasi

Script membutuhkan pustaka Python berikut:

```bash
pip install geopandas pandas matplotlib seaborn

```

## Cara Penggunaan

1. Unggah data Shapefile (Batas Admin & Hotspot Raw) ke Google Drive sesuai struktur di atas.
2. Buka script `.ipynb` di Google Colab.
3. Jalankan sel secara berurutan.
4. Hasil Shapefile bersih dan file CSV akan tersimpan otomatis di folder `Hotspot Clean Jambi` di Google Drive Anda.

## Visualisasi yang Dihasilkan

Script akan menampilkan tiga jenis visualisasi utama:

1. **Line Chart:** Fluktuasi harian/tahunan jumlah hotspot untuk melihat tren kenaikan/penurunan kejadian kebakaran.
2. **Bar Chart (Seasonal):** Akumulasi hotspot per bulan (Jan-Des) untuk mengidentifikasi puncak musim kebakaran.
3. **Heatmap Matrix:** Matriks Tahun vs Bulan untuk melihat intensitas kejadian secara komprehensif.

## Penulis

**Jariyan Arifudin** Mahasiswa Geografi Lingkungan

Universitas Gadjah Mada (UGM)

## Lisensi & Sitasi

Kode ini didistribusikan di bawah **MIT License**.
Jika Anda menggunakan metode ini untuk penelitian, silakan sitasi repositori ini:

> Arifudin, J. (2026). *Analisis Spasiotemporal Hotspot Provinsi Jambi (2010-2020)*. GitHub Repository.
