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
```
## 🚀 Cara Menjalankan Lingkungan Pengembangan (Codespaces)

Proyek ini dirancang agar dapat dijalankan secara instan menggunakan **GitHub Codespaces** tanpa memerlukan instalasi manual di laptop (*zero-setup environment*). Seluruh dependensi MLOps telah dikonfigurasi menggunakan Dev Container.

Berikut adalah langkah-langkah untuk menjalankan Codespaces:
1. Buka halaman repositori proyek ini di GitHub.
2. Klik tombol hijau **`<> Code`** di pojok kanan atas.
3. Pilih tab **`Codespaces`**.
4. Klik tombol **`Create codespace on main`** (atau pada *branch* eksperimen seperti `feat/initial-eda`).
5. Tunggu beberapa saat hingga proses *building container* selesai. Visual Studio Code akan terbuka langsung di *browser*.
6. Lingkungan Python 3.10 beserta seluruh *library* pendukung (seperti XGBoost, FastAPI, dan MLflow) akan otomatis terinstal di latar belakang berdasarkan file `.devcontainer` dan `requirements.txt`.
7. Buka terminal di dalam VS Code (tekan `` Ctrl + ` ``), dan lingkungan pengembangan siap digunakan!
