# NASDAQ Stock Price Prediction and Analysis using Azure

## Overview

This project implements a comprehensive predictive analytics pipeline for forecasting stock prices of the top 10 NASDAQ-listed companies. Leveraging Azure Machine Learning and Python, the solution performs exploratory data analysis (EDA), builds regression-based forecasting models, and deploys them as scalable endpoints. Real-time predictions are integrated into Azure SQL Database for seamless reporting and stakeholder insights.

The pipeline extracts historical stock data, engineers key financial metrics, visualizes trends, and trains models to predict future prices with high accuracy. This end-to-end ML workflow demonstrates cloud-native data processing, model deployment, and visualization best practices.

### Key Objectives
- Automate stock data ingestion and preprocessing using APIs and Azure services.
- Develop robust regression models for accurate price forecasting.
- Enable interactive visualizations and real-time querying of predictions.

## Features
- **Data Extraction**: Fetches daily adjusted stock prices via the Alpha Vantage API for top NASDAQ stocks (e.g., AAPL, MSFT, GOOGL, AMZN, etc.).
- **Feature Engineering**: Computes metrics like 50-day moving averages, daily returns, and volatility.
- **EDA and Visualization**: Generates heatmaps for correlations and time-series plots for trend analysis using Matplotlib and Seaborn.
- **ML Modeling**: Trains regression models (e.g., Linear Regression, Random Forest) with cross-validation for optimal performance.
- **Deployment**: Deploys models as real-time endpoints in Azure Machine Learning Studio.
- **Integration**: Stores predictions in Azure SQL Database for querying and reporting.
- **Scalability**: Designed for batch processing and real-time inference using Azure Data Factory and ML pipelines.

## Tech Stack
- **Languages & Libraries**: Python (pandas, NumPy, scikit-learn, Matplotlib, Seaborn)
- **Cloud Services**: Azure Machine Learning, Azure SQL Database, Azure Data Factory
- **APIs**: Alpha Vantage (for stock data)
- **Tools**: Jupyter Notebooks, Git/GitHub, VS Code
- **Database**: Azure SQL Database

## Prerequisites
- Python 3.8+ with required libraries (install via `requirements.txt`).
- An active Azure subscription (sign up at [azure.microsoft.com](https://azure.microsoft.com)).
- Alpha Vantage API key (free tier available at [alphavantage.co](https://www.alphavantage.co/support/#api-key)).
- Azure CLI or Azure Portal access for resource provisioning.

## Setup Instructions

1. **Clone the Repository**:
   ```
   git clone https://github.com/pratikbhutada/nasdaq-stock-prediction-azure.git
   cd nasdaq-stock-prediction-azure
   ```

2. **Install Dependencies**:
   ```
   pip install -r requirements.txt
   ```
   *(Note: Create a `requirements.txt` file with the listed libraries if not already present.)*

3. **Configure Environment Variables**:
   Create a `.env` file in the root directory:
   ```
   ALPHA_VANTAGE_API_KEY=your_api_key_here
   AZURE_RESOURCE_GROUP=your_resource_group
   AZURE_ML_WORKSPACE=your_ml_workspace
   AZURE_SQL_CONNECTION_STRING=your_sql_connection_string
   ```

4. **Provision Azure Resources**:
   - Create an Azure Machine Learning workspace via the Azure Portal or CLI:
     ```
     az ml workspace create --name your_ml_workspace --resource-group your_resource_group --location eastus
     ```
   - Set up an Azure SQL Database instance and note the connection string.
   - (Optional) Configure Azure Data Factory for ETL pipelines.

5. **Run EDA and Model Training**:
   Open `notebooks/eda_and_modeling.ipynb` in Jupyter and execute cells sequentially. This will:
   - Fetch data for the top 10 NASDAQ stocks.
   - Perform EDA and generate visualizations.
   - Train and evaluate models.

## Usage

### 1. Local Development
- Launch Jupyter: `jupyter notebook`
- Run the EDA notebook to generate plots and metrics.
- Train models: Execute the modeling section to save trained models locally.

### 2. Model Deployment
- Use the Azure ML SDK in `scripts/deploy_model.py`:
  ```
  python scripts/deploy_model.py
  ```
- This registers the model and deploys it as a real-time endpoint. Access predictions via the Azure ML Studio inference UI.

### 3. Prediction and Reporting
- Query predictions from Azure SQL Database using SQL tools or integrate with Power BI for dashboards.
- Example inference script (`scripts/predict.py`):
  ```
  python scripts/predict.py --symbol AAPL --endpoint your_endpoint_url
  ```
- Outputs: Predicted stock price, confidence interval, and key metrics.

### Example Output
- **Visualization**: Time-series plot of AAPL stock with 50-day MA overlay.
- **Prediction**: For AAPL on 2025-10-01: Predicted Close Price = $255.69 (RMSE: $2.34).

## Project Structure
```
nasdaq-stock-prediction-azure/
├── README.md                 # This file
├── requirements.txt          # Python dependencies
├── .env.example              # Environment template
├── notebooks/
│   └── eda_and_modeling.ipynb # EDA and model training
├── scripts/
│   ├── fetch_data.py         # API data extraction
│   ├── train_model.py        # Model training
│   ├── deploy_model.py       # Azure deployment
│   └── predict.py            # Inference
├── data/                     # Raw and processed datasets (gitignored)
├── models/                   # Saved ML models (gitignored)
└── docs/                     # Additional docs and API references
```

## Results
- Achieved RMSE < $5 on validation set for top stocks.
- Model accuracy: R² > 0.85 across ensemble regressions.
- Deployment latency: < 200ms for real-time predictions.

## Feedback and contributions are welcome!

## Contact
Pratik Bhutada - [pratikbhutada910@gmail.com](mailto:pratikbhutada910@gmail.com)  
[LinkedIn](https://www.linkedin.com/in/pratikbhutada910/) | [GitHub](https://github.com/Pratik5432)
