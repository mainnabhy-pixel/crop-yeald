# crop-yeald
# 🌾 Crop Yield Prediction and AgriPrice Web App

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/<USERNAME>/crop-yield-prediction/blob/main/Crop_Yield_Prediction_Deploy.ipynb)
![Python](https://img.shields.io/badge/Python-3.10+-blue)
![License](https://img.shields.io/badge/License-MIT-green)

A machine learning project that predicts **crop yield (tonnes per hectare)** from country, crop type, year, rainfall, pesticide usage and average temperature. Four regression models are compared, and the best one (KNN) is deployed as a web app, **AgriPrice**, using Flask and ngrok.

**Team No. 5** · Chandigarh University · Department of [Branch]
Supervisor: [Name, Designation]

## 👥 Team

| Roll No. | Name |
|---|---|
| 26BAI70121 | Avneet Singh |
| 26BAI70147 | Piyush Chohan |
| 26BAI71030 | Shrey Srivastava |
| 26BAI70155 | Keshavpreet Singh |
| 26BAI70142 | Ronith Sharma |

## 📊 Dataset

- **File:** `combined_crop_master_dataset.csv`
- **Size:** 13,130 rows × 9 columns, no missing values
- **Coverage:** 101 countries, 10 crops, 23 years (1990 onwards)
- **Source:** [add dataset name and link]

| Column | Description |
|---|---|
| `area` | Country |
| `item` | Crop (maize, potatoes, rice, sorghum, soybeans, wheat, and more) |
| `year` | Year of record |
| `average_rain_fall_mm_per_year` | Average annual rainfall (mm) |
| `pesticides_tonnes` | Pesticide use (tonnes) |
| `avg_temp` | Average temperature (°C) |
| `value_hg_ha` | Yield in hg/ha (dropped to avoid target leakage) |
| `yield_tonnes_per_ha` | **Target:** yield in tonnes per hectare |

## 🔬 Workflow

1. Load and explore the data (info, describe, missing values)
2. Exploratory analysis: histograms, correlation heatmap, box and violin plots, yearly trends
3. Feature importance with Extra Trees
4. One-hot encoding, `StandardScaler`, 80/20 train-test split
5. Train and compare Linear Regression, Decision Tree, Random Forest and KNN
6. 10-fold cross-validation, residual plot and actual-vs-predicted analysis
7. Responsible AI scorecard (fairness, reliability, privacy, inclusiveness, transparency, accountability)
8. Export the model and deploy with Flask + ngrok

## 📈 Results

| Model | Test R² | RMSE (t/ha) |
|---|---|---|
| Linear Regression | 0.734 | 4.16 |
| Decision Tree | 0.942 | 1.94 |
| Random Forest (max depth 7) | 0.806 | 3.54 |
| **KNN (k = 10)** | **0.949** | **1.81** |

KNN was chosen because it has the highest test R² and the lowest RMSE. Its train R² is 0.964, so the gap to test is small.

Correlations between the numeric inputs and yield are weak (|r| ≤ 0.14), which is why non-linear models perform much better than linear regression.

## 🚀 How to Run

### Google Colab (recommended)
1. Click the **Open in Colab** badge above.
2. Upload `combined_crop_master_dataset.csv` to `/content/`.
3. Run all cells from top to bottom.
4. For the web app, upload `index.html`, then run the two **Model Deployment** cells.
5. Add your own keys in Colab **Secrets** (🔑 icon):
   - `NGROK_TOKEN` (free at [ngrok.com](https://dashboard.ngrok.com/get-started/your-authtoken))
   - `ANTHROPIC_API_KEY` (optional, only for AI crop-disease diagnosis)

> ⚠️ Never commit API keys or tokens to this repository.

### Locally
```bash
git clone https://github.com/<USERNAME>/crop-yield-prediction.git
cd crop-yield-prediction
pip install -r requirements.txt
jupyter notebook Crop_Yield_Prediction_Deploy.ipynb
```
Change the dataset path in the notebook from `/content/...` to your local path.

## 🗂 Repository Structure

```
├── Crop_Yield_Prediction_Deploy.ipynb   # Full notebook: EDA, models, deployment
├── index.html                           # AgriPrice web page
├── data/
│   └── combined_crop_master_dataset.csv
├── requirements.txt
├── LICENSE
└── README.md
```

## 🖼 Screenshots

<!-- Add images, e.g. ![AgriPrice](images/agriprice.png) -->

## 🛠 Tech Stack

Python · pandas · NumPy · scikit-learn · matplotlib · seaborn · SciPy · Flask · pyngrok · joblib · Google Colab

## 🔮 Future Work

- Add soil, irrigation and fertiliser features
- Tune KNN and try gradient boosting models
- Host the app permanently instead of using ngrok

## 📄 License

Released under the [MIT License](LICENSE).
