## Table of contents
* Title
* Overview
* Checking missing values
* Kaplan Meier
* Random Forest
# IMPACT OF SURVIVED SPOUSE GENDER ON DAYS TO BURIAL OF DECEASED
## Overview
The following tools were used:
* Python programming language.
* Pandas library.
* Sklearn library.
* Lifelines library.
* Kaplan Meier plots.
* Random forest classifier algorithm.

## Missing values
* The Obituaries dataset was imported and previewed using the top 5 rows.
With the focus of my study being on “the impact that the gender of the spouse will have on the number of days taken from death to burial of the deceased”, the dataframe was sliced to have the appropriate attributes. Thereafter, missing values were checked and filled as per the mode of the dataframe features. This was to make sure that the imputed values lied within the distribution of the general data. 
* The data types were then converted appropriately. Since it would be a classification kind of study, converting objects to categories and numerical data type was appropriate. 
#### Box Plot of Days to Burial:
The box plot was used to check for the outlying “Death_to_Burial” values as follows:
![Box Plot of Days to Burial](https://github.com/JOEL-OSEBE/SURVIVAL/blob/master/output_19_0.png)
* Since this attribute is the number of days from death to burial, having a negative number of days would be inapplicable, and assuming them into positive values would impact on the accuracy of the results. Therefore, I truncated the negative values below zero and used the new dataframe for the Kaplan-Meier survival curve. 
Below is the box plot after the truncation of negative values.
#### Box Plot after Truncation:
![Box Plot after Truncation](https://github.com/JOEL-OSEBE/SURVIVAL/blob/master/output_21_0.png)
## KAPLAN-MEIER
* The survival analysis conducted was on the impact that the deceased spouse’s gender will have on the number of days taken to bury an individual. Labels of Spouse_gender were encoded into 1 and 0 i.e. Male = 1 , Female = 0. This was to work with the lifelines Kaplan Meier library. 
Setting the Death_to_Burial attribute as the duration parameter and observation of the event being the gender of the spouse, I plotted the Kaplan Meier curve respectively to the gender as follows:
#### Kaplan Meier Plot for Surviving Female Spouse:
![Kaplan Meier Plot for Female Spouse](https://github.com/JOEL-OSEBE/SURVIVAL/blob/master/output_39_0.png)
#### Kaplan Meier Plot for Surviving Male Spouse:
![Kaplan Meier Plot for Male Spouse](https://github.com/JOEL-OSEBE/SURVIVAL/blob/master/output_39_1.png)
* Below is a comparison of the two observations as per the plot below:
#### COMPARISON OF KAPLAN MEIER PLOTS BY SURVIVING SPOUSE GENDER:
![Comparison of Kaplan Meier Plots Per Gender](https://github.com/JOEL-OSEBE/SURVIVAL/blob/master/output_40_0.png)
* The result shows that there is a higher probability for the deceased survived by a male spouse to be buried after a longer time than the ones that are survived by female spouses
 The result shows that the probability that a survived male spouse would bury their deceased loved ones after a long time is higher as compared to the survived female spouses. 
* For example, the probability of burial after 20 days for the survived female spouses is < 0.2, while for survived male spouses is > 0.2.
# RANDOM FOREST CLASSIFIER
* Three algorithms of classification which are logistic regression, decision tree classifier, and random forest classifier were considered. 
Among these, the random forest classifier algorithm that had the higher accuracy score of 0.78 was selected to predict the burial events that would need fundraising.
The following is the resultant cross tabulation table:
##### Cross Tabulation Table
![Cross Tabulation table](https://github.com/JOEL-OSEBE/SURVIVAL/blob/master/Screenshot%20(33).png)
* In this study, our dependent variable that is to be predicted is the fundraising attribute. Considering the fundraising attribute, the presence of entries with missing values were sliced and used as the predicted dataframe or else be in the original training dataframe. The train dataframe was then used to train the model.
* To avoid overfitting, cross-validation was performed by splitting the original train dataframe further into the actual train and validation test dataframes then trained the model while setting the number of trees (n_estimators) to 500 to increase the accuracy of the model. Thereafter, the fundraising attribute from the original test dataframe was predicted.
