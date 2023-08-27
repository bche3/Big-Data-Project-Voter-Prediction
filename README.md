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

In exploration of how voters’ socioeconomic status (SES), consisting of their income, education, financial security, accessibility to resources, and the like, influence voter participation in the general or primary elections, we decided to explore existing patterns from the past state data as it's notable that societal influences and living conditions, especially when living in certain politicized areas, may have a heavy effect on voter turnout for elections taking place. Specifically, we chose states classified as “swing states,” due to their historical propensity for alternating between major political parties, being closely contested battlegrounds where shifts in turnout and voting patterns could potentially determine the overall election outcome.

Thus, our *main question* and *secondary question* was
- How does voters' socioeconomic background affect voter turnout in swing states?
  
  - Specifically, how does property ownership (household/land), education level, age/gender, and income influence voter turnout or patterns?

The project's focus was on the prediction of voter turnout in our selected swing states (Arizona, Florida, Michigan, Nevada) using 2020 General Election state data consisting of 27,000,000+ total observations through a logistical regression model. My contributions consisted of data preprocessing/cleaning, exploratory data analysis (EDA) for the Nevada dataset, and building the data pipelines using PySpark to predict voter turnout through a logistic regression model, achieving a consistent training and test AUC scores near 72% and both peak training and test AUC's at 73% for Arizona when predicting turnout for four states. Performing ETL using PySpark, I converted the PySpark dataframe into a Pandas dataframe to perform EDA to visualize distributions and explore correlations in order to extract insights into the relationships between various variables, and conducting data preprocessing to ensure the dataset was suitable for analysis, featurizing using string indexers, one-hot encoders, and assemblers. Transitioning to model building, I chose to employ a Logistic Regression approach, focusing on the 'General_2020' response variable for binary classification. The objective was to predict, based on the label column, whether a voter participated (Y=1) or refrained from voting (Y=0) in the 2020 Primary Election. The selected predictor variables encompassed a range of demographic factors including age, gender, education level, ethnicity, dwelling type, median housing value, and estimated household income (See below for variables of focus in *Data Preprocessing*. In summary, the project's meticulous analysis, encompassing data preprocessing, exploratory data analysis, model building, and the interpretation of key metrics, provided nuanced insights into the intricate interplay between socioeconomic factors and voter behavior within swing states during the 2020 General Election.


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
Presented are a few visualizations for each state from the EDA to familiarize ourselves with the relationships and distributions among our data and how they may vary from state to state (To see the entirety of the EDA, please see the *Final_Report.ipynb* notebook):


*Arizona Household Income Countplot (by Matthew Balderrama)*
From our sample, we can see that most voters turned out to be those whose income falls in the category of 'middle-class' This makes sense since the majority of adults in American make up the middle-class in terms of income.

![img](https://github.com/bche3/Big-Data-Project-Voter-Turnout-Prediction/blob/main/img/az-HHincome-countplot.png)

*Florida Age Boxplot (by Brandelyn Nie)*


![img](https://github.com/bche3/Big-Data-Project-Voter-Turnout-Prediction/blob/main/img/fl-age-boxplot.png)

*Michigan Land Sq Boxplot (By Bernie Graves)*
This initial plot is telling us that Republicans tend to have more land in the State of Michigan.

![img](https://github.com/bche3/Big-Data-Project-Voter-Turnout-Prediction/blob/main/img/mi-land-boxplot.png)

*Nevada Education Barplot*
We observe that that the CommercialData_Education level of the Nevada voter data that is most prominent is "Some College - Likely" for over 200,000 while "Vocational Degree - Extremely Likely" and "Less than HS Diploma - Extremely likely" has a count around 0.

![img](https://github.com/bche3/Big-Data-Project-Voter-Turnout-Prediction/blob/main/img/edu-barplot.png)

From the model results, we saw that both the training and testing AUC scores consistently hovered around *72%* across all states while the training and test AUCpeaked at *73.37%* and *73.54%* respectively for the Arizona dataset. These AUC scores indicated the models' capability to effectively predict voter turnout based on the provided features and gives me a under understanding of how specific predictor variables  impacts voter behavior depending on the state as yielded through several pivotal findings. Certain aspects of socioeconomic status play larger roles than others depending on the state, while some of them are the same throughout. 

![img](https://github.com/bche3/Big-Data-Project-Voter-Turnout-Prediction/blob/main/img/auc-scores.png)

These scores reflect that our model performs relatively well with the input columns provided to predicting voter turnout in the 2020 General Election, which we'll be exploring further in the ranked coefficients barplots for the logistic regression models on each individual state state. The ranked coefficients aid us in understanding predictor impact on voter turnout, identifying key variables, and comparing state-specific influences while the visualization help communicate insights, guide decisions, and validate the model's alignment with domain knowledge.

*Florida — Ranked Coefficients Barplot*

![img](https://github.com/bche3/Big-Data-Project-Voter-Turnout-Prediction/blob/main/img/fl-ranking.png)

*Michigan — Ranked Coefficients Barplot*

![img](https://github.com/bche3/Big-Data-Project-Voter-Turnout-Prediction/blob/main/img/mi-ranking.png)

*Nevada — Ranked Coefficients Barplot*

![img](https://github.com/bche3/Big-Data-Project-Voter-Turnout-Prediction/blob/main/img/nv-ranking.png)

*Arizona — Ranked Coeffients Barplot*

![img](https://github.com/bche3/Big-Data-Project-Voter-Turnout-Prediction/blob/main/img/az-ranking.png)

*Age and Gender*
- Considering coefficient rankings for `Voter_Age` and `Voter_Gender` across the four swing states, `Voter_Age` consistently holds a low rank, indicating limited contribution to predicting voter turnout in the 2020 primaries. Voter_Gender, a categorical variable with male as the baseline, also ranks low across states, implying minimal impact on turnout. Although Florida's Voter_Gender rank is relatively higher, its larger population might influence this result. Consequently, campaigns needn't heavily prioritize age, and while Voter_Gender might slightly matter in Florida, focusing on other predictors promises better turnout outcomes.

*Property Ownership*
- To assess property ownership's impact on voter tendencies in swing states, focus shifts to the `CommercialData_DwellingType` variable. With two possible values (Single Family Dwelling Unit and Multi-Family Dwelling), one coefficient corresponds to this variable in the logistic regression model. Multi-Family Dwelling serves as the base, revealing that in Nevada and Florida, voting behavior similarity exists between single and multi-family units. Arizona's above-average coefficient suggests behavioral differences, while Michigan's largest coefficient indicates a substantial pattern distinction based on dwelling type. This variation underscores the need for tailored campaign strategies aligned with each state's tendencies, emphasizing the importance of comprehending property's role in voter behavior for effective campaigns.

*Education*
- The analysis examines education's impact on voter alignment/turnout using `CommercialData_AreaMedianEducationYears` and `CommercialData_Education` variables. `CommercialData_AreaMedianEducationYears` rankings are consistently low across states, indicating minimal impact. For `CommercialData_Education`, coefficients vary by state; in Florida, education levels like Bach Degree - EL and Grad Degree - EL have a high impact, while in Nevada and Michigan, the effect is limited. Arizona's coefficients are relatively high, suggesting education significantly influences turnout. The findings highlight education's diverse impact on voter turnout across states and emphasize the need for strategic campaign targeting.

*Income* 
- Exploring the influence of income and wealth on voter turnout, the analysis delves into the `CommercialData_AreaMedianHousingValue` and `CommercialData_EstimatedHHIncomeAmount` variables. Remarkably, across all four states, the `CommercialData_AreaMedianHousingValue` coefficient consistently receives the lowest rank. This implies that the median housing value in a voter's area has minimal to no bearing on their decision to vote in the 2020 elections. Equally noteworthy is the finding that the `CommercialData_EstimatedHHIncomeAmount` coefficient ranks second lowest in all four states, suggesting that the estimated household income of voters similarly fails to impact voter turnout. In summary, the data underscores that political campaigns might be best served by not prioritizing voters' income and wealth as key factors for targeting strategies, given the possibility that these variables have limited to no effect on influencing voter behavior.

In conclusion, our findings illuminate nuanced patterns within each swing state, emphasizing the multifaceted impact of socioeconomic status. The variance in the significance of property ownership's role across states underscores the necessity for tailored targeting strategies. The pronounced influence of education levels in Florida, coupled with the prominence of ethnic group coefficients in Arizona, Michigan, and Nevada, points towards region-specific campaigning strategies.
Importantly, our analyses indicate that voter age, gender, and income/wealth factors hold minimal sway in the logistic models for each state. Armed with this comprehensive understanding of how socioeconomic factors interact with voter behavior, political campaigns are now equipped to craft highly effective strategies to engage and mobilize voters in these critical swing states. This project serves as a testament to the power of data science in informing strategic decision-making within the realm of political campaigns, with implications extending beyond this specific context.

## Future Work
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
