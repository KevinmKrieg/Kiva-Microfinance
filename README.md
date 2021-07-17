# Kiva Microfinance Loan Funding
![cover_photo](preview_logo_1.jpg)
*Microfinance has become a common tool to provide funding to those without access to formal banking or credit, primarily in developing countries. Loan recipients often borrow in groups, and use the funds for a variety of reasons, from education, to business inventory, to home construction costs. One microfinance institution, Kiva, has become popular by allowing people from around the world to act as the lenders for these small, short term loans. Loan seekers on Kiva create funding pages with descriptions of their life, family, location, and use case for the funds. This project will look at a large sample of Kiva loan requests, and try to predict whether a request will be funded, based on the features of the loan request and the loan seeker.*

## 1. Data

The dataset is a snapshot of all Kiva loan requests, downloaded on 3/15/2021.

> * [Kiva's Website](https://www.kiva.org/build/data-snapshots)


## 2. Data Wrangling 

[Data Wrangling Notebook](https://github.com/KevinmKrieg/Kiva-Microfinance/blob/6ca681986b3c9301d83c15ac3a47fa373ae4d729/data_wrangling.ipynb)

* **1:** The data downloaded from the snapshot was generally pretty clean already. There were aroundn 36,000 rows with 1 or more missing values. Due to the size of data present in the snapshot, these rows were simply dropped. 

* **2:** The pycountry library was used to map countries to their respective continent, for use as features later on  [pycountry library](https://pypi.org/project/pycountry/)


## 3. EDA

* **1:** The data is highly unbalanced, with over 1.8 million instances of successfully funded loan requests, and just over 90,000 expried (unfunded) loan requests. Below is a look at the the highest percentage of unfunded loans in each of variables within the data.

[EDA Notebook](https://github.com/KevinmKrieg/Kiva-Microfinance/blob/1d2b2b34ceadcf891af66a5adb389cf4108cbb32/exploratory_data_analysis.ipynb)


![k](funding_proportions.png)

## 4. Feature Engineering

[Feature Notebook](feature_engineering.ipynb)

The OneHotEncoder package was used to make binary dummy variabbles for the top 5 most frequently appearing categories within the secotr, language, currency & country features. Additionally, dummy variabbles were created for the gender of the borrower, the number of people seeking the loan, whether the loan request had a. picture of the borrower included, and the repayment method. The resulting data set contains 39 different features, as well as the funding status of each loan.

[OneHotEncoder Library](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.OneHotEncoder.html)


## 5. Modeling

*Two different algorithm were used to build classifiers for loan funding status.
 *[XGBoost](https://xgboost.readthedocs.io/en/latest/python/python_api.html)
 *[Random Forest Classifier](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html)

*As stated previously, the class sizes here are very unbalanced. Therefore, a variety of techniques were used to try and prevent the model from simply predicting the dominant (funded) class in each prediction.
 *Over & Under sampling with the [SMOTE package from imblearn library](https://imbalanced-learn.org/stable/references/generated/imblearn.over_sampling.SMOTE.html)
 



[Final Predictions Notebook](modeling.ipynb)


![]()

## 6. Future Improvements

* The biggest challenge for this project was the imbalanced class sizes, future imporvement in data collection could include obtaining more "unfunded" loans, instead of relying on artifical over/under sampling techniques. Additionally, more information about loan seekers could be collected to improve predictive power, such as the history of the loan seeker (previous loan amounts/time/repayment status etc). Finally, other machine learning methods such as deep learning may be able to more accurately capture the differences between these 2 classes. 
