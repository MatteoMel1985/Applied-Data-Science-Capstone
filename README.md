![Skills_Network](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMSkillsNetwork-PY0221EN-Coursera/images/image.png)

<h1 align="center">IBM Applied Data Science Capstone</h1>

<h2 align="center"><i>SpaceX Falcon 9 First Stage Landing Prediction</i></h2>

This repository contains a structured collection of Jupyter Notebooks developed while completing the IBM **Applied Data Science Capstone** project. The project studies SpaceX Falcon 9 launch records in order to predict whether the first stage of a rocket will land successfully.

The business scenario is based on a hypothetical competitor, **Space Y**, which wants to compete with SpaceX. Since SpaceX reduces launch costs by reusing the first stage of Falcon 9 rockets, predicting first-stage landing success can help estimate launch costs, evaluate operational risk, and identify favourable launch conditions.

<h1 align="center"><i>Notebooks Overview</i></h1>

* [**Data Collection with the SpaceX API**](Hands-on%20Lab%20Complete%20the%20Data%20Collection%20API%20Lab%281%29.ipynb)

This notebook collects launch data directly from the SpaceX API. It demonstrates how to send HTTP GET requests, parse JSON responses, extract useful launch information, and transform nested API data into a structured pandas DataFrame. The notebook also filters the dataset to Falcon 9 launches and handles missing payload-mass values.

* [**Web Scraping Falcon 9 and Falcon Heavy Launch Records**](jupyter-labs-webscraping%281%29.ipynb)

This notebook collects additional launch records from Wikipedia using web scraping. It uses `requests` and `BeautifulSoup` to download an HTML page, locate the relevant launch tables, extract column names, parse table rows, clean textual values, and convert the scraped information into a pandas DataFrame.

* [**Data Wrangling Overview**](Data%20Wrangling%20Overview%281%29.ipynb)

This notebook prepares the SpaceX launch dataset for analysis and machine learning. It performs exploratory checks, evaluates missing values, identifies numerical and categorical variables, summarises launches by site and orbit, studies mission outcomes, and creates the binary landing-outcome label used for classification.

* [**Exploratory Data Analysis with SQL**](Complete%20the%20EDA%20with%20SQL%281%29.ipynb)

This notebook explores the SpaceX dataset using SQL queries. It loads the data into a relational database environment and applies SQL operations to answer analytical questions, including counting launch records, identifying successful and failed outcomes, filtering results by date and launch site, grouping by booster version, and ranking landing outcomes.

* [**Exploratory Data Analysis and Visualisation**](IBM-DS0321EN-SkillsNetwork_labs_module_2_jupyter-labs-eda-dataviz.ipynb.jupyterlite%281%29%281%29.ipynb)

This notebook uses pandas, Matplotlib, and Seaborn to visualise relationships between launch variables and landing success. It explores how success rates vary by flight number, payload mass, launch site, and orbit type. Scatter plots and bar charts are used to reveal patterns that may be useful for predictive modelling.

* [**Launch Site Location Analysis with Folium**](IBM-DS0321EN-SkillsNetwork_labs_module_3_lab_jupyter_launch_site_location.jupyterlite%281%29.ipynb)

This notebook analyses the geographical distribution of SpaceX launch sites using Folium. It creates interactive maps with markers, circles, marker clusters, launch outcomes, coordinate labels, and distance lines. The analysis helps evaluate launch-site proximity to coastlines, roads, railways, and other geographical features relevant to safety and logistics.

* [**Machine Learning Prediction of Falcon 9 Landing Success**](IBM-DS0321EN-SkillsNetwork_labs_module_4_SpaceX_Machine_Learning_Prediction_Part_5.jupyterlite%281%29.ipynb)

This notebook builds and evaluates classification models to predict whether a Falcon 9 first stage will land successfully. It prepares the feature matrix, standardises numerical variables, splits the data into training and testing sets, applies GridSearchCV for hyperparameter tuning, and compares Logistic Regression, Support Vector Machine, Decision Tree, and K-Nearest Neighbours classifiers.

