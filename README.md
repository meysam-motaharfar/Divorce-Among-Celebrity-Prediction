# Divorce Rate among Celebrities

[[toc]]

# Introduction
## Section 1
### Subsection 1.1
## Section 2
# Conclusion

The goal of this project is to scrape data from wikipedia for celebrities around the world and then prepare it to build ML classifiers to predict the divorce rate among them. To this end, relevant data was scraped from table of content in wikipedia page of each celebrities. In fact, we scraped the data for actors/actress, singers, musicians, dancers, models, directors, photographers, journalists, playwrights, comedians and writers from following links:

[actress](https://en.wikipedia.org/wiki/Category:Film_actresses_by_nationality) 

https://en.wikipedia.org/wiki/Category:Male_film_actors_by_nationality (actors)

https://en.wikipedia.org/wiki/Category:Women_comedians_by_nationality (female comedians)

https://en.wikipedia.org/wiki/Category:Male_comedians_by_nationality (male comedians)

https://en.wikipedia.org/wiki/Category:21st-century_women_singers_by_nationality (female singers)

https://en.wikipedia.org/wiki/Category:21st-century_male_singers_by_nationality (male singers)

https://en.wikipedia.org/wiki/Category:21st-century_women_writers_by_nationality (female musicians)

https://en.wikipedia.org/wiki/Category:21st-century_male_singers_by_nationality (male musicians)

https://en.wikipedia.org/wiki/Category:Women_film_directors (female directors)

https://en.wikipedia.org/wiki/Category:Film_directors_by_nationality 

https://en.wikipedia.org/wiki/Category:21st-century_women_writers_by_nationality (female writes)

https://en.wikipedia.org/wiki/Category:21st-century_male_singers_by_nationality (male writers)

https://en.wikipedia.org/wiki/Category:Women_dramatists_and_playwrights_by_nationality (female playwrights)

https://en.wikipedia.org/wiki/Category:Male_dramatists_and_playwrights_by_nationality (male playwrights)

https://en.wikipedia.org/wiki/Category:Women_journalists_by_nationality (female journalists)

https://en.wikipedia.org/wiki/Category:Male_journalists_by_nationality (male journalists)

https://en.wikipedia.org/wiki/Category:Female_dancers_by_nationality (female dancers)

https://en.wikipedia.org/wiki/Category:Male_dancers_by_nationality (male dancers)

https://en.wikipedia.org/wiki/Category:Female_models_by_nationality (female models)

https://en.wikipedia.org/wiki/Category:Male_models_by_nationality (male models)

https://en.wikipedia.org/wiki/Category:Women_photographers_by_nationality (female photographers)

https://en.wikipedia.org/wiki/Category:Photographers_by_nationality 

a function is written to scrape name, date of birth, place of birth, date of death, place of death, name of spouse, date of marrige, date of divorce, number of marriage, number of divorce and number of marriages which ended in death for celebrities and also their spouses (see Data_Scraping_and_Data_Cleaing notebook for more details) while scraped data for each celebrities are in Data folder. Then data cleaning and feature engineering on data based on the current features was done. For example age, age at time of marriage, age at the time of divorce, age of spouse , age of spouse at the time of marriage, age of spouse at the time of divorce, duration of marriage and age difference were calculated. Moreover, some other features which describes the marriage was first marriage for both celebrities and their spouse (First_Marriage), spouse was also celebrity (Spouse_is_Celbrities), number of profession and we also find the latitude and longitude of the place of birth of celebrities and their spouses and corresponding geodistance were also added. Finally, I added some categorical features for being married or divorced and being alive or dead (see More_Data_Cleaning_and_Feature_Engineering for more details). Then, explatory data analysis was done in Explatory_Data_Analysis (EDA) notebook where one can find different plots for both continuous and categorical features. Based on these plot I selected relevant features to predict the divorce rate among celebrites. As a matter of fact, I selected number of children, number of children for spouse, sex, Age, age, age at the time of marriage, at of spouse, age at the time of marriage for spouse, age difference, numbe of roles, either the spouse is celebrities or not and geodistance. I used knn imputer to fill missing values in the dataset and then standardized the data and then build six different classifiers (Logistic Regression, KNN classifier, Support Vector Machine, Decision Tree classifier, Random Forest Classifier and XGBoost Classifier) to predict the divorce for each celebrites based on aforementioned features. Iterating over the number of neighbours for imputer, the best values based on the accuracy score was found. Finally, gridsearch was used to tune hyperparameters of each models to improve the accuracy. It was found that XGBoost classifier has the best accuracy for test dataset (see Building_ML_Models notebook for model building and results). 



