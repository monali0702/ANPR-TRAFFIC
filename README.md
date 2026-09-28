# ANPR-Trajectory-Platform

Production-oriented AI platform for city-wide ANPR and traffic analytics.

## Objective
This project is designed to ingest real CCTV footage, extract frames, prepare datasets, train and evaluate detection/OCR models, perform tracking and trajectory analysis, and expose results through APIs and a dashboard.

## Architecture overview
The platform follows a staged pipeline:

- Real videos
- Frame extraction
- Dataset preparation
- Annotation
- Training and evaluation
- Checkpoint selection
- Inference
- Tracking and trajectory generation
- Analytics
- Database persistence
- FastAPI services
- React dashboard

## Technology stack
- Backend: Python 3.11, FastAPI, Uvicorn, Pydantic, SQLAlchemy, PostgreSQL, PostGIS
- CV: OpenCV, PyTorch, Ultralytics YOLO
- OCR: PaddleOCR
- Tracking: ByteTrack or BoT-SORT
- Re-ID: Torchreid / OSNet
- Frontend: React, Vite, Tailwind CSS, Recharts
- Mapping: Google Maps JavaScript API
- Testing: Pytest, Playwright
- MLOps: MLflow
- Deployment: Docker, Docker Compose

## Folder structure
The project is scaffolded with the required directories and entry-point files for future development.

## Setup requirements
- Python 3.11+
- Node.js 18+
- npm or pnpm
- Docker and Docker Compose

## Create the environment

```bash
python -m venv .venv
source .venv/bin/activate  # Linux/macOS
# .venv\Scripts\activate  # Windows
pip install --upgrade pip
pip install -r requirements.txt
```

## Start the backend

```bash
uvicorn src.api.main:app --host 0.0.0.0 --port 8000 --reload
```

## Start the frontend

```bash
cd frontend
npm install
npm run dev -- --host 0.0.0.0 --port 5173
```

## Where to place camera videos
Place the real camera footage in:

- `data/raw/videos/camera_01/`
- `data/raw/videos/camera_02/`
- `data/raw/videos/camera_03/`

## Planned ML training workflow
1. Inspect videos
2. Extract frames
3. Assess frame quality
4. Select representative frames
5. Annotate datasets
6. Split train/validation/test sets
7. Validate dataset integrity
8. Train the detector/OCR model
9. Evaluate using precision, recall, mAP50, mAP50-95, inference speed, FPS, and error analysis
10. Select the best checkpoint
11. Run inference testing
12. Prepare prediction-ready deployment

## Planned inference workflow
1. Load a trained model checkpoint
2. Run inference on extracted frames or live streams
3. Detect vehicles and license plates
4. Run OCR on plate crops
5. Track vehicles across frames
6. Re-identify vehicles across cameras
7. Reconstruct trajectories
8. Aggregate analytics
9. Persist results to the database
10. Expose APIs and dashboard metrics

## Testing

```bash
pytest
```

For frontend validation:

```bash
cd frontend
npm run build
```

## Important note
Models are not trained yet.

This repository currently contains the architectural foundation and scaffolding only.
