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

The project's focus was on the prediction of voter turnout in selected swing states ((Arizona, Florida, Michigan, Nevada, Texas) using for General 2020 state election data consisting of 27,000,000+ observations through. logistical regression model. Using PySpark, I built data pipelines to predict voter turnout through I  a logistic regression model, achieving a consistent training AUC score of 70% and a peak test AUC of 73% in predicting turnout for five states. After initializing the SparkSession and reading in the Parquet data from a GCS path, I converted the PySpark dataframe into a Pandas dataframe to perform Exploratory Data Analysis (EDA) conducted to visualize distributions and explore correlations to extract insights into the relationships between various variables and data preprocessing to ensure the dataset was suitable for analysis, featurizing using string indexers, one-hot encoders, and assemblers. Transitioning to model building, I chose to employ a Logistic Regression approach, focusing on the 'General_2020' response variable for binary classification. The objective was to predict, based on the label column, whether a voter participated (Y=1) or refrained from voting (Y=0) in the 2020 Primary Election. The selected predictor variables encompassed a range of demographic factors including age, gender, education level, ethnicity, dwelling type, median housing value, and estimated household income. In summary, the project's meticulous analysis, encompassing data preprocessing, exploratory data analysis, model building, and the interpretation of key metrics, provided nuanced insights into the intricate interplay between socioeconomic factors and voter behavior within swing states during the 2020 General Election.


## Installation and Setup
- **Technologies:**  Python, Jupyter Notebook (GCP DataProc Web Interface), Google Cloud Platform (Cloud Storage, BigQuery)
- **Python Version:** 3.10.10
- **Packages Used:**
  - **Data Manipulation:** Pandas, Numpy, PySpark
  - **Data Visualization:** Seaborn, Matplotlib
  - **Machine Learning:** PySpark
<!-- - **General Purpose:** General purpose packages like `urllib, os, request`, and many more. -->


## Data

### Source Data
726 variables, lines of code

### Data Acquisition
Data collection is not always as simple as downloading from Kaggle or any open source website; it can also be gathered through API calls or online scraping. So you can elaborate on this step in this section so that the reader can obtain the dataset by following your instructions.

### Data Preprocessing
Acquired data is not always squeaky clean, so preprocessing them are an integral part of any data analysis. In this section you can talk about the same.

## Results and Evaluation
Provide an overview of the results of your project, including any relevant metrics and graphs. Include explanations of any evaluation methodologies and how they were used to assess the quality of the model. You can also make it appealing by including any pictures of your analysis or visualizations.

From the model results, we saw that the training and testing AUC scores consistently hovered around 70% across all states , peaking at  73.54% for the Arizona dataset. These AUC scores indicated the models' capability to effectively predict voter turnout based on the provided features yet how specific predictor variables exhibited distinct impacts on voter behavior depending on the state as the analysis yielded several pivotal findings:

- *Age and Gender*: Voter age and gender demonstrated limited influence on voter turnout across the swing states. Therefore, allocating substantial campaign focus on these variables might yield minimal impact.

- *Property Ownership*: The influence of property ownership on voter behavior manifested differently across states. Notably, Michigan displayed the most pronounced difference in voting patterns based on dwelling type, while other states showcased comparatively less variation.

- *Education*: Education level emerged as a significant factor in Florida and Arizona, implying that tailored campaigns targeting educated voters could be impactful in these states. However, the influence of education was less pronounced in Nevada and Michigan.

- *Income and Wealth*: Metrics derived from the analysis indicated that neither median housing value nor estimated household income significantly affected voter turnout in any of the four states. Hence, crafting campaign strategies based on these factors might yield marginal benefits.


## Future work
Outline potential future work that can be done to extend the project or improve its functionality. This will help others understand the scope of your project and identify areas where they can contribute.

## Acknowledgments/References
- Matthew Balderrama
- Bernie Graves
- Brandelyn Nie

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
