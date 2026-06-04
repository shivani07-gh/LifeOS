# 🛡️ NAV-SMFS
## Neural Authenticity Verification and Synthetic Media Forensics System

**AI-powered Deepfake Detection using Computer Vision, Deep Learning, Explainable AI, and FastAPI**

![Python](https://img.shields.io/badge/Python-3.10+-blue?style=flat-square&logo=python)
![FastAPI](https://img.shields.io/badge/FastAPI-Backend-009688?style=flat-square&logo=fastapi)
![TensorFlow](https://img.shields.io/badge/TensorFlow-AI-FF6F00?style=flat-square&logo=tensorflow)
![MongoDB](https://img.shields.io/badge/MongoDB-Database-47A248?style=flat-square&logo=mongodb)
![OpenCV](https://img.shields.io/badge/OpenCV-Computer%20Vision-5C3EE8?style=flat-square&logo=opencv)
![Status](https://img.shields.io/badge/Status-In%20Development-yellow?style=flat-square)

---

## 🚀 Overview

**NAV-SMFS** is an AI-powered forensics platform engineered to detect manipulated images and videos produced by deepfake technologies. Built on **FastAPI, TensorFlow, OpenCV, and MongoDB**, it combines Computer Vision, Deep Learning, and Explainable AI to identify synthetic media with accuracy and transparency.

Beyond binary classification, NAV-SMFS pinpoints manipulated regions using **Grad-CAM heatmaps** — giving users a clear visual explanation of why media was flagged. The platform is designed to serve cybersecurity professionals, journalists, law enforcement, and fact-checkers working on the front lines of digital misinformation.

---

## 🎯 Problem Statement

Generative AI has made deepfake media indistinguishable from reality. Manual detection is no longer feasible at scale, and the consequences are severe:

| Threat | Impact |
|---|---|
| 📰 Fake News & Misinformation | Erodes public trust and distorts narratives |
| 🔐 Identity Theft | Enables impersonation and fraud |
| 💰 Financial Fraud | Bypasses biometric authentication |
| 🏛️ Political Manipulation | Influences elections and public opinion |
| 🌐 Social Engineering | Facilitates targeted attacks on individuals |

NAV-SMFS directly addresses these threats through an intelligent, automated detection pipeline powered by Deep Learning and Explainable AI.

---

## ⚡ Key Features

| Feature | Description |
|---|---|
| 🔍 **Deepfake Detection** | Identify manipulated images and videos using state-of-the-art deep learning |
| 👁️ **Face Analysis** | Detect facial inconsistencies, blending artifacts, and generation patterns |
| 📊 **Confidence Scoring** | Quantified prediction confidence for every analysis |
| 🔥 **Explainable AI** | Grad-CAM heatmaps reveal exactly which regions triggered the detection |
| 📂 **Media Upload** | Intuitive interface for uploading and queuing images or videos |
| 📈 **Detection History** | Persistent scan records with full prediction reports |
| ⚡ **FastAPI Backend** | Asynchronous, high-performance APIs built for scale |
| 🎥 **Video Processing** | Frame-level deepfake analysis across full video files |

---

## 🏗️ System Architecture

```
                     User Upload
                          │
                          ▼
                 ┌─────────────────┐
                 │  FastAPI Backend │
                 └────────┬────────┘
                          │
         ┌────────────────┼────────────────┐
         ▼                ▼                ▼
      MongoDB      Media Processing     AI Engine
      Database         Pipeline
                             │
                             ▼
                   OpenCV Face Detection
                             │
                             ▼
                     Frame Extraction
                             │
                             ▼
                   Image Preprocessing
                             │
                             ▼
                   XceptionNet / CNN Model
                             │
                             ▼
                    Real / Fake Prediction
                             │
                      ┌──────┴──────┐
                      ▼             ▼
               Confidence     Grad-CAM
                 Score         Heatmap
                      │             │
                      └──────┬──────┘
                             ▼
                    Frontend Dashboard
```

---

## 🧠 Technology Stack

### Backend
`Python` · `FastAPI` · `Pydantic` · `Uvicorn`

### Database
`MongoDB`

### AI / Machine Learning
`TensorFlow` · `Keras` · `Scikit-learn` · `NumPy`

### Computer Vision
`OpenCV`

### Frontend
`HTML` · `CSS` · `JavaScript` · `Tailwind CSS`



---

## 📂 Project Structure

```
NAV-SMFS/
│
├── backend/
│   ├── app.py                  # Application entry point
│   ├── routes/                 # API route definitions
│   ├── services/               # Business logic layer
│   ├── models/                 # Pydantic schemas
│   └── database/               # MongoDB connection & queries
│
├── ai_model/
│   ├── training/               # Model training scripts
│   ├── inference/              # Prediction pipeline
│   ├── gradcam/                # Grad-CAM heatmap generator
│   └── weights/                # Saved model weights
│
├── frontend/
│   ├── templates/              # HTML templates
│   ├── static/                 # Static assets
│   ├── css/                    # Stylesheets
│   └── js/                     # Client-side scripts
│
├── uploads/                    # User-submitted media
├── results/                    # Analysis output files
├── datasets/                   # Training datasets
├── requirements.txt
└── README.md
```

---

## 📂 Training Datasets

| Dataset | Description |
|---|---|
| **FaceForensics++** | Industry-standard benchmark for deepfake detection research |
| **Celeb-DF** | High-quality dataset with realistic celebrity face manipulations |
| **DFDC** | Facebook's Deepfake Detection Challenge dataset with real-world samples |

---

## 🤖 AI Models

### XceptionNet *(Primary Model)*
The backbone detection model, chosen for its performance profile on deepfake benchmarks:
- ✅ Lightweight architecture suitable for fast inference
- ✅ Exceptional feature extraction via depthwise separable convolutions
- ✅ Widely validated on FaceForensics++ and Celeb-DF
- ✅ Strong generalization across manipulation types

### CNN *(Supporting Model)*
Used for extracting low-level visual patterns including texture inconsistencies, compression artifacts, and manipulation traces that complement XceptionNet's deep feature analysis.

---

## 🔥 Explainable AI — Grad-CAM

NAV-SMFS integrates **Gradient-weighted Class Activation Mapping (Grad-CAM)** to generate visual explanations alongside every prediction. Rather than a black-box result, analysts receive a heatmap showing precisely which regions drove the model's decision.

```
🔴 Red     →  High influence — primary manipulation region
🟡 Yellow  →  Medium influence — secondary artifacts
🔵 Blue    →  Low influence — minimal contribution
```

**Why this matters:**
- Builds trust in AI-generated results
- Accelerates forensic review workflows
- Provides defensible evidence for investigations
- Highlights novel manipulation techniques for research

---

## 📊 Evaluation Metrics

The system is benchmarked against the following metrics:

`Accuracy` · `Precision` · `Recall` · `F1 Score` · `ROC-AUC Score` · `Confusion Matrix`

---

## 🚀 API Reference

### Detect Image
```http
POST /api/v1/detect/image
```
Upload an image file. Returns a real/fake prediction, confidence score, and Grad-CAM heatmap.

---

### Detect Video
```http
POST /api/v1/detect/video
```
Upload a video file for frame-level deepfake analysis across the full clip.

---

### Detection History
```http
GET /api/v1/history
```
Retrieve a paginated list of previous detection reports and their results.

---

## 🌍 Use Cases

| Sector | Application |
|---|---|
| 🔒 **Cybersecurity** | Detect identity fraud, impersonation, and biometric spoofing |
| 📰 **Journalism** | Verify media authenticity before publication |
| ⚖️ **Law Enforcement** | Support digital forensic investigations |
| 🔬 **Digital Forensics** | Assist analysts in identifying and documenting synthetic content |
| ✅ **Fact-Checking** | Integrate into misinformation detection workflows |
| 📱 **Social Platforms** | Automatically flag suspicious synthetic content at scale |

---

## 🔒 Security Considerations

- **File Validation** — Strict MIME type and extension checks on all uploads
- **Input Sanitization** — Defense against malformed or malicious payloads
- **API Rate Limiting** — Prevent abuse and ensure fair resource usage
- **Authentication & Authorization** — Role-based access control for API endpoints
- **Secure Upload Handling** — Isolated storage with no direct execution paths
- **Malware Scanning** — Uploaded files scanned before processing



<!-- ---

## 💼 Resume Highlights

- Built an end-to-end AI-powered Deepfake Detection System using **FastAPI, TensorFlow, OpenCV, and MongoDB**
- Implemented **XceptionNet-based classification** for synthetic media detection with high benchmark accuracy
- Integrated **Grad-CAM Explainable AI** to visualize manipulated regions and improve result interpretability
- Developed scalable **REST APIs** with FastAPI for asynchronous image and video inference
- Designed a complete **media forensics pipeline** from upload to prediction and heatmap visualization
- Built the foundation for real-time deepfake detection and enterprise-grade digital forensics applications -->

---

## 👥 Team NAV-SMFS

Building trustworthy AI systems for detecting synthetic media and preserving digital authenticity.

---

> **"AI can create deepfakes — but AI can also detect them."**
>
> NAV-SMFS contributes toward a safer, more trustworthy digital ecosystem by combining **FastAPI, Deep Learning, Computer Vision, and Explainable AI** into one powerful forensics platform.

---

⭐ **Star this repository if you support trustworthy AI and digital authenticity!**