# 🌿 Plant Disease Detection System - Pre-Review Prototype

A **production-ready, demo-ready** plant disease detection system that uses **AI (CNN/TensorFlow)** to identify plant diseases from leaf images and provides treatment recommendations.

> ⚠️ **Pre-Review Note:**  
> Currently uses a **stub predictor** for demo purposes. After review, simply plug in your trained TensorFlow/TFLite model.

---

## 🌐 Live Demo

🔗 **[Click here to view the live application](https://plantdiseasedemo.onrender.com)**  
*(Coming soon after deployment)*

## 📂 GitHub Repository

🔗 [View Source Code](https://github.com/DevTanisha-max/plantdiseasedemo)

---

## 📌 Project Overview

This system helps farmers and agriculturists quickly identify plant diseases by uploading a leaf image. The AI model analyzes the image and provides:

| Feature            | Description                   |
|--------------------|------------------------------|
| 🔍 **Disease Detection** | CNN-based classification      |
| 📊 **Confidence Score**  | Prediction accuracy percentage |
| 💊 **Treatment Plan**    | Organic & chemical remedies   |
| 🗄️ **Disease Database**  | SQLite/PostgreSQL storage     |
| 🐳 **Docker Support**    | Easy containerized deployment |

---

## 🎯 Key Features

| Feature                | Status   | Description                             |
|------------------------|----------|-----------------------------------------|
| ✅ **Image Upload**     | Working  | Upload leaf images via Streamlit UI     |
| ✅ **API Backend**      | Working  | FastAPI with REST endpoints             |
| ✅ **Stub Predictor**   | Working  | Placeholder for your trained model      |
| ✅ **Rule Engine**      | Working  | Disease-specific remedies               |
| ✅ **Database**         | Working  | SQLite with seed data                   |
| ✅ **Docker Compose**   | Working  | Run UI + API together                   |
| ✅ **Unit Tests**       | Working  | Pytest for API validation               |
| 🔜 **Trained Model**    | Pending  | Plug in after pre-review                |

---

## 🧠 System Architecture

```
User Uploads Image
        │
        ▼
Streamlit UI (Port 8501)
    app/ui/streamlit_app.py
        │ (HTTP POST)
        ▼
FastAPI Backend (Port 8000)
    app/backend/main.py
        │
        ▼
Model Predictor (model.py)
    ┌─────────────┬─────────────┐
    │ Stub Model  │ <--- Now    │
    │ Trained CNN │ <--- After  │
    └─────────────┴─────────────┘
        │
        ▼
Rule Engine (rules.py) + Database
Returns: Disease + Remedies + Prevention
```

---

## 🛠️ Tech Stack

| Category            | Technology                             |
|---------------------|----------------------------------------|
| **Backend API**     | FastAPI (Python)                       |
| **Frontend UI**     | Streamlit                              |
| **Deep Learning**   | TensorFlow, Keras, TFLite (plug & play)|
| **Database**        | SQLite (local) / PostgreSQL (prod)     |
| **Containerization**| Docker, Docker Compose                 |
| **Testing**         | Pytest                                 |
| **Deployment**      | Render.com                             |
| **Version Control** | Git & GitHub                           |

---

## 📁 Project Structure

```
plantdiseasedemo/
├── app/
│   ├── backend/
│   │   ├── main.py                # FastAPI endpoints
│   │   ├── model.py               # Stub predictor + TF/TFLite plug-points
│   │   ├── database.py            # SQLite setup & seed data
│   │   ├── schemas.py             # Pydantic models
│   │   └── model_artifacts/       # 👈 Place your trained model here
│   ├── recommendation/
│   │   └── rules.py               # Rule-based disease remedies
│   ├── ui/
│   │   └── streamlit_app.py       # Streamlit UI
│   └── db/
│       ├── schema.sql             # Database schema
│       └── diseases.db            # Auto-created SQLite DB
├── docker/
│   ├── Dockerfile.api             # FastAPI container
│   ├── Dockerfile.ui              # Streamlit container
│   └── docker-compose.yml         # Multi-container setup
├── tests/
│   └── test_api.py                # Pytest unit tests
├── requirements.txt               # Python dependencies
├── postman_collection.json        # API testing collection
└── Demo_cnn.ipynb                 # Model training notebook (optional)
```

---

## 🚀 Quick Start Guide (Local Setup)

### Prerequisites

- Python 3.8+
- pip (Python package manager)
- (Optional) Docker Desktop

### Step-by-Step Local Installation

```bash
# 1. Clone the repository
git clone https://github.com/DevTanisha-max/plantdiseasedemo.git
cd plantdiseasedemo

# 2. Create virtual environment
python -m venv venv

# 3. Activate virtual environment
# Windows:
venv\Scripts\activate
# Mac/Linux:
source venv/bin/activate

# 4. Install dependencies
pip install -r requirements.txt

# 5. Start the FastAPI backend (Terminal 1)
uvicorn app.backend.main:app --reload --port 8000

# 6. Start the Streamlit UI (Terminal 2)
streamlit run app/ui/streamlit_app.py

# 7. Open in browser
# FastAPI API docs: http://localhost:8000/docs
# Streamlit UI:    http://localhost:8501
```

### 🔧 API Endpoints

| Method | Endpoint           | Description                       |
|--------|--------------------|-----------------------------------|
| POST   | /predict           | Upload image for prediction       |
| GET    | /disease/{name}    | Get disease details + remedies    |
| GET    | /health            | API health status                 |

#### Example API Request

```bash
curl -X POST http://localhost:8000/predict \
  -F "image=@leaf.jpg"
```

#### Example Response (Current - Stub)
```json
{
  "disease": "Late Blight",
  "confidence": 94.5,
  "treatment": "Apply copper-based fungicide",
  "prevention": "Crop rotation, resistant varieties",
  "remedies": {
    "organic": "Neem oil spray",
    "chemical": "Mancozeb 75% WP"
  }
}
```

#### 🧪 Testing
Run unit tests:
```bash
pytest tests/test_api.py -v
```

Expected output:
```
tests/test_api.py::test_health_check PASSED
tests/test_api.py::test_predict_endpoint PASSED
tests/test_api.py::test_get_disease PASSED
```

---

## 🤖 Replacing the Stub with Your Trained Model

After pre-review, plug in your model:

1. Train your CNN (MobileNetV2 fine-tuned recommended)
2. Export your model as one of:
    - TensorFlow SavedModel directory
    - `.h5` Keras model
    - TensorFlow Lite `.tflite`
3. Place model in:
    ```
    app/backend/model_artifacts/your_model/
    ```
4. Set environment variables:
    - `MODEL_KIND=keras|savedmodel|tflite`
    - `MODEL_PATH=app/backend/model_artifacts/your_model`
5. Update model.py with your preprocessing logic (expects RGB 224×224)

Model Requirements:

| Parameter         | Value                         |
|-------------------|------------------------------|
| Input Shape       | 224 × 224 × 3 (RGB)          |
| Output            | Softmax over disease classes  |
| Supported Formats | SavedModel, .h5, .tflite      |

---

## 🐳 Deployment on Render

**Option 1: Deploy FastAPI Backend Only**

1. Push code to GitHub
2. On Render.com → New Web Service
3. Connect repository
4. Build Command:  
   `pip install -r requirements.txt`
5. Start Command:  
   `uvicorn app.backend.main:app --host 0.0.0.0 --port 10000`

**Option 2: Deploy Streamlit UI Only**

1. On Render → New Web Service
2. Build Command:  
   `pip install -r requirements.txt`
3. Start Command:  
   `streamlit run app/ui/streamlit_app.py --server.port 10000`

---

## 📊 Project Impact

### Agricultural Impact:

| Metric               | Target         |
|----------------------|---------------|
| Detection Accuracy   | 94%+ (trained)|
| Time to Diagnosis    | < 5 seconds   |
| Farmers Reachable    | 10,000+       |
| Crop Loss Reduction  | 20-30%        |

### UN SDGs Addressed

| SDG        | Goal           | How                         |
|------------|----------------|-----------------------------|
| 🎯 SDG 2   | Zero Hunger    | Reducing crop losses        |
| 🎯 SDG 15  | Life on Land   | Promoting sustainability    |
| 🎯 SDG 9   | Innovation     | AI for social good          |

---

## 👥 Team Role Mapping

| Group      | Responsibility             | Files                        |
|------------|----------------------------|------------------------------|
| Group 1    | ML Model Integration       | model_artifacts/, model.py   |
| Group 2    | Database & API             | schema.sql, database.py, main.py |
| Group 3    | UI & Optimization          | streamlit_app.py, Docker configs |

---

## 📋 Postman Testing

Import `postman_collection.json` to test:

- POST `/predict` (multipart image upload)
- GET `/disease/{name}`

---

## 🤝 Contributors

| GitHub                   | Role                         |
|--------------------------|------------------------------|
| [@Raaunnakk555](https://github.com/Raaunnakk555)           | Project Lead / ML Engineer     |
| [@DevTanisha-max](https://github.com/DevTanisha-max)       | Contributor                   |
| [@riya23605shukla-arch](https://github.com/riya23605shukla-arch) | Contributor                   |

---

## 📄 License

MIT License

---

## 🙏 Acknowledgments

- PlantVillage Dataset (for training)
- FastAPI & Streamlit communities
- TensorFlow/Keras for deep learning framework

---

## ⭐ Show Your Support

Good luck for your pre-review! ✨  
If this project helps you, please give it a ⭐ on GitHub!
