#  Auckland Air Quality Prediction (PM2.5)

---

### Project 2 - Auckland Air Quality Prediction (PM2.5)

#### Overview

Predictive regression modelling of PM2.5 air pollution in Auckland using a multi-source data pipeline. The project applies the full data science workflow: data acquisition via web scraping and APIs, data wrangling, EDA, and supervised machine learning.

#### Data Sources

| # | Source | Method | Description |
|---|--------|--------|-------------|
| 1 | [AQI.in](https://www.aqi.in/dashboard/new-zealand/auckland/auckland/pm) | Web scraping | Live 24-hour half-hourly PM2.5 readings for Auckland |
| 2 | [OpenAQ API v3](https://api.openaq.org/v3) | REST API | Hourly PM2.5 & PM10 from Eskdale Reserve, Auckland (Station ID: 3062106) |
| 3 | [Open-Meteo Archive API](https://archive-api.open-meteo.com) | REST API | Hourly historical weather (temperature, humidity, wind speed, pressure, precipitation) Sep–Dec 2024 |

#### Research Questions

1. Does temperature positively correlate with PM2.5 levels in Auckland?
2. Does higher wind speed help disperse air pollution (lower PM2.5)?
3. Is there a diurnal (time-of-day) pattern in Auckland's PM2.5 levels?
4. Which model best predicts PM2.5 — linear regression or kNN?
5. Which weather feature is the strongest predictor of PM2.5?

#### Key Findings

- Auckland's PM2.5 consistently falls within the WHO 'Good' category (0–6.85 µg/m³ after outlier removal)
- A clear morning peak at 6–10am aligns with rush hour traffic patterns
- kNN with Manhattan distance (k=3) was the best model: **RMSE = 1.27, R² = 0.49**
- Linear regression performed poorly (R² ≈ 0.03) due to weak linear relationships
- Polynomial regression (degree 3) severely overfitted (R² = −29)

#### Models Compared

| Model | RMSE | R² |
|-------|------|----|
| kNN — Manhattan, k=3 | 1.27 | 0.49 |
| kNN — Euclidean, k=3 | ~1.4 | ~0.38 |
| Multiple Linear Regression | ~1.6 | ~0.03 |
| Simple Linear Regression | ~1.6 | ~0.02 |
| Polynomial Regression (deg 3) | High | −29 |

#### Tools & Techniques

- **Python:** pandas, numpy, matplotlib, seaborn, scikit-learn, BeautifulSoup, requests
- **Techniques:** Web scraping, REST API integration, data wrangling, IQR outlier removal, EDA, feature engineering, regression modelling (simple, multiple, polynomial), kNN regression, cross-validation (5-fold), bootstrap confidence intervals, RMSE & R² evaluation

---

## Repository Structure

```
Auckland-Air-Quality-Project/
│
├── README.md
├── Auckland_Air.ipynb

```

## Installation

### Project 2 — Additional Python Packages Required

```bash
pip install requests beautifulsoup4 scikit-learn seaborn matplotlib pandas numpy
```
`
`
> **Note:** The notebook uses live web scraping and API calls. An active internet connection is required to reproduce the data acquisition cells. The OpenAQ API requires a free API key — replace the `OPENAQ_API_KEY` variable in the notebook with your own key from [openaq.org](https://openaq.org).

---

## Author

**Farbin Aziz**  
farbin.aziz07@gmail.com | [linkedin.com/in/farbin](https://www.linkedin.com/in/farbin/)  
Master of Information Sciences — Massey University, Auckland NZ
