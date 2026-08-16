\# Classification of Affective Disorders from EEG Signals



\## Overview



This project investigates the classification of affective disorders from electroencephalography (EEG) signals using power spectral representations and convolutional neural networks (CNNs).



The goal is to distinguish between healthy individuals and individuals diagnosed with an affective disorder based on EEG-derived image representations.



\## Methods



The EEG signals are transformed into two-dimensional representations suitable for CNN-based classification, including:



\- Power Spectral Density (PSD)

\- Spectrograms

\- Topographic scalp maps



The project also investigates segmented EEG representations to increase the number of training samples while preserving subject-level separation between training and evaluation data.



\## Model



A custom convolutional neural network is used for binary classification.



The model consists of:



\- Three convolutional blocks

\- ReLU activations

\- Max-pooling

\- Adaptive/global feature aggregation

\- Fully connected classification layers

\- Dropout regularization



\## Technologies



\- Python

\- PyTorch

\- MNE-Python

\- SciPy

\- NumPy

\- Matplotlib

\- scikit-learn



\## Dataset



The dataset contains EEG recordings from healthy participants and participants diagnosed with an affective disorder.



The original dataset contains 140 participants, with 70 participants per class.



The dataset itself is not publicly available so it isn't included in this repository.



\## Results



Results and visualizations are provided in the `results/` directory.



\## Project Structure



```text

EEG-affective-disorder-classification/

├── src/

├── notebooks/

├── results/

├── docs/

├── README.md

├── requirements.txt

└── .gitignore

