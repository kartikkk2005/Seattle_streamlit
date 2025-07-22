# Seattle_streamlit
import streamlit as st
import pandas as pd
from streamlit_extras.let_it_rain import rain

custom_css = """
<style>
.stApp {
    background-color: #262626; /* Deep Charcoal Gray */
    color: #F0F0F0; /* Off-white for text */
}

.main .block-container {
    background-color: #262626;
}

.stSidebar {
    background-color: #1A1A1A; /* Slightly darker gray for sidebar */
    color: #F0F0F0;
}

/* Ensure text and other elements are visible */
h1, h2, h3, h4, h5, h6, p, label, .stButton > button, .stTextInput > div > div > input,
.st-bb, .st-bd, .st-be, .st-da, .st-df, .st-dr, .st-dq { /* Targeting some internal Streamlit elements for text color */
    color: #F0F0F0;
}

/* For expanders to match the dark theme */
.streamlit-expanderHeader {
    background-color: #333333; /* Slightly lighter gray for expander header */
    color: #F0F0F0;
}
.streamlit-expanderContent {
    background-color: #262626;
}

/* Make sure dataframes have a dark background too */
div[data-testid="stDataFrame"] {
    background-color: #333333; /* Darker gray for dataframe background */
    color: #F0F0F0;
}
div[data-testid="stDataFrame"] table {
    color: #F0F0F0;
}

/* Adjust button text color if needed */
.stButton > button {
    background-color: #4CAF50; /* Example button color */
    color: white;
}
</style>
"""
st.markdown(custom_css, unsafe_allow_html=True)

file=st.file_uploader('upload a csv file') #uploading a file #

if file is not None:
    df=pd.read_csv(file)
    st.dataframe(df.describe())
    st.dataframe(df.head())
    st.dataframe(df.tail())
    rain(
        emoji="✨",  # Replace with any emoji you like!
        font_size=50,  # Adjust the size of the emojis
        falling_speed=5,  # Adjust how fast they fall (higher number = faster)
        animation_length="infinite",  # Make it rain forever
    )
