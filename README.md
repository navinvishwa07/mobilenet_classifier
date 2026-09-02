# MobileNetV2 Image Classifier

A FastAPI web application that classifies uploaded images using the pretrained MobileNetV2 model and ImageNet labels.

## Features

- Upload an image through the browser interface
- Return the top three predicted classes and confidence scores
- Validate image type and limit uploads to 10 MB
- Health check endpoint for deployment monitoring

## Requirements

- Python 3.12 or compatible Python 3 version
- TensorFlow-compatible local environment

## Run Locally

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
uvicorn app:app --reload
```

Open http://127.0.0.1:8000 in a browser.

## API Endpoints

- `GET /` - Serves the web interface
- `GET /health` - Returns application health and model information
- `POST /api/predict` - Accepts an image upload in the `file` form field

Example request:

```bash
curl -X POST -F "file=@image.jpg" http://127.0.0.1:8000/api/predict
```

## Deploy on Render

Create a Render Web Service connected to this repository with:

- **Build Command:** `pip install -r requirements.txt`
- **Start Command:** `uvicorn app:app --host 0.0.0.0 --port $PORT`
- **Root Directory:** leave blank

Render provides the `$PORT` environment variable at runtime.

## Project Structure

```text
.
├── app.py
├── index.html
├── requirements.txt
├── css/
│   └── style.css
└── js/
    └── script.js
```
