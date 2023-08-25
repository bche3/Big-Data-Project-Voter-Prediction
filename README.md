

# Swinging The Vote

> Python (PySpark, Pandas, Numpy, Seaborn), GCP (Cloud Storage, BigQuery, DataProc), Logistic Regression

![GitHub release (latest by date including pre-releases)](https://img.shields.io/github/v/release/pragyy/datascience-readme-template?include_prereleases)
![GitHub last commit](https://img.shields.io/github/last-commit/pragyy/datascience-readme-template)
![GitHub pull requests](https://img.shields.io/github/issues-pr/pragyy/datascience-readme-template)
![GitHub](https://img.shields.io/github/license/pragyy/datascience-readme-template)
![contributors](https://img.shields.io/github/contributors/pragyy/datascience-readme-template) 
![codesize](https://img.shields.io/github/languages/code-size/pragyy/datascience-readme-template) 

![img](https://github.com/bche3/Swinging-The-Vote/blob/main/img/thumbnail.jpg)

## Project Overview

Predicted voter turnout in swing states using a logistical regression model. I built data pipelines to predict voter turnout by using Google Cloud Platform (Cloud Storage, DataProc, PySpark) for 27,000,000+ General 2020 state election data. I featurized using string indexers, one-hot encoders, and assemblers on logistic regression model to achieve consistent training AUC score of 70% and a peak test AUC of 73% in predicting turnout for five states.



## Setup Used
- **Editor Used:**  Jupyter Notebook (GCP DataProc Web Interface)
- **Python Version:**
- **Packages Used:**
  - **Data Manipulation:** Pandas, Numpy, PySpark
  - **Data Visualization:** Seaborn, Matplotlib
  - **Machine Learning:** PySpark
<!-- - **General Purpose:** General purpose packages like `urllib, os, request`, and many more. -->


## Data

### Source Data
In this section, I list all of the data that was used, along with the source link and a few lines that describe each data. You can also explain each of the data attributes in greater detail if you wish.

### Data Acquisition
Data collection is not always as simple as downloading from Kaggle or any open source website; it can also be gathered through API calls or online scraping. So you can elaborate on this step in this section so that the reader can obtain the dataset by following your instructions.

### Data Preprocessing
Acquired data is not always squeaky clean, so preprocessing them are an integral part of any data analysis. In this section you can talk about the same.

## Results and evaluation
Provide an overview of the results of your project, including any relevant metrics and graphs. Include explanations of any evaluation methodologies and how they were used to assess the quality of the model. You can also make it appealing by including any pictures of your analysis or visualizations.

## Future work
Outline potential future work that can be done to extend the project or improve its functionality. This will help others understand the scope of your project and identify areas where they can contribute.

## Acknowledgments/References
Acknowledge any contributors, data sources, or other relevant parties who have contributed to the project. This is an excellent way to show your appreciation for those who have helped you along the way.

For instance, I am referencing the image that I used for my readme header - 
- Image by [rashadashurov](https://www.vectorstock.com/royalty-free-vector/data-science-cartoon-template-with-flat-elements-vector-27984292)

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
