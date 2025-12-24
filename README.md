# AgriSolution
# 🌾 Agriculture AI Assistant

An intelligent web-based platform that leverages Machine Learning and Deep Learning to assist farmers with crop disease detection, crop recommendations, and fertilizer suggestions.

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Flask](https://img.shields.io/badge/Flask-2.3.2-green.svg)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.13.0-orange.svg)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)

## 📋 Table of Contents

- [Features](#-features)
- [Demo](#-demo)
- [Tech Stack](#-tech-stack)
- [Project Architecture](#-project-architecture)
- [Installation](#-installation)
- [Usage](#-usage)
- [API Documentation](#-api-documentation)
- [ML Models](#-ml-models)
- [Dataset Information](#-dataset-information)
- [Screenshots](#-screenshots)
- [Future Enhancements](#-future-enhancements)
- [Contributing](#-contributing)
- [License](#-license)


## ✨ Features

### 🔬 Plant Disease Detection
- **Real-time disease identification** using deep learning (ResNet50)
- Supports **38+ plant diseases** across multiple crops
- **95%+ accuracy** in disease classification
- Detailed treatment recommendations for each disease
- Image upload with drag-and-drop support

### 🌱 Crop Recommendation System
- **ML-powered crop suggestions** based on soil and climate parameters
- Analyzes 7 key factors: N, P, K, Temperature, Humidity, pH, Rainfall
- **99%+ accuracy** using Random Forest algorithm
- Recommends from **22+ crop varieties**
- Provides suitability scores and detailed reasoning

### 💧 Fertilizer Recommendation
- Smart fertilizer suggestions based on soil nutrients
- Calculates NPK deficiencies
- Recommends optimal fertilizer type and quantity
- Considers soil type and crop type for precise recommendations

### 🎨 Additional Features
- **Beautiful, responsive UI** with modern design
- **User authentication** system (login/register)
- **Interactive dashboard** with smooth animations
- **Real-time form validation**
- **Mobile-friendly** responsive design
- **Session management** with local storage

## 🎬 Demo

### Live Demo
> Add your deployed link here (Heroku, Render, PythonAnywhere, etc.)

### Demo Credentials
```
Username: farmer
Password: demo123
```

## 🛠️ Tech Stack

### Backend
- **Python 3.8+** - Core programming language
- **Flask 2.3.2** - Web framework
- **Flask-CORS 4.0.0** - Cross-origin resource sharing

### Machine Learning & AI
- **TensorFlow 2.13.0** - Deep learning framework
- **Keras** - High-level neural networks API
- **Scikit-learn 1.3.0** - Classical ML algorithms
- **ResNet50** - CNN architecture for disease detection
- **Random Forest** - Crop and fertilizer recommendation

### Data Processing
- **NumPy 1.24.3** - Numerical computing
- **Pandas 2.0.3** - Data manipulation
- **Pillow 10.0.0** - Image processing

### Frontend
- **HTML5** - Structure and content
- **CSS3** - Styling with modern features (Grid, Flexbox, Animations)
- **JavaScript ES6+** - Client-side interactivity
- **Fetch API** - Asynchronous HTTP requests

### Data Storage
- **HDF5** - Deep learning model storage
- **Pickle** - ML model serialization
- **JSON** - Configuration and data interchange
- **CSV** - Dataset storage

## 🏗️ Project Architecture

```
agriculture-ai-project/
│
├── app_final.py              # Main Flask application
├── requirements.txt          # Python dependencies
├── README.md                # Project documentation
│
├── models/                   # Trained ML models
│   ├── best_resnet_model.h5     # Disease detection model (ResNet50)
│   ├── crop_model.pkl           # Crop recommendation model
│   ├── fertilizer_model.pkl     # Fertilizer recommendation model
│   └── class_names.json         # Disease class labels
│
├── data/                     # Datasets
│   └── Crop_recommendation.csv  # Crop dataset (2200 samples)
│
├── static/                   # Static assets
│   ├── css/
│   │   └── style.css            # Main stylesheet
│   ├── js/
│   │   └── main.js              # JavaScript functions
│   └── images/                  # Image assets
│
├── templates/                # HTML templates
│   ├── login.html               # Login page
│   ├── register.html            # Registration page
│   └── dashboard.html           # Main dashboard
│
└── notebooks/                # Jupyter notebooks (optional)
    └── model_training.ipynb     # Model training notebooks
```

## 🚀 Installation

### Prerequisites
- Python 3.8 or higher
- pip (Python package installer)
- Virtual environment (recommended)

### Step 1: Clone the Repository
```bash
git clone https://github.com/yourusername/agriculture-ai-assistant.git
cd agriculture-ai-assistant
```

### Step 2: Create Virtual Environment
```bash
# Windows
python -m venv venv
venv\Scripts\activate

# macOS/Linux
python3 -m venv venv
source venv/bin/activate
```

### Step 3: Install Dependencies
```bash
pip install -r requirements.txt
```

### Step 4: Download Datasets & Models

#### Option A: Download Pre-trained Models
1. Download the pre-trained ResNet50 model from [Google Drive/Kaggle]
2. Place it in `models/best_resnet_model.h5`

#### Option B: Train Your Own Models
```bash
# Train crop and fertilizer models
python train_models.py

# For disease detection model
python train_disease_model.py
```

### Step 5: Setup Configuration
Create `models/class_names.json` with disease class names:
```json
[
  "Apple___Apple_scab",
  "Apple___Black_rot",
  "Tomato___Late_blight",
  ...
]
```

### Step 6: Run the Application
```bash
python app_final.py
```

The application will be available at `http://localhost:5000`

## 💻 Usage

### 1. Access the Application
Open your browser and navigate to:
```
http://localhost:5000
```

### 2. Login
Use the demo credentials or create a new account:
```
Username: farmer
Password: demo123
```

### 3. Disease Detection
1. Click on "Disease Detection" tab
2. Upload a plant leaf image (JPG/PNG, max 5MB)
3. Click "Detect Disease"
4. View results with treatment recommendations

### 4. Crop Recommendation
1. Navigate to "Crop Recommendation" tab
2. Enter soil parameters:
   - Nitrogen (N), Phosphorus (P), Potassium (K)
   - Temperature, Humidity, pH, Rainfall
3. Click "Get Crop Recommendation"
4. View recommended crop with suitability score

### 5. Fertilizer Recommendation
1. Go to "Fertilizer Recommendation" tab
2. Select soil type and crop type
3. Enter current NPK values
4. Click "Get Fertilizer Recommendation"
5. View recommended fertilizer type and quantity

## 📡 API Documentation

### Base URL
```
http://localhost:5000
```

### 1. Disease Detection API

**Endpoint:** `POST /api/detect-disease`

**Request:**
```bash
curl -X POST http://localhost:5000/api/detect-disease \
  -F "image=@leaf.jpg"
```

**Response:**
```json
{
  "disease": "Tomato - Late blight",
  "confidence": 94.52,
  "treatment": "Apply copper-based fungicides...",
  "model_type": "ResNet50",
  "demo_mode": false
}
```

### 2. Crop Recommendation API

**Endpoint:** `POST /api/recommend-crop`

**Request:**
```bash
curl -X POST http://localhost:5000/api/recommend-crop \
  -H "Content-Type: application/json" \
  -d '{
    "nitrogen": 90,
    "phosphorus": 42,
    "potassium": 43,
    "temperature": 20.87,
    "humidity": 82.00,
    "ph": 6.50,
    "rainfall": 202.93
  }'
```

**Response:**
```json
{
  "crop": "Rice",
  "suitability": 95,
  "reason": "High humidity and rainfall ideal for rice cultivation..."
}
```

### 3. Fertilizer Recommendation API

**Endpoint:** `POST /api/recommend-fertilizer`

**Request:**
```bash
curl -X POST http://localhost:5000/api/recommend-fertilizer \
  -H "Content-Type: application/json" \
  -d '{
    "soilType": "loamy",
    "cropType": "rice",
    "nitrogen": 37,
    "phosphorus": 20,
    "potassium": 25
  }'
```

**Response:**
```json
{
  "fertilizer": "Urea (46-0-0)",
  "quantity": "180 kg/acre",
  "reason": "Nitrogen deficiency detected. Current N: 37 kg/ha..."
}
```

## 🤖 ML Models

### 1. Disease Detection Model
- **Architecture:** ResNet50 (Residual Neural Network)
- **Input Shape:** 224×224×3 (RGB images)
- **Output:** 38 disease classes
- **Training Dataset:** PlantVillage (87,867 images)
- **Accuracy:** 95-97%
- **Framework:** TensorFlow/Keras

### 2. Crop Recommendation Model
- **Algorithm:** Random Forest Classifier
- **Features:** 7 (N, P, K, Temperature, Humidity, pH, Rainfall)
- **Output:** 22 crop types
- **Training Dataset:** Crop Recommendation Dataset (2,200 samples)
- **Accuracy:** 99%+
- **Framework:** Scikit-learn

### 3. Fertilizer Recommendation Model
- **Algorithm:** Rule-based + Random Forest
- **Features:** 5 (Soil Type, Crop Type, N, P, K)
- **Output:** Fertilizer type and quantity
- **Framework:** Scikit-learn

## 📊 Dataset Information

### Disease Detection Dataset
- **Name:** PlantVillage Dataset
- **Source:** [Kaggle](https://www.kaggle.com/datasets/rashikrahmanpritom/plant-disease-recognition-dataset)
- **Size:** 87,867 images
- **Classes:** 38 disease categories
- **Format:** JPG images (256×256)

### Crop Recommendation Dataset
- **Name:** Crop Recommendation Dataset
- **Source:** [Kaggle](https://www.kaggle.com/atharvaingle/crop-recommendation-dataset)
- **Size:** 2,200 samples
- **Features:** 7 (N, P, K, Temp, Humidity, pH, Rainfall)
- **Target:** 22 crop types
- **Format:** CSV

## 📸 Screenshots

### Login Page
![Login Page](screenshots/login.png)

### Dashboard
![Dashboard](screenshots/dashboard.png)

### Disease Detection
![Disease Detection](screenshots/disease-detection.png)

### Crop Recommendation
![Crop Recommendation](screenshots/crop-recommendation.png)

### Fertilizer Recommendation
![Fertilizer Recommendation](screenshots/fertilizer-recommendation.png)

## 🔮 Future Enhancements

- [ ] **Weather Integration** - Real-time weather data API
- [ ] **Crop Price Prediction** - Market price forecasting
- [ ] **Yield Prediction** - Expected crop yield estimation
- [ ] **Multi-language Support** - Hindi, Telugu, Tamil, etc.
- [ ] **Mobile App** - React Native/Flutter version
- [ ] **Chatbot Integration** - AI-powered farming assistant
- [ ] **IoT Integration** - Sensor data for real-time monitoring
- [ ] **Community Forum** - Farmer discussion platform
- [ ] **Government Schemes** - Information about agricultural schemes
- [ ] **Expert Consultation** - Connect with agricultural experts

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. **Fork the repository**
2. **Create a new branch**
   ```bash
   git checkout -b feature/YourFeatureName
   ```
3. **Make your changes**
4. **Commit your changes**
   ```bash
   git commit -m "Add some feature"
   ```
5. **Push to the branch**
   ```bash
   git push origin feature/YourFeatureName
   ```
6. **Open a Pull Request**

### Contribution Guidelines
- Write clean, documented code
- Follow PEP 8 style guide for Python
- Add unit tests for new features
- Update documentation as needed

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

```
MIT License

Copyright (c) 2024 Your Name

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction...
```

## 👨‍💻 Author

**Your Name**
- GitHub: https://github.com/bhawnadumka24

- Email: bhawnadumka24@gmail.com

## 🙏 Acknowledgments

- **PlantVillage Dataset** - For disease detection training data
- **Kaggle Community** - For datasets and inspiration
- **TensorFlow Team** - For the amazing deep learning framework
- **Flask Community** - For the excellent web framework
- **Unsplash** - For beautiful agriculture images




## ⭐ Show your support

Give a ⭐️ if this project helped you!

---

<p align="center">
  Made with ❤️ for Farmers
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Status-Active-success.svg" />
  <img src="https://img.shields.io/badge/Maintained-Yes-green.svg" />
  <img src="https://img.shields.io/badge/PRs-Welcome-brightgreen.svg" />
</p>
