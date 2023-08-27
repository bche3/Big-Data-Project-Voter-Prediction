# Big Data Project: Predicting Voter Turnout

> Python (PySpark, Pandas, Numpy, Seaborn), GCP (Cloud Storage, BigQuery, DataProc), Logistic Regression

<!--
![GitHub release (latest by date including pre-releases)](https://img.shields.io/github/v/release/pragyy/datascience-readme-template?include_prereleases)
![GitHub last commit](https://img.shields.io/github/last-commit/pragyy/datascience-readme-template)
![GitHub pull requests](https://img.shields.io/github/issues-pr/pragyy/datascience-readme-template)
![GitHub](https://img.shields.io/github/license/pragyy/datascience-readme-template)
![contributors](https://img.shields.io/github/contributors/pragyy/datascience-readme-template) 
![codesize](https://img.shields.io/github/languages/code-size/pragyy/datascience-readme-template) 
-->

![img](https://github.com/bche3/Swinging-The-Vote/blob/main/img/project-thumbnail.jpg)

## Project Overview

The project's focus was on the prediction of voter turnout in selected swing states (Arizona, Florida, Michigan, Nevada) using for General 2020 state election data consisting of 27,000,000+ observations through. logistical regression model. My contributions consisted of building the data pipelines using PySpark to predict voter turnout through a logistic regression model, achieving a consistent training AUC score of 70% and a peak test AUC of 73% in predicting turnout for four states. Performing ETL through initialization with a SparkSession and reading in the Parquet data from a GCS path, I converted the PySpark dataframe into a Pandas dataframe to perform Exploratory Data Analysis (EDA) conducted to visualize distributions and explore correlations to extract insights into the relationships between various variables and data preprocessing to ensure the dataset was suitable for analysis, featurizing using string indexers, one-hot encoders, and assemblers. Transitioning to model building, I chose to employ a Logistic Regression approach, focusing on the 'General_2020' response variable for binary classification. The objective was to predict, based on the label column, whether a voter participated (Y=1) or refrained from voting (Y=0) in the 2020 Primary Election. The selected predictor variables encompassed a range of demographic factors including age, gender, education level, ethnicity, dwelling type, median housing value, and estimated household income. In summary, the project's meticulous analysis, encompassing data preprocessing, exploratory data analysis, model building, and the interpretation of key metrics, provided nuanced insights into the intricate interplay between socioeconomic factors and voter behavior within swing states during the 2020 General Election.


## Installation and Setup
- **Technologies:**  Python, Jupyter Notebook (GCP DataProc Web Interface), Google Cloud Platform (DataProc, Cloud Storage, BigQuery)
- **Python Version:** 3.10.10
- **Packages Used:**
  - **Data Manipulation:** Pandas, Numpy, PySpark
  - **Data Visualization:** Seaborn, Matplotlib
  - **Machine Learning:** PySpark
<!-- - **General Purpose:** General purpose packages like `urllib, os, request`, and many more. -->


## Data

### Source Data
- U.S. General Election and Primary Election Data from 2012 to 2020 consisting of 726 variables (voter registration, participation, and demographic data) stored as Parquet files stored in Google Cloud Storage bucket
- For this project, U.S. 2020 General Election for Arizona, Florida, Michigan, Nevada, and Texas were selected, totaling +27,000,00 observations altogether

### Data Acquisition
- T

### Data Preprocessing

Our variables of focus:

- `General_2020` — The response variable (label column) determining voter turnout by Y as 1 and null as 0
- `Voters_Age` — Age of individual voter
- `Voters_Gender` — Gender of individual voter (M, F)
- `Parties_Description` — Political parties active in the state (Democratic, Republican, Non-Partisan, ...)
- `Ethnic_Description` — Ethnicity of individual voter ()
- `CommercialData_Education` — Categorical likelihood scale of voter level of education from HS Diploma to Graduate Degree
- `CommercialData_DwellingType` — Dwelling type of individual voter (Single-family, Multi-family)
- `CommercialData_AreaMedianHousingValue` — Median housing value from individual voter's area
- `CommercialData_AreaMedianEducationYears` — Median education years from individual voter's area (0, 3, 10, 11, ...)
- `CommercialData_EstimatedHHIncomeAmount` — Estimated household income amount of individual voter

## Results and Evaluation
Provide an overview of the results of your project, including any relevant metrics and graphs. Include explanations of any evaluation methodologies and how they were used to assess the quality of the model. You can also make it appealing by including any pictures of your analysis or visualizations.

From the model results, we saw that the training and testing AUC scores consistently hovered around 70% across all states , peaking at  73.54% for the Arizona dataset. These AUC scores indicated the models' capability to effectively predict voter turnout based on the provided features yet how specific predictor variables exhibited distinct impacts on voter behavior depending on the state as the analysis yielded several pivotal findings:

1. Test`
2. Test


## Future work
Outline potential future work that can be done to extend the project or improve its functionality. This will help others understand the scope of your project and identify areas where they can contribute.

## Acknowledgments/References
- Matthew Balderrama —  Arizona EDA & Model Interpretation/Conclusion
- Bernie Graves      —  Michigan EDA & Model Interpretation/Conclusion
- Brandelyn Nie      —  Florida EDA & Model Interpretation/Conclusion

<!--
## Code structure
Explain the code structure and how it is organized, including any significant files and their purposes. This will help others understand how to navigate your project and find specific components. 

Here is the basic suggested skeleton for your data science repo (you can structure your repository as needed ):

```bash
├── data
│   ├── data1.csv
│   ├── data2.csv
│   ├── cleanedData
│       ├── cleaneddata1.csv
|       └── cleaneddata2.csv
├── data_acquisition.py
├── data_preprocessing.ipynb
├── data_analysis.ipynb
├── data_modelling.ipynb
├── Img
│   ├── img1.png
│   └── Headerheader.jpg
├── LICENSE
├── README.md
└── .gitignore
```
-->
