# ☀️ Forecasting Daya PLTS (PoC MLOps)

Proyek ini adalah *Proof of Concept* (PoC) sistem prediksi produksi daya Pembangkit Listrik Tenaga Surya (PLTS) secara *hyperlocal*. Menggunakan algoritma **XGBoost Regressor** dan diintegrasikan ke dalam alur **MLOps** untuk menangani *data drift* akibat perubahan cuaca musiman.

## 📁 Project Organization

```text
├── .gitignore         <- File yang diabaikan Git
├── LICENSE            <- Open-source license (MIT)
├── Makefile           <- Perintah otomatisasi: `make data` (ingest) atau `make train` (training)
├── README.md          <- Dokumentasi utama proyek
├── data
│   ├── external       <- Data dari sumber pihak ketiga (Open-Meteo API)
│   ├── interim        <- Data yang sudah melalui transformasi tahap awal
│   ├── processed      <- Dataset final yang siap digunakan untuk modeling (Feature Store)
│   └── raw            <- Data mentah asli yang tidak boleh diubah (Immutable)
│
├── docs               <- Dokumentasi teknis berbasis MkDocs
│   ├── mkdocs.yml     <- Konfigurasi MkDocs
│   └── docs/          <- Halaman dokumentasi (index.md, getting-started.md)
│
├── models             <- Model XGBoost (.json/.pkl) yang sudah dilatih & Model Registry
│
├── notebooks          <- Jupyter notebooks untuk eksperimen (E.g: 1.0-Initial-EDA.ipynb)
│
├── plts_forecaster    <- Source code utama (Python Module)
│   ├── __init__.py    <- Menjadikan folder ini sebagai modul Python
│   ├── config.py      <- Pengaturan variabel lingkungan dan URL API
│   ├── dataset.py     <- Script untuk download data cuaca (Data Ingestion)
│   ├── features.py    <- Code untuk Feature Engineering
│   ├── modeling       
│   │   ├── __init__.py 
│   │   ├── predict.py <- Script untuk menjalankan inferensi (Inference Engine)
│   │   └── train.py   <- Script untuk melatih ulang model (Continuous Training)
│   └── plots.py       <- Script untuk pembuatan visualisasi otomatis
│
├── pyproject.toml     <- Konfigurasi metadata package, Ruff, dan formatters
│
├── references         <- Kamus data, manual API, dan materi pendukung lainnya
│
├── reports            <- Hasil analisis dalam bentuk HTML, PDF, atau LaTeX
│   └── figures        <- Grafik hasil prediksi dan evaluasi model (MAE/RMSE plots)
│
├── requirements.txt   <- Daftar dependensi Python (XGBoost, FastAPI, MLflow, dll)
│
└── tests              <- Unit tests dan integration tests
    └── test_data.py   <- Test untuk modul dataset
```