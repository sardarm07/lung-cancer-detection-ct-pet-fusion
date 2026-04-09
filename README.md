# IMADOT — Intelligent Medical Analysis and Diagnosis of Tumors

A full-stack web application for lung cancer detection using CT and PET scan image fusion with deep learning. The system performs tumor segmentation using U-Net and classification through intermediate and late fusion strategies.

## Overview

IMADOT provides a web-based interface for medical professionals to upload CT and PET scan images and receive automated tumor analysis. The backend processes the scans through deep learning models to perform:

1. **Tumor Segmentation** — U-Net-based segmentation of lung regions from CT/PET scans
2. **Intermediate Fusion** — Feature-level fusion combining CT and PET scan features before classification
3. **Late Fusion** — Decision-level fusion combining predictions from separate CT and PET models
4. **3D Visualization** — Three-dimensional rendering of scan data

## Tech Stack

### Frontend
- **Angular 14** with TypeScript
- Angular Material for UI components
- Responsive dashboard with sidebar navigation
- Components: Dashboard, Statistics, Settings

### Backend
- **Flask** (Python) REST API
- **TensorFlow / Keras** for deep learning models
- **OpenCV** for image processing
- **NumPy** for numerical computation
- Flask-CORS for cross-origin support

### Deep Learning Models
- **U-Net** for image segmentation
- **Intermediate Fusion Model** — combines CT and PET feature maps
- **Late Fusion Model** — ensembles CT-only and PET-only classifiers

## Project Structure

```
.
├── imadotAngular/              # Angular frontend
│   ├── src/
│   │   ├── app/
│   │   │   ├── dashboard/      # Main dashboard component
│   │   │   ├── statistics/     # Statistics view
│   │   │   ├── settings/       # Settings panel
│   │   │   ├── sidenav/        # Navigation sidebar
│   │   │   ├── footer/         # Footer component
│   │   │   └── path/           # Prediction service
│   │   └── assets/             # Images and static resources
│   └── package.json
│
├── imadotBackend/              # Flask backend
│   ├── App.py                  # Main Flask application
│   └── Models/
│       ├── UNETFunctions.py    # U-Net segmentation logic
│       ├── FusionFunctions.py  # Intermediate & Late fusion
│       └── plot3DFunction.py   # 3D visualization
│
└── README.md
```

## Prerequisites

- [Node.js](https://nodejs.org/) (v14+)
- [Angular CLI](https://angular.io/cli) (`npm install -g @angular/cli`)
- Python 3.8+
- TensorFlow 2.x
- Flask

## Installation

### 1. Download Pre-trained Weights

Download the trained model weights and place them in `imadotBackend/static/`:

[Download Weights from Google Drive](https://drive.google.com/drive/folders/1X-rMwKNGwjN9u9tGATH9P5mO2YIV2had?usp=drive_link)

### 2. Frontend Setup

```bash
cd imadotAngular
npm install
ng serve
```

The frontend will be available at `http://localhost:4200`.

### 3. Backend Setup

```bash
cd imadotBackend
pip install flask flask-cors tensorflow numpy opencv-python pillow
python App.py
```

The API will be running at `http://localhost:5000`.

## Usage

1. Open the application in your browser at `http://localhost:4200`
2. Navigate to the Dashboard
3. Upload CT scan folder and PET scan folder
4. The system will process the images and display:
   - Segmented tumor image
   - Tumor type classification
   - Prediction probability (intermediate fusion)
   - Prediction probability (late fusion)

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/predict` | Upload CT/PET scans for tumor prediction |
| POST | `/api/plot3D` | Generate 3D visualization of scans |

## License

This project was developed as part of academic research.
