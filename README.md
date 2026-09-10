# VITICUS
PROJECT FOR THE ROAD ACCEDENTS


<img width="748" height="288" alt="image" src="https://github.com/user-attachments/assets/44fb0b59-f1d7-4ffa-b86e-b8a53e8e10eb" />


**Columns you already have:**
Severity → your prediction target
Precipitation(in), **Visibility**(mi), **Weather_Condition** → weather ​
**Start_Time** → extract night/rush hour/weekend ​
**Start_Lat**, **Start_Lng** → location ​
**Sunrise_Sunset** → day/night ​
Traffic_Signal, **Junction**,** Crossing** → road features ​


STEPS TO FOLLOW FOR THE DIR:-

# Create your project folder
mkdir RoadSafe-AI
cd RoadSafe-AI

# Create virtual environment
python -m venv venv
venv\Scripts\activate  # Windows

# Install everything
pip install pandas xgboost shap streamlit scikit-learn plotly folium


