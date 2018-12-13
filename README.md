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

Even with the nuanced approach of the PMT, accuracy (among of metrics) remains a problem. As the Latin American population grows and poverty declines, reorientation of the PMT is necessary. The [Inter-American Development Bank](https://www.iadb.org) (IDB) has launched a public Kaggle competition to improve the PMT. The IDB is branching away from traditional econometrics in an effort to attain better, more reliable predictions. 

Beyond Costa Rica, many countries face this same problem of inaccurately assessing social need. If Kagglers can generate an improvement, the new algorithm could be implemented in other countries around the world.

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

___ 
## Feature Engineering

___ 
## Considerations

___
## Model Results

___
## Acknowledgments and References
- [Will Koehrsen](https://www.kaggle.com/willkoehrsen/a-complete-introduction-and-walkthrough)
  - Will's detailed exploratory analysis and modeling were helpful for building my understanding of the data.
