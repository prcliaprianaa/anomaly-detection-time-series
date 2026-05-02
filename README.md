# Anomaly Detection on Time Series Data

> Comparing **Z-Score** and **Moving Average** methods for anomaly detection on KPI (Key Performance Indicator) time series data.
>
> Project ini dikembangkan sebagai bagian dari proses seleksi masuk **Intelligent System and Machine Learning (I-SMILE) Laboratory**, Telkom University.

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-Numerical-013243?logo=numpy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-11557c?logo=matplotlib&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-success)

---

## Overview

Project ini bertujuan untuk membandingkan dua metode statistik sederhana — **Z-Score** dan **Moving Average** — dalam mendeteksi anomali pada data time series KPI. Tujuannya adalah memahami kelebihan dan keterbatasan masing-masing metode dalam konteks deteksi anomali.

**Goals:**
- Memahami karakteristik data KPI time series melalui EDA
- Mengimplementasikan dua pendekatan statistik untuk anomaly detection
- Membandingkan sensitivitas dan stabilitas kedua metode

---

## Dataset

Dataset yang digunakan berasal dari **NetManAIOps – KPI Anomaly Detection**:

🔗 [NetManAIOps/KPI-Anomaly-Detection](https://github.com/NetManAIOps/KPI-Anomaly-Detection)

**File:** `train.csv` (Preliminary Dataset)

| Column | Description |
|--------|-------------|
| `timestamp` | Unix timestamp (detik) |
| `value` | Nilai KPI yang dipantau |
| `label` | Ground truth anomaly (0 = normal, 1 = anomaly) |
| `KPI ID` | Identifier untuk masing-masing KPI |

> ⚠️ **Note:** Dataset tidak di-upload ke repository ini karena ukurannya >90 MB. Silakan download langsung dari [link sumber dataset](https://github.com/NetManAIOps/KPI-Anomaly-Detection).

---

## Tools & Libraries

- **Python 3** — Core programming language
- **Pandas** — Data manipulation & preprocessing
- **NumPy** — Numerical computations
- **Matplotlib** — Data visualization
- **Google Colab** — Development environment

---

## Methodology

### 1. Data Loading & Preprocessing
- Convert `timestamp` (Unix) ke format datetime
- Sort data berdasarkan waktu
- Handle missing values pada kolom `value`

### 2. Exploratory Data Analysis (EDA)
- Statistik deskriptif data KPI
- Visualisasi pola time series

### 3. Method 1 — Z-Score
Mendeteksi anomali berdasarkan standar deviasi dari mean. Data point dianggap anomali jika |Z-Score| > **threshold (3)**.

```
Z = (x - μ) / σ
```

### 4. Method 2 — Moving Average
Mendeteksi anomali berdasarkan deviasi dari nilai rata-rata bergerak (rolling mean) dengan **window = 20**. Data point dianggap anomali jika residual melebihi 3 × standar deviasi residual.

```
Residual = x - Moving Average
Anomaly if |Residual| > 3 × σ(Residual)
```

### 5. Comparison
Perbandingan jumlah anomali yang terdeteksi oleh kedua metode, divisualisasikan dalam bar chart.

---

## Key Findings

| Aspect | Z-Score | Moving Average |
|--------|---------|----------------|
| **Sensitivity** | Lebih sensitif terhadap nilai ekstrem | Lebih stabil terhadap fluktuasi kecil |
| **Best Use Case** | Saat membutuhkan deteksi anomali ekstrem | Saat data memiliki tren atau pola berulang |
| **Limitation** | Asumsi distribusi normal | Bergantung pada ukuran window |

**Kesimpulan utama:**
- **Z-Score** efektif untuk deteksi anomali ekstrem pada data dengan distribusi mendekati normal
- **Moving Average** lebih cocok untuk data dengan tren/pola, karena lebih tahan terhadap noise
- Pemilihan metode bergantung pada karakteristik data dan kebutuhan sistem (sensitivitas vs stabilitas)

---

## Repository Structure

```
anomaly-detection-time-series/
│
├── Riset_ISmile.ipynb     # Main notebook (full pipeline)
└── README.md              # Project documentation
```

---

## How to Run

### Option 1: Open in Google Colab (Recommended)

1. Buka [Google Colab](https://colab.research.google.com/)
2. Upload file `Riset_ISmile.ipynb`
3. Download `train.csv` dari [NetManAIOps repository](https://github.com/NetManAIOps/KPI-Anomaly-Detection)
4. Upload `train.csv` ke folder yang sama dengan notebook di Colab
5. Run all cells

### Option 2: Run Locally

```bash
# Clone repository
git clone https://github.com/prcliaprianaa/anomaly-detection-time-series.git
cd anomaly-detection-time-series

# Install dependencies
pip install pandas numpy matplotlib jupyter

# Download dataset dari NetManAIOps, simpan sebagai 'train.csv' di folder ini

# Run notebook
jupyter notebook Riset_ISmile.ipynb
```

---

## References

- Chandola, V., Banerjee, A., & Kumar, V. (2009). *Anomaly Detection: A Survey*. ACM Computing Surveys.
- NetManAIOps. *KPI Anomaly Detection Dataset*. [GitHub Repository](https://github.com/NetManAIOps/KPI-Anomaly-Detection)

---

## Project Context

Project ini dikerjakan secara individu sebagai bagian dari proses seleksi **Intelligent System and Machine Learning (I-SMILE) Laboratory** di Telkom University. Setelah berhasil menyelesaikan project ini, saya diterima sebagai **Laboratory Assistant** di I-SMILE Lab.

---

## 👤 Author

**Pricilia Apriana**

🎓 Computer Engineering Student at Telkom University
💡 Aspiring AI/ML Engineer

🔗 [LinkedIn](https://www.linkedin.com/in/pricilia-apriana-975366280)
📧 priciliaapriana01@gmail.com

---

⭐ **If you find this project helpful, feel free to star this repository!**
