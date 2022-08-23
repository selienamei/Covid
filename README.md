# COVID-19: Which NYC counties are at high risk and what are the possible predictors. 
There are 2 goals in this project:
1. Develop models to accurately classify U.S. counties based on COVID positivity and fatality rates.
2. Identify predictors of COVID positivity and fatality rates in the U.S.

Datasets:
1. 2016 US Presidential Election Data, usa-2016-presidential-election-by-county.csv
2. [COVID data (2021) from opendatasoft](https://public.opendatasoft.com/explore/dataset/coronavirus-covid-19-pandemic-usa-counties/information/?disjunctive.province_state&disjunctive.admin2)

## Definitions

This project will classify in 2-class and 6-class. A column for Positivity Rate was added to the dataset. This value will be used to define classes for the data. 
The column was calculated as follows:
<br  />
<br  />
Positivity Rate = Confirmed Cases / Total Population
<br  />
<br  />
_2-Class Definition:_

The fields ‘high risk positivity ’ and ‘high risk fatality’ were created as a 2-class categorization for the data.
<br  />
Class 0: positivity/fatality rate less than or equal to the national average 
<br  />
Class 1: positivity/fatality rate greater than the national average
<br  />
<br  />

_6-Class Definition:_

The fields ‘risk level positivity’ and ‘risk level fatality’ were created as a 6-class categorization for the data.
<br  />
The six classes partition data by positivity/fatality rate based on thresholds of the average plus or minus 1 or 2 standard deviations.
<br  />
The fatality rate is noticeably less normally-distributed than the positivity rate, with the lowest class threshold falling below 0 and the class counts being less symmetric around the average.

## Methods
**Goal 1:**
Logistic Regression, SVM, Neural Network 

**Goal 2:**
Coefficient of the features

## Result 
### Goal 1: Develop models to accurately classify U.S. counties based on COVID positivity and fatality rates.

*highest percentage is highlighted below*

2-class:
<br  />
![alt text](https://github.com/selienamei/Covid/blob/main/images/2_class.JPG "Logo Title Text 1")
<br  />
6-class:
<br  />
![alt text](https://github.com/selienamei/Covid/blob/main/images/6_class.JPG "Logo Title Text 1")
<br  />
All three models perform very similarly across the board. The neural network performed the best or tied for best in 14 of 16 parameters in the summary. 

For 2-class positivity rate, the models are performed similarly for recall and F1-score as well, with the neural network performing slightly better than the other two models. However, the performance gap is not very large.

Model performance for positivity rate and fatality rate were close for 2-class and 6-class, with 2-class values around 0.7 and 6-class values around 0.5. The models did not seem to have more difficulty predicting positivity rate than fatality rate or vice versa. 

### Goal 2: Identify predictors of COVID positivity and fatality rates in the U.S.

Occupations in production, transportation, and material moving were associated with higher positivity rates, indicating that people who travel for their job are more likely to spread COVID. 

Age and diabetes are risk factors for fatality rate, but not positivity rate. This indicates that older, more sickly people are less likely to spread COVID , but more likely to die from COVID if they catch it. 

 Education level appears to be connected with COVID spread as several features with coefficients of greater magnitude in logistic regression were related to education (e.g. School Enrollment in Fatality, At least Bachelor’s Degree, Less Than High School Diploma and Graduate Degree in Positivity). 

The Gini Coefficient was also correlated with probability of being high risk for both positivity rate and fatality rate in binary classification, indicating that counties with greater income inequality are hit harder by COVID. 

The latitude and longitude of a county also were strongly relevant features for binary fatality rate classification, indicating that certain geographical regions are hit harder by COVID deaths. This makes intuitive sense, as a COVID breakout in one county would be likely to affect neighboring counties. 

Potential future steps would include redefining the multiclass in terms of percentiles instead of average and standard deviation. Defining classes in terms of percentiles would lead to more balanced classes which may improve model performance for multi-class classification. 





_This is a group project, I only have logistic regression code._
