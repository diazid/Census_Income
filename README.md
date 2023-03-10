# Census Income

By: Israel Diaz

email: idiazg@udd.cl

## Project Description

### 1. Source: [UCI -  Census Income Data Set](http://archive.ics.uci.edu/ml/datasets/Census+Income)

US Census Bureau.

### 2. Description of the Data: 

Extraction was done by Barry Becker from the 1994 Census database.  A set of reasonably clean records was extracted using the following conditions:

`((AAGE>16) && (AGI>100) && (AFNLWGT>1)&& (HRSWK>0))`

* `age`: continuous.
* `workclass`: Private, Self-emp-not-inc, Self-emp-inc, Federal-gov, Local-gov, State-gov, Without-pay, Never-worked.
* `fnlwgt`: The number of people the census takers believe that observation represents. continuous.
* `education`: The highest level of education achieved for that individual. This is nominal attribute. The ordered levels of the attributes: Preschool < 1st-4th < 5th-6th < 7th-8th < 9th < 10th < 11th < 12th < HS-grad < Prof-school < Assoc-acdm < Assoc-voc < Some-college < Bachelors < Masters < Doctorate.
* `education-num`: Highest level of education in numerical form. This is continuous attribute.
* `marital-status`: Married-civ-spouse, Divorced, Never-married, Separated, Widowed, Married-spouse-absent, Married-AF-spouse.
* `occupation`: Tech-support, Craft-repair, Other-service, Sales, Exec-managerial, Prof-specialty, Handlers-cleaners, Machine-op-inspct, Adm-clerical, Farming-fishing, Transport-moving, Priv-house-serv, Protective-serv, Armed-Forces.
* `relationship`: Wife, Own-child, Husband, Not-in-family, Other-relative, Unmarried.
* `race`: White, Asian-Pac-Islander, Amer-Indian-Eskimo, Other, Black.
* `sex`: Female, Male.
* `capital-gain`: Capital gains recorded. continuous.
* `capital-loss`: Capital Losses recorded. continuous.
* `hours-per-week`: continuous.
* `native-country`: United-States, Cambodia, England, Puerto-Rico, Canada, Germany, Outlying-US(Guam-USVI-etc), India, Japan, Greece, South, China, Cuba, Iran, Honduras, Philippines, Italy, Poland, Jamaica, Vietnam, Mexico, Portugal, Ireland, France, Dominican-Republic, Laos, Ecuador, Taiwan, Haiti, Columbia, Hungary, Guatemala, Nicaragua, Scotland, Thailand, Yugoslavia, El-Salvador, Trinadad&Tobago, Peru, Hong, Holand-Netherlands.
* `class`: >50K, <=50K

### Description of fnlwgt (final weight)

The weights on the CPS files are controlled to independent estimates of the civilian noninstitutional population of the US. These are prepared monthly for us by Population Division here at the Census Bureau.  We use 3 sets of controls.

These are:
1.  A single cell estimate of the population 16+ for each state.
2.  Controls for Hispanic Origin by age and sex.
3.  Controls by Race, age and sex.

We use all three sets of controls in our weighting program and "rake" through them 6 times so that by the end we come back to all the controls we used. The term estimate refers to population totals derived from CPS by creating "weighted tallies" of any specified socio-economic characteristics of the population.

People with similar demographic characteristics should have similar weights.  There is one important caveat to remember about this statement.  That is that since the CPS sample is actually a collection of 51 state samples, each with its own probability of selection, the statement only applies within state.

### Target
Prediction task is to determine whether a person makes over 50K a year.

## Explanatory Analysis

### ![](/img/correlation_plot.jpg)

* The variables in general have a very low correlation with each other and with the target variable. 

### Age vs Capital Gain per class

![](/img/age_vs_fnlwgt_per_class.jpg)

* The line plot shows the aggregation over multiple `y` values at each value of `x` and shows an estimate of the central tendency (mean in this case) and a confidence interval for that estimate.
* In <=50K class capital-gain averages seems pretty low, near 0, on the contrary with >50K that has variability in the averages.
* The histogram shows a concentration in the botton left on both graphs

### Age vs Hours per Weed per Class

![](/img/age_vs_hours-per-week_per_class.jpg)

* In avarege people of `>50K` works more thatn the people `<=50K` in every age.
* The histogram shows that also people despite there are people that works a few hours, and other works lots of hours, there are concentration between 40 and 50 hours for the people in the class `>50K`

## MODEL PERFORMANCE

I executed 3 model: 

* Logistic Regresion
* KNN Classifier
* XGBoost.

and I had these results:

**Logistic Regresion**
* Accuracy: .80
* Precision: .55
* Recall: .83

**KNN**
* Accuracy: .79
* Precision: .55
* Recall: .70

**XGBoost**
* Accuracy: .82
* Precision: .59
* Recall: .76

The three models did it bad in precision, very low precision, but if we see at accuracy and recall, Logistic Performed better.

I am giving importance to recall because is telling me how many of the of the positive cases were predicted correctly over all the positive. This is very important if I am trying to predict who is waging more than 50K a year, I want to predict this value correctly.

After PCA, I got these results:

**Logistic Regression With PCA**
* Accuracy = .79
* Precision = .54
* Recall = .84

The model performed better without PCA.

## RECOMMENDATION

Despite PCA is a powerful tool for avoiding overfiting, in this case, it didn't add performance to the model. I recomend the Logistic Regression without the PCA.