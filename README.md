# ☀️ Prediksi Output Daya PLTS Berbasis MLOps (Proof of Concept)

Proyek ini merupakan *Proof of Concept* (PoC) untuk sistem peramalan (*forecasting*) produksi daya Pembangkit Listrik Tenaga Surya (PLTS) secara *hyperlocal*. Sistem ini mengintegrasikan *machine learning* (XGBoost Regressor) dengan alur kerja *Continuous Training* (CT) MLOps untuk beradaptasi terhadap *data drift* akibat transisi cuaca.

## 📁 Struktur Direktori
Proyek ini mengadopsi struktur konvensi industri (*Cookiecutter Data Science*):
```text
├── config/          # File konfigurasi sistem dan parameter model
├── data/
│   ├── processed/   # Data cuaca yang sudah dinormalisasi (Feature Store)
│   └── raw/         # Data JSON mentah dari Open-Meteo API
├── models/          # Model XGBoost yang telah dilatih (Model Registry lokal)
├── notebooks/       # Jupyter notebooks untuk tahap Exploratory Data Analysis (EDA)
├── src/             # Source code utama (Data ingestion, Training, FastAPI)
├── .devcontainer/   # Konfigurasi isolasi lingkungan GitHub Codespaces
├── requirements.txt # Daftar dependensi library Python
└── README.md        # Dokumentasi utama proyek