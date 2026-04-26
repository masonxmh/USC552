# DSCI 552 Homework 7

This directory contains the Homework 7 work for DSCI 552:

1. Character-level LSTM text generation on Bertrand Russell corpus.
2. CNN-based image colorization on CIFAR-10 birds.

## Files

- `Homework7.pdf`: assignment prompt
- `notebook/hw7_LSTM.ipynb`: Part 1 (Generative Models for Text)
- `notebook/hw7_CNN.ipynb`: Part 2 ((Deep) CNNs for Image Colorization)
- `requirements.txt`: package list used by notebooks
- `data/`: Russell text files + CIFAR-10 data
- `model/`: saved checkpoints

## Environment

Install:

```bash
pip install -r requirements.txt
```

Run:

```bash
jupyter notebook
```

### Windows GPU Note

`requirements.txt` is pinned for native Windows TensorFlow GPU support:

- `tensorflow==2.10.1`
- `numpy==1.23.5`

Use Python `3.10` for GPU on Windows (for example `py310` / kernel `py310 (GPU TF2.10)`).
Python `3.13` can still be used for general notebook work, but native TensorFlow GPU is not supported there.

## Part 1 - Generative Models for Text (`hw7_LSTM.ipynb`)

Aligned to PDF Section 1(c):

- Concatenate Russell corpus text files.
- Character-level preprocessing (ASCII/integer encoding + scaling).
- Sliding window sequence generation (`W=100`, stride `S=1`).
- One-hot encoded character targets.
- Model: `LSTM(256) -> Dropout(0.5) -> Dense(softmax)`.
- Loss: categorical cross-entropy; optimizer: Adam.
- Checkpoint best model by training loss.
- Generate text using the required seed sentence from the prompt.

Notebook training details:

- 30 epochs initial training, plus additional continued training from checkpoint.
- Batch size: 128.

## Part 2 - (Deep) CNNs for Image Colorization (`hw7_CNN.ipynb`)

Aligned to PDF Section 2:

- Load CIFAR-10 and select class `birds` (6000 images).
- Build 4 color classes using k-means (`k=4`).
- Convert RGB images to grayscale inputs.
- Build pixel-wise classifier with output shape `32x32x4`.
- Reconstruct RGB image from predicted 4-class outputs.

Model and training flow in notebook:

- CNN blocks with `Conv2D(5x5)`, max pooling, and dropout.
- MLP head with `Dense(4096)` layers, reshape to `(32, 32, 4)`, softmax output.
- Train with validation split and checkpoint best model by `val_accuracy`.
- Plot train/validation/test error curves and visualize colorized outputs.

## Reproducibility Notes

- Exact metrics may vary across runs due to random initialization and training order.
- Checkpoints in `model/` capture best-performing epochs used for final sample outputs.