* [**Capstone Story Presentation**](capstone-story-template%201%281%29.pptx)

This presentation summarises the full capstone project as a business-oriented data science story. It describes the objective, methodology, exploratory findings, interactive visual analytics, machine-learning results, and conclusions.

<h1 align="center"><i>Technical Methodologies and Mathematical Foundations</i></h1>

## 1. API-Based Data Collection

The first stage of the project collects data from the SpaceX API. An API response is usually returned as JSON, which can be interpreted as a collection of nested key-value pairs. The notebook sends GET requests, receives structured launch data, and extracts relevant fields such as booster version, launch site, payload mass, orbit, date, and landing outcome.

From a data engineering perspective, this stage transforms semi-structured JSON data into tabular form:

$$
\text{JSON records} \rightarrow \text{pandas DataFrame}
$$

This is useful when data comes from web services, operational platforms, public APIs, or cloud applications rather than from static CSV files.

## 2. Web Scraping and HTML Parsing

The web scraping notebook collects launch records from Wikipedia. The process begins by downloading the HTML page and parsing it with `BeautifulSoup`. HTML tables are then converted into structured rows and columns.

Conceptually, the workflow is:

```text
Request web page → Parse HTML → Locate table → Extract rows → Clean values → Create DataFrame
```

Web scraping is useful when valuable data is available publicly on web pages but not directly exposed through an API. In this project, it complements API data collection by adding historical launch records from a tabular web source.

## 3. Data Wrangling and Cleaning

Data wrangling prepares raw data for analysis. The notebooks check missing values, filter Falcon 9 launches, convert data types, remove unnecessary fields, and prepare the variables required for machine learning.

A dataset can be represented as a matrix:

$$
X =
\begin{bmatrix}
x_{11} & x_{12} & \dots & x_{1p} \\
x_{21} & x_{22} & \dots & x_{2p} \\
\vdots & \vdots & \ddots & \vdots \\
x_{n1} & x_{n2} & \dots & x_{np}
\end{bmatrix}
$$

where each row is a launch and each column is a feature, such as payload mass, orbit, launch site, or booster version.

## 4. Feature Engineering and Binary Target Creation

The project transforms the landing outcome into a binary classification target. Successful landing outcomes are labelled as `1`, while unsuccessful outcomes are labelled as `0`.

The target vector can be represented as:

$$
y =
\begin{bmatrix}
y_1 \\
y_2 \\
\vdots \\
y_n
\end{bmatrix},
\quad
y_i \in \{0,1\}
$$

This converts the business question into a supervised machine-learning task: predict whether a new launch is likely to result in a successful first-stage landing.

## 5. SQL-Based Exploratory Data Analysis

SQL is used to explore the dataset in a relational format. The notebook applies operations such as `SELECT`, `WHERE`, `GROUP BY`, `ORDER BY`, aggregate functions, filtering by dates, and ranking.

Typical SQL analytical questions include:

* How many launches were performed?
* Which launch sites had the most missions?
* Which booster versions were associated with failed landings?
* How did landing outcomes change over time?
* Which outcomes occurred most frequently during a specific period?

SQL is especially useful when analysing structured datasets stored in relational databases, data warehouses, or enterprise reporting environments.

## 6. Descriptive Statistics and Aggregation

The EDA notebooks use counts, averages, grouping, and frequency summaries to understand the structure of the launch data. For example, the number of launches per site can be calculated as:

$$
\text{Count(site)} = \sum_{i=1}^{n} I(x_i = \text{site})
$$

where \(I\) is an indicator function that equals 1 when the condition is true and 0 otherwise.

Aggregations are useful for identifying dominant launch sites, common orbit types, frequently used boosters, and historical success patterns.

## 7. Data Visualisation with Scatter Plots and Bar Charts

The project uses scatter plots and bar charts to visually explore relationships between variables.

**Scatter plots** are used when both variables are numerical, such as:

