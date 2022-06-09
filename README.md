# Multitask Baseline Performance Evaluation
A notebook that computes, visualizes, and saves the basline performance of multiple classical Machine Learning Algorithms using the DementiaBank dataset. The full 
explanation is found directly in the notebook, togheter with some numerical results.

## Prerequisites
### Data
The data that must be used is the output of my previous project [Dementia Features Extractor](https://github.com/EdoStoppa/Dementia_Features_Extractor).
In particular, both the full dataset and the feature group datasets will be needed. The names and the path of each folder are configurable in the "Preliminary Section"
of the notebook, but the standard (and tested) configuration is this:
```
'Project Folder'
│
├── baseline_performance.ipynb
│
└── data/
    ├── feature_dataset.csv
    └── separate_datasets/
        ├── acoustic_info.csv
        ├── anagraphic_info.csv
        ├── discourse_info.csv
        ├── lexicosyntactic_info.csv
        ├── psycholinguistic_info.csv
        └── spatial_info.csv
```
While running the notebook another folder will be created (in the main directory) containing the verbose results of all executions.

### Imports
To run the notebook these libraries must be installed:
- numpy
- pandas
- matplotlib
- sklearn

## High Level Overview
The objective of this notebook is to have some `basline performance` using the DementiaBank dataset that we could use later to compare our results using Graph
Machine Learning.<br /><br />
The task that we explored are:
- `Binary Classification`: A conversation is related to a patient with Dementia or to a Control Patient
- `Multi class Classification`: Each class is the level of Dementia showed by the patient (No Dementia, Possible Dementia, Mild Dementia, Dementia, Severe Dementia)
- `Regression`: The target is the MMSE score (on a scale from 0 to 30)

Furthermore, it's interesting to understand the `performance impact of each feature group`. Thus, partial datasets are created: each one of those has all the features,
excepts the ones of a specific category. So, we have a dataset without Acoustic Features, a dataset without Spatial Features, etc... This showed us the impact of
each feature group on the total performance level.

Each evaluation is done using 5-fold cross validation to strenghten the results.

## Conclusions
After completing all the tests, we can say for certainty 3 things:
- `Boosted Trees are the best` performer in all tasks
- `Removing Acoustic features` almost always lead to a performance increase. This is probably related to the `extremely high dimensionality` of that feature group (170
  features of the total 350 are acoustic)
- The only task were a passable results is achieved is Binary Classification. For `both Regression and Multi class Classification` the baseline `performances are
  extremely low`. Thus, we hope that Graph Machine Learning could help achieve better results


