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

Our objective for this project is to determine how aspects of individual voters’ socioeconomic status (SES), consisting of their income, education, financial security, accessibility to resources, and the like, influence how they decide to vote in the general or primary elections. It’s notable that societal influences and their living conditions, especially when living in certain politicized areas, may have a heavy effect on voter turnout for elections taking place so we’ve decided to explore any existing patterns from the state data provided. The datasets we chose to work with are states that are classified as “swing states,” meaning any state that could reasonably be won by either the Democratic or Republican candidate in a statewide election.

Thus, our *main question* and *secondary question* is:
- How does socioeconomic background (education, income, ethnicity, etc ) affect voter turnout?
  
  - How does property (household/land) ownership, education level, and age/gender individually affect voter turnouts or patterns?

The project's focus was on the prediction of voter turnout in our selected swing states (Arizona, Florida, Michigan, Nevada) using for 2020 General Election state data consisting of 27,000,000+ observations through a logistical regression model. My contributions consisted of data preprocessing/cleaning, exploratory data analysis (EDA) for the Nevada dataset, and building the data pipelines using PySpark to predict voter turnout through a logistic regression model, achieving a consistent training and test AUC scores near 72% and both peak training and test AUC's at 73% for Arizona when predicting turnout for four states. Performing ETL using PySpark, I converted the PySpark dataframe into a Pandas dataframe to perform EDA conducted to visualize distributions and explore correlations to extract insights into the relationships between various variables and data preprocessing to ensure the dataset was suitable for analysis, featurizing using string indexers, one-hot encoders, and assemblers. Transitioning to model building, I chose to employ a Logistic Regression approach, focusing on the 'General_2020' response variable for binary classification. The objective was to predict, based on the label column, whether a voter participated (Y=1) or refrained from voting (Y=0) in the 2020 Primary Election. The selected predictor variables encompassed a range of demographic factors including age, gender, education level, ethnicity, dwelling type, median housing value, and estimated household income. In summary, the project's meticulous analysis, encompassing data preprocessing, exploratory data analysis, model building, and the interpretation of key metrics, provided nuanced insights into the intricate interplay between socioeconomic factors and voter behavior within swing states during the 2020 General Election.


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
  - These 4 states were chosen due to their historical propensity for alternating between major political parties, being closely contested battlegrounds where shifts in turnout and voting patterns could potentially determine the overall election outcome.

### Data Acquisition
- As the data was stored as Parquet files in a GCS Bucket, we create a single-node DataProc cluster using the Google Cloud SDK command-line tool
  - This cluster is a managed Apache Spark and Apache Hadoop service designed to simplify the process of running big data processing workloads.
- We then initialize a SparkSession and read the GCS path of the parquet file

### Data Preprocessing

- We select our variables of focus and convert the PySpark dataframe to a Pandas dataframe to be cleaned as seen in the processing function consisting of casting to IntegerType, dealing with missing values, and featurizing with string indexers, one hot encoders, and assemblers

Our variables of focus:

- `General_2020` — The response variable (label column) determining voter turnout by Y as 1 and null as 0
- `Voters_Age` — Age of individual voter
- `Voters_Gender` — Gender of individual voter (M, F)
- `Parties_Description` — Political parties active in the state (Democratic, Republican, Non-Partisan, ...)
- `Ethnic_Description` — Ethnicity of individual voter ()
- `CommercialData_Education` — Categorical likelihood scale of level of education from HS Diploma to Graduate Degree
- `CommercialData_DwellingType` — Dwelling type of individual voter (Single-family, Multi-family)
- `CommercialData_AreaMedianHousingValue` — Median housing value from individual voter's area
- `CommercialData_AreaMedianEducationYears` — Median education years from individual voter's area (0, 3, 10, ...)
- `CommercialData_EstimatedHHIncomeAmount` — Estimated household income amount of individual voter

## Results and Evaluation
From the model results, we saw that both the training and testing AUC scores consistently hovered around *72%* across all states while the training and test AUCpeaked at *73.37%* and *73.54%* respectively for the Arizona dataset. 

![img](https://github.com/bche3/Big-Data-Project-Voter-Turnout-Prediction/blob/main/img/az-HHincome-countplot.png)
![img](https://github.com/bche3/Big-Data-Project-Voter-Turnout-Prediction/blob/main/img/fl-age-boxplot.png)
![img](https://github.com/bche3/Big-Data-Project-Voter-Turnout-Prediction/blob/main/img/mi-land-boxplot.png)
![img](https://github.com/bche3/Big-Data-Project-Voter-Turnout-Prediction/blob/main/img/edu-barplot.png)
![img](https://github.com/bche3/Big-Data-Project-Voter-Turnout-Prediction/blob/main/img/auc-scores.png)
![img](https://github.com/bche3/Big-Data-Project-Voter-Turnout-Prediction/blob/main/img/fl-ranking.png)
![img](https://github.com/bche3/Big-Data-Project-Voter-Turnout-Prediction/blob/main/img/mi-ranking.png)
![img](https://github.com/bche3/Big-Data-Project-Voter-Turnout-Prediction/blob/main/img/nv-ranking.png)
![img](https://github.com/bche3/Big-Data-Project-Voter-Turnout-Prediction/blob/main/img/az-ranking.png)

These AUC scores indicated the models' capability to effectively predict voter turnout based on the provided features and gives me a under understanding of how specific predictor variables  impacts voter behavior depending on the state as yielded through several pivotal findings. Certain aspects of socioeconomic status play larger roles than others depending on the state, while some of them are the same throughout. 


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
