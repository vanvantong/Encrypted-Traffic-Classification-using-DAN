# Traffic Classification Dataset for Deep Adaptation Network

## Abstract
This dataset contains the results of a cross-sectional study that examined the association between air pollution and respiratory health outcomes in a sample of 500 adults living in Hanoi, Vietnam. The data includes demographic, lifestyle, and medical information of the participants, as well as measurements of air quality and lung function. The main finding of the analysis is that exposure to high levels of particulate matter (PM2.5) is associated with reduced lung function and increased risk of chronic obstructive pulmonary disease (COPD).

## Keywords
air pollution, health, respiratory, PM2.5, lung function, COPD

## Data collection
The data was collected in March 2024 by a team of researchers from the University of Hanoi. The participants were randomly selected from the population registry of Hanoi and invited to participate in the study by phone. The inclusion criteria were: age between 18 and 65 years, living in Hanoi for at least one year, and no history of respiratory diseases. The exclusion criteria were: pregnancy, smoking, or use of respiratory medications. The participants were asked to complete a questionnaire on their demographic, lifestyle, and medical characteristics, and to visit a local clinic for a physical examination and a spirometry test. The air quality data was obtained from the Hanoi Air Quality Monitoring Network, which measures the concentration of various pollutants in the ambient air every hour at 10 locations across the city. The data was aggregated to obtain the daily average of PM2.5 for each participant based on their residential address. The study protocol was approved by the ethical committee of the University of Hanoi and all participants gave informed consent.

## Data processing
The data was processed using R version 4.1.0 and the following packages: tidyverse, lubridate, janitor, and ggplot2. The data processing steps included:

- Checking and correcting data entry errors, such as missing values, outliers, and invalid values.
- Converting categorical variables into dummy variables, such as gender, education, and occupation.
- Calculating body mass index (BMI) from height and weight, and categorizing it into underweight, normal, overweight, and obese.
- Calculating the exposure to PM2.5 for each participant by matching their residential address to the nearest air quality monitoring station and interpolating the daily average of PM2.5 for the date of their clinic visit.
- Calculating the lung function parameters, such as forced expiratory volume in one second (FEV1), forced vital capacity (FVC), and FEV1/FVC ratio, and categorizing them into normal, mild, moderate, and severe impairment according to the Global Initiative for Chronic Obstructive Lung Disease (GOLD) criteria.
- Performing descriptive and inferential statistics to explore the distribution of the variables and test the hypotheses of the study.

## Data structure
The dataset consists of two files in CSV format:

- `participants.csv`: This file contains the information of the 500 participants, with one row per participant and 15 columns for the following variables:

| Variable | Description | Type | Values |
| --- | --- | --- | --- |
| id | Unique identifier of the participant | Numeric | 1-500 |
| gender | Gender of the participant | Categorical | 0 = Male, 1 = Female |
| age | Age of the participant in years | Numeric | 18-65 |
| education | Highest level of education completed by the participant | Categorical | 1 = Primary, 2 = Secondary, 3 = Tertiary |
| occupation | Occupation of the participant | Categorical | 1 = Unemployed, 2 = Student, 3 = Manual, 4 = Non-manual, 5 = Professional |
| income | Monthly income of the participant in Vietnamese dong (VND) | Numeric | 0-10000000 |
| height | Height of the participant in centimeters (cm) | Numeric | 140-200 |
| weight | Weight of the participant in kilograms (kg) | Numeric | 40-150 |
| bmi | Body mass index of the participant in kg/m2 | Numeric | 15-50 |
| bmi_cat | Body mass index category of the participant | Categorical | 1 = Underweight, 2 = Normal, 3 = Overweight, 4 = Obese |
| address | Residential address of the participant | Text | Hanoi districts |
| pm25 | Exposure to PM2.5 of the participant in micrograms per cubic meter (µg/m3) | Numeric | 0-500 |
| fev1 | Forced expiratory volume in one second of the participant in liters (L) | Numeric | 0-6 |
| fvc | Forced vital capacity of the participant in liters (L) | Numeric | 0-8 |
| fev1fvc | FEV1/FVC ratio of the participant | Numeric | 0-1 |
| fev1fvc_cat | FEV1/FVC category of the participant | Categorical | 1 = Normal, 2 = Mild, 3 = Moderate, 4 = Severe |

- `air_quality.csv`: This file contains the air quality data of Hanoi for March 2024, with one row per hour and 11 columns for the following variables:

| Variable | Description | Type | Values |
| --- | --- | --- | --- |
| date | Date of the measurement in YYYY-MM-DD format | Date | 2024-03-01 to 2024-03-31 |
| time | Time of the measurement in HH:MM:SS format | Time | 00:00:00 to 23:00:00 |
| station | Name of the air quality monitoring station | Text | 10 stations in Hanoi |
| pm25 | Concentration of PM2.5 in µg/m3 | Numeric | 0-500 |
| pm10 | Concentration of PM10 in µg/m3 | Numeric | 0-500 |
| no2 | Concentration of nitrogen dioxide (NO2) in parts per billion (ppb) | Numeric | 0-200 |
| so2 | Concentration of sulfur dioxide (SO2) in ppb | Numeric | 0-200 |
| co | Concentration of carbon monoxide (CO) in parts per million (ppm) | Numeric | 0-10 |
| o3 | Concentration of ozone (O3) in ppb | Numeric | 0-200 |
| temp | Temperature in degrees Celsius (°C) | Numeric | 0-40 |
| hum | Humidity in percentage (%) | Numeric | 0-100 |

## Data quality
The data quality of this dataset is high, as the data collection and processing methods followed rigorous standards and protocols. The data has no missing values, outliers, or invalid values. The data is accurate, complete, and reliable, as it was collected from a representative sample of the population and verified by the researchers. The data has some limitations, such as:

- The data is cross-sectional, which means it only captures the association between air pollution and health outcomes at one point in time, and does not imply causation or temporal relationship.
- The data is based on self-reported information, which may be subject to recall bias, social desirability bias, or measurement error.
- The data is based on a single exposure measure of PM2.5, which may not reflect the long-term or cumulative exposure to air pollution or other pollutants.
- The data is based on a single outcome measure of lung function, which may not capture the full spectrum of respiratory health outcomes or comorbidities.

## Data access
The data is available for download from the GitHub repository of the project: [Air Pollution and Health Dataset](^1^). The data is licensed under the Creative Commons Attribution 4.0 International License, which means you are free to share and adapt the data for any purpose, as long as you give appropriate credit, provide a link to the license, and indicate if changes were made. You may do so in any reasonable manner, but not in any way that suggests the licensor endorses you or your use. You may not apply legal terms or technological measures that legally restrict others from doing anything the license permits.

---

I hope this example helps you create your own dataset description. If you have any questions or feedback, please let me know. 😊

Source: Conversation with Bing, 3/4/2024
(1) Free Public Data Sets For Analysis | Tableau. https://www.tableau.com/learn/articles/free-public-data-sets.
(2) Data Set: Definition, Types, Examples & Public Data Sets. https://analystanswers.com/data-set-definition-types-examples-public-data-sets/.
(3) Descriptive Statistics | Definitions, Types, Examples. https://www.scribbr.com/statistics/descriptive-statistics/.
(4) Data Description Document Guidelines - Scholarly Communications. https://scholarlycommunications.byu.edu/data-description-guidelines.
(5) Describing your data | University of Westminster, London. https://www.westminster.ac.uk/research/researcher-support/research-data/create-and-store-data/describing-your-data.
