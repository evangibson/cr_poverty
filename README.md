# Costa Rican Household Poverty Level Prediction
A folder for the [Inter-American Development Bank's 2018 Costa Rican Household Poverty Prediction Challenge](https://www.kaggle.com/c/costa-rican-household-poverty-prediction)

Author: Evan Gibson

___ 
## Table of Contents (ReadMe)
- [Summary](https://github.com/evangibson/cr_poverty#summary)
- [File Descriptions](https://github.com/evangibson/cr_poverty#file-descriptions)
- [Exploratory Analysis](https://github.com/evangibson/cr_poverty/blob/master/README.md#exploratory-analysis)
- [Feature Engineering](https://github.com/evangibson/cr_poverty#feature-engineering)
- [Considerations](https://github.com/evangibson/cr_poverty#considerations)
- [Model Results](https://github.com/evangibson/cr_poverty#model-results)
- [Acknowledgments and References](https://github.com/evangibson/cr_poverty#acknowledgments-and-references)

## Summary

Social programs have a hard time making sure the right people are given enough aid. It makes sense for these programs to establish thresholds for aid "worthiness." Income/expense measurements provide the standard baseline for credit worthiness in most parts of the world. But how can aid programs develop practical criteria when members of their target populations frequently lack "acceptable" income/expense verification? The least affluent members of any society often lack robust income/expense records; therefore, those individuals have a hard time proving that they qualify for certain aid programs. 

Microfinance organizations around the world have spent years developing "just right" methods to determine how their funds should be allocated. To make things difficult for those organizations, the poorest segment of any population experiences especially acute outlier circumstances. From income level to the number of mobile phones, the variability of descriptive characteristics among those who occupy the poorest level of society is staggering. In Latin America, one popular method utilizes a unique algorithm to verify income qualification using measurable characteristics outside of income/expense records. It’s called the Proxy Means Test (or PMT). With PMT, agencies use a model that considers a family’s observable household attributes like the material of their walls and ceiling, or the assets found in the home to classify them and predict their level of need.

Even with the nuanced approach of the PMT, accuracy (among other metrics) remains a problem. As the Latin American population grows and poverty declines, reorientation of the PMT is necessary. The [Inter-American Development Bank](https://www.iadb.org) (IDB) has launched a public Kaggle competition to improve the PMT. The IDB is branching away from traditional econometrics in an effort to attain better, more reliable predictions. 

Beyond Costa Rica, many countries face this same problem of inaccurately assessing social need. 

The present repository will address the following:
  - Detail the author's exploration of the given data.
  - Attempt to tune an alternative PMT model.
  - Investigate the PMT as a concept for the betterment of development practices.

___ 
## File Descriptions
- simple_predictions [(Folder)](https://github.com/evangibson/cr_poverty/tree/master/simple_predictions)
  - All of the enclosed models are the simplest versions of their title purpose. As they contain little parameter tuning, feature engineering, and data considerations, they are most useful for orienting oneself to classifier models that could work for this project and for understanding the focus of the competition. 
- images [(Folder)](https://github.com/evangibson/cr_poverty/tree/master/images)
  - This folder contains PNG images that are used in the README
- [Exploratory Analysis.ipynb](https://github.com/evangibson/cr_poverty/blob/master/Exploratory%20Analysis.ipynb)
  - This notebook is used for the exploration of the poverty dataset. It contains descriptive charts and is here to explain some of the nuance within our research context.
- [Random Forest and Decision Tree Models.ipynb](https://github.com/evangibson/cr_poverty/blob/master/Random%20Forest%20and%20Decision%20Tree%20Models%20(Tuned).ipynb)
  - This file contains tuned Random Forest and Decision Tree models. This file also contains details for visualizing a single tree of a random forest or a decision tree.
___ 
## Exploratory Analysis

Without understanding the data we will use, we cannot hope to derive meaningful, scalable predictions. 

The training data contains 143 "unique" variables. For comparison, the test data contains 142 variables. The only difference between the variables in the two files are in the presence of the `Target` column. The following details some of the most important characteristics of both sets:

| Data Set        | Train           | Test  |
| ------------- |:-------------:| :-----:|
| Participants      | 9,557 | 23,856 |
| Households      | 2,988      |   7,352 |
| Mean Income `v2a1` |   165231.6    |    174872.6 |
| Refrigerator Ratio `refrig` | 0.96 | 0.96 |
| Mean Education `meaneduc`| 9.23      | 9.15 |
| Gender Proportion  `male` |   0.48    |    0.49 |
| Household Size `hhsize` |   x    |    x |
| Head of Household Education `edjefe` | x | x |
| Head of Household Education `edjefa` | x | x |
| Mean Age `age` |   34.3    |    34.5 |

In all, the training and test sets are reasonably
___ 
## Feature Engineering

Of all the variables included in the present data, there were few that related composite details concerning an individual's household. For instance, the variable `qmobilephone` indicates the number of mobile phones in a given individual's household. However, feature engineering is required to run a model that considers the proportion of mobile phones per household to a household size (`phones_per_person_household`). The following illustrates how the author engineered the `qmobilephone`/`hhsize` feature for modeling:

```python
df_train['phone_per_person_household'] = df_train['qmobilephone']/df_train['hhsize']
```

As it turns out, the `phone_per_person_household` variable ended up being one of the most important variables in the models in which it was employed. By engineering custom features, we can focus modeling efforts to deal with unique variable combinations. In addition to `phone_per_person_household`, the author engineered 40 other variables. 

Most of the engineered variables were built to clarify relationships throughout households. By clarifying the experience an individual has within their immediate familial context, we can better understand our data.

The author also built variables that consolidated some of the underrepresented groups under the assumption that the dimensionality of certain groups do not effectively add insight to the data. For example, the author combined the `techozinc`, `techoentrepiso`, `techocane`, and `techootro` variables into `roof_waste_material` because the materials noted in those "techo..." variables are waste materials. It may be the case that the impacts each of the roofing variables has on `Target` is similiar in characteristic, meaning that the most salient fact about all the people who fall into those groups is that they have roofs made of _waste_ materials. 
___ 
## Considerations

___
## Model Results

| Model    | Random Forest (Tuned)   | Random Forest (Simple)  | Decision Tree (Simple) | Decision Tree (Tuned) | Gradient Boosting |
| ------    |:-----------------------:| :----------------------:| :---------------------:| :--------------------:|:-----------------:|
| Accuracy  |      **95.71**                |     91.79           |  91.68                |       86.72     |       88.65        |
| Macro F1  |      **0.930**     |         0.874             |       0.875                |      0.796          |       0.839          |
| Weighted F1  |      **0.956**         |     0.915          |       0.917           |           0.867       |            X    |

In the most relevant metrics of evaluation, the present random forest model (tuned) performed the best. 
___
## Acknowledgments and References
- [Will Koehrsen](https://www.kaggle.com/willkoehrsen/a-complete-introduction-and-walkthrough)
  - Will's detailed exploratory analysis and modeling were helpful for building my understanding of the data.
