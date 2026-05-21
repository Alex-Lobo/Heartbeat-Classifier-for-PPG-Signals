
The project was completed as part of the AI ​​in Biomedicine course (Politecnico di Milano, 2024)

# Heartbeat Classifier for PPG Signals

This project focuses on heartbeat classification using Photoplethysmography (PPG) signals. PPG is a non-invasive optical method used to measure changes in blood volume and is widely applied in cardiovascular monitoring, including wearable devices such as smartwatches.

## Project Goal

The main goal of the project is to build a classifier for heartbeat peaks in PPG signals.

The classification task consists of two stages:

1. Binary classification:
   - Normal beats (N)
   - Abnormal beats (non-N)

2. Multi-class classification:
   - N — Normal peaks
   - S — Supraventricular peaks
   - V — Ventricular peaks

## Dataset

The dataset contains 105 records with:

- PPG signals
- Detected peaks
- Peak labels

The data is highly imbalanced, with normal peaks representing more than 90% of all samples.

## Preprocessing

The preprocessing pipeline includes:

- Resampling signals to 250 Hz
- Low-pass filtering to remove noise
- Z-score normalization
- One-hot label encoding
- Train/validation/test split
- Signal segmentation around individual peaks

Each segment contains one heartbeat peak and is adjusted to a fixed length using cropping or zero-padding.

## Models

Several neural network architectures were tested, including:

- CNN
- LSTM
- Bidirectional LSTM
- GRU
- ResNet
- Inception-based models

### N vs non-N Classification

The best binary classifier was based on an LSTM architecture.  
It achieved an overall accuracy of about 94%.

### N, S, V Classification

For the three-class classification task, a ResNet-based 1D convolutional model was selected.  
The model performed well on normal beats but had lower accuracy for S and V classes due to class imbalance and difficulty separating abnormal peak types.

## Results

- Binary classification showed strong performance for distinguishing normal and abnormal beats.
- Multi-class classification remained challenging, especially for S and V peak types.
- Class weights and custom metrics were used to improve performance on minority classes.

## Technologies

- Python
- NumPy
- TensorFlow / Keras
- Signal processing techniques
- Deep learning for time-series classification

## Conclusion

This project demonstrates the application of deep learning methods to heartbeat classification from PPG signals. While binary classification achieved good results, further improvements are needed for reliable multi-class classification of abnormal heartbeat types.
