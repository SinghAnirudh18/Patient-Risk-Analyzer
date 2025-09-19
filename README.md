# Patient Deterioration Risk Dashboard

A Streamlit-based web application for predicting patient deterioration risk using machine learning. This dashboard allows healthcare professionals to upload patient data and receive risk scores to identify high-risk patients who may require immediate attention.

## 🏥 Overview

This application uses a pre-trained LightGBM model to analyze patient data and predict the risk of deterioration within 90 days. The model considers various health metrics including DALY (Disability-Adjusted Life Years), QALY (Quality-Adjusted Life Years), QOLS (Quality of Life Score), and other clinical indicators.

## ✨ Features

- **Interactive Dashboard**: User-friendly Streamlit interface for data upload and visualization
- **Risk Assessment**: Real-time prediction of patient deterioration risk
- **Customizable Thresholds**: Adjustable risk threshold to identify high-risk patients
- **Data Export**: Download predictions as CSV files for further analysis
- **Comprehensive Metrics**: Analysis of multiple health indicators and temporal features

## 🚀 Quick Start

### Prerequisites

- Python 3.7 or higher
- pip package manager

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/SinghAnirudh18/Patient-Risk-Analyzer.git
   cd Patient-Risk-Analyzer
   ```

2. **Install required dependencies**
   ```bash
   pip install streamlit pandas lightgbm numpy
   ```

3. **Run the application**
   ```bash
   streamlit run streamlit/streamlit_app.py
   ```

4. **Access the dashboard**
   - Open your web browser
   - Navigate to `http://localhost:8501`

## 📊 Data Requirements

The application expects a CSV file with the following structure:

### Required Columns

- **Patient Information**:
  - `PATIENT_ID`: Unique patient identifier
  - `OBS_DATE`: Observation date
  - `BIRTHDATE`: Patient's birth date
  - `AGE_AT_OBS`: Age at observation

- **Health Metrics**:
  - `DALY`: Disability-Adjusted Life Years
  - `QALY`: Quality-Adjusted Life Years
  - `QOLS`: Quality of Life Score
  - `308136`, `310798`, `314076`, `59621000`: Clinical indicators

- **Temporal Features** (lagged values):
  - `DALY_lag_1`, `DALY_lag_7`, `DALY_lag_30`
  - `QALY_lag_1`, `QALY_lag_7`, `QALY_lag_30`
  - `QOLS_lag_1`, `QOLS_lag_7`, `QOLS_lag_30`
  - Similar lagged features for other metrics

- **Rolling Averages**:
  - `DALY_rollmean_7`, `DALY_rollmean_30`
  - `QALY_rollmean_7`, `QALY_rollmean_30`
  - `QOLS_rollmean_7`, `QOLS_rollmean_30`
  - Similar rolling averages for other metrics

- **Temporal Indicators**:
  - `day_of_week`: Day of the week (0-6)
  - `month`: Month (1-12)
  - `day`: Day of the month
  - `is_weekend`: Weekend indicator (0 or 1)

- **Target Variable**:
  - `deterioration_90d`: Deterioration within 90 days (0 or 1)

## 🎯 How to Use

1. **Upload Data**: Use the file uploader to select your patient data CSV file
2. **Set Risk Threshold**: Adjust the slider to define what constitutes "high risk"
3. **View Results**: The dashboard displays:
   - Risk scores for all patients
   - High-risk patient identification
   - Sortable data table
4. **Export Results**: Download the predictions as a CSV file for further analysis

## 🧠 Model Information

- **Algorithm**: LightGBM (Light Gradient Boosting Machine)
- **Model File**: `lgb_deterioration_model.txt`
- **Features**: 52 engineered features including:
  - Current health metrics
  - Historical lagged values (1, 7, 30 days)
  - Rolling averages (7, 30 days)
  - Temporal features (day, month, weekend indicators)

## 📁 Project Structure

```
Patient-Risk-Alanyzer/
├── streamlit_app.py              # Main Streamlit application
├── lgb_deterioration_model.txt   # Pre-trained LightGBM model
├── patient_day_df_small.csv      # Sample patient dataset
└── README.md                     # This file
```

## 🔧 Technical Details

### Dependencies

- **streamlit**: Web application framework
- **pandas**: Data manipulation and analysis
- **lightgbm**: Machine learning model for predictions
- **numpy**: Numerical computing

### Key Features

- **Caching**: Data loading is cached for improved performance
- **Interactive UI**: Real-time updates based on user inputs
- **Responsive Design**: Works on desktop and mobile devices
- **Error Handling**: Graceful handling of data format issues

## 📈 Performance Considerations

- The model is optimized for real-time predictions
- Data caching reduces loading times for repeated uploads
- Efficient feature engineering for large datasets
- Memory-optimized data processing

## 🤝 Contributing

We welcome contributions! Please feel free to submit issues, feature requests, or pull requests.

### Development Setup

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 👥 Authors

- **Sujal Khera** - *Initial work and development*
- **Anirudh Singh** - *Development and testing*

## 🙏 Acknowledgments

- Healthcare professionals who provided domain expertise
- Open source community for the excellent tools and libraries
- Medical institutions for data validation and testing

## 📞 Support

For support, questions, or feedback, please:
- Open an issue on GitHub
- Contact the development team
- Check the documentation for common questions

## 🔮 Future Enhancements

- [ ] Real-time data integration
- [ ] Advanced visualization features
- [ ] Model retraining capabilities
- [ ] Multi-language support
- [ ] API endpoints for integration
- [ ] Enhanced reporting features
- [ ] Mobile app development

---

**Note**: This application is designed for healthcare professionals and should be used in conjunction with clinical judgment. The predictions are meant to assist, not replace, medical decision-making.
