![Python 3.8](https://img.shields.io/badge/python-3.8-green.svg)

# Geo Reviews Dataset 2023
Dataset Description:

    500,000 unique reviews
    Reviews exclusively for organizations in Russia
    Available on Yandex Maps
    Published from January to July 2023
    The dataset excludes short single-word reviews
    Texts are cleansed of personal information (phone numbers, email addresses)

Dataset Composition:

The dataset in tskv format includes the following information:

    Organization's address (address)
    Organization name (name_ru)
    List of categories to which the organization belongs (rubrics)
    User rating from 0 to 5 (rating)
    Review text (text)


## Baselines & Results
We have implemented several baseline models; 

F1-weighted is the base metric for evaluating the balanced precision and recall in multi-class classification tasks, providing a harmonized measure that considers the impact of class imbalance on overall model performance

Test results:

| Model | F1-weighted | time |
| ------ | :------: | :------: |
|MultinomialNB | 0.75 | **3.98 s** | 
|SVM | 0.77 |  32.05/49.40  | 
|LogisticRegression | 0.78  |  3min 13s  |
|CatBoost | 0.78  |   41min 31s  |
|LSTM | 0.78  |   41min 31s  |
|RuBERT | 39.54/62.29 | 18.55/34.22 | 
|RuPoolBERT | 47.45/70.44 | 34.94/52.05 | 
|RuBioBERT* | 43.55/68.86 | 28.94/44.55 |
|RuBioRoBERTa* | 46.72/72.87 | **44.01/58.95** |
|Human | 25.06/48.54 | 7.23/12.53 | **93.36** | 
