# Mobile Usage Analysis for Nigerian Youth

A data-driven approach to analyzing mobile data usage and spending to identify pain points for improving the data usage experience and minimize spending.

![data usage image](https://www.pcsteps.com/wp-content/uploads/2018/01/Smart-Ways-to-Save-Mobile-Data-00.png)

## Table of Content

- [Introduction](#Introduction)
- [Background](#Background)
- [Data Collection and Processing](#Data-Collection-and-Processing)
- 
- 





### Introduction
---

The project examines mobile phone usage patterns among Nigerian youth using a dataset provided by TechTrendNG. The goal is to provide actionable insights to enhance user experience and guide product development strategies. The data, mobile_usage_ng.xlsx, is cleaned and preprocessed using Python and Excel. The findings reveal behavioral patterns, enabling TechTrendNG to make informed decisions, such as prioritizing features for heavy data users or launching targeted campaigns in high-usage states


### Background
---

In today’s hyperconnected world, mobile technology has become a defining aspect of daily life, particularly among youth. In Nigeria, where over 60% of the population is under 25, mobile phone usage has surged in recent years, driven by increased access to smartphones, affordable data plans, and widespread digital literacy. This youth demographic represents a massive opportunity for tech startups aiming to innovate and scale mobile-based solutions tailored to everyday needs, including communication, entertainment, education, and finance.

TechTrendNG, a Nigerian technology startup, is one such company committed to developing mobile applications that resonate with the habits and preferences of young Nigerians. However, successful innovation in this space requires more than assumptions, it demands data-driven understanding of how youth engage with mobile technology across different regions and socio-economic brackets.

To support this, TechTrendNG provided a dataset containing mobile usage information across various Nigerian states. The dataset includes attributes such as user ID, age, state, monthly data consumption (in megabytes), and monthly spending (in naira). While rich in potential, the raw dataset suffers from several data quality issues such as missing values, inconsistent state formatting, duplicate entries, and numerical outliers. Without proper cleaning and preprocessing, these issues can lead to misleading insights and poor decision-making.

This project is designed to clean, transform, and analyze the mobile usage dataset to extract meaningful insights. The outcome will help TechTrendNG understand user behavior patterns, identify high-value user segments, and optimize app features and marketing efforts based on region-specific usage trends. Ultimately, this work lays the foundation for smarter, more targeted digital solutions that reflect the real habits and needs of Nigerian youth.

### Data Collection and Processing
---

### Data Source
The dataset used for the analysis contains 2000 rows and 6 columns. It contained information on mobile data consumption, spending habits, age, and state of residence for a sample of Nigerian youth.

### Preprocessing Steps
1. Data Loading 
   - Loaded the dataset mobile_usage_ng.xlsx using pandas.
   - Inspected the structure, column names, and data types.
2. Handling Missing Values
   - Identified missing values in key columns.
   - Imputed missing values in numerical columns:(age, monthly_data_mb, spending_ngn) using the median, which is robust to outliers.
 3. Standardizing Categorical Data
   - Cleaned and standardized the state column:
       - Removed leading/trailing whitespaces.
       - Converted all entries to title case (e.g., lagos, Lagos → Lagos).
 4. Data Type Corrections
    - Ensured that the following columns were in correct numeric format: (age, monthly_data_mb, spending_ngn).
    - Converted any non-numeric entries to NaN and re-imputed using the median.
 5. Removing Duplicates
    - Checked for and removed duplicate entries based on user_id.
 6. Outlier Detection
   - Applied three different methods to detect outliers in age and spending_ngn:
     - Z-Score Method: Flagged values with |z-score| > 3.
     - IQR Method: Flagged values outside 1.5 * IQR from the quartiles.
     - Threshold Method: Flagged manually unrealistic values (e.g., age > 80 or spending > ₦500,000).
  7. Data Normalization and Standardization
     - Normalized spending_ngn to a [0, 1] range using MinMaxScaler.
     - Standardized monthly_data_mb to mean 0 and std 1 using StandardScaler.
     - Decided not to transform age due to its already narrow and meaningful range (15–35).
    
  ### Exploratory Data Analysis (EDA)
