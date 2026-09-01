# ProjectOfLife — ECG Arrhythmia Detection

Machine learning project for classifying heartbeat arrhythmias (Normal, PVC, etc.) from raw ECG signals using the MIT-BIH Arrhythmia Database.

## Problem

Sudden cardiac events require immediate detection, but continuously monitoring ECG streams manually is not scalable for doctors. This project builds a classifier that automatically flags arrhythmic heartbeats from raw ECG waveform data.

## Dataset

[MIT-BIH Arrhythmia Database](https://physionet.org/content/mitdb/1.0.0/) — 48 half-hour ECG recordings, annotated by cardiologists.

> Note: the dataset is not included in this repo (see `.gitignore`). Download it manually from PhysioNet and place it under `data/`.

## Approach

- **Input:** 1D time-series ECG signal, segmented per heartbeat around each R-peak
- **Output:** Arrhythmia classification (grouped by AAMI standard: N, S, V, F, Q)
- **Methods:**
  - Histogram-based Gradient Boosting (`HistGradientBoostingClassifier`) on hand-engineered features (R-R interval, QRS width, peak amplitude, etc.)
  - 1D Convolutional Neural Network on raw waveform segments
- **Evaluation:** Sensitivity, Specificity, F1-Score (macro), Confusion Matrix — with emphasis on minimizing False Negatives

## Project Structure

ProjectOfLife/
├── src/ # Core reusable code (data loading, preprocessing, training, evaluation)
├── notebooks/ # Exploration and experimentation notebooks
├── data/ # MIT-BIH dataset (not tracked in git)
├── requirements.txt
└── README.md


## Setup

```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

## Status

🚧 Work in progress — data loading and preprocessing stage.

## Team

- Luu Nhut Tan 
- Ha Tien Dat