* Flight Number vs Payload Mass
* Flight Number vs Launch Outcome
* Payload Mass vs Landing Success

Each observation is represented as a point:

$$
(x_i, y_i)
$$

Scatter plots are useful for detecting trends, clusters, and outliers.

**Bar charts** are used for categorical comparisons, such as success rate by orbit or launch site. They are effective when comparing groups and identifying which categories have stronger or weaker landing outcomes.

## 8. Geospatial Analysis with Folium

The Folium notebook maps SpaceX launch sites using latitude and longitude coordinates. Launch sites and outcomes are displayed with markers, circles, and marker clusters.

A geographical point can be represented as:

$$
(\text{latitude}, \text{longitude})
$$

Distance analysis is used to estimate proximity between launch sites and nearby geographical or infrastructural features. A common spherical distance method is the Haversine formula:

$$
d = 2r \arcsin\left(\sqrt{\sin^2\left(\frac{\Delta \phi}{2}\right) + \cos(\phi_1)\cos(\phi_2)\sin^2\left(\frac{\Delta \lambda}{2}\right)}\right)
$$

where \(r\) is the Earth radius, \(\phi\) represents latitude, and \(\lambda\) represents longitude.

Geospatial analysis is useful when location affects operational strategy, safety, logistics, infrastructure access, or environmental risk.

## 9. Interactive Visual Analytics

The capstone project also uses interactive visual analytics to explore launch data dynamically. Interactive dashboards allow users to filter by launch site, inspect payload ranges, and compare landing outcomes visually.

This is useful when stakeholders need to explore data without editing code. Interactive tools help transform technical analysis into business-facing decision support.

## 10. Feature Matrix Preparation

Before machine learning, categorical variables are converted into numerical features and combined with numerical variables into a feature matrix:

$$
X = [x_1, x_2, \dots, x_p]
$$

The target variable remains the landing outcome:

$$
y \in \{0,1\}
$$

This structure allows classification algorithms to learn patterns that distinguish successful landings from unsuccessful ones.

## 11. Standardisation

The machine-learning notebook standardises numerical features so they have mean 0 and standard deviation 1:

$$
z = \frac{x - \mu}{\sigma}
$$

where \(x\) is the original value, \(\mu\) is the mean, and \(\sigma\) is the standard deviation.

Standardisation is especially important for distance-based and margin-based algorithms such as K-Nearest Neighbours and Support Vector Machines, because variables measured on larger scales can otherwise dominate the model.

## 12. Train-Test Split

The dataset is split into training and testing sets. The training set is used to fit the model, while the testing set is used to evaluate how well the model generalises to unseen data.

Conceptually:

$$
D = D_{train} \cup D_{test}
$$

This method is used to reduce overfitting and estimate real-world model performance.

## 13. Logistic Regression

Logistic Regression is a classification model used when the target variable is binary. It estimates the probability of a successful landing:

$$
P(y=1|X) = \frac{1}{1 + e^{-(\beta_0 + \beta_1x_1 + \dots + \beta_px_p)}}
$$

If the probability is above a chosen threshold, the model predicts success; otherwise, it predicts failure.

Logistic Regression is useful when interpretability matters and the relationship between features and the log-odds of the outcome is approximately linear.

## 14. Support Vector Machine

Support Vector Machine classifies observations by finding a decision boundary that separates classes with the largest possible margin.

For a linear SVM, the decision boundary can be written as:

$$
w^Tx + b = 0
$$

The model tries to maximise the margin between the two classes. SVMs are useful for classification problems where a clear separating boundary may exist, and kernel methods can extend them to non-linear cases.

## 15. Decision Tree Classifier

A Decision Tree splits the dataset into branches based on feature conditions. At each node, the model chooses the split that best separates the target classes.

One common splitting criterion is Gini impurity:

$$
Gini = 1 - \sum_{k=1}^{K} p_k^2
$$

where \(p_k\) is the proportion of observations belonging to class \(k\).

