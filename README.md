# 🎧 AudioSense – Environmental Sound Classification (ESC) using CNNs

AudioSense is a complete machine-learning system for **classifying environmental sounds** using **Mel-spectrograms** and a **Convolutional Neural Network (CNN)**.  
This repository contains **two folders**:

- **backend/** → ML model, preprocessing, training pipeline & inference API  
- **frontend/** → Web UI for uploading audio & viewing predictions  

---

## 🚀 Features

- Converts raw audio (`.wav`) into **Mel-spectrograms**
- Deep learning classification using a **CNN**
- **ESC-50 (50 environmental classes)** support
- Built-in audio **data augmentation** (time shift, pitch shift, amplitude scaling)
- 5-Fold **cross-validation** compatible pipeline
- FastAPI backend API for inference
- React frontend for real-time predictions and visualization

---

## 📂 Project Structure

```
.
├── backend/
│   ├── src/
│   │   ├── prep.py          # Audio loading + spectrogram extraction
│   │   ├── model.py         # CNN architecture
│   │   ├── train.py         # Training script
│   │   ├── eval.py          # Evaluation
│   │   └── main.py          # FastAPI inference server
│   ├── requirements.txt
│
├── frontend/
│   ├── src/
│   ├── public/
│   └── package.json
│
└── README.md
```

---

## 🧠 Methodology Overview

### 1️⃣ Audio Preprocessing  
- Load audio (`.wav`)
- Pad/trim to 5 seconds  
- Convert to **Mel-spectrogram (128×Time)**  
- Normalize to 0–1

### 2️⃣ CNN Model Architecture  
- 3 Convolutional blocks  
- BatchNorm + MaxPooling  
- Global Average Pooling  
- Dense (256) + Dropout  
- Output layer: `Softmax (50 classes)`

### 3️⃣ Training  
- Categorical Crossentropy  
- Adam optimizer  
- EarlyStopping + Checkpointing  
- Optional data augmentation

### 4️⃣ Inference  
- FastAPI endpoint:  
```
POST /predict
```
- Returns:
  - top class index  
  - top-5 probabilities  

---

## ⚙️ Installation & Setup

### **Backend Setup**
```bash
cd backend
pip install -r requirements.txt
uvicorn src.main:app --reload
```
API will run at:
```
http://localhost:8000
```

---

### **Frontend Setup**
```bash
cd frontend
npm install
npm start
```
App will run at:
```
http://localhost:3000
```

---

## 🔥 API Example Request
```bash
curl -X POST "http://localhost:8000/predict" \
     -F "file=@example.wav"
```

Sample response:
```json
{
  "prediction_index": 17,
  "top5": [
    {"index": 17, "probability": 0.92},
    {"index": 4,  "probability": 0.03},
    {"index": 12, "probability": 0.02}
  ]
}
```

---

## 📊 Dataset
This project uses the **ESC-50 Dataset** (50 classes, 2000 audio clips, 5-second each).

---

## 🛠️ Future Improvements
- Real-time microphone input  
- Multi-feature fusion (MFCC + Spectrogram)  
- Larger audio datasets  
- Model quantization for mobile deployment  

---

## 🤝 Contributing
Pull requests are welcome!  
If you'd like to improve training, augmentations, or UI, feel free to submit.

---

## 📜 License
MIT License © 2025

---

## 👤 Author
**Alaukik Patel**  
VII Semester – CSE  
IIIT Senapati, Manipur
