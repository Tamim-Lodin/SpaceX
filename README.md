# SpaceX
# IBM-Data-Science-Capstone-SpaceX

## Overview

![](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DS0701EN-SkillsNetwork/api/Images/landing_1.gif)

## Background
SpaceX is at the forefront of the space industry, aiming to make space travel accessible to all. Their achievements include launching spacecraft to the International Space Station, deploying a satellite constellation for internet access, and conducting crewed missions. The company’s innovative approach to reusing the first stage of the Falcon 9 rocket enables them to offer launches at a competitive cost of $62 million, compared to over $165 million from other providers. By predicting whether the first stage will land successfully, we can better assess launch pricing. This project leverages public data and machine learning to forecast whether SpaceX or its competitors can achieve a successful first-stage recovery.

## Investigation
* Analyze how payload mass, launch site, flight frequency, and orbits impact first-stage landing success.
* Examine trends in successful landings over time.
* Identify the most effective predictive model for determining landing success (binary classification).

## Executive Summary
This study aims to pinpoint the factors that contribute to a successful rocket landing. The methodologies employed include:
* **Data Collection:** Utilizing the SpaceX REST API and web scraping methods.
* **Data Wrangling:** Preparing the data to define success and failure outcomes.
* **Data Exploration:** Visualizing data to assess factors like payload, launch site, flight count, and yearly trends.
* **Data Analysis:** Employing SQL to compute key statistics: total payload, payload range for successful launches, and counts of successes and failures.
* **Geographical Analysis:** Evaluating launch site success rates relative to geographic features.
* **Data Visualization:** Mapping successful launch sites and their corresponding payload ranges.
* **Model Building:** Developing models to predict landing outcomes using logistic regression, SVM, decision trees, and KNN.

## Results

### Exploratory Data Analysis:
* Launch success rates have increased over time.
* KSC LC-39A recorded the highest landing success rate among launch sites.
* Orbits ES-L1, GEO, HEO, and SSO achieved a 100% success rate.

### Visualization / Analytics:
* Most launch sites are positioned near the equator, and all are located close to coastlines.

### Predictive Analytics:
* All models showed similar performance on the test data, with the decision tree model showing a slight edge in terms of .best_score_.

# Methodology

## Data Collection - API
* **Request data** from the SpaceX API for rocket launch information.
* **Decode the response** with .json() and convert it into a dataframe using .json_normalize().
* **Gather launch details** through custom API functions.
* **Construct a dictionary** from the gathered data.
* **Create a dataframe** from the dictionary.
* **Filter for Falcon 9 launches only** and replace any missing Payload Mass values with the mean.
* **Export the data** to a CSV file.

## Data Collection - Web Scraping
* **Fetch Falcon 9 launch data** from Wikipedia.
* **Generate a BeautifulSoup object** from the HTML response.
* **Extract column names** from the HTML table header.
* **Parse HTML tables** to collect the data.
* **Construct a dictionary** and create a dataframe.
* **Export this data** to a CSV file.

## Data Wrangling
* **Encode outcomes** as 1 for successful landings and 0 for unsuccessful ones.

## Exploratory Data Analysis with Visualization
* **Generate charts** to examine relationships and comparisons.

## Exploratory Data Analysis with SQL
* **Query the dataset** for deeper insights.

## Mapping with Folium
* **Create maps** to visualize launch sites, their outcomes, and distances to key geographic features.

## Dashboard with Plotly Dash
* **Develop a dashboard** featuring:
  * A pie chart of successful launches.
  * A scatter plot comparing Payload Mass against Success Rate by Booster Version.

## Predictive Analytics
* **Create a NumPy array** from the Class column.
* **Standardize the data** using StandardScaler, then fit and transform it.
* **Split the data** into training and testing sets.
* **Utilize GridSearchCV** with cv=10 for optimizing parameters across various algorithms: logistic regression, SVC, decision tree, and KNN.
* **Evaluate accuracy** on the test data and assess confusion matrices for all models.
* **Identify the best-performing model** using metrics like Jaccard Score, F1 Score, and accuracy.

# Conclusion
* **Model Performance:** All models performed similarly, with the decision tree model slightly outperforming others.
* **Geographical Factors:** Most launch sites are located near the equator, leveraging the Earth's rotational speed to reduce fuel costs.
* **Coastal Proximity:** All launch sites are situated near coastlines.
* **Increasing Launch Success:** Success rates have improved over time.
* **KSC LC-39A:** Holds the highest success rate, particularly for launches under 5,500 kg.
* **Orbits:** ES-L1, GEO, HEO, and SSO have maintained a 100% success rate.
* **Payload Mass Impact:** Higher payload masses correlate with higher success rates across all launch sites.

## Additional Considerations
* **Dataset Expansion:** A larger dataset could enhance predictive analytics and the generalizability of findings.
* **Feature Analysis / PCA:** Conducting further feature analysis or principal component analysis may improve model accuracy.
* **Exploration of XGBoost:** Investigating the performance of XGBoost could yield insights into its efficacy compared to the models used in this study.
