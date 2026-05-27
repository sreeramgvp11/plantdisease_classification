# 🌱 Plant Disease Classification

[![Python](https://img.shields.io/badge/Python-3.9%2B-blue.svg)](https://www.python.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.17%2B-orange.svg)](https://www.tensorflow.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.110%2B-009688.svg)](https://fastapi.tiangolo.com/)
[![React](https://img.shields.io/badge/React-18.3%2B-61DAFB.svg)](https://reactjs.org/)
[![Docker](https://img.shields.io/badge/Docker-Enabled-blue.svg)](https://www.docker.com/)

An end-to-end deep learning solution designed to help farmers and researchers identify plant diseases with high precision. Leveraging **EfficientNet** architectures, this project provides a scalable pipeline from model training to real-time inference via a web interface.

<p align="center">
  <img src="./Screenshot 2026-05-26 224428.png
" alt="Plant Disease Classification Banner" width="100%">
</p>

---

## 🚀 Key Features

- **EfficientNet Backbone**: Uses state-of-the-art CNNs for optimal balance between accuracy and performance.
- **Multi-Plant Support**: Classifies diseases across 20+ plant varieties (Apple, Potato, Tomato, etc.).
- **TFLite Integration**: Optimized models for fast inference and edge deployment.
- **Responsive UI**: Modern dashboard built with React and Material UI.
- **Dockerized Server**: Easy deployment with Docker and Docker Compose.
- **Complete Pipeline**: Scripts for data preparation, training, evaluation, and model conversion.

---

## 🛠️ Tech Stack

### AI & Machine Learning
- **Framework**: TensorFlow, Keras
- **Architecture**: EfficientNet (B0-B7)
- **Format**: H5 for training, TFLite for production
- **Optimization**: Compound scaling (Width, Depth, Resolution)

### Backend
- **Framework**: FastAPI
- **Server**: Uvicorn
- **API**: RESTful API for predictions and metadata
- **Containerization**: Docker, Docker Compose

### Frontend
- **Framework**: React.js (v18)
- **Styling**: Material UI (MUI)
- **API Client**: Axios
- **Notifications**: React-Toastify

---

## 📂 Project Structure

```bash
PlantDisease_classification/
├── client/                 # React Web Application
├── server/                 # FastAPI Prediction Server
│   ├── app/                # Application logic & API routes
│   └── ModelLight/         # TFLite model storage
├── Images/                 # Documentation assets
├── model.py                # EfficientNet model definitions
├── train_multiple_model.py # Bulk training script
├── evaluate.py             # Model performance analysis
├── convert_tflite.py       # H5 to TFLite conversion utility
├── prepare_data.py         # Dataset preprocessing
├── requirements.txt        # Core ML dependencies
└── README.md
```

---

## ⚙️ Installation & Setup

### 1. Clone & Environment
```bash
git clone git@github.com:tinh2044/PlantDisease_classification.git
cd PlantDisease_classification

# Create virtual environment
conda create --name plant-disease python=3.9
conda activate plant-disease
pip install -r requirements.txt
```

### 2. Server Setup (FastAPI)
```bash
cd server
pip install -r requirements.txt

# Run the server
uvicorn app.main:app --host 0.0.0.0 --port 5000
```
*Note: Ensure TFLite models are placed in `server/ModelLight/`.*

### 3. Client Setup (Next.js)
```bash
cd client
npm install
npm run dev
```
*Configuration: Update `client/.env.local` with `NEXT_PUBLIC_API_URL=http://localhost:5000`.*

---

## 🏋️ Model Development Lifecycle

### 📊 Dataset Preparation
Download the dataset from [Kaggle](https://www.kaggle.com/datasets/nguyenchitinh/plantdisease-with-20-plant) and organize it as follows:
```
Datasets/
  ├── Apple/
  ├── Tomato/
  └── ...
```

### 🚀 Training
Train models across multiple plant categories:
```bash
python train_multiple_model.py --epoch 100 --batch_size 32 --root_dir ./Datasets
```

### 🔄 Conversion to TFLite
Optimize your trained models for production:
```bash
python convert_tflite.py
```

---

## 🌐 API Documentation

### `GET /diseases`
Returns a list of supported plant categories and their metadata.

### `POST /predict?name={plant_name}`
Predicts the disease for a given image.
- **Body**: `multipart/form-data` (file)
- **Response**: JSON containing class name, confidence, and disease info.

---

## 🔬 Scientific Background: EfficientNet

EfficientNet scales all three dimensions of the network—width, depth, and resolution—using a **compound coefficient**. This results in models that are significantly smaller and faster than traditional architectures like ResNet while achieving superior accuracy.

<p align="center">
  <img src="./Images/efficientNet.png" alt="EfficientNet Scaling" width="600px">
</p>

---

## 📜 References

- [EfficientNet: Rethinking Model Scaling for CNNs](https://arxiv.org/abs/1905.11946)
- [TensorFlow Hub - Image Classification](https://tfhub.dev/)
- [PlantVillage Dataset](https://www.kaggle.com/datasets/emmarex/plantvillage-dataset)

---

ataset](https://www.kaggle.com/datasets/emmarex/plantvillage-dataset)

---

