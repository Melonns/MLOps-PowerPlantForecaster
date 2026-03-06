# Forecasting Daya PLTS (PoC MLOps)

Proyek ini adalah *Proof of Concept* (PoC) sistem prediksi produksi daya **Pembangkit Listrik Tenaga Surya (PLTS)** secara *hyperlocal*. Menggunakan algoritma **XGBoost Regressor** dan diintegrasikan ke dalam alur **MLOps** untuk menangani *data drift* akibat perubahan cuaca musiman.

## 🎯 Tujuan Proyek

| Tujuan | Keterangan |
|---|---|
| **Prediksi Daya** | Memprediksi output daya PLTS (kWh) berdasarkan data cuaca *hyperlocal* dari Open-Meteo API |
| **Otomasi MLOps** | Membangun pipeline otomatis mulai dari ingest data, feature engineering, training, hingga inferensi |
| **Continuous Training** | Model diperbarui secara berkala untuk mengatasi *data drift* akibat perubahan musim/cuaca |
| **Reproducibility** | Setiap eksperimen dapat direproduksi oleh siapa pun menggunakan GitHub Codespaces |

---

## Cara Menjalankan di GitHub Codespaces

Lingkungan kerja proyek ini sudah dikonfigurasi penuh via **Dev Container** (`.devcontainer/devcontainer.json`), sehingga tidak perlu setup manual.

### Langkah-langkah

1. Buka repositori ini di GitHub
2. Klik tombol **`<> Code`** → tab **`Codespaces`** → **`Create codespace on main`**
3. Tunggu hingga environment selesai dibangun otomatis (± 2-3 menit pertama kali)
4. Semua dependensi akan ter-install otomatis melalui `pip install -r requirements.txt`

### Yang Sudah Terkonfigurasi Otomatis

| Komponen | Detail |
|---|---|
| **Python** | 3.10 (via Dev Container image) |
| **Dependencies** | `requirements.txt` di-install via `postCreateCommand` |
| **VS Code Extensions** | `ms-python.python`, `ms-python.vscode-pylance` |

### Menjalankan Pipeline

```bash
# Install dependencies
make requirements

# Download data cuaca dari Open-Meteo API
make data

# Jalankan linting & format check
make lint

# Jalankan semua unit tests
make test
```

---

## Branching Strategy (GitHub Flow)

Proyek ini menggunakan **GitHub Flow**:

```
main  ←── merge (setelah review & validasi)
  └── feat/initial-eda   ← branch eksperimen awal (EDA & baseline model)
```

| Branch | Tujuan |
|---|---|
| `main` | Branch stabil, hanya menerima merge setelah divalidasi |
| `feat/initial-eda` | Eksperimen awal: EDA, baseline model, dan feature engineering pertama |

> **Aturan:** Tidak ada push langsung ke `main`. Semua perubahan harus melalui branch fitur dan Pull Request.

---

## Project Organization

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