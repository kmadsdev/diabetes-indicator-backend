# Diabetes Indicator - Backend
**API for the Diabetes Indicator App <br>**
- Access the website here: [https://kmads.dev/diabetes-indicator](https://kmads.dev/diabetes-indicator/) <br>
- Access the repository here: [https://kmads.dev/source-code/diabetes-indicator](https://kmads.dev/source-code/diabetes-indicator)

# Deployment
- **Frontend: [Source](https://source.kmads.dev/diabetes-indicator/) | [Live Deploy](https://kmads.dev/diabetes-indicator/)**
- **Backend + Machine Learning: [Source](https://source.kmads.dev/diabetes-indicator-backend/)**

# API
You can access the API here:
```
https://api.kmads.dev/diabetes-indicator/<args>
```

### Endpoints:
Endpoint | Method | Description
---------|--------|-----------------
/        | GET    | API status with current model info
/health  | GET    | Health check endpoint
/models  | GET    | List all available trained models
/predict | GET    | Diabetes prediction with confidence percentage

### Health Indicators (Prediction Input)
The `/predict` endpoint accepts 17 comma-separated health indicators:
| # | Field | Type | Values |
|---|-------|------|--------|
| 1 | HighBP | int | 0, 1 |
| 2 | HighChol | int | 0, 1 |
| 3 | CholCheck | int | 0, 1 |
| 4 | BMI | float | 0-275 |
| 5 | Smoker | int | 0, 1 |
| 6 | Stroke | int | 0, 1 |
| 7 | HeartDiseaseorAttack | int | 0, 1 |
| 8 | PhysActivity | int | 0, 1 |
| 9 | Fruits | int | 0, 1 |
| 10 | Veggies | int | 0, 1 |
| 11 | HvyAlcoholConsump | int | 0, 1 |
| 12 | AnyHealthCare | int | 0, 1 |
| 13 | NoDocbcCost | int | 0, 1 |
| 14 | GenHlth | int | 1-5 |
| 15 | DiffWalk | int | 0, 1 |
| 16 | Sex | int | 0, 1 |
| 17 | Age | int | 0-13 (age groups) |

# Architecture
![Architecture](assets/infra/architecture-2025-11-18.svg)
```
    diabetes-indicator-backend
    ⊢ trained-models/ 
    |  ⌞ <.pkl files> (models trained and ready for production)
    ⊢ machine-learning/
    |  ⌞ ml.ipynb (python notebook where the models are trained)
    ⊢ main.py (API made with fastapi and uvicorn)
    ⊢ requirements.txt (python dependencies)
    ⊢ vercel.json (vercel deploy config)
    ⌞ README.md
```

# Flow
- **`client`** Request request prediction from the **`frontend`**
- **`frontend`** gets prediction from **`api/`**
- **`backend`** choose the latest model (.pkl) from **`trained-models/`**
- **`trained-models/`** receives the model (.pkl) from **`machine-learning/`**

Simplified:
- Client -> Frontend <-> Backend -> `<model>.pkl` (trainedModels/)

# Copyright
No restrictions of use, just give some credits if you want