Decision Trees are useful because they are interpretable and can capture non-linear relationships between features and outcomes.

## 16. K-Nearest Neighbours

K-Nearest Neighbours classifies a new observation based on the majority class among its \(k\) closest neighbours.

A common distance metric is Euclidean distance:

$$
d(x,a) = \sqrt{\sum_{j=1}^{p}(x_j-a_j)^2}
$$

KNN is useful when similar observations are expected to have similar outcomes. Because it depends on distance, feature scaling is particularly important.

## 17. Hyperparameter Tuning with GridSearchCV

The machine-learning notebook uses GridSearchCV to test combinations of hyperparameters and select the best model settings.

For a set of candidate hyperparameters:

$$
\Theta = \{\theta_1, \theta_2, \dots, \theta_m\}
$$

GridSearchCV trains and evaluates models across these combinations using cross-validation. This helps avoid arbitrary parameter choices and improves model reliability.

## 18. Classification Metrics and Accuracy

Model performance is evaluated using accuracy and confusion matrices.

Accuracy is defined as:

$$
Accuracy = \frac{TP + TN}{TP + TN + FP + FN}
$$

where:

* \(TP\) = true positives
* \(TN\) = true negatives
* \(FP\) = false positives
* \(FN\) = false negatives

Accuracy is useful when classes are reasonably balanced, but it should be interpreted with the confusion matrix to understand the types of errors being made.

## 19. Confusion Matrix

A confusion matrix compares actual labels with predicted labels:

$$
\begin{bmatrix}
TN & FP \\
FN & TP
\end{bmatrix}
$$

In this project, it shows how many launches were correctly or incorrectly predicted as successful or unsuccessful landings. It is especially useful because false predictions can have important business implications when estimating launch cost and risk.

<h1 align="center"><i>Skills Demonstrated</i></h1>

* Collecting structured launch data from a public API.
* Scraping HTML tables from Wikipedia with BeautifulSoup.
* Cleaning, transforming, and preparing real-world datasets with pandas.
* Creating binary classification labels from raw outcome values.
* Performing exploratory data analysis with SQL queries.
* Using grouping, aggregation, filtering, and ranking to analyse launch records.
* Creating scatter plots and bar charts to study launch trends and success patterns.
* Building interactive geospatial maps with Folium.
* Analysing launch-site proximity to coastlines, transport infrastructure, and other landmarks.
* Preparing machine-learning feature matrices and target vectors.
* Standardising features before classification.
* Splitting data into training and testing sets.
* Training and comparing Logistic Regression, SVM, Decision Tree, and KNN classifiers.
* Using GridSearchCV for hyperparameter optimisation.
* Evaluating models with accuracy scores and confusion matrices.
* Translating technical results into a business-oriented capstone narrative.

<h1 align="center"><i>Technologies Used</i></h1>

<table align="center">
<tr>
<td>
<i>

* Python
* Jupyter Notebook / JupyterLite
* pandas
* NumPy
* requests
* BeautifulSoup
* SQL / SQL Magic
* IBM Db2
* Matplotlib
* Seaborn
* Folium
* Plotly Dash
* scikit-learn
* PowerPoint

</i>
</td>
</tr>
</table>

<h1 align="center"><i>Overall Summary</i></h1>

Together, these notebooks present the complete workflow of an applied data science capstone project. The analysis begins with data collection from the SpaceX API and Wikipedia, continues with data wrangling and exploratory analysis through pandas, SQL, visualisation, and geospatial mapping, and concludes with machine-learning models designed to predict Falcon 9 first-stage landing success.

The project demonstrates how public data can be transformed into actionable business insight. By studying launch sites, payload mass, orbit type, flight number, and historical landing outcomes, the notebooks show how data science can support cost estimation, launch-risk assessment, and strategic decision-making for a hypothetical competitor in the commercial space industry.

# Author
# ***[Matteo Meloni](https://www.linkedin.com/in/matteo-meloni-40a357154/)***
