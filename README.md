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


**BASIC CODE TO CHECK WHAT WAS WORKING AND BASIC IDEA (LATER WE CAN REPLACE WITH THE ML THEORY CODE )******

import streamlit as st
import pandas as pd
import numpy as np

st.set_page_config(page_title="RoadSafe AI", page_icon="🚗", layout="wide")

st.title("🚗 RoadSafe AI — Safety Simulator")
st.markdown("**Predict accident risk before it happens**")

st.sidebar.header("🎛️ Enter Road Conditions")

rainfall = st.sidebar.slider("Rainfall (inches)", 0.0, 2.0, 0.0, 0.1)
visibility = st.sidebar.slider("Visibility (miles)", 0.0, 10.0, 10.0, 0.5)
traffic = st.sidebar.slider("Traffic Density (1-10)", 1, 10, 3)
speed = st.sidebar.slider("Vehicle Speed (mph)", 10, 100, 50)
is_night = st.sidebar.toggle("Night Time?")
road_type = st.sidebar.selectbox("Road Type", ["Highway", "City Road", "Rural Road"])

# Simple rule-based risk score for now (replace with ML model later)
risk = 0
risk += rainfall * 20
risk += (10 - visibility) * 5
risk += traffic * 3
risk += max(0, speed - 60) * 0.5
if is_night:
    risk += 15

risk = min(risk, 100)

st.subheader("📊 Accident Risk Assessment")

col1, col2, col3 = st.columns(3)
col1.metric("Risk Score", f"{risk:.0f}/100")
col2.metric("Visibility", f"{visibility} mi")
col3.metric("Rainfall", f"{rainfall} in")

if risk < 30:
    st.success("✅ LOW RISK — Road conditions are safe.")
elif risk < 60:
    st.warning("⚠️ MODERATE RISK — Drive carefully.")
else:
    st.error("🚨 HIGH RISK — Avoid this route if possible!")

st.subheader("🔍 Contributing Factors")
factors = {
    "Rainfall": rainfall * 20,
    "Poor Visibility": (10 - visibility) * 5,
    "Traffic": traffic * 3,
    "Speed": max(0, speed - 60) * 0.5,
    "Night Time": 15 if is_night else 0,
}
st.bar_chart(factors)

**for running use this :-
**
streamlit run app.py


**what lib and what they accutal need and purpose**

import pandas as pd

➡️ Pandas → Used to handle data.

from xgboost import XGBClassifier

➡️ XGBoost → Used to create/train the AI model.

from sklearn.model_selection import train_test_split

➡️ train_test_split → Splits data into training data and testing data.

from sklearn.metrics import classification_report

➡️ classification_report → Checks how well the AI performed.

import pickle

➡️ pickle → Used to save the trained AI model.
