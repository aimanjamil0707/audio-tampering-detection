# 🎙️ Audio Tampering Detection and Localization

An AI-powered system that detects and localizes tampering in audio files using deep learning (ANN & CNN). Built for the **SZABIST ANN Lab Project** by Aqsa, Mewish, and Aiman.

---

## 🔍 Overview

This project implements a full pipeline for audio forensics — detecting whether an audio clip has been tampered with, and **localizing exactly where** the tampering occurred. It supports four types of tampering:

| Tampering Type | Description |
|---|---|
| **Cut** | A segment of audio is removed |
| **Splice** | A foreign audio segment is inserted |
| **Noise Injection** | Loud noise is added to a region |
| **Compression Artifact** | Heavy quantization applied to a segment |

---

## 🧠 Models

### ANN (Artificial Neural Network)
- Input: Tabular feature vectors (MFCC, spectral, ZCR, RMS, Chroma)
- Architecture: Dense → BatchNorm → Dropout (×3 layers)
- Output: Binary classification (Clean / Tampered)

### CNN (Convolutional Neural Network)
- Input: 64×64 Mel-spectrogram images
- Architecture: Conv2D → BatchNorm → MaxPool (×3 blocks) → GlobalAvgPool → Dense
- Output: Binary classification (Clean / Tampered)

Both models fall back to `sklearn` (MLPClassifier) if TensorFlow is unavailable.

---

## 🔧 Features Extracted

- **MFCC** — 40 coefficients (mean + std) → 80 values
- **Spectral Centroid, Rolloff, Bandwidth** — mean + std → 6 values
- **Zero Crossing Rate** — mean + std → 2 values
- **RMS Energy** — mean + std → 2 values
- **Chroma STFT** — 12 mean values

---

## 🗂️ Project Structure

```# audio-tampering-detection
AI-powered audio tampering detection and localization using ANN and CNN models.
