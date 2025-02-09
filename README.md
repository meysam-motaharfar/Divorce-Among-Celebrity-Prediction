# Divorce Rate Among Celebrities

- [Project Description](#project-description)
- [Data Collection](#data-collection)
- [Data Cleaning and Feature Engineering](#data-cleaning-and-feature-engineeering)
- [Explatory Data Analysis (EDA)](#explatory-data-analysiseda)
- [Models Building and Results](#models-building-and-results)
- [Conclusion and Future Direction](#conclusion-and-future-direction)

# Project Description

The goal of this project is to scrape data from Wikipedia pages for celebrities around the world and then prepare it to build ML classifiers to predict the divorce rate among them. 

# Data Collection

To this end, relevant data was scraped from table of content in Wikipedia page of each celebrities. In fact, I scraped the data for [actress](https://en.wikipedia.org/wiki/Category:Film_actresses_by_nationality), [actors](https://en.wikipedia.org/wiki/Category:Male_film_actors_by_nationality), [female comedians](https://en.wikipedia.org/wiki/Category:Women_comedians_by_nationality), [male comedians](https://en.wikipedia.org/wiki/Category:Male_comedians_by_nationality), [female singers](https://en.wikipedia.org/wiki/Category:21st-century_women_singers_by_nationality), [male singers](https://en.wikipedia.org/wiki/Category:21st-century_male_singers_by_nationality), [female musicians](https://en.wikipedia.org/wiki/Category:21st-century_women_writers_by_nationality), [male musicians](https://en.wikipedia.org/wiki/Category:21st-century_male_singers_by_nationality), [female directors](https://en.wikipedia.org/wiki/Category:Women_film_directors), [male directors](https://en.wikipedia.org/wiki/Category:Film_directors_by_nationality) ,[female writes](https://en.wikipedia.org/wiki/Category:21st-century_women_writers_by_nationality), [male writers](https://en.wikipedia.org/wiki/Category:21st-century_male_singers_by_nationality), [female playwrights](https://en.wikipedia.org/wiki/Category:Women_dramatists_and_playwrights_by_nationality), [male playwrights](https://en.wikipedia.org/wiki/Category:Male_dramatists_and_playwrights_by_nationality), [female journalists](https://en.wikipedia.org/wiki/Category:Women_journalists_by_nationality), [male journalists](https://en.wikipedia.org/wiki/Category:Male_journalists_by_nationality), [female dancers](https://en.wikipedia.org/wiki/Category:Female_dancers_by_nationality), [male dancers](https://en.wikipedia.org/wiki/Category:Male_dancers_by_nationality), [female models](https://en.wikipedia.org/wiki/Category:Female_models_by_nationality), [male models](https://en.wikipedia.org/wiki/Category:Male_models_by_nationality), [female photographers](https://en.wikipedia.org/wiki/Category:Women_photographers_by_nationality), [male photographers](https://en.wikipedia.org/wiki/Category:Photographers_by_nationality). More accurately, a function was written to scrape name, date of birth, place of birth, date of death, place of death, name of spouse, date of marrige, date of divorce, number of marriage, number of divorce and number of marriages which ended in death for celebrities and also their spouses (see this [notebook](https://github.com/meysam-motaharfar/Divorce-Rate-among-Celebrities/blob/main/Notebooks/More_Data_Cleaning_and_Feature_Engineering.ipynb) for more details about data scraping) while scraped data can be found [here](https://github.com/meysam-motaharfar/Divorce-Rate-among-Celebrities/tree/main/Data). 

# Data Cleaning and Feature Engineeering

Then data cleaning and feature engineering on scraped data based on the current features was done. For instance, age, age at time of marriage, age at the time of divorce, age of spouse, age of spouse at the time of marriage, age of spouse at the time of divorce, duration of marriage and age difference were calculated using date of birth, date of death, date of marriage and date of divorce for both celebrity and their spouses. Moreover, other features were also extracred such as the marriage was first marriage for both celebrities and their spouse (First_Marriage), spouse was also celebrity (Spouse_is_Celbrities), number of unique professions and I also found the latitude and longitude of the place of birth of celebrities and their spouses and corresponding geodistance were added too. Finally, I added some categorical features for being married or divorced and being alive or dead (see this [notebook](https://github.com/meysam-motaharfar/Divorce-Rate-among-Celebrities/blob/main/Notebooks/More_Data_Cleaning_and_Feature_Engineering.ipynb) for more details) and while scraped data can be found [here](https://github.com/meysam-motaharfar/Divorce-Rate-among-Celebrities/tree/main/Data). Here is the data dictionary describing all the features in the dataset:

| Feature | Description 
| -------- | -------- 
| Name | Full name scraped from the table of content, otehrwise the name scraped from the Wikipedia list | 
| Date_of_Birth | date of birth for celebrity | 
| Place_of_Birth | place of birth for celebrity | 
| Date_of_Death| date of death for celebrity|
|Place_of_Death| place of death for celebrity|
|Name_of_Spouse| name of first spouse for celebrity|
|Date_of_Marriage|date of marriage|
|Date_of_Divorce|date of divorce|
|Number_of_Marriage|number of marriage for celebrity|
|NumbeR_of_Divorce|number of divorce for celebrity those ended in death are excluded|
|Number_of_Children|number of children for celebrity from all marriages|
|Marriages_End_in_Death|number of marriages which ended in death not divorce either the death of celebrity or their spouses|
| Date_of_Birth_Spouse | date of birth for spouse of celebrity | 
| Place_of_Birth_Spouse | place of birth for spouse of celebrity | 
| Date_of_Death_Spouse| date of death for spouse of celebrity|
|Place_of_Death_Spouse| place of death for spouse of celebrity|
|Name_of_Spouse_Spouse| name of first spouse for spouse of celebrity|
|Number_of_Marriage_Spouse|number of marriage for spouse of celebrity|
|NumbeR_of_Divorce_Spouse|number of divorce for spouse of celebrity those ended in death are excluded|
|Number_of_Children_Spouse|number of children for sposue of celebrity from all marriages|
|First_Marriage|check that the marriage of both celebrity and their spouses is the first marriage or not|
|Sex|sex|
|Age|age of celebrity|
|Age_at_Marriage| age of celebrity at the time of marriage|
|Age_at_Divorce|age of celebrity at the time of first divorce|
|Age_of_Spouse| age of spouse of celebrity|
|Age_at_Marriage_Spouse| age of sposue of celebrity at the time of marriage|
|Age_at_Divorce_Spouse|age of sposue of celebrity at the time of first divroce|
|Duration_of_Marriage|duration of first marriage|
|Age_Difference|age difference|
|Number_of_Roles|number of unique professions|
|Profession|name of unique profession which celebrity has|	
|Spouse_is_Celebrity|checking that the spouse is also celebrity if his/her name is also in the Name column |
|Married	|married or not|
|Divorced	|divorced or not|
|Alive_or_Dead	| alive or dead|
|Alive_or_Dead_Spouse	|alive or dead spouse|
|Latitude	|latitude for the place of birth of celebrity|
|Longitude	|longitude for the place of birth of celebrity|
|Latitude_Spouse	|latitude for the place of birth for sposue of celebrity|
|Longitude_Spouse	|longitude for the place of birth of spouse of celebirty|
|Distance|geodistance between the place of birth of celebrity and their spouses|


# Explatory Data Analysis(EDA)

Locating the place of birth for each celebrity on world map results in the following figure:

![al](https://github.com/meysam-motaharfar/Divorce-Rate-among-Celebrities/blob/main/Figs/Distribution_of_Celebrities.png)

from which one can clearly see that the number of celebrities are denser in US, Europe and india and that might be related to the fact these place have strong media and so there are more information about celebrities from these countries. 


# Models Building and Results

Based on explatory data analysis, I selected relevant features to predict the divorce rate among celebrites. As a matter of fact, I selected number of children, number of children for spouse, sex, age, age at the time of marriage, age at of spouse, age at the time of marriage for spouse, age difference, numbe of roles, either the spouse is celebrities or not and geodistance. Since the dataset is not large enough, I used knn imputer to fill missing values in the dataset and then standardized the data before spliting to training and test sets and then build six different classifiers (Logistic Regression, KNN classifier, Support Vector Machine, Decision Tree classifier, Random Forest Classifier and XGBoost Classifier) to predict the divorce for each celebrites based on aforementioned features. Iterating over the number of neighbours for imputer, the best number of beighbors based on the accuracy score was found. Finally, gridsearch was used to tune hyperparameters of each models to improve the accuracy. It was found that XGBoost classifier has the best accuracy among others for test dataset (see this [notebook](https://github.com/meysam-motaharfar/Divorce-Rate-among-Celebrities/blob/main/Notebooks/Building_ML_Models.ipynb) for more details). Here are the results in nutshell:

![GitHub Logo](https://github.com/meysam-motaharfar/Divorce-Rate-among-Celebrities/blob/main/Figs/divorce_prediction_results.png)

# Conclusion and Future Direction

In this project, the divorce among celebrities was predicted by scraping data from wikipedia pages. However, given the age of celebrities at hand, one can also build a regression model to predict the age of celebrities based on the scraped data and also figure out is there any connection between the marital status of celebrities and their life expectancy. 







