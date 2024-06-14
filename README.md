# Data_Wrangler
# Overview
This repository contains code for cleaning and visualizing a dataset. The script includes functions to preprocess the data by handling missing values, dropping unnecessary columns, and transforming specific columns. Additionally, it generates histograms for all columns in the cleaned dataset.

# Link to the dataset
As the file size is big, pasting link of the dataset that is used for this repository
https://www.kaggle.com/datasets/arianazmoudeh/airbnbopendata

# Contents
clean_data.py: Script for cleaning the dataset.
visualization.py: Script for generating histograms for all columns in the cleaned dataset.
README.md: This file, providing an overview of the repository.
Data Cleaning
clean_data(df)
This function performs several data cleaning steps on the input DataFrame df:

# Drop Columns:

license
house_rules
country code
service fee
price
# Fill Missing Values:

Replace missing values with the median for numerical columns such as availability 365, calculated host listings count, review rate number, reviews per month, minimum nights, service_fee_edited, and price_edited.
Replace missing values using forward fill for last review and Construction year.
Replace missing values with the mode for categorical columns like cancellation_policy and country.
Drop Rows with Missing Data:

Drop rows if there are missing values in any of the following columns: long, neighbourhood, neighbourhood group, host name, host_identity_verified, NAME, instant_bookable.
Column Transformations:

Derive service_fee_edited from service fee by extracting and converting the value to a float.
Derive price_edited from price by extracting and converting the value to a float.
Rename columns availability 365 to availability_365 and minimum nights to minimum_nights.
Filter Data:

Filter rows where availability_365 is less than or equal to 600.
Filter rows where minimum_nights is between 0 and 6 inclusive.
Filter rows where the number of reviews is less than or equal to 36.


import pandas as pd
from clean_data import clean_data

# Load your dataset
df = pd.read_csv('your_dataset.csv')

# Clean the dataset
df_clean = clean_data(df)

# Display the first few rows of the cleaned dataset
print(df_clean.head())


The visualization script generates histograms for each column in the cleaned dataset. This provides insights into the distribution of data for each feature.

import seaborn as sns
import matplotlib.pyplot as plt
from visualization import plot_histograms
plot_histograms(df_clean)

# Assume df_clean is your cleaned DataFrame

import seaborn as sns
import matplotlib.pyplot as plt

def plot_histograms(df):
    # Iterate through each column in the DataFrame
    for column in df.columns:
        # Create a figure
        plt.figure()
        # Plot the histogram of the current column
        sns.histplot(x=column, data=df, kde=True)
        # Set the title of the plot
        plt.title(f"Histogram of {column}")
        # Show the plot
        plt.show()

# Installation

git clone https://github.com/yourusername/data-cleaning-visualization.git
cd data-cleaning-visualization
pip install -r requirements.txt

# Requirements
pandas
seaborn
matplotlib
