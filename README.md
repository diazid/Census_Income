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
* `fnlwgt`: continuous.
* `education`: Bachelors, Some-college, 11th, HS-grad, Prof-school, Assoc-acdm, Assoc-voc, 9th, 7th-8th, 12th, Masters, 1st-4th, 10th, Doctorate, 5th-6th, Preschool.
* `education-num`: continuous.
* `marital-status`: Married-civ-spouse, Divorced, Never-married, Separated, Widowed, Married-spouse-absent, Married-AF-spouse.
* `occupation`: Tech-support, Craft-repair, Other-service, Sales, Exec-managerial, Prof-specialty, Handlers-cleaners, Machine-op-inspct, Adm-clerical, Farming-fishing, Transport-moving, Priv-house-serv, Protective-serv, Armed-Forces.
* `relationship`: Wife, Own-child, Husband, Not-in-family, Other-relative, Unmarried.
* `race`: White, Asian-Pac-Islander, Amer-Indian-Eskimo, Other, Black.
* `sex`: Female, Male.
* `capital-gain`: continuous.
* `capital-loss`: continuous.
* `hours-per-week`: continuous.
* `native-country`: United-States, Cambodia, England, Puerto-Rico, Canada, Germany, Outlying-US(Guam-USVI-etc), India, Japan, Greece, South, China, Cuba, Iran, Honduras, Philippines, Italy, Poland, Jamaica, Vietnam, Mexico, Portugal, Ireland, France, Dominican-Republic, Laos, Ecuador, Taiwan, Haiti, Columbia, Hungary, Guatemala, Nicaragua, Scotland, Thailand, Yugoslavia, El-Salvador, Trinadad&Tobago, Peru, Hong, Holand-Netherlands.
* `class`: >50K, <=50K

Target variable will be `class`

## Explanatory Analysis

### Age histogram and Boxplot

![](/img/age_histogram_age_boxplot.jpg)

* The age distribution is right skewed
* Median age = 37

### ![](/img/correlation_plot.jpg)

* The variables in general doesn't have correlation with each other and with the target variable. 

### Age vs FNLWGT per class

![](/img/age_vs_fnlwgt_per_class.jpg)

* The line plot shows the aggregation over multiple `y` values at each value of `x` and shows an estimate of the central tendency (mean in this case) and a confidence interval for that estimate.
* Then, we see that in both classes the central tendency look similar except on extreme values
* The histogram shows a concentration in the botton left on both graphs

### Age vs Hours per Weed per Class

![](/img/age_vs_hours-per-week_per_class.jpg)

* In avarege people of `>50K` works more thatn the people `<=50K` in every age.
* The histogram shows that also people despite there are people that works a few hours, and other works lots of hours, there are concentration between 40 and 50 hours for the people in the class `>50K`