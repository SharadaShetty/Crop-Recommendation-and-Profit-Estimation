# Dynamic Crop Recommendation & Profit Estimation

An end-to-end web application that predicts optimal crops based on soil and environmental inputs, quantifies uncertainty, provides SHAP-based explanations, and simulates risk-adjusted profits using real commodity price data.

---

## 🚀 Features

- **Real-time Crop Prediction**  
  A Multilayer Perceptron (MLP) served via FastAPI for low-latency inference.

- **Uncertainty Quantification**  
  Monte Carlo Dropout at inference to estimate predictive entropy.

- **Explainability**  
  SHAP (SHapley Additive exPlanations) for per-feature contribution insights.

- **Probability Calibration**  
  Temperature scaling to align model confidences with real-world accuracies.

- **Profit Simulation**  
  Monte Carlo sampling of historical modal prices for expected profit ± risk.

- **Responsive UI**  
  Glassmorphic design with scroll animations and dynamic district loading.

---

## 🔧 Tech Stack

### Backend
- Python 3.9+  
- FastAPI, Uvicorn  
- PyTorch, scikit-learn, SHAP  

### Frontend
- HTML5, CSS3 (Glassmorphism)  
- Bootstrap 5  
- AOS animations  
- jQuery  

### Data
- **Soil parameters CSV** (N, P, K, pH, rainfall, temperature, humidity)  
- **Government commodity prices CSV**

---

## 📁 Repository Structure

```
.
├── data/
│   ├── Crop_recommendation.csv       # Training data
│   └── Current_Daily_Price_...csv    # Commodity prices
├── model/
│   └── baseline/
│       └── baseline.hdf5             # Trained MLP weights
├── utils/
│   ├── pred_crop.py                  # Prediction + SHAP utilities
│   └── pred_profit.py                # Profit simulation logic
├── main.py                           # FastAPI app
├── index.html                        # Frontend skeleton
├── index.js                          # Frontend logic (AJAX, DOM updates)
├── requirements.txt                  # Python dependencies
├── profit_visualization.ipynb        # Jupyter notebook for profit plots
└── README.md                         # ← you are here
```

---

## ⚙️ Getting Started

### Prerequisites
- Python 3.8+  
- pip or conda  
- Node.js (optional, for front-end tooling)

### Installation

1. **Clone the repo**  
   ```bash
   git clone https://github.com/shvm2/A-Dynamic-Crop-Prediction-and-Profit-Estimation-Web-Application-with-Real-Time-User-Input-Adaptation.git
   cd A-Dynamic-Crop-Prediction-and-Profit-Estimation-Web-Application-with-Real-Time-User-Input-Adaptation
   ```

2. **Create & activate a virtual environment**  
   ```bash
   python3 -m venv venv
   source venv/bin/activate    # macOS/Linux
   venv\Scripts\activate     # Windows
   ```

3. **Install Python dependencies**  
   ```bash
   pip install -r requirements.txt
   ```

---

## 🚀 Running the App

1. **Start the backend**  
   ```bash
   uvicorn main:app --reload
   ```
   The FastAPI server will run at `http://127.0.0.1:8000`.

2. **Open the frontend**  
   - Simply open `index.html` in your browser, **or**  
   - Serve via any static server:
     ```bash
     npx serve .
     ```
3. **Interact!**  
   - Enter soil N, P, K, pH  
   - Select State, District, Month  
   - Click **Predict**  
   - View crop recommendation, confidence, SHAP explanations, & profit estimates

---

## 📘 Usage Examples

### API Endpoints

#### `POST /predict`

- **Payload (JSON):**
  ```json
  {
    "nitrogen": 90.0,
    "phosphorous": 42.0,
    "potassium": 43.0,
    "ph": 6.5,
    "state": "KARNATAKA",
    "district": "BANGALORE RURAL",
    "month": "JAN"
  }
  ```

- **Response (JSON):**
  ```json
  {
    "crop": "apple",
    "probabilities": {
      "apple": 0.85,
      "banana": 0.10,
      "..."
    },
    "uncertainty": 0.12,
    "shap_values": {
      "N": 0.15,
      "pH": 0.05,
      "..."
    },
    "profit_estimates": [
      {
        "crop": "apple",
        "expected_profit": 5320,
        "risk": 450
      }
    ]
  }
  ```

---

## 📊 Notebooks & Visualization

- **profit_visualization.ipynb**  
  Generates tables and plots of expected profit ± risk across all crops.

- **SHAP Summary**  
  Use the notebook to produce bar charts of mean |SHAP| per feature for publication figures.

---

## 🤝 Contributing

1. **Fork** this repository  
2. **Create** your feature branch  
   ```bash
   git checkout -b feature/YourFeature
   ```
3. **Commit** your changes  
   ```bash
   git commit -m "Add feature"
   ```
4. **Push** to your branch  
   ```bash
   git push origin feature/YourFeature
   ```
5. **Open** a Pull Request

Please fill out issues and PRs with clear descriptions, and adhere to the existing code style.

---

## 📝 License

This project is licensed under the MIT License. See `LICENSE` for details.

---

## ✉️ Contact
For questions or feedback, feel free to reach out:
- **Email:** <sharadashetty03@gmail.com>, <shivamsingh271104@gmail.com>  
- **GitHub**: [Sharada Shetty](https://github.com/SharadaShetty), 
              [shvm2](https://github.com/shvm2)

happy farming! 🌱
