🚦 Integrated Smart Traffic Management System

An AI-powered traffic monitoring system that performs vehicle detection, direction-based counting, congestion analysis, and emergency vehicle detection using visual and siren audio signals.

The system processes traffic videos and provides real-time analytics through a dashboard built with Streamlit, while the backend processing is handled using FastAPI and deep learning models.

📌 Project Overview

Urban traffic congestion and emergency vehicle delays are major problems in modern cities.
This project introduces an AI-based smart traffic monitoring system that analyzes traffic videos to automatically detect vehicles, count traffic flow, identify congestion, and detect emergency vehicles.

The system combines:

Computer Vision for vehicle detection

Audio Classification for siren detection

Machine Learning models

FastAPI backend

Streamlit dashboard

The output helps simulate smart traffic signal prioritization.

🧠 Technologies Used
Programming Language

Python 3.11

Machine Learning & AI

YOLOv8 (Vehicle detection)

ResNet18 (Audio siren classifier)

HuggingFace Transformers (Audio classification)

Backend

FastAPI

Uvicorn

Frontend

Streamlit

Libraries

PyTorch

Ultralytics

OpenCV

Librosa

Transformers

Pandas

NumPy

SQLAlchemy

Matplotlib

Seaborn

🏗 System Architecture
Traffic Video Input
        │
        ▼
Video Processing Pipeline
        │
        ▼
Vehicle Detection (YOLOv8)
        │
        ▼
Vehicle Tracking & Counting
        │
        ▼
Direction Detection
(N→S, S→N, E→W, W→E)
        │
        ▼
Congestion Analysis
        │
        ▼
Emergency Detection
 ├─ Visual Detection (YOLOv8)
 └─ Audio Siren Detection (ResNet18)
        │
        ▼
Traffic Signal Priority Decision
        │
        ▼
Results Stored in Database
        │
        ▼
Displayed on Streamlit Dashboard

📁 Project Structure
vehicle-counting-and-tracking
│
├── backend
│   ├── main.py
│   ├── database.py
│
├── frontend
│   └── app.py
│
├── inference
│   ├── video_inference.py
│   ├── audio_inference.py
│   ├── media_utils.py
│   └── runs
│
├── models
│   ├── vehicle_detector_best.pt
│   ├── emergency_visual_best.pt
│   ├── audio_siren_resnet18.pt
│
├── requirements.txt
└── main.py
🚗 Key Features
Vehicle Detection

Detects multiple vehicle classes such as:

Cars

Trucks

Buses

Motorcycles

Using YOLOv8 object detection model.

Direction-Based Vehicle Counting

Vehicles are counted based on movement direction:

North → South
South → North
East → West
West → East

This allows better traffic flow analysis.

Congestion Detection

The system calculates:

Average vehicles per frame

Peak vehicle count

Congestion level

Low
Medium
High
Emergency Vehicle Detection

Emergency vehicles are detected using two independent methods:

1️⃣ Visual detection

YOLOv8 identifies ambulance or police vehicles.

2️⃣ Audio detection

ResNet18 classifier detects siren sound.

Emergency is confirmed when both visual and audio detection match.

Smart Signal Priority

Based on congestion or emergency vehicle detection, the system suggests signal changes such as:

Extend North-South green signal
Prioritize emergency lane
⚙️ Installation Guide
1️⃣ Clone the repository
git clone https://github.com/yourusername/vehicle-counting-and-tracking.git
cd vehicle-counting-and-tracking
🐍 Create Virtual Environment
python -m venv venv

Activate environment.

Windows
venv\Scripts\activate
Linux / Mac
source venv/bin/activate
📦 Install Dependencies

pip install -r requirements.txt
🚀 Running the Project

The system runs using two services:

Backend API (FastAPI)
Frontend Dashboard (Streamlit)
▶ Run Backend Server

Open terminal and run:

uvicorn backend.main:app --host 127.0.0.1 --port 8000

Backend will start at:

http://127.0.0.1:8000

API documentation available at:

http://127.0.0.1:8000/docs
▶ Run Frontend Dashboard

Open another terminal and run:

streamlit run frontend/app.py

Dashboard will start at:

http://localhost:8501
🖥 Using the Dashboard

1️⃣ Open the dashboard

http://localhost:8501

2️⃣ Upload a traffic video

3️⃣ Click

Start Video Inference

4️⃣ System processes the video and displays:

Vehicle counts

Direction counts

Congestion level

Emergency alerts

Processed output video

📊 API Endpoints
Health Check
GET /health

Checks backend status.

Video Inference
POST /infer/video

Uploads video for traffic analysis.

Audio Inference
POST /infer/audio

Detects siren sound from audio.

Vehicle History
GET /vehicle-counts

Returns previous inference runs.

Emergency Alerts
GET /emergency-alerts

Returns detected emergency vehicle alerts.

Processed Video
GET /runs/{run_id}/video

Returns processed output video.

📂 Output Files

Processed files are stored inside:

inference/runs/

Each run contains:

input video
extracted audio
processed video
metadata
📈 Dashboard Analytics

The dashboard provides visual analytics including:

Traffic congestion trends

Direction traffic statistics

Vehicle class distribution

Emergency detection history

Model performance metrics

⚠️ System Requirements

Recommended configuration:

Python 3.10+
8 GB RAM
GPU optional (for faster inference)



👨‍💻 Author

Vennapusa Yaswanth Reddy

B.Tech Computer Science and Engineering
Machine Learning Stream
