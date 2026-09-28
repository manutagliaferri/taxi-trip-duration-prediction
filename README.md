# NYC Taxi Ride Duration Prediction

An end-to-end Data Analytics and Machine Learning pipeline developed for the **Data Analytics course at Università della Svizzera italiana (USI)**.  
The project focuses on predicting the total trip duration of New York City taxi rides by processing over 1.4 million records using advanced geospatial feature engineering and gradient boosting.

---

## 📊 Project Workflow & Key Steps

1. **Exploratory Data Analysis (EDA):**
   - Univariate analysis of the target variable (`trip_duration`), identifying and handling massive technical outliers (trips lasting over a month).
   - Temporal dynamics analysis revealing clear rush-hour commuting peaks and weekly trends.
   - Spatial distribution mapping via **Folium heatmaps**, detecting GPS glitches and isolating traffic within Manhattan and major airports.

2. **Data Pre-processing & Cleaning:**
   - Applied geographical bounding boxes to filter out invalid coordinates.
   - Duration clipping (removing rides under 33 seconds or over 6 hours).
   - Speed constraints validation to match physical urban limits ($0$ to $130\text{ km/h}$).

3. **Advanced Feature Engineering:**
   - **Distance Metrics:** Computed Haversine distance and grid-based **Manhattan distance** calibrated for New York's layout.
   - **Geometric Directionality:** Extracted compass **bearing** to capture asymmetric grid orientation and traffic flow.
   - **The "Golden Feature":** Estimated trip duration derived from Manhattan distance divided by the historical average speed per hour.

4. **Predictive Modeling:**
   - Trained an **XGBoost Regressor** optimized via log-transformed targets ($\log(1+y)$) to penalize relative errors.
   - Implemented custom learning rate decay, depth tuning, and early stopping.

---

## 📈 Results

- **RMSLE:** `0.32520`
- **Mean Absolute Error (MAE):** `174.53` seconds (an average error of less than 3 minutes in a chaotic urban environment).

---

## 📂 Repository Structure

```text
├── ride_duration_prediction.ipynb   # Complete data pipeline (EDA, features, XGBoost)
├── Report.pdf                       # Formal project report (PDF format)
└── README.md
