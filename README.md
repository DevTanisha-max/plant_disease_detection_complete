\# 🌿 Plant Disease Detection System - Pre-Review Prototype



A \*\*production-ready, demo-ready\*\* plant disease detection system that uses \*\*AI (CNN/TensorFlow)\*\* to identify plant diseases from leaf images and provides treatment recommendations.



> ⚠️ \*\*Pre-Review Note:\*\* Currently uses a \*\*stub predictor\*\* for demo purposes. After review, simply plug in your trained TensorFlow/TFLite model.



\---




\## 🌐 Live Demo

🔗 \*\*\[Click here to view the live application](https://plantdiseasedemo.onrender.com)\*\* \*(Coming soon after deployment)\*



\## 📂 GitHub Repository

🔗 \[View Source Code](https://github.com/DevTanisha-max/plantdiseasedemo)



\---




\## 📌 Project Overview



This system helps farmers and agriculturists quickly identify plant diseases by uploading a leaf image. The AI model analyzes the image and provides:



| Feature | Description |

|---------|-------------|

| 🔍 \*\*Disease Detection\*\* | CNN-based classification |

| 📊 \*\*Confidence Score\*\* | Prediction accuracy percentage |

| 💊 \*\*Treatment Plan\*\* | Organic \& chemical remedies |

| 🗄️ \*\*Disease Database\*\* | SQLite/PostgreSQL storage |

| 🐳 \*\*Docker Support\*\* | Easy containerized deployment |



\---





\## 🎯 Key Features



| Feature | Status | Description |

|---------|--------|-------------|

| ✅ \*\*Image Upload\*\* | Working | Upload leaf images via Streamlit UI |

| ✅ \*\*API Backend\*\* | Working | FastAPI with REST endpoints |

| ✅ \*\*Stub Predictor\*\* | Working | Placeholder for your trained model |

| ✅ \*\*Rule Engine\*\* | Working | Disease-specific remedies |

| ✅ \*\*Database\*\* | Working | SQLite with seed data |

| ✅ \*\*Docker Compose\*\* | Working | Run UI + API together |

| ✅ \*\*Unit Tests\*\* | Working | Pytest for API validation |

| 🔜 \*\*Trained Model\*\* | Pending | Plug in after pre-review |



\---






\## 🧠 System Architecture

┌─────────────────────────────────────────────────────────────┐

│ User Uploads Image │

└─────────────────────────┬───────────────────────────────────┘

↓

┌─────────────────────────────────────────────────────────────┐

│ Streamlit UI (Port 8501) │

│ app/ui/streamlit\_app.py │

└─────────────────────────┬───────────────────────────────────┘

↓ (HTTP POST)

┌─────────────────────────────────────────────────────────────┐

│ FastAPI Backend (Port 8000) │

│ app/backend/main.py │

└─────────────────────────┬───────────────────────────────────┘

↓

┌─────────────────────────────────────────────────────────────┐

│ Model Predictor (model.py) │

│ ┌─────────────────────────────────┐ │

│ │ Stub Predictor (Current) │ │

│ │ ↓ After Review ↓ │ │

│ │ Trained CNN/TensorFlow/TFLite │ │

│ └─────────────────────────────────┘ │

└─────────────────────────┬───────────────────────────────────┘

↓

┌─────────────────────────────────────────────────────────────┐

│ Rule Engine (rules.py) + Database │

│ Returns: Disease + Remedies + Prevention │

└─────────────────────────────────────────────────────────────┘





\---



\## 🛠️ Tech Stack



| Category | Technology |

|----------|------------|

| \*\*Backend API\*\* | FastAPI (Python) |

| \*\*Frontend UI\*\* | Streamlit |

| \*\*Deep Learning\*\* | TensorFlow, Keras, TFLite (ready for plug-in) |

| \*\*Database\*\* | SQLite (local) / PostgreSQL (production) |

| \*\*Containerization\*\* | Docker, Docker Compose |

| \*\*Testing\*\* | Pytest |

| \*\*Deployment\*\* | Render.com |

| \*\*Version Control\*\* | Git \& GitHub |





\---



\## 📁 Project Structure

plantdiseasedemo/

├── app/

│ ├── backend/

│ │ ├── main.py # FastAPI endpoints

│ │ ├── model.py # Stub predictor + TF/TFLite plug-points

│ │ ├── database.py # SQLite setup \& seed data

│ │ ├── schemas.py # Pydantic models

│ │ └── model\_artifacts/ # 👈 Place your trained model here

│ ├── recommendation/

│ │ └── rules.py # Rule-based disease remedies

│ ├── ui/

│ │ └── streamlit\_app.py # Streamlit UI

│ └── db/

│ ├── schema.sql # Database schema

│ └── diseases.db # Auto-created SQLite DB

├── docker/

│ ├── Dockerfile.api # FastAPI container

│ ├── Dockerfile.ui # Streamlit container

│ └── docker-compose.yml # Multi-container setup

├── tests/

│ └── test\_api.py # Pytest unit tests

├── requirements.txt # Python dependencies

├── postman\_collection.json # API testing collection

└── Demo\_cnn.ipynb # Model training notebook (optional)




\---



\## 🚀 Quick Start Guide (Local Setup)



\### Prerequisites



```bash

\# Required:

\- Python 3.8+

\- pip package manager



\# Optional (for Docker):

\- Docker Desktop



Step-by-Step Local Installation

\# 1. Clone the repository

git clone https://github.com/DevTanisha-max/plantdiseasedemo.git

cd plantdiseasedemo



\# 2. Create virtual environment

python -m venv venv



\# 3. Activate virtual environment

\# Windows:

venv\\Scripts\\activate

\# Mac/Linux:

source venv/bin/activate



\# 4. Install dependencies

pip install -r requirements.txt



\# 5. Start the FastAPI backend (Terminal 1)

uvicorn app.backend.main:app --reload --port 8000



\# 6. Start the Streamlit UI (Terminal 2)

streamlit run app/ui/streamlit\_app.py



\# 7. Open in browser

\# FastAPI API docs: http://localhost:8000/docs

\# Streamlit UI: http://localhost:8501




🔧 API Endpoints

Method	Endpoint	Description

POST	/predict	Upload image for disease prediction

GET	/disease/{name}	Get disease details + remedies

GET	/health	Check API health status


Example API Request

curl -X POST http://localhost:8000/predict \\

&#x20; -F "image=@leaf.jpg"


Example Response (Current - Stub)
{

&#x20; "disease": "Late Blight",

&#x20; "confidence": 94.5,

&#x20; "treatment": "Apply copper-based fungicide",

&#x20; "prevention": "Crop rotation, resistant varieties",

&#x20; "remedies": {

&#x20;   "organic": "Neem oil spray",

&#x20;   "chemical": "Mancozeb 75% WP"

&#x20; }

}


🧪 Testing
# Run unit tests

pytest tests/test\_api.py -v



\# Expected output:

\# tests/test\_api.py::test\_health\_check PASSED

\# tests/test\_api.py::test\_predict\_endpoint PASSED

\# tests/test\_api.py::test\_get\_disease PASSED


🤖 Replacing the Stub with Your Trained Model

After pre-review, plug in your model:

1.Train your CNN (MobileNetV2 fine-tuned recommended)



2.Export your model as one of:



&#x20; TensorFlow SavedModel directory



&#x20; .h5 Keras model



&#x20; TensorFlow Lite .tflite



3.Place model in:
app/backend/model\_artifacts/your\_model/

4.Set environment variables:
MODEL\_KIND=keras|savedmodel|tflite

MODEL\_PATH=app/backend/model\_artifacts/your\_model

5.Update model.py with your preprocessing logic (expects RGB 224×224)
Model Requirements:

Parameter	Value

Input Shape	224 × 224 × 3 (RGB)

Output	Softmax over disease classes

Supported Formats	SavedModel, .h5, .tflite


🐳 Deployment on Render

Option 1: Deploy FastAPI Backend Only

Push code to GitHub



On Render.com → New Web Service



Connect repository



Build Command: pip install -r requirements.txt



Start Command: uvicorn app.backend.main:app --host 0.0.0.0 --port 10000



Option 2: Deploy Streamlit UI Only

On Render → New Web Service



Build Command: pip install -r requirements.txt



Start Command: streamlit run app/ui/streamlit\_app.py --server.port 10000


📊 Project Impact



Agricultural Impact:



Metric	Target

Detection Accuracy	94%+ (with trained model)

Time to Diagnosis	< 5 seconds

Farmers Reachable	10,000+

Crop Loss Reduction	20-30%





UN SDGs Addressed:



SDG	Goal	How

🎯 SDG 2	Zero Hunger	Reducing crop losses

🎯 SDG 15	Life on Land	Promoting sustainable agriculture

🎯 SDG 9	Innovation	AI for social good







👥 Team Role Mapping



Group	Responsibility	Files

Group 1	ML Model Integration	model\_artifacts/, model.py

Group 2	Database \& API	schema.sql, database.py, main.py

Group 3	UI \& Optimization	streamlit\_app.py, Docker configs





📋 Postman Testing

Import postman\_collection.json to test:



POST /predict (multipart image upload)



GET /disease/{name}







🤝 Contributors

GitHub	Role

@Raaunnakk555	Project Lead / ML Engineer

@DevTanisha-max	Contributor

@riya23605shukla-arch	Contributor

📄 License

MIT License







🙏 Acknowledgments

PlantVillage Dataset for training (to be used)



FastAPI \& Streamlit communities



TensorFlow/Keras for deep learning framework







⭐ Show Your Support

Good luck for your pre-review! ✨



If this project helps you, please give it a ⭐ on GitHub!

