Monsoon Temperature Anomaly Detection & Forecasting 🌧️📈
📌 Project Overview
This project leverages historical climate data, feature engineering, and machine learning to detect unusual monsoon temperature patterns in India and forecast potential future anomalies.

By combining unsupervised anomaly detection (Isolation Forest) with time series forecasting (Prophet), we move from a reactive analysis of past weather to a proactive early warning system that can help governments, farmers, and disaster management teams prepare in advance.

🎯 Problem Statement
Monsoon temperatures have a direct impact on:

Agricultural yields & food security

Water resource planning

Disaster preparedness (floods/droughts)

Economic stability in rural communities

Traditional methods rely heavily on historical averages, which often miss rare but critical anomalies that could signal high-risk years.

💡 Solution
Our pipeline:

Fetches & cleans seasonal temperature data from a MySQL database.

Engineers climate-specific features (rolling means, seasonal contrasts, long-term anomalies, lagged variables, trends).

Identifies past anomalies using Isolation Forest — no labeled dataset required.

Forecasts next 10 years using Prophet, then applies the same anomaly detection on predicted values.

Visualizes past anomalies (red) & forecasted anomalies (orange) for decision-making clarity.

⚙️ Tech Stack
Database: MySQL

Data Processing: Python (Pandas, NumPy)

Machine Learning:

Isolation Forest — robust outlier detection

Prophet — interpretable time series forecasting

Visualization: Matplotlib

Deployment Ready: Flask API endpoint for predictions

📂 Data
Source: Ministry of Earth Sciences – India Meteorological Department (IMD)

Columns:

YEAR — Observation year

JAN-FEB, MAR-MAY, JUN-SEP, OCT-DEC — Seasonal average temperatures

ANNUAL — Yearly average temperature

🛠️ Installation & Setup
bash
Copy
Edit
# Clone repo
git clone https://github.com/yourusername/monsoon-anomaly-forecast.git
cd monsoon-anomaly-forecast

# Create virtual environment (optional but recommended)
python -m venv venv
source venv/bin/activate   # Linux/Mac
venv\Scripts\activate      # Windows

# Install dependencies
pip install -r requirements.txt
🚀 Usage
1. Database Connection
Update your MySQL credentials in the script:

python
Copy
Edit
engine = create_engine("mysql+pymysql://USERNAME:PASSWORD@HOST:PORT/DATABASE")
2. Run the Pipeline
bash
Copy
Edit
python main.py
3. Output
Plots: Visualizing temperature trends, past anomalies, and forecasted anomalies.

CSV: Combined dataset with anomaly flags.

API: Flask endpoint (/predict) to check anomaly probability for given inputs.

📊 Example Output

Red dots = past anomalies
Orange dots = forecasted anomalies

📈 ML Workflow
Data Cleaning & Transformation:

Convert columns to numeric

Fill missing values (forward-fill)

Add date column (ds) for time series models

Feature Engineering:

Rolling averages & standard deviations

Anomalies vs. long-term mean

Lag features (t-1, t-2)

Monsoon vs. pre-monsoon contrast

Rolling trend slope over 5 years

Anomaly Detection:

IsolationForest(contamination=0.07) detects outliers

is_anomaly flag set for each year

Forecasting with Prophet:

Train on year & JUN-SEP temp

Predict next 10 years

Apply same feature engineering to predicted values

Future Anomaly Detection:

Apply Isolation Forest on forecast features

Flag future anomalies as is_anomaly_future

📌 Impact
Proactive decision-making for climate risk management

Supports agricultural planning & disaster preparedness

Scalable to other variables (rainfall, pressure, ENSO indices)

🔮 Future Enhancements
Add rainfall & atmospheric pressure data for multi-variable detection

Deploy real-time anomaly detection API for ministries

Build interactive dashboards with Plotly/Dash or Power BI

