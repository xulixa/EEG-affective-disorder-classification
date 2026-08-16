# Classification of Affective Disorders from EEG Signals

This project investigates the classification of affective disorders from electroencephalography (EEG) signals using spectral and topographic representations combined with convolutional neural networks (CNNs).

The goal is to distinguish between healthy individuals and individuals diagnosed with an affective disorder based on EEG-derived two-dimensional representations.

## Project Overview

EEG signals are transformed into image-like representations that can be processed by convolutional neural networks. Several representations and segmentation strategies are investigated and compared.

The experiments include:

- Power Spectral Density (PSD)
- Segmented Power Spectral Density
- Spectrograms
- Segmented spectrograms
- EEG topographic scalp maps
- Segmented EEG topographic scalp maps

For segmented representations, each participant's recording is divided into five segments. Subject-level separation is maintained during dataset splitting to prevent data from the same participant from appearing in different subsets.

## Dataset

The dataset contains EEG recordings from 140 participants:

- 70 healthy participants
- 70 participants diagnosed with an affective disorder

The classification task is binary:

- `0` — healthy
- `1` — affective disorder

The original EEG dataset and derived image datasets are not included in this repository.

The notebooks therefore contain the experimental pipeline and model implementations, while the data paths must be configured locally according to the available dataset.

## EEG Representations

### Power Spectral Density

Welch's method is used to estimate the power spectral density of the EEG signals. PSD representations are used as inputs to the CNN models.

### Spectrograms

Time-frequency representations are generated using spectrograms, allowing both temporal and frequency information to be represented in a two-dimensional form.

### Topographic Scalp Maps

Spectral power is projected onto the scalp using EEG sensor locations. Five frequency bands are considered:

- Delta: 0.5–4 Hz
- Theta: 4–8 Hz
- Alpha: 8–13 Hz
- Beta: 13–30 Hz
- Gamma: 30–45 Hz

## Model

A custom convolutional neural network is used for binary classification.

The architecture consists of:

- Three convolutional layers with progressively increasing feature dimensions
- ReLU activations
- Max-pooling
- Adaptive/global feature aggregation
- Fully connected classification layers
- Dropout regularization

For multi-image inputs, feature representations from five corresponding images are extracted and combined before the final classification stage.

## Experimental Setup

The experiments are implemented using Python and PyTorch.

The dataset is divided into training, validation, and test subsets while preserving subject-level separation. This prevents images originating from the same participant from being distributed across different subsets.

The main training configuration includes:

- Image size: depends on dataset
- Batch size: 16 (8 in CNN_topomap_5seg)
- Optimizer: Adam
- Loss function: Cross-Entropy Loss
- Training epochs: 30
- Dropout: 0.5

## Results

The experiments compare the performance of CNN classifiers using different EEG representations.

Among the investigated representations, PSD-based representations achieved strong classification performance, while the topographic representation with segmented inputs also showed promising results.

Detailed results, evaluation metrics, and visualizations are available in the corresponding Jupyter notebooks.

## Repository Structure

```text
EEG-affective-disorder-classification/
│
├── notebooks/
│   ├── CNN_PS.ipynb
│   ├── CNN_PS_5seg.ipynb
│   ├── CNN_spektrogram.ipynb
│   ├── CNN_spektrogram_5seg.ipynb
│   ├── CNN_topomap.ipynb
│   └── CNN_topomap_5seg.ipynb
│
├── .gitignore
├── README.md
└── …
```

## Technologies

Python
PyTorch
torchvision
MNE-Python
SciPy
NumPy
pandas
scikit-learn
Matplotlib

## Reproducibility

The notebooks contain the CNN training and evaluation workflow used in the experiments.

Because the original EEG dataset and derived image datasets are not included in this repository, the data must be obtained separately and the corresponding files must be placed in a local data/ directory.

The notebooks use relative paths to the project data/ directory rather than machine-specific absolute paths.

## Academic Context

This project was developed as part of a graduate thesis in Data Science at the University of Zagreb, Faculty of Electrical Engineering and Computing (FER).

The project focuses on applying deep learning and image-based representations to EEG signal analysis for the classification of affective disorders.
