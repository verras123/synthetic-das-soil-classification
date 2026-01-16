Synthetic DAS Soil Classification — A1 (Baseline)

This repository contains a baseline, fully reproducible pipeline for generating synthetic Distributed Acoustic Sensing (DAS) data and performing multiclass soil classification using physics-inspired signal features and classical machine learning models.

The goal of this version is to provide a transparent, inspectable, and extensible reference implementation, suitable for experimentation, benchmarking, and methodological discussion.

IMPORTANT NOTE
A more advanced version of this framework — including extended modeling, deeper analysis, and additional validation — is currently under active investigation for academic publication.
This repository intentionally contains a simplified and non-final version.

----------------------------------------------------------------

OVERVIEW

This pipeline performs the following steps:

1. Synthetic DAS data generation
   - One soil class per sample
   - Simple depth-dependent wave propagation model
   - Gaussian-modulated pulses with attenuation, jitter, and noise
   - Class-dependent P-wave velocity distributions

2. Feature extraction
   - Energy and envelope statistics
   - Spectral features (centroid, bandwidth, rolloff, peak frequency)
   - Shape descriptors (kurtosis, skewness)
   - A simple physics-inspired Vp estimator based on arrival picking

3. Baseline machine learning
   - Logistic Regression (with scaling)
   - Histogram-based Gradient Boosting
   - Stratified train/test split
   - Confusion matrix, accuracy, macro-F1

4. Artifact generation
   - CSV feature table
   - Confusion matrix plot
   - Dataset composition plot
   - Per-class example visualizations
   - Optional HDF5 dataset export

All outputs are saved in a reproducible, timestamped structure.

----------------------------------------------------------------

SOIL CLASSES

The default configuration includes the following soil / lithology classes:

- Turfa / Lama
- Loam
- Argila mole
- Argila firme / Limo
- Silt Arenoso
- Areia solta
- Areia densa / Seixo
- Areia / Gravel
- Rocha macia
- Xisto / Calcário
- Basalto / Granito

Each class is associated with a representative P-wave velocity range used during simulation.

----------------------------------------------------------------

REQUIREMENTS

Python >= 3.9

Main dependencies:
- numpy
- pandas
- scikit-learn
- matplotlib
- h5py
- joblib (optional)

Install with:
pip install -r requirements.txt

----------------------------------------------------------------

RUNNING THE PIPELINE

Basic execution:
python Synthetic_das_soil_A1.py

Example:
python Synthetic_das_soil_A1.py --samples-per-class 300 --n-channels 128 --z-max 120 --make-h5

Help:
python Synthetic_das_soil_A1.py --help

----------------------------------------------------------------

OUTPUT STRUCTURE

saida_synthetic_das_A1/
├── run_YYYYMMDD_HHMM/
│   ├── features.csv
│   ├── class_hist.png
│   ├── confusion_matrix.png
│   ├── metrics.json
│   ├── summary.json
│   ├── examples/
│   └── dataset_A1.h5 (optional)
└── latest/

----------------------------------------------------------------

DESIGN PHILOSOPHY

- Interpretability first
- Physics-aware, not physics-heavy
- Baseline-focused and reproducible

----------------------------------------------------------------

RELATION TO ONGOING RESEARCH

This repository represents a baseline implementation.
A separate and more advanced version is currently being prepared and evaluated for academic publication.

----------------------------------------------------------------

LICENSE

MIT License

----------------------------------------------------------------

DISCLAIMER

This software is provided for research and experimental purposes only.
Synthetic data and simplified models should not be interpreted as field-calibrated results.

