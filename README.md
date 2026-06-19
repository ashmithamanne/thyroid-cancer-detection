# Thyroid Disease Detection using Deep Learning (CNN)

A Flask web application that classifies thyroid ultrasound images into five categories
using a Convolutional Neural Network: **Hyperthyroidism, Hypothyroidism, Thyroid Nodule,
Goiter, and Normal**.

## Overview

Thyroid nodules and disorders are increasingly common, and ultrasound-based diagnosis is
often dependent on radiologist experience. This project explores a deep learning approach
to assist in classifying thyroid conditions from ultrasound images, inspired by recent
research on CNN-based thyroid nodule diagnosis (Guo et al., 2020; Rehman et al., 2021).

## Features

- User registration & login (SQLite-backed)
- Image upload and classification through a trained CNN
- Real-time prediction with confidence score
- Simple, lightweight Flask web interface

## Tech Stack

- **Backend:** Python, Flask
- **Deep Learning:** TensorFlow, TFLearn
- **Image Processing:** OpenCV, NumPy
- **Database:** SQLite

## Model

The CNN (`cnn.py`) is a 5-layer convolutional network trained on labeled thyroid ultrasound
images (50x50 input), with two fully connected layers and dropout for regularization.
Trained weights are stored under `/model`.

## Project Structure

```
thyroid-cancer-detection/
├── app.py              # Flask app & inference pipeline
├── cnn.py              # Model training script
├── model/              # Saved trained model weights
├── static/images/      # Uploaded images for inference
├── templates/          # HTML templates (add your own, see note below)
├── requirements.txt
└── README.md
```

> **Note:** HTML templates (`index.html`, `userlog.html`) referenced by `app.py` are not
> included in this repo yet — add your own under `/templates`, or this app will need that
> step completed before running.

## Setup

```bash
git clone https://github.com/<your-username>/thyroid-cancer-detection.git
cd thyroid-cancer-detection
pip install -r requirements.txt
python app.py
```

Then visit `http://127.0.0.1:5000` in your browser.

## Training Your Own Model

To retrain the model on your own dataset:
1. Place training images in a `train/` folder, named with a leading label character
   (`a` = Hyperthyroidism, `h` = Hypothyroidism, `b` = Thyroid Nodule, `d` = Goiter,
   `n` = Normal).
2. Run:
   ```bash
   python cnn.py
   ```

## Evaluation Metrics

Model performance can be evaluated using Accuracy, Precision, Recall, and Confusion Matrix
(see references for benchmark comparisons from related literature).

## References

- Guo et al., *An Improved Deep Learning Approach for Thyroid Nodule Diagnosis*, IEEE ISBI 2020.
- Rehman et al., *Deep Learning Based Fast Screening Approach on Ultrasound Images for Thyroid
  Nodules Diagnosis*, Diagnostics 2021.

## Disclaimer

This project is for educational/research purposes only and is **not** intended for clinical
or diagnostic use.
